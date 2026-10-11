# free-git — Gitea + Runner + Mirror + Cloudflare Tunnel

Self-hosted Git at `https://free-git.org`, deployed as one Compose project, backed up here, run in Arcane.

| Service | Image | Exposed as |
|---|---|---|
| `server` (Gitea) | `docker.gitea.com/gitea:1` + `postgres:16-alpine` | `https://free-git.org` via Tunnel |
| `runner` (Gitea Actions) | `gitea/runner:latest-dind` | internal, registers to Gitea |
| `mirror` (gitea-mirror) | `ghcr.io/raylabshq/gitea-mirror:latest` | `https://mirror.free-git.org` via Tunnel |
| `tunnel` | `cloudflare/cloudflared:latest` | token from Zero Trust dashboard |

## 1. Cloudflare Tunnel (one-time)

1. Domain `free-git.org` nameservers → Cloudflare.
2. Zero Trust → Networks → Tunnels → Create tunnel `free-git` (connector `cloudflared`) → copy token.
3. Public Hostnames:
   - `free-git.org` → `http://server:3000`
   - `mirror.free-git.org` → `http://mirror:4321`
4. TLS: Full (Strict if origin has cert — not needed, cloudflared terminates at edge).

## 2. Local run

```bash
cp .env.example .env   # then fill in real secrets
docker compose config  # validate
docker compose up -d db server
# open https://free-git.org, create admin
# Gitea Admin → Actions → Runners → copy token → put in .env as RUNNER_TOKEN
docker compose up -d runner mirror tunnel
docker compose ps
```

Mirror setup: open `https://mirror.free-git.org`, first signup = admin, add GitHub source token + Gitea dest `http://server:3000` (internal DNS) + Gitea token. Start with a manual mirror, then enable `SCHEDULE_ENABLED` if desired.

## 3. Notes / limits

- Compose publishes `3001`/`4321` on `127.0.0.1` only. Public traffic comes through the Tunnel container on the same `free-git` network.
- Git SSH (`2222:22`) is LAN-only. Cloudflare Tunnel forwards HTTP(S); SSH needs separate `cloudflared access ssh` setup. Use HTTPS clone URLs remotely.
- Runner uses DIND (`privileged: true`). If the host forbids privileged, use `gitea/runner:latest` + `- /var/run/docker.sock:/var/run/docker.sock` (less isolated).
- `ROOT_URL=https://free-git.org/` must be set before first boot; changing it later requires editing `app.ini` inside `gitea-data`, not just env.

## 4. Data backup (not in git)

Git stores config only. Volumes (`pgdata`, `gitea-data`, `runner-data`, `mirror-data`) hold data. Example nightly backup:

```bash
docker compose exec db pg_dump -U gitea gitea > backup-$(date +%F).sql
docker compose exec server sh -c 'gitea dump -c /data/gitea/conf/app.ini -t /tmp && ls /tmp/*backup*.zip'
```

## 5. Import into Arcane (http://192.168.31.147:3552/)

1. Arcane → Customization → Git Repositories → Add `https://github.com/Heretek-AI/free-git`, branch `main`.
2. Projects → Create ▼ → From Git Repo → Pull: name `free-git`, path `compose.yaml`, ON `Sync Files` + `Redeploy After Sync`.
3. Project → Environment Configuration: paste `POSTGRES_PASSWORD`, `RUNNER_TOKEN`, `CLOUDFLARE_TUNNEL_TOKEN`, `BETTER_AUTH_SECRET`, `ENCRYPTION_SECRET`.
4. Deploy. Edit config in GitHub → Sync from Git in Arcane (Pull projects are read-only in Arcane).
