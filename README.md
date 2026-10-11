# Whisper Flow 0.3 — one local TypeScript app

A **194 × 32**, fully rounded Linux widget. Press **Alt+P**, speak, then press **Alt+P** again. The transcription is pasted into the focused app.

- Uses `faster-whisper-ts` 1.2.1 and `decibri` microphone capture.
- No Python, FastAPI, URL, port, localhost request, connection button, runtime Node installation, or separately started backend.
- Tauri starts the included TypeScript engine and communicates only through private stdin/stdout process pipes.
- The installer contains Node, native speech libraries, and the local `base.en` model. Audio stays on-device.

## Platform

The package documentation supplied with the request says `faster-whisper-ts` 1.2.1 has a stable **Linux CPU** target only. This source honestly builds Linux x64 `.deb` and `.AppImage` artifacts, not broken Windows/macOS installers. Linux needs X11, `xclip`, and `xdotool` for focused-app insertion.

## Push and build

```bash
git init
git add .
git commit -m "Whisper Flow TypeScript desktop"
git branch -M main
git remote add origin https://github.com/YOUR-NAME/YOUR-NEW-REPO.git
git push -u origin main
```

Open **Actions → Build Linux desktop app** and download `whisper-flow-linux-x64`. The workflow compiles the native CTranslate2 bridge, tests the overlap logic, downloads the model at build time, and includes everything in one desktop installer.

## Develop

Install Node 22, Rust, CMake, a C++17 compiler, Tauri Linux prerequisites, `xclip`, and `xdotool`.

```bash
npm ci
npm run engine:test
npm run desktop
```

The Vite browser preview cannot use native speech or a system-wide shortcut; use Tauri. The uploaded text was package documentation, not HTML/CSS design, so this keeps and shrinks the previous dark rounded pill. Tauri's small Rust shell remains because Tauri is Rust and owns native lifecycle and Alt+P; the speech pipeline is TypeScript.
