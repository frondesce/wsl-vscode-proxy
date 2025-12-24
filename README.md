# WSL + VS Code Proxy Helper

🌐 **English** | [中文版](#中文版)

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

## Installation

Run the installer script:

```bash
bash install.sh
```

Then reload your shell:

```bash
source ~/.bashrc
```

**Important:**  
After enabling or disabling the proxy,  
you must reload the VS Code WSL window or restart VS Code  
for extensions to pick up the change.

---

## Usage

```bash
proxy on
proxy off
proxy status
```

### Custom proxy port

By default, the script uses port `7890`.

If your proxy is running on a different port, you can specify it via
the `PORT` environment variable:

```bash
PORT=7891 proxy on
```

---

## Notes

- Designed for **WSL2 + VS Code Remote**
- Assumes your proxy (e.g. Clash) is running on Windows
- Proxy changes affect:
  - current WSL shell (immediately)
  - VS Code extensions (after reload)

---

# 中文版

🌐 [English](#wsl--vs-code-proxy-helper) | **中文版**

一个用于**正确开启 / 关闭 HTTP 代理**的小工具，适用于：

- WSL Shell 环境
- VS Code Remote（WSL）扩展运行环境

用于解决以下常见问题：

> WSL 终端中代理已生效，  
> 但 VS Code 扩展（Copilot、Codex 等）无法联网。

---

## 为什么需要这个工具？

VS Code Remote（WSL）中的扩展运行在**独立的进程树**中。  
仅在 Shell 中设置代理环境变量并不足以让扩展生效。

本工具会将代理配置**注入到 VS Code Remote Server 环境中**，  
从而确保扩展能够正常访问网络。

---

## 功能特性

- 提供统一命令：`proxy on / off / status`
- 适用于 Windows 上运行的 Clash 等代理工具
- 正确配置 VS Code Remote（WSL）的代理环境
- 可随时开启 / 关闭，安全可逆
- 不修改任何系统级配置

---

## 安装方法

运行安装脚本：

```bash
bash install.sh
```

然后重新加载 shell：

```bash
source ~/.bashrc
```

**注意：**  
每次开启或关闭代理后，  
需要 **Reload VS Code 的 WSL 窗口** 或重启 VS Code，  
扩展侧的代理配置才会生效。

---

## 使用方式

```bash
proxy on
proxy off
proxy status
```

### 自定义代理端口

默认情况下，脚本使用端口 `7890`。

如果你的代理运行在其他端口，可以通过设置 `PORT` 环境变量来指定：

```bash
PORT=7891 proxy on
```

---

## 说明

- 本工具适用于 **WSL2 + VS Code Remote**
- 默认假设代理程序（如 Clash）运行在 Windows 上
- 代理配置影响范围：
  - 当前 WSL Shell（立即生效）
  - VS Code 扩展（需 Reload 后生效）
