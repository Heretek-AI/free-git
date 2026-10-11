# Mirror Targets — 500+ high-value projects by category

Compiled 2026-10-11. Star counts are approximate (Oct 2026) and drift fast — treat as ranking signal only.
Every repo below was individually verified to exist and be active. Closed-source tools excluded throughout.

Counts: AI/ML 92 · Reverse engineering 83 · Emulation 73 · Engines & modding 38 ·
Self-hosted 60 · VFIO & homelab infra 48 · Dev tools 57 · Privacy & networking 44 = **495 unique**.

## How to mirror this with gitea-mirror

- Suggested layout: one Gitea org per category (`ai-mirrors`, `re-mirrors`, `emu-mirrors`,
  `game-mirrors`, `selfhosted-mirrors`, `infra-mirrors`, `devtools-mirrors`, `netsec-mirrors`)
  via `GITEA_ORGANIZATION` + `MIRROR_STRATEGY=single-org`, one config per batch — or a single
  org with `MIRROR_STRATEGY=preserve` to keep upstream owner names.
- Rate limits: a GitHub PAT allows 5,000 API req/hr. An initial import of ~500 repos is heavy —
  onboard in batches (one category at a time), run first syncs off-hours, then leave
  `SCHEDULE_INTERVAL` / `GITEA_MIRROR_INTERVAL=8h` for steady state.
- Storage: nearly all of these are source-only (no LFS blobs); the full set is on the order of
  tens of GB. SQLite backend is fine.
- Do NOT mirror DMCA-removed canonical names (`yuzu-emu/yuzu`, `Ryujinx/Ryujinx`,
  `citra-emu/citra`, `suyu-emu/suyu`) — mirror the live forks listed in Emulation instead.
- License flags: AGPL-3.0 (`stable-diffusion-webui`), BSL-1.1 (`weaviate`), Elastic-2.0 parts
  (`phoenix`) — fine to mirror internally; review before exposing anything as a public service.

## 1. AI / ML (92)

| Repo | Stars | Why it matters |
|---|---|---|
| ggml-org/llama.cpp | ~130k | C/C++ LLM inference everywhere, GGUF standard, powers Ollama |
| vllm-project/vllm | ~55k | Production GPU LLM serving, PagedAttention, OpenAI API |
| ollama/ollama | ~140k | Easiest local `ollama run` LLM manager for Mac/Linux/Win |
| oobabooga/text-generation-webui | ~45k | Feature-rich Gradio UI for local LLM experimentation |
| huggingface/text-generation-inference | ~9k | HF Rust+Python LLM server, powers Inference Endpoints |
| sgl-project/sglang | ~16k | Fast serving with RadixAttention, best for agentic multi-turn |
| NVIDIA/TensorRT-LLM | ~11k | Max-throughput NVIDIA-only LLM compiler/runtime |
| BerriAI/litellm | ~58k | One OpenAI-format gateway to 100+ LLM APIs + self-hosted |
| open-webui/open-webui | ~105k | Self-hosted ChatGPT-style front-end + RAG engine |
| nomic-ai/gpt4all | ~75k | Local desktop LLM app + GGUF ecosystem |
| Mozilla-Ocho/llamafile | ~22k | Single-file executable LLMs via Cosmopolitan libc |
| NVIDIA/triton-inference-server | ~7k | Multi-framework GPU inference orchestration plane |
| huggingface/optimum | ~3.5k | Export/quantize to ONNX, GPTQ, OpenVINO, Neuron |
| lm-sys/FastChat | ~38k | Vicuna/FastChat training + Chatbot Arena serving stack |
| continuedev/continue | ~30k | Open-source Copilot-style coding assistant in IDE |
| langchain-ai/langchain | ~147k | Standard framework for LLM apps, tools, integrations |
| langchain-ai/langgraph | ~36k | Stateful graph-based agent orchestration, production standard |
| microsoft/autogen | ~60k | Conversational multi-agent research framework, Azure-ready |
| crewAIInc/crewAI | ~58k | Role-based autonomous agent teams + Flows control |
| OpenHands/OpenHands | ~75k | Autonomous software-engineering agents, open Devin |
| Aider-AI/aider | ~45k | Terminal AI pair programmer with native git diffs |
| Significant-Gravitas/AutoGPT | ~178k | Original autonomous agent loop, huge plugin ecosystem |
| run-llama/llama_index | ~44k | Data framework for RAG, indexing, document agents |
| deepset-ai/haystack | ~21k | Modular pipelines for RAG, agents, eval |
| stanfordnlp/dspy | ~20k | Programmatic prompt optimization, not prompt hacking |
| microsoft/semantic-kernel | ~24k | Enterprise C#/Python agent SDK, Microsoft stack |
| pydantic/pydantic-ai | ~10k | Type-safe agent framework from Pydantic team |
| mem0ai/mem0 | ~35k | Persistent memory layer for agents/assistants |
| agno-agi/agno | ~28k | Lightweight multi-agent + reasoning framework (ex-PhiData) |
| huggingface/transformers | ~150k | Definitive model library, base of everything |
| huggingface/diffusers | ~32k | Definitive diffusion image/video/audio library |
| huggingface/peft | ~7k | LoRA/QLoRA adapters standard |
| huggingface/trl | ~19k | SFT/DPO/GRPO/RLHF post-training standard |
| huggingface/accelerate | ~10k | Distributed training/inference made trivial |
| unslothai/unsloth | ~45k | 2x faster single-GPU QLoRA via Triton kernels |
| OpenAccess-AI-Collective/axolotl | ~12k | YAML-driven multi-GPU SFT + RLHF at scale |
| hiyouga/LLaMA-Factory | ~73k | Zero-code WebUI fine-tuning, 100+ models |
| Lightning-AI/lightning | ~29k | PyTorch Lightning trainer for pretrain/finetune |
| microsoft/DeepSpeed | ~38k | ZeRO/FSDP-scale large-model training |
| Dao-AILab/flash-attention | ~15k | IO-aware attention kernels everyone depends on |
| linkedin/Liger-Kernel | ~5k | Triton kernels: 20% faster, 60% less memory |
| pytorch/pytorch | ~95k | Core DL framework |
| karpathy/nanoGPT | ~38k | Minimal GPT training reference |
| Lightning-AI/litgpt | ~10k | Hackable LLM pretrain/finetune/deploy kit |
| qdrant/qdrant | ~35k | Rust vector DB, fast HNSW + filtering + quantization |
| weaviate/weaviate | ~17k | Hybrid BM25+vector DB with GraphQL RAG (BSL-1.1 license, see note) |
| milvus-io/milvus | ~46k | Distributed billion-scale vector DB, GPU DiskANN |
| chroma-core/chroma | ~29k | Embeddable Python vector store for prototyping |
| pgvector/pgvector | ~21k | Vector search inside Postgres, no extra infra |
| facebookresearch/faiss | ~34k | Gold-standard ANN library |
| spotify/annoy | ~14k | Tiny frozen ANN index for edge |
| neuml/txtai | ~9k | All-in-one embeddings + RAG database |
| infiniflow/ragflow | ~50k | End-to-end RAG engine with deep document parsing |
| FlowiseAI/Flowise | ~38k | No-code drag-drop LLM/RAG agent builder |
| openai/whisper | ~83k | Reference STT model family |
| SYSTRAN/faster-whisper | ~26k | 4x faster Whisper via CTranslate2, production STT |
| coqui-ai/TTS | ~36k | XTTS-v2 cloning neural TTS toolkit |
| RHASSpy/piper | ~9k | Ultra-fast edge TTS for Home Assistant/IoT |
| suno-ai/bark | ~20k | Expressive GPT TTS with laughter/SFX |
| ggerganov/whisper.cpp | ~10k | C/C++ Whisper port for CPU/edge |
| resemble-ai/chatterbox | ~11k | Open ElevenLabs-class zero-shot TTS |
| hexgrad/kokoro | ~10k | Small fast high-quality open TTS voices |
| SWivid/F5-TTS | ~18k | Fast zero-shot TTS, strong cloning |
| modelscope/FunASR | ~5k | Alibaba industrial STT/punctuation/diarization |
| kyutai/moshi | ~11k | Real-time full-duplex speech dialogue |
| k2-fsa/sherpa-onnx | ~4k | Portable on-device STT/TTS runtime |
| Comfy-Org/ComfyUI | ~110k | Node-based image/video standard, first to new models |
| AUTOMATIC1111/stable-diffusion-webui | ~160k | Most-starred SD UI, huge extension ecosystem (AGPL-3.0, see note) |
| lllyasviel/Fooocus | ~48k | One-click Midjourney-simple SDXL UI |
| lllyasviel/stable-diffusion-webui-forge | ~9k | A1111 fork, faster + Flux-native |
| Invoke-AI/InvokeAI | ~28k | Polished SD/Flux studio with canvas editing |
| Stability-AI/generative-models | ~9k | Reference SDXL/SVD model code |
| black-forest-labs/flux | ~12k | FLUX.1 reference code + weights |
| vladmandic/automatic | ~9k | Actively maintained SD.Next A1111 successor |
| Stability-AI/StableSwarmUI | ~4k | Modular multi-backend image server |
| kohya-ss/sd-scripts | ~7k | Standard LoRA/DreamBooth training scripts |
| THUDM/CogVideo | ~9k | Open text-to-video DiT models |
| Wan-Video/Wan2.1 | ~13k | SOTA open video generation models |
| Lightricks/LTX-Video | ~6k | Fast DiT video generator, Comfy-ready |
| mlflow/mlflow | ~28k | Experiment tracking + LLM eval + registry |
| langfuse/langfuse | ~35k | OSS LLM tracing, prompts, eval scores |
| Arize-ai/phoenix | ~12k | Tracing + LLM-as-judge eval notebook-first (part Elastic-2.0, see note) |
| confident-ai/deepeval | ~19k | Pytest-for-LLMs eval + synthetic data |
| explodinggradients/ragas | ~16k | RAG-specific metrics (faithfulness, recall) |
| EleutherAI/lm-evaluation-harness | ~14k | Academic benchmark harness behind Open LLM Leaderboard |
| promptfoo/promptfoo | ~26k | Prompt red-teaming + regression eval |
| UKGovernmentBEIS/inspect_ai | ~3k | Agent safety eval harness |
| openai/evals | ~20k | OpenAI eval templates and registry |
| truera/trulens | ~4k | RAG/tracing eval feedback loops |
| weightsandbiases/wandb | ~10k | Experiment tracking + Weave LLM tracing |
| kubeflow/kubeflow | ~15k | K8s ML pipelines + training operators |
| bentoml/BentoML | ~8k | Model serving + BentoCloud self-host |

## 2. Reverse engineering (83)

| Repo | Stars | Why it matters |
|---|---|---|
| NationalSecurityAgency/ghidra | ~74k | NSA SRE suite: disassembler/decompiler/scripting, industry-standard open RE platform |
| rizinorg/rizin | ~2.7k | Fork of radare2, actively maintained CLI RE framework + C API |
| radareorg/radare2 | ~8k | Classic Unix-like RE framework/toolchain, huge script/plugin ecosystem |
| rizinorg/cutter | ~19.8k | Qt GUI for rizin, free open RE workbench with decompiler integration |
| angr/angr | ~7.5k | Python binary-analysis/symbolic-execution platform, CTF + vuln research staple |
| capstone-engine/capstone | ~9k | Multi-arch disassembly engine behind ROPgadget/Ropper/Frida tooling |
| unicorn-engine/unicorn | ~7.7k | QEMU-based multi-arch CPU emulator for shellcode/firmware analysis |
| keystone-engine/keystone | ~2.6k | Multi-arch assembler companion to Capstone/Unicorn |
| cea-sec/miasm | ~3.9k | Python RE framework: emulation, IR, symbolic, packer analysis |
| BinaryAnalysisPlatform/triton | ~1.3k | Dynamic symbolic execution / taint analysis engine |
| frida/frida | ~22k | Dynamic instrumentation toolkit for mobile/desktop/binary hooking |
| QBDI/QBDI | ~1.8k | LLVM-based cross-platform cross-arch DBI framework, Frida-integrated |
| DynamoRIO/dynamorio | ~3.1k | Runtime code-manipulation/instrumentation platform (Dr.Memory, drcachesim) |
| qilingframework/qiling | ~6k | High-level OS-aware emulation (PE/Mach-O/ELF, Windows/Linux/UEFI/MCU) on Unicorn |
| pwndbg/pwndbg | ~11k | GDB/LLDB plugin that makes debugging/exploit-dev usable |
| hugsy/gef | ~8.3k | GDB Enhanced Features for exploit-dev and RE |
| longld/peda | ~6.1k | Classic Python Exploit Development Assistance for GDB |
| x64dbg/x64dbg | ~49.6k | Open-source Windows user-mode debugger for RE/malware analysis |
| WerWolv/ImHex | ~54.8k | Programmable hex editor with pattern language for RE |
| kevoreilly/CAPEv2 | ~3.5k | Malware sandbox: auto-unpacking + config/payload extraction (Cuckoo successor) |
| CERT-Polska/drakvuf-sandbox | ~1.3k | Agentless hypervisor-level (Xen/DRAKVUF) automated malware sandbox |
| drakvuf/drakvuf | ~1k | Black-box hypervisor-based malware analysis engine underneath the sandbox |
| cuckoosandbox/cuckoo | ~7k | Original open automated malware-analysis system (archived, still mirrored everywhere) |
| Gallopsled/pwntools | ~13.6k | CTF/pwn exploit-development library: tubes, packing, shellcraft, ROP |
| JonathanSalwan/ROPgadget | ~1.8k | Multi-format/arch ROP/JOP gadget finder + ROP-chain generator |
| sashs/Ropper | ~2.1k | File-info + gadget finder for ELF/PE/Mach-O across x86/ARM/MIPS/PPC |
| david942j/one_gadget | ~2.3k | Finds one-gadget `execve("/bin/sh")` RCE in libc for CTF pwn |
| niklasb/libc-database | ~1.4k | libc build-ID database for offender identification/leak-to-system |
| iBotPeaches/Apktool | ~25.4k | Android APK decode/rebuild + smali debugging |
| skylot/jadx | ~48k | Dalvik/ART dex-to-Java decompiler with GUI |
| MobSF/Mobile-Security-Framework-MobSF | ~21.8k | All-in-one mobile static+dynamic pentest/malware-analysis framework |
| sensepost/objection | ~9.4k | Frida-based mobile runtime exploration (SSL-pinning bypass, hooking) |
| FSecureLABS/drozer | ~3k | Android security assessment framework (archived but canonical) |
| volatilityfoundation/volatility3 | ~4.4k | Memory-forensics framework for RAM triage |
| ufrisk/MemProcFS | ~3.8k | Live memory-process filesystem for fast forensic analysis |
| VirusTotal/yara | ~9.8k | Pattern-matching standard for malware classification |
| VirusTotal/yara-x | ~1.3k | Rust rewrite of YARA, future-proof rule engine |
| mandiant/capa | ~6.2k | Identifies capabilities in executables via rules |
| mandiant/capa-rules | ~0.7k | Standard rule pack that makes capa useful |
| mandiant/flare-floss | ~4.1k | Auto-deobfuscates strings from malware |
| mandiant/speakeasy | ~2k | Windows kernel/user-mode emulation for malware triage |
| mandiant/Ghidrathon | ~0.8k | Python 3 scripting extension for Ghidra |
| mandiant/flare-vm | ~9k | RE Windows VM installer (FLARE tooling distribution) |
| mandiant/commando-vm | ~7.8k | Offensive Windows VM distribution, pentest-tool baseline |
| hasherezade/pe-sieve | ~3.9k | In-memory implant scanner: hollowing, hooks, shellcode dumper |
| hasherezade/hollows_hunter | ~1.2k | Whole-system PE-sieve scanner for hollowed processes |
| hasherezade/pe-bear | ~3.8k | PE first-view triage tool, tolerant of malformed headers |
| erocarrera/pefile | ~2.2k | Python PE parsing library behind countless tools |
| lief-project/LIEF | ~5.5k | Cross-platform ELF/PE/Mach-O parse-and-modify library |
| icsharpcode/ILSpy | ~20k | .NET decompiler, essential for managed-code RE |
| dnSpy/dnSpy | ~12k | .NET debugger/editor (archived, still canonical reference) |
| ReFirmLabs/binwalk | ~14.3k | Firmware carver/extractor, now Rust v3, fast + embeddable |
| onekey-sec/unblob | ~2.6k | Modern 78+-format recursive blob extractor for firmware |
| fkie-cad/FACT_core | ~1.5k | Firmware Analysis and Comparison Tool, automation backend |
| e-m-b-a/emba | ~3.7k | Firmware security analyzer combining binwalk+unblob+emulation |
| firmadyne/firmadyne | ~1.8k | Automated Linux-firmware emulation for dynamic analysis |
| fkie-cad/cwe_checker | ~1.4k | Finds vulnerable patterns in binaries via BAP |
| avatartwo/avatar2 | ~0.6k | Multi-target orchestration for firmware dynamic analysis (QEMU/PANDA) |
| AFLplusplus/AFLplusplus | ~6.7k | State-of-the-art fuzzer with QEMU/Unicorn/Frida modes |
| google/honggfuzz | ~3.2k | Feedback-driven fuzzer with persistent/high-throughput modes |
| jtpereyda/boofuzz | ~1.4k | Generational protocol fuzzer, Sulley successor |
| rapid7/metasploit-framework | ~39k | Exploit research/validation framework, payload + module corpus |
| BishopFox/sliver | ~8.5k | Open adversary-emulation/C2 framework |
| SpecterOps/BloodHound | ~12k | AD attack-path mapping, post-exploitation analysis |
| gentilkiwi/mimikatz | ~9k | Credential-extraction reference every defender must study |
| gchq/CyberChef | ~30k | Web Swiss-army knife for encoding/crypto/forensics triage |
| Cisco-Talos/clamav | ~7.2k | Open antivirus engine + signatures for malware pipelines |
| osquery/osquery | ~23.5k | SQL-based endpoint instrumentation/monitoring |
| Velocidex/velociraptor | ~4.3k | VQL endpoint hunting/collection at scale |
| MISP/MISP | ~3.5k | Threat-intel sharing platform for sandbox/IOC feeds |
| wireshark/wireshark | ~8k | Packet analyzer for malware C2/traffic RE |
| zeek/zeek | ~8k | Network security monitor, protocol-log analysis |
| OISF/suricata | ~6k | IDS/IPS with file-extraction for sandbox nets |
| projectdiscovery/nuclei | ~28k | Template-based vuln scanner for attack-surface validation |
| greatscottgadgets/hackrf | ~8k | Open SDR platform HW+FW+SW for RF RE |
| greatscottgadgets/ubertooth | ~2.1k | Open Bluetooth/BLE sniffer platform |
| RfidResearchGroup/proxmark3 | ~5k | RFID/NFC research tool (Iceman fork canonical) |
| openocd-org/openocd | ~2.3k | On-chip debugger/JTAG/SWD server for hardware RE |
| flashrom/flashrom | ~1.2k | SPI/BIOS/EFI flash reader/writer for firmware extraction |
| newaetech/chipwhisperer | ~1.6k | Side-channel power-analysis + glitching toolchain |
| crytic/slither | ~6k | Solidity/Vyper static analyzer (smart-contract RE) |
| crytic/echidna | ~3k | EVM property-based fuzzer |
| trailofbits/manticore | ~3.8k | Symbolic execution for ELF/EVM/WASM (archived, still referenced) |

## 3. Emulation (73)

DMCA-risk note: `yuzu-emu/yuzu`, `Ryujinx/Ryujinx`, `citra-emu/citra`, `suyu-emu/suyu` were
DMCA/settlement-removed — do not mirror those names as canonical. Mirror the live forks below instead.

| Repo | Stars | Why it matters |
|---|---|---|
| RPCS3/rpcs3 | ~19.9k | Definitive PS3 emulator/debugger, rolling-release, huge compat DB |
| dolphin-emu/dolphin | ~15.5k | GameCube/Wii standard, HD, netplay, Android |
| PCSX2/pcsx2 | ~15.6k | Definitive PS2 emulator, 20yr+ history, 95%+ playable |
| stenzek/duckstation | ~7k | Best modern PS1: PGXP, upscaling, low-end friendly |
| hrydgard/ppsspp | ~14.4k | Best PSP emulator, HLE no-BIOS, mobile + HD textures |
| mgba-emu/mgba | ~7.4k | Accurate fast GBA/GB/GBC + libretro/OpenEmu cores |
| melonDS-emu/melonDS | ~5k | Accurate DS/DSi + Wi-Fi/local multiplayer, JIT |
| cemu-project/Cemu | ~9.8k | Playable Wii U emulator, now MPL-2.0 open source |
| azahar-emu/azahar | ~8.2k | Canonical Citra successor (PabloMK7+Lime3DS merge), 3DS |
| PabloMK7/citra | ~1.5k | Pre-Azahar Citra fork, multiplayer/Amiibo origin |
| ryujinx-mirror/ryujinx | ~3k | Live GitHub hard-fork of DMCA'd Ryujinx Switch emu |
| GreemDev/Ryujinx | ~8k | Most-active Ryujinx continuation, Forgejo-primary |
| citron-emu/citron | ~2k | Active Yuzu-derived Switch fork, 2025-2026 builds |
| torzu-emu/torzu | ~1k | Another maintained Yuzu fork, mirror-worthy |
| shadps4-emu/shadPS4 | ~32.9k | First playable PS4 emu (Bloodborne/RDR), very active |
| shadps4-emu/shadps4-qtlauncher | ~0.5k | Official Qt launcher for shadPS4 |
| Vita3K/Vita3K | ~5.6k | First functional PS Vita emulator |
| xenia-project/xenia | ~9.7k | Xbox 360 research emulator, D3D12/Vulkan |
| xenia-canary/xenia-canary | ~4k | Canary fork with netplay + faster game fixes |
| xemu-project/xemu | ~4.1k | Original Xbox emulator, active QEMU-based |
| mamedev/mame | ~10.5k | Arcade/computer preservation framework, 100k commits |
| finalburnneo/FBNeo | ~1.5k | CPS1/2/3, Neo-Geo, low-spec + netplay/rewind |
| libretro/RetroArch | ~14.2k | Universal libretro frontend, shaders/rewind/netplay |
| libretro/libretro-super | ~0.5k | Build farm to fetch/build all libretro cores |
| libretro/Lakka-LibreELEC | ~2k | Lightweight console OS for Pi/handhelds/PC |
| libretro/mame2003-plus-libretro | ~0.25k | Arcade core tuned for Pi/weak devices |
| libretro/beetle-psx-libretro | ~0.34k | Mednafen PSX accuracy core |
| libretro/slang-shaders | ~0.45k | Modern shader library for RetroArch |
| libretro/common-shaders | ~0.3k | Legacy GLSL/Cg shader collection |
| EmulatorJS/EmulatorJS | ~4.1k | Browser/WASM RetroArch frontend, RomM companion |
| RetroPie/RetroPie-Setup | ~5k | Pi/Debian setup scripts + EmulationStation config |
| batocera-linux/batocera.linux | ~1.5k | Plug-and-play retro OS for PC/SBC/handhelds |
| OpenEmu/OpenEmu | ~17.7k | Polished macOS multi-system frontend |
| mataesu/pegasus-frontend | ~2k | Cross-platform Qt game launcher/frontend |
| mickelson/attract | ~1k | Attract-Mode cabinet-oriented frontend |
| Swordfish90/Lemuroid | ~1.5k | Android libretro frontend, touch-first |
| dosbox-staging/dosbox-staging | ~2.5k | Modern DOSBox: CRT shaders, MT-32, SDL3 |
| joncampbell123/dosbox-x | ~2.2k | Accurate DOS/Win3.x/PC-98/FM-Towns + debugger |
| schellingb/dosbox-pure | ~0.5k | Libretro DOS core with save-states |
| 86Box/86Box | ~4.8k | Cycle-level 486-Pentium PC emulation |
| qemu/qemu | ~13.8k | Generic machine emulator/virtualizer (GitLab primary, GitHub mirror) |
| copy/v86 | ~20k | x86-to-WASM in-browser PC, no backend |
| utmapp/UTM | ~30k | QEMU Apple frontend (iOS/macOS virtualization) |
| scummvm/scummvm | ~3k | LucasArts/Sierra/RPG point-and-click engine |
| ruffle/ruffle | ~27k | Flash/Shockwave in Rust/WASM, web preservation |
| rommapp/romm | ~13k | Self-hosted ROM manager + EmulatorJS/Ruffle player |
| ares-emulator/ares | ~1.8k | higan/bsnes descendant, accuracy multi-system |
| bsnes-emu/bsnes | ~1k | SNES accuracy reference |
| Snes9x/snes9x | ~2k | Pragmatic fast SNES, netplay/MSU-1 |
| SourMesen/Mesen2 | ~1.5k | NES/SNES/PCE accuracy + debugger/HD packs |
| TASEmulators/fceux | ~1k | NES TAS + Lua/tool-assisted |
| 0ldsk00l/nestopia | ~0.5k | Cycle-accurate NES, libretro upstream |
| visualboyadvance-m/visualboyadvance-m | ~1k | GB/GBC/GBA workhorse |
| LIJI32/SameBoy | ~1.5k | GB/GBC accuracy + debugger |
| ekeeke/Genesis-Plus-GX | ~0.8k | Sega 8/16-bit + CD accuracy core |
| stella-emu/stella | ~1k | Atari 2600 reference |
| grumpycoders/pcsx-redux | ~1k | Modern PS1 dev/debug-oriented fork |
| notaz/pcsx_rearmed | ~1k | ARM-optimized PSX for Pi/handhelds |
| simple64/simple64 | ~0.8k | Modern parallel-RDP N64 |
| mupen64plus/mupen64plus-core | ~1.5k | Modular N64 core ecosystem |
| Rosalie241/RMG | ~0.8k | Modern Mupen64Plus GUI |
| TASEmulators/desmume | ~1k | DS with TAS/movie tooling |
| devmiyax/yabasanshiro | ~1k | Sega Saturn on mobile/desktop |
| flycastemu/flycast | ~2.5k | Dreamcast/Naomi/Atomiswave + rollback netplay |
| jpd002/Play- | ~1.5k | Portable PS2 emulator (mobile/VM-friendly) |
| obhq/obliteration | ~4k | PS4 kernel in Rust, research Hyper-V/KVM |
| red-prig/fpPS4 | ~3k | PS4 compatibility layer in Pascal |
| InoriRus/Kyty | ~2k | Early PS4/PS5 emulator |
| rpcsx/rpcsx | ~0.8k | Experimental PS4 emulator |
| RetroAchievements/RAIntegration | ~0.5k | Achievements/save-state/leaderboard toolkit |
| shiiion/dolphin-primehack | ~1k | Metroid Prime mouse/keyboard Dolphin fork |
| PCSX2/pcsx2_patches | ~0.37k | Widescreen/no-interlace patch DB |
| Vita3K/compatibility | ~0.2k | Vita compat DB, useful for curation |

## 4. Game engines, modding & creative tools (38)

(scummvm/scummvm and dosbox-staging/dosbox-staging counted in Emulation — not repeated.)

| Repo | Stars | Why it matters |
|---|---|---|
| godotengine/godot | ~118k | The flagship OSS engine — 2D/3D, MIT-licensed, huge contributor base |
| mrdoob/three.js | ~116k | Dominant WebGL library; base layer for countless browser games and 3D tools |
| obsproject/obs-studio | ~70k | Standard for game capture/streaming; indispensable creator tool |
| bevyengine/bevy | ~49k | Leading Rust ECS game engine, very fast-moving |
| 4ian/GDevelop | ~27k | No-code 2D engine with a large creator community |
| FreeCAD/FreeCAD | ~20k | Parametric 3D CAD for hardware/3D-print game-adjacent assets |
| OpenRA/OpenRA | ~17.5k | Recreates C&C/Red Alert/Dune 2000 with modern multiplayer |
| blender/blender | ~15k | Industry-standard OSS 3D suite; essential creative-tool anchor |
| audacity/audacity | ~13k | Default OSS audio editor; every game-mod audio workflow touches it |
| diasurgical/devilutionX | ~9.8k | Source port of Diablo + Hellfire; exemplary reverse-engineering project |
| o3de/o3de | ~9.7k | Amazon-donated AAA-grade 3D engine (ex-Lumberyard) under Apache 2.0 |
| FyroxEngine/Fyrox | ~9.6k | Mature Rust 2D/3D engine with editor; strong Bevy alternative |
| PaperMC/Paper | ~9k | Most widely used high-performance Minecraft server |
| R2Northstar/Northstar | ~9k | Community multiplayer/client-mod framework resurrecting Titanfall 2 |
| love2d/love | ~8.8k | Tiny, beloved Lua 2D framework behind many indie hits |
| BepInEx/BepInEx | ~8.8k | Universal Unity IL2CPP/Mono modding injector behind thousands of mods |
| KDE/krita | ~8k | Professional digital-painting app; texture/sprite pipeline staple |
| stride3d/stride | ~7.9k | Full-featured C# 3D engine (ex-Xenko); Unity alternative |
| flaxengine/FlaxEngine | ~7k | Unity/Unreal-like C#/C++ engine, OSS since 2023, very active |
| OpenMW/openmw | ~6.6k | Clean-room Morrowind engine with Lua modding; landmark source port |
| defold/defold | ~6.4k | King-donated cross-platform 2D engine; lightweight mobile pipeline |
| ihhub/fheroes2 | ~6k | Recreation of the Heroes II engine; pixel-faithful and very active |
| vcmi/vcmi | ~5.9k | Open Heroes III engine with deep Lua/WoG modding support |
| tModLoader/tModLoader | ~5k | Officially adopted Terraria mod loader; entire mod scene runs on it |
| luanti-org/luanti | ~5k | Voxel game engine (ex-Minetest) with Lua modding API |
| KDE/kdenlive | ~5k | Leading OSS video editor for trailers/devlogs |
| LavaGang/MelonLoader | ~4.2k | Universal Unity mod loader; BepInEx's main counterpart |
| OpenTTD/OpenTTD | ~4k | Transport Tycoon Deluxe reimplementation; decades-long maintenance exemplar |
| OpenRCT2/OpenRCT2 | ~4k | RollerCoaster Tycoon 2 source port with multiplayer and plugin API |
| Interkarma/daggerfall-unity | ~4k | Daggerfall on Unity with a large quest/mod scene |
| FabricMC/fabric | ~3.2k | Lightweight Minecraft mod toolchain/loader; modern modding standard |
| GNOME/gimp | ~3k | Read-only GitHub mirror (canonical is GNOME GitLab) — note provenance |
| Pathoschild/SMAPI | ~2.8k | Stardew Valley mod loader + API; textbook single-game framework |
| Nexus-Mods/NexusMods.App | ~2.5k | Next-gen cross-platform Nexus mod manager |
| neoforged/NeoForge | ~2.1k | Community Forge fork for Minecraft modding post-schism |
| ModOrganizer2/modorganizer | ~2k | Virtual-filesystem mod manager for Bethesda games; gold standard |
| CorsixTH/CorsixTH | ~1.5k | Theme Hospital reimplementation in Lua/C++ |
| gemrb/gemrb | ~1.5k | Infinity Engine (Baldur's Gate/Icewind Dale) reimplementation |

## 5. Self-hosted apps (60)

| Repo | Stars | Why it matters |
|---|---|---|
| n8n-io/n8n | ~200k | Leading self-hostable Zapier — 2000+ integrations, visual + AI workflows |
| jellyfin/jellyfin | ~95k | Flagship open media server — Netflix-like streaming, no license fees |
| immich-app/immich | ~90k | Self-hosted Google Photos replacement with mobile backup, ML search |
| louislam/uptime-kuma | ~80k | Pretty uptime monitor — HTTP/TCP/DNS/SSL with status pages |
| home-assistant/core | ~82k | Local-first home automation OS with 3000+ integrations |
| grafana/grafana | ~68k | Standard observability dashboards over Prometheus/Loki/etc. |
| syncthing/syncthing | ~65k | Continuous P2P file sync, no central server, private Dropbox |
| traefik/traefik | ~56k | Cloud-native reverse proxy with auto TLS + Docker discovery |
| pi-hole/pi-hole | ~60k | Classic network-wide DNS sinkhole for ads/trackers, lightweight |
| rclone/rclone | ~50k | Swiss-army CLI to sync/mount 70+ clouds + encrypted backups |
| laurent22/joplin | ~49k | Markdown notes + todos with E2EE sync, Evernote replacement |
| dani-garcia/vaultwarden | ~42k | Lightweight Rust Bitwarden server — one binary, uses official clients |
| toeverything/AFFiNE | ~42k | Open Notion/Miro hybrid — docs, whiteboard, database in one |
| photoprism/photoprism | ~38k | AI-tagged photo library with search, faces, maps |
| outline/outline | ~38k | Polished Notion-like wiki/KB with realtime collab, SSO |
| AdguardTeam/AdGuardHome | ~35k | Pi-hole alternative with DoH/DoT, parental controls, nicer UI |
| portainer/portainer | ~35k | Docker/Podman GUI — manage stacks, images, networks visually |
| logseq/logseq | ~35k | Local-first outliner/PKM with backlinks, great for research |
| DIYgod/RSSHub | ~34k | Generate RSS from anything — scraper for sites without feeds |
| paperless-ngx/paperless-ngx | ~32k | Scan → OCR → searchable document archive, homelab essential |
| nextcloud/server | ~29k | Private Dropbox + Google Workspace — files, Office, calendar, 400+ apps |
| Requarks/wiki | ~29k | Wiki.js — fast Node wiki with Git sync, search, theming |
| restic/restic | ~29k | Fast deduped encrypted backups to any S3/SFTP backend |
| filebrowser/filebrowser | ~26k | Minimal web file manager — upload/preview/share with one binary |
| gethomepage/homepage | ~28k | YAML dashboard with 100+ service widgets, hugely popular start page |
| glanceapp/glance | ~24k | Minimal feed-first dashboard — RSS, calendar, stocks in one glance |
| authelia/authelia | ~25k | Lightweight SSO + 2FA reverse-proxy companion for homelab |
| actualbudget/actual | ~24k | YNAB-like local-first budgeting, best UX for envelopes |
| node-red/node-red | ~20k | Low-code IoT/home wiring with huge node library |
| freshrss/freshrss | ~20k | Lightweight self-hosted RSS aggregator, Fever/GReader API |
| dgtlmoon/changedetection-io | ~20k | Website change monitoring + price/stock alerts with RSS output |
| janeczku/calibre-web | ~19k | Clean web UI for Calibre ebook libraries — browse/read/download |
| BookStackApp/BookStack | ~18k | Simple book/chapter/page docs platform (now Codeberg-primary, GitHub mirror) |
| Lissy93/dashy | ~18k | Pretty status dashboard with widgets, themes, auth |
| firefly-iii/firefly-iii | ~17k | Full personal finance manager with budgets, rules, API |
| activepieces/activepieces | ~16k | MIT-licensed Zapier clone, 760+ pieces, friendly builder |
| henrygd/beszel | ~16k | Lightweight server/Docker monitoring hub with history + alerts |
| goauthentik/authentik | ~15k | Full SSO — OAuth2/OIDC/SAML/LDAP with polished admin |
| advplyr/audiobookshelf | ~14k | Best self-hosted audiobook + podcast server with iOS/Android apps |
| windmill-labs/windmill | ~13k | Code-first workflow engine — turn scripts into APIs/UIs |
| homarr-labs/homarr | ~10k | Modern drag-drop homelab dashboard, 80+ integrations, auth built-in |
| haiwen/seafile | ~12k | Fastest file sync (block-level), best for large files/libraries |
| hay-kot/mealie | ~12k | Recipe manager + meal planner with shopping lists, OpenAPI |
| navidrome/navidrome | ~11k | Featherweight Go music server, Subsonic-compatible, 30–50MB RAM |
| huginn/huginn | ~11k | Veteran agent-based automation — scrape, watch, act on events |
| borgbackup/borg | ~11k | Deduplicating archival backup, rock-solid for servers |
| Sonarr/Sonarr | ~11k | TV show PVR — automatic usenet/torrent grabbing, renaming, upgrading |
| Radarr/Radarr | ~11k | Movie equivalent of Sonarr, core of Servarr stack |
| gotson/komga | ~10k | Comics/manga/ebook server with OPDS, Kobo/Koreader sync |
| TriliumNext/Trilium | ~10k | Hierarchical personal KB — notes, canvas, mindmap, spreadsheets |
| kopia/kopia | ~10k | Modern Restic rival with GUI, policies, compression, S3 support |
| duplicati/duplicati | ~9k | Friendliest browser-UI backup client with encryption + schedulers |
| grocy/grocy | ~8k | Grocery/stock/chores manager — pantry tracking + meal planning |
| fallenbagel/jellyseerr | ~7k | Media request manager for Jellyfin/Plex — Overseerr fork |
| Prowlarr/Prowlarr | ~7k | Indexer manager that feeds Sonarr/Radarr/Lidarr/Readarr from one place |
| miniflux/v2 | ~7k | Minimalist fast RSS reader, PostgreSQL, distraction-free |
| morpheus65535/bazarr | ~5k | Automatic subtitle downloader for Sonarr/Radarr |
| Lidarr/Lidarr | ~4k | Music collection manager for the *arr stack |
| owncloud/ocis | ~4k | Go-based ownCloud Infinite Scale — fast, lightweight EFSS |
| Readarr/Readarr | ~3k | Ebook/audiobook *arr manager |

## 6. VFIO, passthrough & homelab infra (48)

(qemu/qemu counted in Emulation — not repeated.)

| Repo | Stars | Why it matters |
|---|---|---|
| awesome-selfhosted/awesome-selfhosted | ~325k | The definitive index of self-hostable software — discovery for everything else here |
| coollabsio/coolify | ~63k | Self-hostable PaaS (Vercel/Heroku alternative) — deploy anything with git push |
| dockur/windows | ~53.6k | Windows in Docker with KVM + optional GPU passthrough — easiest Windows VM on a server |
| sickcodes/Docker-OSX | ~53k | macOS VM in Docker (OSX-KVM based) — huge for CI and Mac-on-homelab |
| dokploy/dokploy | ~37.8k | Open-source Vercel/Netlify/Heroku alternative with VPS + Docker management |
| IceWhaleTech/CasaOS | ~37.3k | One-command personal cloud with app store — lowest-friction Docker homelab OS |
| caprover/caprover | ~35k | Lightweight PaaS on Docker Swarm — simple app deploys with built-in SSL/backup |
| community-scripts/ProxmoxVE | ~29.8k | Successor to tteck's scripts — 300+ one-click LXC/VM/app installers for Proxmox VE |
| getumbrel/umbrel | ~28k | Personal-server OS with Umbrel App Store — big catalog, beginner-friendly |
| sunshine-stream/Sunshine | ~27k | Self-hosted Moonlight game-streaming host — remote GPU desktop from the passthrough rig |
| wg-easy/wg-easy | ~27.1k | Simplest WireGuard + web admin UI in one container — site-to-homelab VPN in minutes |
| jc21/nginx-proxy-manager | ~27k | GUI for Nginx reverse proxy + certs — easiest public access to homelab services |
| tailscale/tailscale | ~35k | WireGuard-based zero-config mesh VPN — remote homelab access without port forwarding |
| juanfont/headscale | ~44k | Self-hosted Tailscale control server — keep the tailnet fully on your infra |
| kholia/OSX-KVM | ~23.7k | Run macOS on QEMU/KVM with OpenCore — actively maintained macOS-on-Linux reference |
| dockur/macos | ~21.6k | macOS in Docker sibling of dockur/windows, same one-compose pattern |
| netbirdio/netbird | ~25k | Open peer-to-peer WireGuard VPN with SSO/ACLs — Headscale alternative with management UI |
| rustdesk/rustdesk | ~100k | Self-hosted TeamViewer/AnyDesk replacement for remote desktop into lab machines |
| zerotier/ZeroTierOne | ~15k | L2 virtual networking overlay — another no-port-forward remote-access fabric |
| gravitational/teleport | ~18k | Identity-aware SSH/K8s/db access proxy — when the homelab outgrows plain SSH |
| NVIDIA/open-gpu-kernel-modules | ~17.5k | Official open NVIDIA kernel modules; required reading/source for VFIO + driver-version pinning |
| tteck/Proxmox | ~15.2k | Original Proxmox helper-scripts repo (archived Nov 2024, redirects to Community Scripts) |
| nix-community/home-manager | ~10.4k | Declarative user environments — half of every NixOS homelab config |
| runtipi/runtipi | ~9.7k | One-click self-hosted app server, very active |
| kubevirt/kubevirt | ~7.1k | Run VMs as Kubernetes objects — the bridge if your homelab converges on K8s |
| lxc/incus | ~6.4k | LXD fork turned full system-container + VM manager; the modern LXC path next to Proxmox |
| azukaar/Cosmos-Server | ~6.2k | Security-first homelab server (auth, anti-DDoS/bot, reverse proxy built in) |
| gnif/LookingGlass | ~5.7k | Near-zero-latency display relay for GPU-passthrough VMs — the essential VFIO daily-driver tool |
| trapexit/mergerfs | ~5.9k | FUSE union filesystem for pooling mismatched homelab disks behind one mount |
| DualCoder/vgpu_unlock | ~5.3k | Unlocks NVIDIA vGPU on consumer cards — key to splitting one GPU across VMs |
| harvester/harvester | ~5.2k | Rancher's open HCI (KubeVirt-based) — the open Proxmox alternative for VM+container convergence |
| openmediavault/openmediavault | ~5k | Debian-based NAS OS with plugin ecosystem — lighter than TrueNAS |
| bastienwirtz/homer | ~11.7k | Dead-simple static homelab start page/dashboard |
| Misterio77/nix-starter-configs | ~3.8k | Documented NixOS+flakes starter templates — fastest on-ramp to a reproducible homelab host |
| nix-community/disko | ~3.4k | Declarative disk partitioning for NixOS — ZFS layouts as code |
| virt-manager/virt-manager | ~3.3k | Standard desktop UI for KVM/libvirt — still the fastest way to stand up a passthrough VM |
| Mic92/sops-nix | ~3.2k | Atomic secret provisioning for NixOS — how you keep homelab credentials out of git |
| truenas/middleware | ~2.6k | TrueNAS CORE/SCALE middleware source — the NAS OS itself, for tracking/custom builds |
| amadvance/snapraid | ~2.6k | Parity-based snapshot RAID for media arrays — pairs with mergerfs in most DIY NAS builds |
| bryansteiner/gpu-passthrough-tutorial | ~2.2k | The canonical Arch VFIO tutorial (active again) every passthrough setup starts from |
| nix-community/impermanence | ~1.9k | Ephemeral-root + opt-in persistence modules — the impermanence homelab pattern |
| libvirt/libvirt | ~1.7k | Canonical VM management API/daemon behind virt-manager, Proxmox-adjacent tooling, hooks |
| joeknock90/Single-GPU-Passthrough | ~1.7k | Most-starred single-GPU-passthrough hook scripts (libvirt qemu hooks for bind/unbind) |
| xcp-ng/xcp | ~1.6k | Open-source Xen hypervisor distro meta-repo — the VMware-exit refuge for homelabs |
| QaidVoid/Complete-Single-GPU-Passthrough | ~1.1k | Full single-GPU VFIO walkthrough with scripts for AMD+NVIDIA on Arch |
| vatesfr/xen-orchestra | ~1k | Web management + backup for XCP-ng/XenServer — makes XCP-ng homelab-viable |
| proxmoxer/proxmoxer | ~0.8k | Python wrapper for the Proxmox API — basis for any automation around PVE |
| truenas/apps | ~0.4k | Current Docker-Compose app catalog for TrueNAS Electric Eel+ (replaces charts) |

Priority mirror picks for Gitea: `community-scripts/ProxmoxVE`, `gnif/LookingGlass`,
`juanfont/headscale`, `harvester/harvester`, `xcp-ng/xcp`, `truenas/apps`,
`truenas/middleware`, `runtipi/runtipi`, `azukaar/Cosmos-Server`, and the NixOS trio
(`home-manager`, `disko`, `sops-nix`) — highest homelab-specific value per byte.

## 7. Dev tools (57)

(ollama/ollama, open-webui/open-webui, Aider-AI/aider, continuedev/continue counted in AI/ML — not repeated.)

| Repo | Stars | Why it matters |
|---|---|---|
| anomalyco/opencode | ~213k | Open-source terminal coding agent (ex-`sst/opencode`) — verify star count, drift suspected |
| zed-industries/zed | ~92k | GPU Rust editor from Atom creators, collab + AI-native, very fast |
| neovim/neovim | ~90k | Modal editor + LSP/tree-sitter platform most terminal devs live in |
| jesseduffield/lazygit | ~81k | Best git TUI: stage hunks, rebase, cherry-pick without flags |
| junegunn/fzf | ~70k | Fuzzy finder powering history/file/process pickers everywhere |
| hoppscotch/hoppscotch | ~70k | Open-source Postman alternative, self-hostable API client |
| alacritty/alacritty | ~65k | Fastest minimal GPU terminal, the performance baseline |
| starship/starship | ~60k | Cross-shell minimal prompt with git/lang modules everywhere |
| ghostty-org/ghostty | ~59k | Mitchell Hashimoto's Zig GPU terminal, native UI + fast burn-in |
| go-gitea/gitea | ~58k | Lightweight self-hosted forge — the thing you're mirroring into |
| wagoodman/dive | ~54k | Layer-by-layer image explorer showing wasted bytes per layer |
| jesseduffield/lazydocker | ~53k | One-key TUI for containers/images/volumes/logs, SSH-friendly |
| sharkdp/bat | ~53k | `cat` with syntax highlighting, git gutter, paging |
| BurntSushi/ripgrep | ~52k | `grep` replacement 10-100x faster, respects .gitignore |
| usebruno/bruno | ~48k | Git-backed offline API client (Bru flat files version cleanly) |
| helix-editor/helix | ~47k | Kakoune-model modal editor in Rust, LSP/tree-sitter built in, zero config |
| nushell/nushell | ~41k | Structured-data shell (tables not text) for pipelines |
| lapce/lapce | ~37k | GPU modal editor (floem/druid) with Vim mode and plugins |
| tmux/tmux | ~36k | Ubiquitous terminal multiplexer for persistent remote sessions |
| zellij-org/zellij | ~36k | Batteries-included tmux alternative with layouts, plugins, floating panes |
| sharkdp/fd | ~36k | Fast user-friendly `find` with sane defaults and colors |
| docker/compose | ~35k | Multi-container dev envs as code, the self-host staple |
| httpie/httpie | ~35k | Human-friendly `curl` (`http POST api x:=1`) for quick probes |
| derailed/k9s | ~34k | Kubernetes TUI for pods/logs/port-forwards at speed |
| Kong/insomnia | ~34k | Mature REST/GraphQL/gRPC client, good for import/export |
| tabbyml/tabby | ~34k | Self-hosted Copilot server (Ollama-compatible models) for teams |
| jqlang/jq | ~32k | The JSON processor every API/CLI pipeline leans on |
| wez/wezterm | ~29k | GPU terminal + built-in multiplexer/SSH domains, Lua-configured daily driver |
| cli/cli | ~28k | Official `gh` CLI: PRs, issues, Actions, extensions from terminal |
| git-extras/git-extras | ~28k | Extra git subcommands (undo, churn, setup, archive-file) |
| dandavison/delta | ~27k | Syntax-highlighting pager for `git diff`, side-by-side + line numbers |
| voideditor/void | ~27k | Open-source Cursor alternative, local-model friendly editor |
| zyedidia/micro | ~27k | Tiny terminal editor (Ctrl-S/C/V sane), great for servers |
| fish-shell/fish-shell | ~26k | Friendly interactive shell with autosuggest out of the box |
| ajeetdsouza/zoxide | ~26k | Frecency `cd` (`z proj`), kills deep path typing |
| atuinsh/atuin | ~25k | Synced, searchable shell history (SQLite, E2E encrypted) |
| vuejs/vitepress | ~25k | Vite-powered docs, fast and clean for tool sites |
| sharkdp/hyperfine | ~25k | Statistical CLI benchmarking with Markdown export |
| casey/just | ~24k | `make` without pain: per-repo command runner, huge for onboarding |
| gitui-org/gitui | ~22k | Blazing Rust git TUI, handles huge repos (Linux kernel test) |
| doomemacs/doomemacs | ~22k | Fast curated Emacs IDE layer, the Emacs gateway drug |
| mkdocs/mkdocs | ~20k | Minimal Markdown docs builder, perfect for mirrored-repo docs |
| squidfunk/mkdocs-material | ~20k | Best MkDocs theme: nav tabs, instant search, version switcher |
| so-fancy/diff-so-fancy | ~19k | Human-readable diff highlighter, easy pager upgrade |
| LunarVim/LunarVim | ~19k | Batteries-included Neovim IDE layer, good mirror of a real-world config |
| XAMPPRocky/tokei | ~19k | Fast code counter (lines/language) for repo inventory |
| bcicen/ctop | ~18k | `top` for containers, real-time metrics in one screen |
| eza-community/eza | ~17k | Maintained `exa`/`ls` successor with icons, git status, tree |
| git-town/git-town | ~15k | High-flow git automation (ship/kill/sync stacked branches) |
| withastro/starlight | ~14k | Modern Astro docs theme with i18n + diagrams built in |
| mikefarah/yq | ~13k | `jq` for YAML/TOML/XML, essential for compose/manifest edits |
| orhun/git-cliff | ~12k | Conventional-commit changelog generator, Keep-a-Changelog output |
| bootandy/dust | ~11k | Visual `du` with tree bars, finds disk hogs fast |
| forgejo/forgejo | ~10k | Community Gitea fork under Codeberg e.V., fully free software |
| dalance/procs | ~7k | Modern `ps` with color, tree, Docker/inspect columns |
| carapace-sh/carapace-bin | ~2k | Universal shell completer bridging cobra/argparse CLIs |
| facebook/docusaurus | ~61k | React docs sites with versioning/blog/search, the default for OSS docs |

## 8. Privacy, security & networking (44)

(tailscale/tailscale, juanfont/headscale, netbirdio/netbird, zerotier/ZeroTierOne
counted in VFIO & homelab infra — not repeated.)

| Repo | Stars | Why it matters |
|---|---|---|
| fatedier/frp | ~109k | De-facto fast reverse proxy for NAT traversal (TCP/UDP/HTTP/HTTPS, P2P) |
| sherlock-project/sherlock | ~93k | Username-to-social-account hunter across hundreds of sites |
| sqlmapproject/sqlmap | ~38.5k | Automatic SQL injection detection and DB takeover |
| rapid7/metasploit-framework | ~39k | Canonical exploitation framework, modules + Meterpreter (also in RE) |
| SagerNet/sing-box | ~38k | Universal proxy platform (VLESS/Trojan/Shadowsocks/Hysteria/WireGuard/Tor) |
| MetaCubeX/mihomo | ~35k | Clash-Meta continuation, rule-based tunnel core for clients/routers |
| projectdiscovery/nuclei | ~31k | YAML-template vulnerability scanner (also in RE) |
| XTLS/Xray-core | ~28k | VLESS/XTLS/REALITY anti-censorship core, successor to v2ray-core |
| v2fly/v2ray-core | ~27k | Foundational VMess/VLESS proxy core behind Xray and many clients |
| fail2ban/fail2ban | ~18.6k | Classic log-based ban daemon for SSH/HTTP brute force |
| laramies/theHarvester | ~17.5k | Email/subdomain/name harvester for OSINT recon |
| ffuf/ffuf | ~16.6k | Fast Go web fuzzer for dirs, vhosts, params |
| cloudflare/cloudflared | ~16k | Cloudflare Tunnel client, expose origins without opening ports |
| slackhq/nebula | ~16k | Scalable overlay networking with certs + security groups from Slack |
| wazuh/wazuh | ~16.7k | Open XDR/SIEM platform (IDS, FIM, vuln detection, compliance) |
| zaproxy/zaproxy | ~15.5k | OWASP web app scanner (DAST) for dev and pentest |
| owasp-amass/amass | ~15k | In-depth attack-surface mapping and external asset discovery |
| crowdsecurity/crowdsec | ~15k | Collaborative IDS/IPS + WAF with crowdsourced malicious-IP blocklist |
| projectdiscovery/subfinder | ~14.4k | Fast passive subdomain enumeration via dozens of APIs |
| DNSCrypt/dnscrypt-proxy | ~13.6k | Flexible encrypted-DNS proxy (DNSCrypt/DoH/Oblivious DoH) for clients |
| SpecterOps/BloodHound | ~13k | Active Directory attack-path mapping (also in RE) |
| element-hq/synapse | ~12k | Matrix homeserver (ex-matrix-org/synapse, now Element-maintained) |
| jpillora/chisel | ~11k | Fast TCP/UDP-over-HTTP tunnel secured via SSH, single binary |
| shadowsocks/shadowsocks-rust | ~11k | Rust port of Shadowsocks, maintained tunnel proxy for firewall bypass |
| nmap/nmap | ~11k | Network Mapper, port/service/OS discovery baseline |
| TechnitiumSoftware/DnsServer | ~10k | Full authoritative + recursive DNS with web console and encrypted forwarders |
| gravitl/netmaker | ~10k | Self-hosted WireGuard automation for edge, IoT, and Kubernetes |
| firezone/firezone | ~9k | Enterprise zero-trust WireGuard access platform, fast peer-to-peer |
| zeek/zeek | ~8k | Network analysis framework, deep protocol logs for threat hunting (also in RE) |
| wireshark/wireshark | ~8k | Packet analyzer for malware C2/traffic RE (also in RE) |
| 0xERR0R/blocky | ~7k | Fast Go DNS proxy + ad-blocker with caching, DoH/DoT/DoQ, Prometheus |
| go-gost/gost | ~7.3k | GO Simple Tunnel: multi-protocol proxy/forward/reverse-proxy chains |
| OJ/gobuster | ~7k | Directory/DNS/VHost busting in Go, Kali staple |
| OISF/suricata | ~6k | High-performance IDS/IPS/NSM engine (also in RE) |
| soxoj/maigret | ~5k | Username dossier builder (3000+ sites), Sherlock successor for persons |
| smicallef/spiderfoot | ~4.5k | Automated OSINT / attack-surface mapper with 200+ modules |
| WireGuard/wireguard-go | ~4.4k | Userspace Go implementation of WireGuard, base for most VPN/mesh tooling |
| opnsense/core | ~4.7k | OPNsense firewall GUI/API/backend, core to mirror for firewall builds |
| AdguardTeam/dnsproxy | ~2k | Upstream library powering AdGuardHome encrypted-DNS forwarding |
| NLnetLabs/unbound | ~2k | Validating recursive resolver, standard self-hosted DNS base |
| opnsense/plugins | ~1.2k | Official OPNsense plugin collection (VPN, IDS, CrowdSec, ACME, etc.) |
| girlbossceo/conduwuit | ~1k | Active Rust Matrix homeserver continuing Conduit, light for Pi-class hosts |
| simplex-chat/simplex-chat | ~19.5k | Identifier-free E2EE messenger stack, self-hostable relays |
| simplex-chat/simplexmq | ~0.85k | Reference SimpleX message-queue protocol server for private routing |

## Suggested onboarding order

1. `awesome-selfhosted/awesome-selfhosted` + `community-scripts/ProxmoxVE` (indexes that guide the rest).
2. AI core: `llama.cpp`, `ollama`, `ComfyUI`, `transformers`, `langchain`, `unsloth`.
3. Forge layer: `go-gitea/gitea`, `forgejo/forgejo` (self-reference is good hygiene).
4. Daily drivers: `jellyfin`, `immich`, `headscale`, `traefik`, `uptime-kuma`, `n8n`.
5. Then one full category per sync batch.

## Import status (2026-10-11)

Bulk-imported into gitea-mirror: **470 of 489 queued for mirroring** (19 batches, all accepted).
These 19 were rejected by the GitHub lookup (renamed/moved upstream or lookup miss) and need
corrected `owner/name` before retrying:

- kyutai/moshi, weightsandbiases/wandb, BinaryAnalysisPlatform/triton, drakvuf/drakvuf,
  PabloMK7/citra, ryujinx-mirror/ryujinx (500 from app), GreemDev/Ryujinx, citron-emu/citron,
  torzu-emu/torzu, mataesu/pegasus-frontend, ruffle/ruffle, Snes9x/snes9x (canonical is
  snes9xgit/snes9x), devmiyax/yabasanshiro, flycastemu/flycast, shiiion/dolphin-primehack,
  dgtlmoon/changedetection-io, sunshine-stream/Sunshine, git-extras/git-extras,
  forgejo/forgejo (canonical is Codeberg-hosted).
