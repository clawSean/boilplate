# 🦞 OpenClaw QMD Memory Setup Guide

This guide covers how to swap the default OpenClaw memory system for the **QMD backend**—a local-first search sidecar that combines BM25 (keyword) + Vector (semantic) search with local reranking.

---

## 🏗️ Prerequisites

### 1. Bun Runtime
QMD is built on Bun.
- **Linux/macOS:**
  ```bash
  curl -fsSL https://bun.sh/install | bash
  ```
- **Windows (WSL2 recommended):** See [bun.sh](https://bun.sh) for details.

### 2. SQLite (with Extension Support)
QMD needs a modern SQLite that allows loading extensions.
- **Ubuntu/Debian:** `sudo apt install sqlite3`
- **macOS:** `brew install sqlite` (The Homebrew version is preferred over the system-preinstalled one).

### 3. Compiler Toolset
Required for building `node-llama-cpp` (the local inference engine).
- **Ubuntu/Debian:** `sudo apt install build-essential`
- **macOS:** `xcode-select --install`

---

## 📦 Installation

### 1. Install QMD CLI
Install the latest version directly from GitHub via Bun:
```bash
bun install -g https://github.com/tobi/qmd
```

### 2. Make QMD Accessible
The OpenClaw gateway service needs to find the `qmd` binary. Since Bun installs to your home directory, it’s best to create a system-wide symlink or wrapper.

**Linux Example:**
```bash
sudo ln -s $HOME/.bun/bin/bun /usr/local/bin/bun
sudo ln -s $HOME/.bun/bin/qmd /usr/local/bin/qmd
```

**macOS Note:** If using Homebrew or a managed PATH, ensure `/usr/local/bin` is in the gateway's environment.

---

## ⚙️ Configuration

Update your `~/.openclaw/openclaw.json` to enable the backend. 

**Critical:** If you currently have `agents.defaults.memorySearch` settings, keep them—but add the top-level `"memory"` key shown below:

```json
{
  "memory": {
    "backend": "qmd",
    "citations": "auto",
    "qmd": {
      "command": "/usr/local/bin/qmd",
      "includeDefaultMemory": true,
      "searchMode": "search",
      "update": {
        "interval": "5m",
        "onBoot": true
      },
      "limits": {
        "maxResults": 6
      }
    }
  }
}
```

---

## 🚀 First Run & Warm-up

QMD downloads local GGUF models (~1GB+) on the first search/embed. To avoid timing out the OpenClaw gateway, run the initial sync manually in your terminal first.

1. **Initialize the collection:**
   ```bash
   qmd collection add memory-root ~/.openclaw/workspace
   ```

2. **Run the initial update & embedding:**
   ```bash
   qmd update
   qmd embed
   ```
   *Note: On a Mac mini (Apple Silicon), this will be very fast due to Metal acceleration. On a VPS without a GPU, this will run on the CPU and take longer.*

3. **Restart OpenClaw Gateway:**
   ```bash
   openclaw gateway restart
   ```

---

## 🔍 Verification

Check if the gateway correctly armed the sidecar:
```bash
openclaw status
```
Look for: `Memory: ... plugin memory-core · vector ready (backend: qmd)`

Try a search via the CLI to confirm it's hitting the new index:
```bash
openclaw memory search "your query"
```

---

## 💡 Troubleshooting & Platform Tips

- **Mac Mini (M1/M2/M3):** You get native GPU acceleration via Metal. QMD will be significantly faster at reranking and vectorizing than on a standard VPS.
- **Deep Freeze:** If the first search feels like it hung, check `qmd status`. It likely just needs more time to download the expansion and reranker models.
- **Permissions:** If you see `EACCES` or `command not found` in the gateway logs, double-check your symlinks in `/usr/local/bin`.
