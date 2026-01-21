# Phase 3: Expose Server Publicly

This phase shows you how to make your local FastAPI server accessible from anywhere on the internet using Cloudflare Tunnel.

## Step 1: Keep Your API Running

Make sure your FastAPI server is already running in one Termux session:

```bash
cd ~/cloud_server
source venv/bin/activate
uvicorn main:app --host 0.0.0.0 --port 8000
```

Keep this session running. Do not close it.

## Step 2: Open a NEW Termux Session

To run the tunnel while keeping your server active:

1. **Swipe from left** in Termux
2. Select **"New session"**

💡 This is like opening a second SSH tab on a server - your first session continues running while you work in the second.

## Step 3: Install Cloudflare Tunnel

### Why not ngrok?

❌ **Note**: `ngrok` doesn't work in Termux. If you try `pkg install ngrok`, you'll get:

```
E: Unable to locate package ngrok
```

