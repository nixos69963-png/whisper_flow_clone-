# Architecture
- Keep speech in an included TypeScript child process with stdin/stdout only, so there is no backend connection surface.
- Keep Tauri responsible for Alt+P and child lifecycle, so the shortcut works while another app is focused.
- Target Linux x64 until faster-whisper-ts declares stable native support elsewhere, so installers match the validated runtime.
