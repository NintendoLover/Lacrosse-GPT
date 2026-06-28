# LAX GPT — Deployment Guide

A single-page AI lacrosse expert powered by Claude with live web search.

## Project Structure

```
lacrosse-gpt-site/
├── api/
│   └── chat.js          ← Vercel serverless function (API proxy)
├── public/
│   └── index.html       ← Full website + chat app
├── vercel.json          ← Vercel routing config
├── package.json
└── README.md
```

## Deploy to Vercel (Free — ~2 minutes)

### Option A: GitHub (recommended)

1. Push this folder to a GitHub repo
2. Go to vercel.com → "Add New Project" → Import your repo
3. Add environment variable:
   - Key: `ANTHROPIC_API_KEY`
   - Value: your Anthropic API key (get one at console.anthropic.com)
4. Click Deploy

Done — you get a live URL like `https://lacrosse-gpt.vercel.app`

### Option B: Vercel CLI

```bash
npm install -g vercel
cd lacrosse-gpt-site
vercel
# Follow prompts, then add env var:
vercel env add ANTHROPIC_API_KEY
```

## Get Your Anthropic API Key

1. Go to console.anthropic.com
2. Sign up / log in
3. Go to API Keys → Create Key
4. Copy and paste into Vercel as `ANTHROPIC_API_KEY`

## Custom Domain (Optional)

In Vercel dashboard → your project → Settings → Domains → Add your domain.

## How It Works

- `public/index.html` — full website with chat UI, RSS fetch, quick chips
- `api/chat.js` — serverless function that proxies requests to Anthropic API
  - Keeps your API key secret (server-side only)
  - Passes web search beta header automatically
  - Handles CORS so the browser can call it

## Features

- 🟢 RSS auto-fetch from PLL, Inside Lacrosse, USA Lacrosse on every load
- 🔍 Live web search for current standings, scores, news, trades
- 🎙️ YouTuber-inspired personality (Pehlke + Rabil + ECD + TLN)
- 🥍 10 lacrosse topics covered, off-topic declined with swagger
- 📡 Sources: premierlacrosseleague.com, usalacrosse.com, lacrossereference.com, insidelacrosse.com, laxpower.com, espn.com/pll, ncaa.com
