# Aurora V7

**Aurora** is a pure C# personal AI assistant built on .NET 10 — no Python, no cloud dependency, fully local.
Hand-written neural networks, local voice (Piper TTS + Whisper STT), continuous listening, and learns from every conversation.

> ⚠️ This repository contains **compiled releases only**. Source code is maintained privately.

---

## Latest Release

| Channel | Version | Date |
|---------|---------|------|
| Stable  | 7.0.0   | 2026-03-31 |

→ [Download from Releases](https://github.com/maj-adm/aurora-release/releases)

---

## What's included in v7.0.0

- **Transformer Language Model** — 7M parameter model (DModel=256, 4 layers, 32K BPE vocab), GPU-accelerated via CUDA
- **CRNN Intent Classifier** — 226 intents, multilingual (EN / NL / ES / IT / JP / ZH / KO / GR / AR)
- **Reasoning Engine** — Chain-of-thought reasoning with causal inference, comfort/physical state detection, multi-action dispatch
- **Smart Home** — Thermostat + lights control with implicit intent detection ("I'm cold", "it's too dark")
- **Skills** — Timer/alarm, weather, calendar, email, Discord, system control, design/simulate, and more
- **Proactive Engine** — Background event-driven proactive responses
- **Distributed Nodes** — Multi-node support with leader election and auto-update
- **REST API** — Full HTTP API for external integrations and the web dashboard
- **Avalonia Dashboard** — Cross-platform desktop UI (Windows + Linux)
- **Continuous Learning** — RL-based policy updater, conversation memory, emotion tracking

---

## Downloads

| Build | Platform | File |
|-------|----------|------|
| Aurora Server | Windows x64 | `aurora-server-win-x64-v7.0.0.zip` |
| Aurora Server | Linux x64   | `aurora-server-linux-x64-v7.0.0.zip` |
| Aurora Client (Dashboard) | Windows x64 | `aurora-client-win-x64-v7.0.0.zip` |
| Aurora Client (Dashboard) | Linux x64   | `aurora-client-linux-x64-v7.0.0.zip` |

---

## Installation — Server

1. Download `aurora-server-win-x64-v7.0.0.zip` (or linux build)
2. Extract to a folder of your choice (e.g. `C:\Aurora`)
3. Place voice model files in the `voice/` folder:
   ```
   voice/
     piper.exe                        ← from github.com/rhasspy/piper/releases
     ggml-small.en.bin                ← from huggingface.co/ggerganov/whisper.cpp
     voices/
       en_US-kathleen-low.onnx        ← from huggingface.co/rhasspy/piper-voices
       en_US-kathleen-low.onnx.json
   ```
4. Run `Aurora.app.exe`

## Installation — Client (Dashboard)

1. Download `aurora-client-win-x64-v7.0.0.zip`
2. Extract and run `Aurora.Dashboard.Avalonia.exe`
3. The dashboard connects to the Aurora server REST API on `localhost:5000`

---

## Nodes — Auto-Update

Aurora nodes check `version.json` on startup and auto-download new releases.

```
Node boot → fetch version.json → compare local version
          → newer found: download zip → extract → restart
```

Update interval is configurable (default: 60 minutes).

---

## Requirements

| Component | Requirement |
|-----------|-------------|
| OS | Windows 10/11 x64 or Linux x64 |
| Runtime | .NET 10 (included, self-contained) |
| RAM | 8 GB minimum, 16 GB recommended |
| GPU | NVIDIA (CUDA) recommended for LM training |
| Storage | ~500 MB for base install + model files |

---

## Configuration

On first boot Aurora creates `aurora_data/` for user profiles, memory, and settings.
API keys (weather, email) can be configured via the dashboard or REST API.
