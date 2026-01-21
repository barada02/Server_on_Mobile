# Phase 2: Python Installation

## Install Python and pip

Install Python along with pip package manager in a single command:

```bash
pkg install -y python python-pip
```

### What this command does:
- `pkg install`: Termux package installation command
- `-y`: Automatically answers "yes" to all prompts
- `python`: Installs the latest Python version available in Termux
- `python-pip`: Installs pip (Python package manager)

### Verify Installation

After installation completes, verify Python is installed correctly:

```bash
python --version
```

Check pip version:

```bash
pip --version
```

You should see version numbers for both Python and pip, confirming successful installation.

## Important: Prepare for FastAPI Installation

Before installing FastAPI, you may encounter errors related to Rust and pydantic-core during the installation process. To prevent these issues, install the required build tools:

```bash
pkg install clang rust binutils
```

### What this solves:
- **Rust compiler errors**: FastAPI's dependency `pydantic-core` requires Rust to compile
- **Build tool issues**: Clang and binutils provide necessary compilation tools
- **Installation failures**: Prevents "error: can't find Rust compiler" and similar build errors

### Why this is needed:
Pydantic (a core dependency of FastAPI) uses Rust extensions for better performance. Without these tools, pip will fail to build the required packages.

---
# Phase 3: 

## Step 1: Create Project Directory

Create a dedicated directory for your cloud server:

```bash
mkdir cloud_server
```

Navigate into the directory:

```bash
cd ~/cloud_server
```

