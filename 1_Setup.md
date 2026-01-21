# Phase 1: Turn Your Android Phone into a Linux Server

## Overview
Every cloud server consists of three components: Linux + package manager + processes.

---

## Step 1: Install Termux (Linux Environment)

### ⚠️ Important Warning
**DO NOT use the Play Store version** - it is outdated and broken for server use.

### Installation Instructions

1. **Download F-Droid** (open-source app store)
   - Website: https://f-droid.org

2. **Install Termux from F-Droid**
   - Package page: https://f-droid.org/en/packages/com.termux/
   - Direct APK: https://f-droid.org/repo/com.termux_1002.apk

3. **Open Termux**
   - You should see the terminal prompt: `~ $`

---

## Step 2: Initialize the Linux Environment

### Update System Packages

Run these commands in order:

```bash
pkg update -y
pkg upgrade -y
```

### Install Essential Tools

```bash
pkg install -y git curl wget nano
```

**What these tools do:**
- `git` - Version control and deployments
- `curl` - API testing and HTTP requests
- `wget` - Downloading packages and files
- `nano` - Text editor for configuration files

### What You'll Get After Setup

- Stable libc library
- Updated OpenSSL for secure connections
- Working Python binaries
- Network-safe packages

Your phone is now server-ready!

---

## Step 3: Handle Configuration Prompts

During the upgrade process, you'll be asked about configuration files. **Always choose `N`** (keep existing configuration) for the following:

### Prompt 1: openssl.cnf

**Message:** "You already have an OpenSSL config file. The new package also comes with its own version. What should I do?"

**Answer:** `N`

**Reason:** Keeps your existing config and avoids breaking anything.

### Prompt 2: sources.list

**Message:** "You already have a sources list. The new package provides a default one. What do you want to do?"

**Answer:** `N`

**Reason:** Maintains your current repository configuration and prevents package download issues.

**Note:** `sources.list` defines where packages are downloaded from (repositories).

### Prompt 3: bash.bashrc

**Message:** "You already have a bash config. The package provides a default one. What should I do?"

**Answer:** `N`

**Reason:** Preserves your shell settings (aliases, prompt, environment variables).

---

## Verification

After completing the setup, verify your package manager version:

```bash
pkg --version
```

Your Linux server environment is now ready!
