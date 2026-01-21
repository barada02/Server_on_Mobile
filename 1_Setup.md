# Phase 1: Turn Your Android Phone into a Linux Server

## Overview
Every cloud server consists of three components: Linux + package manager + processes.

---

## Step 1: Install Termux (Linux Environment)

### ⚠️ Important Warning
**DO NOT use the Play Store version** - it is outdated and broken for server use.

### Installation Instructions

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

### What Will Happen Immediately After Upgrade

Once it finishes, you’ll have:

Stable libc

Updated OpenSSL

Working Python binaries (important later)

Network-safe packages

Which means:

Your phone is now server-ready

### Tiny Check After It Completes (Don’t Run Yet)

I’ll ask you to run:
pkg --version

> At the time of the upgrade :

(image place holder)

it will ask about 

openssl.cnf

Termux is saying:

“You already have an OpenSSL config file.
The new package also comes with its own version.
What should I do?”

``` N ```

Why N is correct

Keeps your existing config

Safest option

Avoids breaking anything

Standard DevOps practice on servers

Even on AWS / Ubuntu servers, we usually keep current config unless we know what we’re doing.
What NOT to Choose (For Now)

Y / I → overwrites config (unnecessary)

D → shows diff (not needed)

Z → drops into shell (confusing now)

### it will ask for 

sources.list Means

sources.list defines where packages are downloaded from (repositories).

Termux is asking:

“You already have a sources list.
The new package provides a default one.
What do you want to do?”

This happens on every real Linux server during upgrades.

Choose : N

Why?

Keeps your current repository configuration

Avoids breaking package downloads

Safest option

Industry best practice unless you explicitly changed repos


### Then it will ask for
bash.bashrc 

What bash.bashrc Is

bash.bashrc controls:

Shell behavior

Aliases

Prompt settings

Environment variables

Termux is asking:

“You already have a bash config.
The package provides a default one.
What should I do?”

choose : N 