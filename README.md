# Green Analytics Group — Public Marketing Site (slim bundle)

A **standalone, static** marketing website for the whole group: the logo-reveal **video → chat**
front door plus a section for every company and product (Green Analytics Consulting, Green Metrics
Technology — BuildSense, BuildBlox, Birch, BRICS — Open Housing Canada / DASH, Precision Livestock
Diagnostics, the Wolastoqey Forest Partnership, and Impact Natural Capital).

**Slim by design:** no internal corpus tool, no database, no server required. Just three files —
nothing internal (Level 2+) is included or reachable.

## Files
- `index.html` — the entire site (HTML + CSS + JS in one file).
- `GreenAnalytics-Logo-Reveal.mp4` — the intro video.
- `GreenAnalytics-Logo.png` — logo.

## Preview locally
Double-click `index.html`, or serve the folder:
```bash
cd ga-marketing-site
python3 -m http.server 8080   # → http://localhost:8080
```
The chat runs in **demo mode** out of the box (sample answers) so the whole site is reviewable now.

## Connect the live AI chat (optional)
Open `index.html`, find the `CONFIG` block near the bottom, and set:
```js
RAG_ENDPOINT: "https://<your-app>.up.railway.app/api/chat",
```
The site POSTs `{ messages, maxLevel: 1 }` and expects `{ reply, sources }` — capped to **public
(Level 1)** content, so the chat only ever answers from public information.

## Deploy (any static host)
Because it's static, it deploys anywhere in seconds:
- **Netlify / Vercel / Cloudflare Pages:** drag-and-drop the folder, or connect a repo.
- **Railway:** add a static service, or serve the folder with any static server.
- **GitHub Pages / S3 + CloudFront:** upload the three files.

No build step, no environment variables (unless you wire the live chat endpoint).

## Editing content
All copy lives directly in `index.html` (each company is a `<section>`), and brand colors are the
CSS variables at the top (`--green`, `--navy`). Easy to hand to a designer or edit inline.
