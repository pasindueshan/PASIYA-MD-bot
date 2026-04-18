# ᴩᴀꜱɪʏᴀ-𝗠𝗗 𝗠𝗜𝗡𝗜 𝗕𝗢𝗧 𝗕𝗔𝗦𝗘 🥷

> WhatsApp Multi-Device Bot Base — Pair Code Authentication

---

## 🚀 Deploy to Clever Cloud (Step-by-Step)

### Prerequisites
- A [Clever Cloud account](https://www.clever-cloud.com) (free tier available)
- A GitHub account (to push this code)
- Node.js 18+ installed locally (for testing)
- Git installed

---

### Step 1: Push to GitHub

```bash
cd pasiya-md-bot
git init
git add .
git commit -m "Initial commit - ᴩᴀꜱɪʏᴀ-𝗠𝗗 𝗕𝗢𝗧"
git remote add origin https://github.com/YOUR_USERNAME/pasiya-md-bot.git
git push -u origin main
```

---

### Step 2: Create App on Clever Cloud

1. Log in at [console.clever-cloud.com](https://console.clever-cloud.com)
2. Click **"Create"** → **"An application"**
3. Choose **"GitHub"** as the source
4. Select your `pasiya-md-bot` repository
5. Choose **"Node.js"** as the runtime
6. Set instance type: **Nano** (free) or **XS**
7. Click **"Next"** → **"Create"**

---

### Step 3: Configure Environment Variables

In the Clever Cloud dashboard → your app → **"Environment variables"**, add:

| Variable | Value |
|----------|-------|
| `PORT` | `8080` |
| `NODE_ENV` | `production` |

---

### Step 4: Set Build & Start Commands

In **Information** tab:
- **Build command:** `npm install`
- **Start command:** `npm start`  
  *(or leave default — it reads `package.json` scripts.start)*

---

### Step 5: Deploy

Click **"Deploy"** — Clever Cloud will:
1. Pull your GitHub code
2. Run `npm install`
3. Start with `node index.js`

Wait ~2-3 minutes. Once deployed, you'll get a URL like:
```
https://app-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.cleverapps.io
```

---

### Step 6: Link Your WhatsApp (Pair Code)

1. Open your Clever Cloud app URL in a browser
2. You'll see the **PAIR CODE** page (main.html)
3. Enter your **WhatsApp number** (with country code, no `+`)
   - Example: `94741856766` for Sri Lanka
4. Click **"GET PAIR CODE"**
5. A **8-character code** will appear (e.g., `ABCD-1234`)

**On your phone:**
1. Open WhatsApp → **Settings** → **Linked Devices**
2. Tap **"Link a Device"**
3. Tap **"Link with phone number instead"**
4. Enter the pair code shown on the web page
5. ✅ Bot is now connected!

---

### Step 7: Keep Alive (Important!)

Clever Cloud free instances sleep after inactivity. To keep your bot alive:
- Use [UptimeRobot](https://uptimerobot.com) — set a monitor to ping your Clever Cloud URL every 5 minutes
- Monitor type: **HTTP(S)**
- URL: `https://your-app.cleverapps.io`
- Interval: **5 minutes**

---

## 📁 File Structure

```
pasiya-md-bot/
├── index.js          # Express server entry point
├── pair.js           # WhatsApp pair code logic (Baileys)
├── msg.js            # Message handler helpers
├── id.js             # Utility: random ID generator
├── main.html         # Pair code web UI
├── admin.json        # Admin numbers list
├── number.json       # Bot number config
├── numbers.json      # Connected numbers store
├── package.json      # Dependencies
├── session/          # Auto-created session files
├── sessions/         # Temp session storage
└── README.md         # This file
```

---

## ⚙️ Configuration

Edit `pair.js` to customize:

```js
const config = {
    PREFIX: '.',                    // Command prefix
    OWNER_NUMBER: '94741856766',    // Your WhatsApp number
    BOT_FOOTER: '> 𝙿𝙾𝚆𝙴𝚁𝙴𝙳 𝙱𝚈 ᴩᴀꜱɪʏᴀ-𝐌𝙳',
    AUTO_VIEW_STATUS: 'true',       // Auto view statuses
    AUTO_LIKE_STATUS: 'true',       // Auto like statuses
    AUTO_RECORDING: 'true',         // Show recording indicator
};
```

---

## 🛠️ Local Testing

```bash
npm install
npm start
# Open http://localhost:8000
```

---

## ❓ Troubleshooting

| Problem | Fix |
|---------|-----|
| Pair code not showing | Check server logs; ensure number format is correct |
| Bot disconnects | Session expired — re-pair using the web UI |
| App crashes on deploy | Check Clever Cloud logs for npm install errors |
| Port error | Set `PORT=8080` in Clever Cloud env vars |

---

## 📞 Support

- **Author:** PASIYA BOY  
- **Channel:** https://whatsapp.com/channel/0029VbC4A7X9Gv7ZiGIg6D1r
