# Aurora V7 — Releases

Official release distribution for **Aurora V7**, a pure C# personal AI assistant built on .NET 10.

> ⚠️ This repository contains **compiled releases only**. Source code is maintained privately.

---

## Latest Release

| Channel | Version | Date |
|---------|---------|------|
| Stable  | 7.0.0   | 2026-03-31 |

Download the latest release from the [Releases page](https://github.com/maj-adm/aurora-release/releases).

---

## Installation

1. Download `aurora-v{version}-win-x64.zip` from [Releases](https://github.com/maj-adm/aurora-release/releases)
2. Extract to a folder of your choice (e.g. `C:\Aurora`)
3. Place your voice model files:
   - `piper/piper.exe`
   - `voices/en_US-kathleen-low.onnx` + `.json`
   - `models/ggml-small.en.bin` (Whisper STT)
4. Run `Aurora.app.exe`

---

## Nodes — Auto-Update

Aurora nodes check `version.json` on startup and pull new releases automatically.

```
Node boot → checks version.json → compares local version
          → if newer: downloads zip → extracts → restarts
```

The update interval is configurable (default: 60 minutes).

---

## Requirements

- Windows 10/11 x64
- .NET 10 Runtime (included in release zip)
- NVIDIA GPU recommended (CUDA for LM training)
- 8 GB RAM minimum, 16 GB recommended
