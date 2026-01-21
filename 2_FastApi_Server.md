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

## Step 2: Set Up Virtual Environment

Create a virtual environment:

```bash
python -m venv venv
```

Activate the virtual environment:

```bash
source venv/bin/activate
```

You should see `(venv)` prefix in your terminal:

```bash
(venv) $
```

## Step 3: Install FastAPI and Uvicorn

Install both packages using pip:

```bash
pip install fastapi uvicorn
```

This will install:
- **FastAPI**: Modern web framework for building APIs
- **Uvicorn**: Lightning-fast ASGI server

## Step 4: Create Your API Application

Create a new file called `main.py`:

```bash
nano main.py
```

Add the following code:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def root():
    return {
        "status": "running",
        "message": "Hello from my Android cloud server"
    }
```

### Save the file:
1. Press `CTRL + O` → Press `Enter` (to write/save)
2. Press `CTRL + X` (to exit nano)

## Step 5: Run the Server

Start your FastAPI server:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

You should see output like:

```
INFO:     Started server process [xxxxx]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)
```

🎉 **Your phone is now running a cloud API!**

## Step 6: Test Your Server

### Test from the same phone:

Open your mobile browser and navigate to:

```
http://127.0.0.1:8000
```

You should see JSON output:

```json
{
  "status": "running",
  "message": "Hello from my Android cloud server"
}
```
