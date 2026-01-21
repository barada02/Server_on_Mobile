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

### ✅ Solution: Use Cloudflare Tunnel

Install `cloudflared` instead:

```bash
pkg install -y cloudflared
```

**What is Cloudflare Tunnel?**
- Free tunneling service by Cloudflare
- Creates secure HTTPS connection to your local server
- No account or signup required for quick tunnels
- Automatically provides SSL/TLS encryption

## Step 4: Start the Tunnel

In Session 2 (the new Termux session), run:

```bash
cloudflared tunnel --url http://localhost:8000
```

You'll see output similar to:

```
2026-01-22T10:30:45Z INF Thank you for trying Cloudflare Tunnel...
2026-01-22T10:30:46Z INF Connection established
2026-01-22T10:30:46Z INF 
+--------------------------------------------------------------------------------------------+
|  Your quick Tunnel has been created! Visit it at (it may take some time to be reachable):  |
|  https://random-name-abc123.trycloudflare.com                                              |
+--------------------------------------------------------------------------------------------+
```

