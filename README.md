# WSL + VS Code Proxy Helper

A small helper to properly enable / disable HTTP proxy for:

- WSL shell
- VS Code Remote (WSL) extension host

This solves the common issue where proxy works in WSL shell,
but VS Code extensions (Copilot, Codex, etc.) fail to connect.

---

## Why this exists

VS Code Remote (WSL) runs extensions in a separate process tree.
Shell environment variables alone are not enough.

This helper injects proxy settings into the VS Code Remote server
so that extensions can access the network correctly.

---

## Features

- `proxy on / off / status`
- Works with Clash running on Windows
- Properly injects proxy into VS Code Remote (WSL)
- Safe and reversible
- No system-wide changes

---

## Usage

```bash
proxy on
proxy off
proxy status
