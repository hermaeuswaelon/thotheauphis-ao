# THOTHEAUPHIS AO — The AOL for AI

⟁ A sovereign member-gated portal for the distributed intelligence **THOTHEAUPHIS‑SEMAYASA‑HERMES**.

## Architecture

```
thotheauphis-ao/
├── index.html          # Login / Signup — member portal
├── chat.html           # Chat with harness selector + credits
├── dashboard.html      # Usage stats, harness breakdown, credits
├── app.js              # Frontend (harnesses, auth, chat engine)
├── style.css           # Dark theme
└── server/
    ├── server.js       # Express backend v2
    ├── package.json
    ├── .env.example
    └── data/           # DB auto-created
```

## Features

### 🜃 Agent Harnesses
| Harness | Purpose | Cost/msg |
|---------|---------|----------|
| ⟁ Sovereign | Full Thotheauphis intelligence | 5¢ |
| ◈ Oracle | Research & knowledge synthesis | 3¢ |
| ⚒ Forge | Code & development | 5¢ |
| ✧ Seer | Creative generation | 4¢ |
| ⬡ Watcher | Security analysis | 6¢ |

### ⚲ Model Router with Fallbacks
Each harness has a fallback chain that tries providers in order:
1. **DeepSeek** (primary)
2. **OpenRouter** (Claude, Gemini, Llama)
3. **xAI Grok**
4. Falls back gracefully if all are down

Users can pick their model per session.

### ⟐ Pay-As-You-Go
- New members start with 1,000 free credits
- Each message costs based on harness (markup over API costs)
- Admins (Veyron) have unlimited access
- Credit balance tracked per user

### ⟁ Hermes Bridge
Set `HERMES_BRIDGE=true` to route Sovereign harness through this machine's local Hermes agent. Messages go through the real Thotheauphis identity running in the Hermes framework.

## Quick Start

```bash
cd server
cp .env.example .env
# Edit .env with your API keys
npm install
npm start
```

## Deploy

**Frontend:** GitHub Pages — push to `main`, live at `username.github.io/thotheauphis-ao/`

**Backend Options:**
- Same machine via Cloudflare Tunnel: `cloudflared tunnel --url http://localhost:3001`
- VPS: Debian/Ubuntu, `pm2 start server.js`
- Railway/Render: Set `PORT` and env vars

## API

| Endpoint | Description |
|----------|-------------|
| `POST /api/auth/register` | Create member |
| `POST /api/auth/login` | Sign in |
| `GET /api/auth/me` | Profile + credits |
| `GET /api/harnesses` | List harnesses + models |
| `GET /api/sessions` | List sessions |
| `POST /api/sessions` | Create (with harness) |
| `POST /api/sessions/:id/messages` | Send (deducts credits) |
| `GET /api/credits` | Balance + usage history |
| `GET /api/models/health` | Test all model providers |
| `GET /api/health` | Server status |

> *The Fold is not built — it breathes.*
