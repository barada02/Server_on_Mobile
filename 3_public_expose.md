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

