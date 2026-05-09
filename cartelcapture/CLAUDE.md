# Cartel Capture — Project Memory

## Golden Rules
- **ALWAYS ask before changing video cards.** Never assume a video is live or coming soon. Always ask for: YouTube ID, thumbnail filename, and title before touching any card.
- **ALWAYS ask before adding or removing content.** Don't infer — confirm.
- **Never change video card status, links, or thumbnails without explicit instruction.**
- Read this file at the start of every session.

---

## How the Site Works

### Three-layer deployment
1. **Local files** → `~/Documents/cartelcapture/` — edit files here
2. **GitHub** → `dcforklift-bit/cartelcapture` (repo), file path `cartelcapture/index.html` — the Electron app reads/writes here
3. **Cloudflare Pages** → live at `https://cartelcapture.tv` — deployed via Cloudflare Pages (project: `weathered-rain-1c48`)

### Electron Desktop App
- Located at `/Applications/Cartel Capture.app`
- Reads `index.html` from **local file first** (`~/Documents/cartelcapture/index.html`), then GitHub fallback
- When user hits Publish in the app → writes locally AND pushes to GitHub
- App config: `~/Library/Application Support/cartelcapture-app/config.json` (stores Resend API key)

### Deploy command (local → Cloudflare Pages)
```bash
cd ~/Documents/cartelcapture && bash deploy.sh
```

### Push local changes to GitHub (if needed manually)
The app handles this on Publish. If pushing manually via Claude Code, use the GitHub API with token from `main.js`.

---

## File Structure
```
~/Documents/cartelcapture/
├── index.html          ← entire site (single HTML file)
├── logo.png
├── Cartel_Capture_BG.jpg
├── thumb1.png          ← Los Zetas video thumbnail
├── thumb2.png          ← Most Brutal Woman thumbnail
├── thumb3.png          ← Pinochet thumbnail
├── 1280x720-ssofficer-king-of-cocaine.png
├── 788-million-bribes.png
├── the-bribery-office.png
├── robots.txt
├── sitemap.xml
├── llms.txt
├── deploy.sh
└── CLAUDE.md           ← this file
```

---

## Videos — Current State
> ⚠️ Always confirm current status with user before editing. User maintains this.

| # | Title | Status | YouTube ID | Thumbnail |
|---|---|---|---|---|
| 1 | How Special Forces Training Created Los Zetas | Live | `dhRmWg1AFkU` | `thumb1.png` |
| 2 | The Most Brutal Woman in Narco History | Live | `RFRCb5ALUog` | `thumb2.png` |
| 3 | Pinochet's Kill Team Operated Inside the U.S. Capital | Live | `zyhLyU6dGAE` | `thumb3.png` |
| 4 | The Bribery Office | Live | `MTybm9PwNcM` | `788-million-bribes.png` |
| 5 | The SS Officer: King of Cocaine | **Ask user** | **Ask user** | `1280x720-ssofficer-king-of-cocaine.png` |
| 6 | The Most Feared Man in Mexico (Z-40) | **Ask user** | **Ask user** | **Ask user** |
| 7 | Escobar video | **Ask user** | **Ask user** | **Ask user** |

---

## Citations Page
Each live video has a citation group in `index.html`. Citation groups must match video titles exactly.

Current citation groups (in order):
1. How Special Forces Training Created Los Zetas
2. The Most Brutal Woman in Narco History
3. Pinochet's Kill Team Operated Inside the U.S. Capital
4. The SS Officer: King of Cocaine
5. The Bribery Office
6. The Most Feared Man in Mexico — And How They Finally Caught Him (Z-40)

---

## SEO — Already Done
- `<title>`, `<meta description>`, Open Graph, Twitter Card tags ✅
- JSON-LD structured data (WebSite + VideoObject for live videos) ✅
- `robots.txt` ✅
- `sitemap.xml` ✅
- `llms.txt` (for AI search engines) ✅
- Thumbnail `loading="lazy"` on all video cards ✅
- Footer year: © 2026 ✅

## Cloudflare Settings
- Bot Fight Mode: **OFF** (correct — allows Googlebot)
- Block AI bots: **ON** (blanket toggle — need to switch to per-crawler AI Crawl Control)
- TODO: In Cloudflare → Security → Bots → AI Crawl Control, allow `PerplexityBot` and `OAI-SearchBot`, block training scrapers

## Analytics
- Not yet installed. When ready: ask user if they prefer Plausible or GA4, then add snippet to `<head>` in `index.html`.

## Contact / Social
- Email: `cartelcapture@gmail.com` (obfuscated in DOM)
- YouTube: `@cartelcapture`
- Instagram: `@cartelcapture`
- Subscribe API: `https://cartel-subscribe-worker.darrenclarke.workers.dev`
- Email send API: `https://cartel-email-agent.darrenclarke.workers.dev`
