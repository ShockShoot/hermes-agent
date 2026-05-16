<p align="center">
  <img src="assets/banner.png" alt="Hermes Agent" width="100%">
</p>

# Hermes Agent ☤

<p align="center">
  <a href="https://hermes-agent.nousresearch.com/docs/"><img src="https://img.shields.io/badge/Docs-hermes--agent.nousresearch.com-FFD700?style=for-the-badge" alt="Documentation"></a>
  <a href="https://discord.gg/NousResearch"><img src="https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord"></a>
  <a href="https://github.com/NousResearch/hermes-agent/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License: MIT"></a>
  <a href="https://nousresearch.com"><img src="https://img.shields.io/badge/Built%20by-Nous%20Research-blueviolet?style=for-the-badge" alt="Built by Nous Research"></a>
  <a href="README.md"><img src="https://img.shields.io/badge/Lang-English-lightgrey?style=for-the-badge" alt="English"></a>
  <a href="README.zh-CN.md"><img src="https://img.shields.io/badge/Lang-中文-red?style=for-the-badge" alt="中文"></a>
</p>

**AI agent ที่เรียนรู้และพัฒนาตัวเอง สร้างโดย [Nous Research](https://nousresearch.com)** Hermes เป็น agent ที่มี learning loop ในตัว — สร้าง skills จากประสบการณ์ ปรับปรุง skills ระหว่างใช้งาน เตือนตัวเองให้บันทึกความรู้ ค้นบทสนทนาเก่า และค่อย ๆ สร้างความเข้าใจว่าคุณเป็นใครข้ามหลาย session ได้ ใช้งานได้ตั้งแต่ VPS ราคา $5, GPU cluster, ไปจนถึง serverless infrastructure ที่แทบไม่มีค่าใช้จ่ายตอน idle และไม่จำเป็นต้องผูกติดกับ laptop — คุยกับมันผ่าน Telegram ได้ขณะที่มันทำงานอยู่บน cloud VM

ใช้โมเดลใดก็ได้ — [Nous Portal](https://portal.nousresearch.com), [OpenRouter](https://openrouter.ai) (200+ models), [NVIDIA NIM](https://build.nvidia.com) (Nemotron), [Xiaomi MiMo](https://platform.xiaomimimo.com), [z.ai/GLM](https://z.ai), [Kimi/Moonshot](https://platform.moonshot.ai), [MiniMax](https://www.minimax.io), [Hugging Face](https://huggingface.co), OpenAI หรือ endpoint ของคุณเอง สลับโมเดลด้วย `hermes model` — ไม่ต้องแก้โค้ด และไม่ถูกล็อกกับ provider ใด provider หนึ่ง

<table>
<tr><td><b>Terminal interface จริง</b></td><td>TUI เต็มรูปแบบ พร้อม multiline editing, slash-command autocomplete, conversation history, interrupt-and-redirect และ streaming tool output</td></tr>
<tr><td><b>อยู่ได้ทุกที่ที่คุณใช้งาน</b></td><td>Telegram, Discord, Slack, WhatsApp, Signal และ CLI — ทั้งหมดผ่าน gateway process เดียว รองรับ voice memo transcription และ conversation continuity ข้าม platform</td></tr>
<tr><td><b>Closed learning loop</b></td><td>Agent-curated memory พร้อม periodic nudges สร้าง skills อัตโนมัติหลังงานซับซ้อน Skills ปรับปรุงตัวเองระหว่างใช้งาน FTS5 session search พร้อม LLM summarization สำหรับ recall ข้าม session รองรับ <a href="https://github.com/plastic-labs/honcho">Honcho</a> dialectic user modeling และเข้ากันได้กับมาตรฐานเปิด <a href="https://agentskills.io">agentskills.io</a></td></tr>
<tr><td><b>Scheduled automations</b></td><td>มี cron scheduler ในตัว ส่งผลลัพธ์ไปยัง platform ใดก็ได้ รายงานรายวัน backup กลางคืน audit รายสัปดาห์ — เขียนด้วยภาษาธรรมชาติแล้วปล่อยให้ทำงานเอง</td></tr>
<tr><td><b>Delegate และ parallelize ได้</b></td><td>spawn subagents แบบแยก context เพื่อทำงานคู่ขนาน เขียน Python scripts ที่เรียก tools ผ่าน RPC เพื่อบีบ multi-step pipelines ให้กลายเป็น turn ที่แทบไม่กิน context</td></tr>
<tr><td><b>รันได้ทุกที่ ไม่ใช่แค่ laptop</b></td><td>terminal backends 7 แบบ — local, Docker, SSH, Singularity, Modal, Daytona และ Vercel Sandbox โดย Daytona และ Modal รองรับ serverless persistence: environment ของ agent หลับตอน idle และตื่นเมื่อเรียกใช้ ทำให้แทบไม่มีค่าใช้จ่ายระหว่างพัก รันได้ทั้ง VPS ราคา $5 หรือ GPU cluster</td></tr>
<tr><td><b>พร้อมสำหรับ research</b></td><td>batch trajectory generation, Atropos RL environments และ trajectory compression สำหรับฝึก tool-calling models รุ่นถัดไป</td></tr>
</table>

---

## Quick Install

### Linux, macOS, WSL2, Termux

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

### Windows native ผ่าน PowerShell — Early Beta

> **หมายเหตุ:** Native Windows support ยังเป็น **early beta** ติดตั้งและรันได้ แต่ยังไม่ได้ผ่านการทดสอบกว้างเท่า Linux/macOS/WSL2 ถ้าเจอปัญหา กรุณา [เปิด issue](https://github.com/NousResearch/hermes-agent/issues) สำหรับ setup ที่ battle-tested ที่สุดบน Windows ตอนนี้ แนะนำให้ใช้ one-liner ฝั่ง Linux ด้านบนใน **WSL2**

รันคำสั่งนี้ใน PowerShell:

```powershell
irm https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.ps1 | iex
```

Installer จะจัดการทุกอย่างให้: uv, Python 3.11, Node.js, ripgrep, ffmpeg และ **portable Git Bash** (MinGit ที่แตกไฟล์ไว้ใน `%LOCALAPPDATA%\hermes\git` — ไม่ต้องใช้ admin และแยกจาก system Git) Hermes ใช้ Git Bash ชุดนี้เพื่อรัน shell commands

ถ้ามี Git ติดตั้งอยู่แล้ว installer จะตรวจเจอและใช้ตัวนั้นแทน ไม่เช่นนั้นจะดาวน์โหลด MinGit ประมาณ 45MB โดยไม่แตะหรือรบกวน system Git

> **Android / Termux:** manual path ที่ทดสอบแล้วอยู่ใน [Termux guide](https://hermes-agent.nousresearch.com/docs/getting-started/termux) บน Termux Hermes จะติดตั้ง `.[termux]` extra ที่คัดไว้ เพราะ `.[all]` เต็มชุดยังดึง voice dependencies ที่ไม่เข้ากับ Android
>
> **Windows:** Native Windows รองรับแบบ **early beta** — PowerShell one-liner ด้านบนจะติดตั้งทุกอย่างให้ แต่ยังอาจมี rough edges ถ้าต้องการทางที่เสถียรกว่า ให้ใช้ WSL2 และรันคำสั่ง Linux ด้านบน Native Windows ติดตั้งไว้ใต้ `%LOCALAPPDATA%\hermes`; WSL2 ติดตั้งไว้ใต้ `~/.hermes` เหมือน Linux ฟีเจอร์ Hermes เดียวที่ตอนนี้ยังต้องใช้ WSL2 โดยเฉพาะคือ browser-based dashboard chat pane เพราะใช้ POSIX PTY; classic CLI และ gateway รัน native ได้

หลังติดตั้ง:

```bash
source ~/.bashrc    # reload shell หรือ source ~/.zshrc
hermes              # เริ่มคุยได้เลย
```

---

## Getting Started

```bash
hermes              # Interactive CLI — เริ่ม conversation
hermes model        # เลือก LLM provider และ model
hermes tools        # ตั้งค่า tools ที่เปิดใช้งาน
hermes config set   # ตั้งค่า config รายตัว
hermes gateway      # เริ่ม messaging gateway เช่น Telegram, Discord ฯลฯ
hermes setup        # เปิด setup wizard แบบครบชุด
hermes claw migrate # migrate จาก OpenClaw ถ้ามาจาก OpenClaw
hermes update       # อัปเดตเป็นเวอร์ชันล่าสุด
hermes doctor       # ตรวจและวินิจฉัยปัญหา
```

📖 **[เอกสารเต็ม →](https://hermes-agent.nousresearch.com/docs/)**

## CLI vs Messaging Quick Reference

Hermes มี entry point 2 แบบ: เริ่ม terminal UI ด้วย `hermes` หรือรัน gateway แล้วคุยจาก Telegram, Discord, Slack, WhatsApp, Signal หรือ Email เมื่ออยู่ใน conversation แล้ว slash commands หลายคำสั่งใช้ร่วมกันได้ทั้งสอง interface

| Action | CLI | Messaging platforms |
|---------|-----|---------------------|
| เริ่มคุย | `hermes` | รัน `hermes gateway setup` + `hermes gateway start` แล้วส่งข้อความหา bot |
| เริ่ม conversation ใหม่ | `/new` หรือ `/reset` | `/new` หรือ `/reset` |
| เปลี่ยน model | `/model [provider:model]` | `/model [provider:model]` |
| ตั้ง personality | `/personality [name]` | `/personality [name]` |
| retry หรือ undo turn ล่าสุด | `/retry`, `/undo` | `/retry`, `/undo` |
| compress context / ดู usage | `/compress`, `/usage`, `/insights [--days N]` | `/compress`, `/usage`, `/insights [days]` |
| Browse skills | `/skills` หรือ `/<skill-name>` | `/<skill-name>` |
| Interrupt งานที่กำลังทำ | `Ctrl+C` หรือส่งข้อความใหม่ | `/stop` หรือส่งข้อความใหม่ |
| สถานะเฉพาะ platform | `/platforms` | `/status`, `/sethome` |

ดูรายการคำสั่งเต็มได้ที่ [CLI guide](https://hermes-agent.nousresearch.com/docs/user-guide/cli) และ [Messaging Gateway guide](https://hermes-agent.nousresearch.com/docs/user-guide/messaging)

---

## Documentation

เอกสารทั้งหมดอยู่ที่ **[hermes-agent.nousresearch.com/docs](https://hermes-agent.nousresearch.com/docs/)**:

| Section | สิ่งที่ครอบคลุม |
|---------|------------------|
| [Quickstart](https://hermes-agent.nousresearch.com/docs/getting-started/quickstart) | ติดตั้ง → setup → conversation แรกใน 2 นาที |
| [CLI Usage](https://hermes-agent.nousresearch.com/docs/user-guide/cli) | Commands, keybindings, personalities, sessions |
| [Configuration](https://hermes-agent.nousresearch.com/docs/user-guide/configuration) | Config file, providers, models และ options ทั้งหมด |
| [Messaging Gateway](https://hermes-agent.nousresearch.com/docs/user-guide/messaging) | Telegram, Discord, Slack, WhatsApp, Signal, Home Assistant |
| [Security](https://hermes-agent.nousresearch.com/docs/user-guide/security) | Command approval, DM pairing, container isolation |
| [Tools & Toolsets](https://hermes-agent.nousresearch.com/docs/user-guide/features/tools) | 40+ tools, toolset system, terminal backends |
| [Skills System](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills) | Procedural memory, Skills Hub, การสร้าง skills |
| [Memory](https://hermes-agent.nousresearch.com/docs/user-guide/features/memory) | Persistent memory, user profiles, best practices |
| [MCP Integration](https://hermes-agent.nousresearch.com/docs/user-guide/features/mcp) | เชื่อม MCP server ใดก็ได้เพื่อขยายความสามารถ |
| [Cron Scheduling](https://hermes-agent.nousresearch.com/docs/user-guide/features/cron) | Scheduled tasks พร้อม platform delivery |
| [Context Files](https://hermes-agent.nousresearch.com/docs/user-guide/features/context-files) | Project context ที่ shape ทุก conversation |
| [Architecture](https://hermes-agent.nousresearch.com/docs/developer-guide/architecture) | Project structure, agent loop, key classes |
| [Contributing](https://hermes-agent.nousresearch.com/docs/developer-guide/contributing) | Development setup, PR process, code style |
| [CLI Reference](https://hermes-agent.nousresearch.com/docs/reference/cli-commands) | Commands และ flags ทั้งหมด |
| [Environment Variables](https://hermes-agent.nousresearch.com/docs/reference/environment-variables) | Env var reference แบบครบถ้วน |

---

## Migrating from OpenClaw

ถ้าคุณมาจาก OpenClaw, Hermes สามารถ import settings, memories, skills และ API keys ให้โดยอัตโนมัติ

**ระหว่าง first-time setup:** setup wizard (`hermes setup`) จะตรวจ `~/.openclaw` อัตโนมัติและเสนอให้ migrate ก่อนเริ่ม configuration

**หลังติดตั้งแล้วก็ทำได้ทุกเมื่อ:**

```bash
hermes claw migrate              # Interactive migration แบบ full preset
hermes claw migrate --dry-run    # Preview สิ่งที่จะ migrate
hermes claw migrate --preset user-data   # Migrate โดยไม่รวม secrets
hermes claw migrate --overwrite  # Overwrite conflict ที่มีอยู่
```

สิ่งที่จะถูก import:
- **SOUL.md** — persona file
- **Memories** — entries จาก MEMORY.md และ USER.md
- **Skills** — skills ที่ผู้ใช้สร้างเอง → `~/.hermes/skills/openclaw-imports/`
- **Command allowlist** — approval patterns
- **Messaging settings** — platform configs, allowed users, working directory
- **API keys** — secrets ใน allowlist เช่น Telegram, OpenRouter, OpenAI, Anthropic, ElevenLabs
- **TTS assets** — workspace audio files
- **Workspace instructions** — AGENTS.md พร้อม `--workspace-target`

ดู options ทั้งหมดที่ `hermes claw migrate --help` หรือใช้ skill `openclaw-migration` เพื่อให้ agent ช่วย migrate แบบ interactive พร้อม dry-run previews

---

## Contributing

ยินดีรับ contributions ดู [Contributing Guide](https://hermes-agent.nousresearch.com/docs/developer-guide/contributing) สำหรับ development setup, code style และ PR process

Quick start สำหรับ contributors — clone แล้วใช้ `setup-hermes.sh` ได้เลย:

```bash
git clone https://github.com/NousResearch/hermes-agent.git
cd hermes-agent
./setup-hermes.sh     # ติดตั้ง uv, สร้าง venv, ติดตั้ง .[all], symlink ~/.local/bin/hermes
./hermes              # auto-detect venv ไม่ต้อง source ก่อน
```

Manual path ที่เทียบเท่ากัน:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv venv .venv --python 3.11
source .venv/bin/activate
uv pip install -e ".[all,dev]"
scripts/run_tests.sh
```

> **RL Training (optional):** RL/Atropos integration (`environments/`) — ดู setup เต็มใน [`CONTRIBUTING.md`](https://github.com/NousResearch/hermes-agent/blob/main/CONTRIBUTING.md#development-setup)

---

## Community

- 💬 [Discord](https://discord.gg/NousResearch)
- 📚 [Skills Hub](https://agentskills.io)
- 🐛 [Issues](https://github.com/NousResearch/hermes-agent/issues)
- 🔌 [HermesClaw](https://github.com/AaronWong1999/hermesclaw) — Community WeChat bridge: รัน Hermes Agent และ OpenClaw บน WeChat account เดียวกัน

---

## License

MIT — ดู [LICENSE](LICENSE)

สร้างโดย [Nous Research](https://nousresearch.com)
