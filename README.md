<div align="center">

<pre>
          

  🛡️  TELEGRAM GROUP MANAGEMENT BOT  🛡️
</pre>

<p align="center">
<img src="https://readme-typing-svg.herokuapp.com?font=Courier+New&weight=700&size=18&duration=4000&pause=500&color=00D4FF&center=true&vCenter=true&width=650&lines=🛡️+Open-Source+Group+Management+Bot;⚡+Raw+HTTP+Webhook+%2B+Flask;🗄️+MongoDB+Per-Group+Storage;📝+Notes%2C+Filters+%26+Blacklist;🚀+Deploy+Anywhere+in+Minutes" alt="typing" />
</p>

</div>

---

[![Render](https://img.shields.io/badge/Deploy-Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)](https://render.com/deploy?repo=https://github.com/kurukshethrathepride/KustRobot)


## ✨ Features

| Feature | Description |
|---|---|
| 🛡️ **Full Moderation** | ban, tban, kick, mute, tmute, warn, promote, demote |
| ⚠️ **Warning System** | Auto-ban at configurable warn threshold |
| 🎯 **Content Locks** | Lock links, media, stickers, polls, forwards per-group |
| 🚫 **Blacklist** | Word blacklist with auto-delete & auto-warn |
| 📝 **Notes System** | Save & retrieve notes with `#name` triggers (FallenRobot-style) |
| 🔤 **Custom Filters** | Keyword auto-reply filters stored per-group |
| 👋 **Welcome Messages** | Customizable with `{name}` `{id}` `{title}` placeholders |
| 🤖 **Captcha Verification** | Math captcha on join with auto-kick timeout |
| 📌 **Pin Management** | pin, unpin, unpinall, purge ranges, cleanup |
| ⏱️ **Slowmode** | Set message cooldown via `/slowmode <seconds>` |
| 🎉 **Fun Commands** | roll, flip, 8ball, hug, slap, pat, kiss, meme, quote, poll |
| 📊 **Statistics** | Group stats, user lookup, admin list |
| 🗄️ **MongoDB** | Per-group persistent settings, warnings, notes, filters |
| ⚡ **Webhook-based** | Raw HTTP + Flask — no polling, instant updates |
| 🔧 **Modular** | 9 clean modules, easy to extend or disable |

---

## 📁 Project Structure

```
KustRobot/
├── main.py                  ← Flask app + webhook dispatcher
├── config.py                ← Environment variables & constants
├── requirements.txt         ← Flask, requests, pymongo
├── database/
│   └── mongo.py             ← MongoDB collections manager
├── utils/
│   ├── api.py               ← Raw HTTP Telegram API helper with retries
│   └── helpers.py           ← is_admin, resolve_target, get/set_chat_setting
└── modules/
    ├── admin.py             ← ban, kick, mute, warn, promote, demote
    ├── greetings.py         ← welcome messages, captcha verification
    ├── rules.py             ← setrules, rules, clearrules
    ├── filters.py           ← lock/unlock, custom keyword filters
    ├── notes.py             ← save, get, #triggers (FallenRobot-style)
    ├── blacklist.py         ← word blacklist with auto-warn
    ├── pins.py              ← pin, unpin, purge, cleanup, slowmode
    ├── fun.py               ← roll, 8ball, hug, slap, meme, quote
    └── misc.py              ← start, help, id, whois, stats
```

---

## 🚀 Quick Deploy

> **Fork this repo first before deploying!**

<div align="center">

[![Deploy on Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/kurukshethrathepride/KustRobot) [![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new?template=https://github.com/kustbots/KustRobot) [![Deploy on Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/kustbots/KustRobot) [![Deploy on Koyeb](https://www.koyeb.com/static/images/deploy/button.svg)](https://app.koyeb.com/deploy?type=git&repository=github.com/kustbots/KustRobot&branch=main&name=kust-robot)

</div>

---

## 🔧 Environment Variables

Set these on your platform or in a `.env` file:

| Variable | Required | Description |
|---|---|---|
| `BOT_TOKEN` | ✅ | Your Telegram bot token from [@BotFather](https://t.me/BotFather) |
| `WEBHOOK_SECRET` | ✅ | Any random secret string for webhook security |
| `MONGO_URI` | ✅ | MongoDB connection string (local or Atlas) |
| `ADMIN_IDS` | ✅ | Your Telegram user ID(s), comma-separated |
| `DB_NAME` | ❌ | Database name (default: `kustrobot`) |
| `PORT` | ❌ | Server port (default: `5000`) |

---

## 📦 Platform-Specific Deployment

### ☁️ Render (Recommended)

1. Fork this repo
2. Go to [render.com](https://render.com) → **New Web Service**
3. Connect your forked repo
4. Set **Build Command:** `pip install -r requirements.txt`
5. Set **Start Command:** `python main.py`
6. Add environment variables in the dashboard
7. Deploy — Render gives you a public HTTPS URL
8. Set your webhook:
```bash
curl -X POST "https://api.telegram.org/bot<BOT_TOKEN>/setWebhook" \
     -d "url=https://your-app.onrender.com/webhook/<WEBHOOK_SECRET>"
```

---

### 🚂 Railway

1. Fork this repo
2. Go to [railway.app](https://railway.app) → **New Project → Deploy from GitHub**
3. Connect your forked repo
4. Add environment variables under **Variables**
5. Add a **MongoDB** plugin from Railway's marketplace (or use Atlas)
6. Railway auto-detects Python and deploys — grab your public URL
7. Set your webhook using the Railway URL

---

### 🟣 Heroku

1. Fork this repo
2. Go to [heroku.com](https://heroku.com) → **New App**
3. Connect your GitHub fork under **Deploy** tab
4. Set environment variables under **Settings → Config Vars**
5. Set **buildpack** to `heroku/python`
6. Enable **Automatic Deploys** or deploy manually
7. Set your webhook using `https://your-app.herokuapp.com/webhook/<SECRET>`

> **Note:** Add a `Procfile` if not present:
> ```
> web: python main.py
> ```

---

### 🔵 Koyeb

1. Fork this repo
2. Go to [koyeb.com](https://koyeb.com) → **Create App**
3. Select **GitHub** → connect your fork
4. Set **Run command:** `python main.py`
5. Add environment variables in the app settings
6. Koyeb gives a public HTTPS URL — set your webhook to it

---

### 🖥️ VPS / Self-Hosted

```bash
# 1. Clone your fork
git clone https://github.com/YOUR_USERNAME/KustRobot
cd KustRobot

# 2. Install dependencies
pip install -r requirements.txt

# 3. Set environment variables
export BOT_TOKEN="your_token"
export WEBHOOK_SECRET="your_secret"
export MONGO_URI="mongodb://localhost:27017"
export ADMIN_IDS="your_user_id"

# 4. Run (use tmux or screen to keep it alive)
tmux new -s kustrobot
python main.py
# Press Ctrl+B then D to detach
```

**Set up HTTPS with nginx + Let's Encrypt:**
```bash
# Install nginx + certbot
sudo apt install nginx certbot python3-certbot-nginx

# Get SSL certificate
sudo certbot --nginx -d yourdomain.com

# Add nginx reverse proxy to port 5000
# Then set webhook to: https://yourdomain.com/webhook/<SECRET>
```

---

### 🍃 MongoDB Setup

**Option 1 — MongoDB Atlas (Cloud, Free):**
1. Go to [mongodb.com/atlas](https://www.mongodb.com/atlas)
2. Create a free cluster
3. Get your connection string: `mongodb+srv://user:pass@cluster.mongodb.net/kustrobot`
4. Set this as `MONGO_URI`

**Option 2 — Local MongoDB:**
```bash
# Install MongoDB
sudo apt install mongodb

# Start service
sudo systemctl start mongodb

# Use this URI:
# mongodb://localhost:27017
```

---

## 📋 Commands

### 🛡️ Moderation
| Command | Description |
|---|---|
| `/ban @user` | Ban a user |
| `/tban @user 1h` | Temporarily ban (use `s/m/h/d`) |
| `/unban @user` | Unban a user |
| `/kick @user` | Kick a user |
| `/mute @user` | Mute a user |
| `/tmute @user 30m` | Temporarily mute |
| `/unmute @user` | Unmute a user |
| `/warn @user <reason>` | Warn a user |
| `/unwarn @user` | Remove one warning |
| `/warnings @user` | Check warning count |
| `/clearwarns @user` | Clear all warnings |
| `/setwarnlimit <n>` | Set auto-ban threshold |
| `/promote @user` | Promote to admin |
| `/demote @user` | Demote admin |
| `/banlist` | List banned users |
| `/getadmins` | List all admins |

### ⚙️ Settings
| Command | Description |
|---|---|
| `/setwelcome <msg>` | Set welcome message (`{name}` `{id}` `{title}`) |
| `/welcome on\|off` | Toggle welcome messages |
| `/setcaptcha on\|off` | Toggle captcha for new members |
| `/setrules <text>` | Set group rules |
| `/rules` | Show group rules |
| `/clearrules` | Clear group rules |
| `/setwarnlimit <n>` | Set warning threshold before auto-ban |

### 🔒 Content Control
| Command | Description |
|---|---|
| `/lock links\|media\|stickers\|all\|forward\|polls` | Lock content type |
| `/unlock <type>` | Unlock content type |
| `/locks` | Show current lock status |
| `/filter <keyword> <reply>` | Add auto-reply keyword filter |
| `/stop <keyword>` | Remove a filter |
| `/filters` | List all active filters |
| `/addblacklist <word>` | Add word to blacklist |
| `/rmblacklist <word>` | Remove from blacklist |
| `/blacklist` | List blacklisted words |

### 📝 Notes (FallenRobot-style)
| Command | Description |
|---|---|
| `/save <name> <content>` | Save a note |
| `/save <name>` (reply) | Save replied message as note |
| `#name` | Retrieve note instantly |
| `/get <name>` | Get a note by name |
| `/delnote <name>` | Delete a note |
| `/notes` | List all saved notes |

### 📌 Pins & Cleanup
| Command | Description |
|---|---|
| `/pin` | Pin replied message |
| `/unpin` | Unpin current pinned message |
| `/unpinall` | Unpin all pinned messages |
| `/purge` | Delete messages from reply to now |
| `/cleanup <n>` | Delete last n messages (max 100) |
| `/slowmode <seconds>` | Set slowmode (0 to disable) |

### 🎉 Fun
| Command | Description |
|---|---|
| `/roll [sides]` | Roll a dice |
| `/flip` or `/toss` | Flip a coin |
| `/8ball <question>` | Magic 8-ball |
| `/hug [@user]` | Send a hug |
| `/slap [@user]` | Slap someone |
| `/pat [@user]` | Pat someone |
| `/kiss [@user]` | Send a kiss |
| `/meme` | Random meme |
| `/quote` | Inspirational quote |
| `/poll <q>\|opt1\|opt2` | Create a poll |
| `/stickerid` | Get sticker file ID |

### ℹ️ Utility
| Command | Description |
|---|---|
| `/start` | Bot info and overview |
| `/help` | Interactive help menu |
| `/id` | Your user & chat ID |
| `/whois [@user]` | User info and warnings |
| `/stats` | Group statistics |

---

## 🗄️ Database Collections

| Collection | Stores |
|---|---|
| `chat_settings` | Per-group settings (welcome, rules, locks, warn threshold) |
| `warnings` | User warnings with timestamps and reasons |
| `banned_users` | Banned user records per group |
| `captcha_challenges` | Pending captcha verifications |
| `notes` | Saved notes (text, photos, videos, stickers, etc.) |
| `blacklist` | Blacklisted words per group |
| `filters` | Custom keyword auto-reply filters |

---

## ⚙️ Tech Stack

| Component | Technology |
|---|---|
| Language | Python 3.7+ |
| Web Framework | Flask 2.3.3 |
| Database | MongoDB 4.6+ (via pymongo) |
| HTTP Client | Requests 2.31.0 |
| Bot API | Raw Telegram HTTP API |

---

## 📜 License

GNU General Public License v3.0 — See [LICENSE](LICENSE)

---

## 🤝 Contributing

Pull requests are welcome. For major changes, open an issue first.

1. Fork the repo
2. Create your branch: `git checkout -b feature/my-feature`
3. Commit changes: `git commit -m "Added my feature"`
4. Push: `git push origin feature/my-feature`
5. Open a Pull Request

---

## 📞 Support

<div align="center">

[![Updates Channel](https://img.shields.io/badge/Updates-@kustbots-blue?style=for-the-badge&logo=telegram)](https://t.me/kustbots)
[![Support Group](https://img.shields.io/badge/Support-@kustbotschat-blue?style=for-the-badge&logo=telegram)](https://t.me/kustbotschat)
[![GitHub Issues](https://img.shields.io/badge/Issues-GitHub-black?style=for-the-badge&logo=github)](https://github.com/kustbots/KustRobot/issues)

</div>

---

<div align="center">
Made with ❤️ by <a href="https://github.com/kustbots">@kustbots</a>
</div>
