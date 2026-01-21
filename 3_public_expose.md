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

🎉 **The HTTPS URL shown is your PUBLIC endpoint!**

Copy this URL - anyone can access your API through it.

## Step 5: Test From Anywhere

### Test the main endpoint:

Open any browser (on any device anywhere in the world) and visit:

```
https://random-name-abc123.trycloudflare.com
```

You should see your JSON response:

```json
{
  "status": "running",
  "message": "Hello from my Android cloud server"
}
```

### Access Interactive API Documentation:

Visit the auto-generated docs:

```
https://random-name-abc123.trycloudflare.com/docs
```

This opens the Swagger UI where anyone can test your API interactively.

---

## Summary

Now you have:
- ✅ **Session 1**: Running your FastAPI server locally
- ✅ **Session 2**: Running Cloudflare tunnel
- ✅ **Public URL**: Your API is now accessible worldwide via HTTPS

### To Stop Everything:

1. In Session 2: Press `CTRL + C` (stops tunnel)
2. In Session 1: Press `CTRL + C` (stops FastAPI server)

### Important Notes:

⚠️ The tunnel URL changes each time you restart `cloudflared`  
⚠️ Keep both Termux sessions running for continuous access  
⚠️ Your phone must stay connected to the internet  

**Next**: Consider implementing authentication if exposing real services!

---

## 🧠 What You Just Built (This Is Huge)

You now have a complete cloud architecture running on your phone:

```
Internet
  ↓
Cloudflare Edge (HTTPS)
  ↓
Secure Tunnel
  ↓
FastAPI on your Phone
```

### This is identical in concept to:

- **Cloud Run** (Google Cloud)
- **Fly.io**
- **Railway**
- **Render**
- **Heroku**

**But it's running on your phone!** 🤯

---

