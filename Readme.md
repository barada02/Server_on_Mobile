# Running FastAPI Server on Mobile using Termux

This guide provides step-by-step instructions for setting up and running a FastAPI server on your Android mobile device using Termux.

## Prerequisites

- Android device
- Termux app installed from F-Droid (recommended) or Google Play Store

## Setup Steps

### 1. Update and Upgrade Termux

```bash
pkg update && pkg upgrade
```

### 2. Install Python

```bash
pkg install python
```

### 3. Install pip (if not already installed)

```bash
pkg install python-pip
```

### 4. Install FastAPI and Uvicorn

```bash
pip install fastapi uvicorn
```

### 5. Create Your FastAPI Application

Create a new Python file (e.g., `main.py`):

```bash
nano main.py
```

Add your FastAPI code:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello from FastAPI on Mobile!"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "q": q}
```

Save and exit (Ctrl+X, then Y, then Enter)

### 6. Run the FastAPI Server

```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

Options explained:
- `--host 0.0.0.0`: Makes server accessible from other devices on the same network
- `--port 8000`: Port number (change as needed)
- `--reload`: Auto-reload on code changes (useful for development)

### 7. Access Your API

- **On the same device**: `http://localhost:8000`
- **From another device**: `http://<your-mobile-ip>:8000`
- **Interactive docs**: `http://localhost:8000/docs`
- **Alternative docs**: `http://localhost:8000/redoc`

## Finding Your Mobile IP Address

```bash
ifconfig
```

Look for your IP address under `wlan0` (usually starts with 192.168.x.x)

## Useful Commands

### Stop the server
Press `Ctrl+C` in the terminal

### Run server in background
```bash
nohup uvicorn main:app --host 0.0.0.0 --port 8000 &
```

### Check if server is running
```bash
ps aux | grep uvicorn
```

### Kill background process
```bash
pkill -f uvicorn
```

## Tips

1. **Keep screen on**: Install Termux:Wake Lock to prevent the device from sleeping
2. **Storage access**: Grant storage permissions to save/edit files easily
   ```bash
   termux-setup-storage
   ```
3. **Install additional packages** as needed:
   ```bash
   pip install sqlalchemy pydantic python-multipart
   ```
4. **Use virtual environments** for project isolation:
   ```bash
   pip install virtualenv
   virtualenv venv
   source venv/bin/activate
   ```

## Troubleshooting

- **Port already in use**: Change the port number or kill the existing process
- **Connection refused**: Check firewall settings and ensure `--host 0.0.0.0` is set
- **Package installation fails**: Run `pkg update && pkg upgrade` first
- **Import errors**: Ensure all required packages are installed with pip

## Common FastAPI Dependencies

```bash
pip install python-multipart  # For form data
pip install python-jose[cryptography]  # For JWT tokens
pip install passlib[bcrypt]  # For password hashing
pip install sqlalchemy  # For database ORM
pip install databases  # For async database support
```

## Security Notes

- Don't expose your server to the public internet without proper security measures
- Use authentication and authorization for production APIs
- Keep Termux and all packages updated
- Consider using HTTPS for production (use reverse proxy like nginx)

## Resources

- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Termux Wiki](https://wiki.termux.com/)
- [Uvicorn Documentation](https://www.uvicorn.org/)

