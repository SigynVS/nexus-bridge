# Nexus Bridge

> Cross-device file transfer desktop app built with Electron, Express, and LocalTunnel. Share files instantly between any devices on any network — no cables, no cloud accounts, just scan a QR code.

![Electron](https://img.shields.io/badge/Electron-Desktop-blue) ![Node.js](https://img.shields.io/badge/Node.js-Express-green) ![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey)

---

## What This Project Demonstrates

- **Electron desktop app** packaged as a Windows `.exe` installer via `electron-builder`
- **Express HTTP server** embedded inside the Electron app for local file serving
- **LocalTunnel integration** — exposes the local server to the public internet with a shareable URL
- **QR code generation** — auto-generates a QR code so mobile devices can connect instantly
- **Multer file handling** — drag-and-drop file uploads with multipart form support
- **Preload/IPC architecture** — secure Electron main↔renderer communication via `preload.js`

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Desktop shell | Electron |
| Local server | Express 5 |
| Tunnel | LocalTunnel |
| File uploads | Multer |
| QR code | qrcode |
| Packaging | electron-builder (NSIS Windows installer) |

---

## How It Works

```
  Your PC (Electron App)
  ├── Express server (localhost)
  ├── LocalTunnel → public URL
  └── QR code displayed in UI
            ↓
  Any device scans QR code
            ↓
  Browser opens → drag & drop files → transferred instantly
```

1. Launch Nexus Bridge on your PC
2. A QR code appears with a public tunnel URL
3. Scan the QR code on any phone, tablet, or other computer
4. Drag and drop files in the browser — they land on your PC instantly

---

## Project Structure

```
nexus-bridge/
  main.js         Electron main process — window, IPC, tunnel management
  preload.js      Secure context bridge (main ↔ renderer)
  server.js       Express server — file upload/download endpoints
  lib/            Shared utilities
  public/         Frontend UI (HTML/CSS/JS)
```

---

## Running Locally

**Prerequisites:** Node.js v18+

```bash
npm install
npm start
```

---

## Building the Windows Installer

```bash
npm run dist
# Output: dist/Nexus Bridge Setup.exe
```

---

*Built by [Brian Justice](https://github.com/SigynVS)*