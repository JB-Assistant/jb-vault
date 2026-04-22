# Browser Harness + Browser Use Cloud — Session Summary & Use Cases

**Date:** 2026-04-22
**Setup:** browser-harness on VPS (headless) + Browser Use Cloud remote browsers
**Repo:** `/home/hermes/browser-harness` (github.com/browser-use/browser-harness)

---

## What We Built Today

### 1. Installed & Configured browser-harness
- Cloned `browser-use/browser-harness` (4.8k stars, actively maintained)
- Installed globally via `uv tool install -e .`
- Configured Browser Use Cloud API key in `.env` (remote browser mode — no local Chrome needed)
- Created Hermes skill: `~/.hermes/skills/productivity/browser-harness/`

### 2. Hacker News Scraping Test
- Connected to Browser Use Cloud remote browser (free tier)
- Navigated to `news.ycombinator.com/show`
- Extracted top 15 "Show HN" posts using `js()` — DOM selector approach
- Saved to `/tmp/show_hn.json` with title, score, author, comment count, URL
- Contributed domain skill: `domain-skills/ycombinator.com/browser-scraping.md`

### 3. YouTube Thumbnail Grid
- Scraped David Ondrej's channel (`@davidondrej/videos`) for 12 most recent videos
- Handled lazy-loaded thumbnails (constructed URLs from video IDs: `https://i.ytimg.com/vi/{ID}/hqdefault.jpg`)
- Built 4-column thumbnail grid (2064x1162, 1.4MB) with PIL/Pillow
- Saved as `/home/hermes/ondrej_grid.png`
- Created reusable helper: `domain-skills/youtube/grid_builder.py`
- Contributed domain skill: `domain-skills/youtube/browser-scraping.md`

---

## Architecture

```
Hermes Agent (VPS)
    │
    ├── browser-harness CLI
    │       │
    │       └── admin.py → Browser Use Cloud API
    │               │
    │               └── Remote Chrome (cloud)
    │                       └── CDP websocket
    │
    └── Python helpers (grid_builder.py, etc.)
```

**Key difference from built-in browser tools:**
- Hermes built-in browser: Browserbase (cloud, isolated sessions, no real logins)
- browser-harness: Browser Use Cloud OR your real Chrome (with existing cookies/logins)
- browser-harness can also connect to local Chrome via `chrome://inspect` remote debugging

---

## How It Works

### Starting a remote browser
```bash
cd /home/hermes/browser-harness
python3 -c "from admin import start_remote_daemon; start_remote_daemon('work')"
```

### Running commands
```bash
BU_NAME=work browser-harness <<'PY'
new_tab("https://example.com")
wait_for_load()
print(page_info())
PY
```

### Key functions (from `helpers.py`)
| Function | Purpose |
|----------|---------|
| `new_tab(url)` | Open URL in new tab (NOT goto — clobbers active tab) |
| `wait_for_load()` | Wait for page load |
| `page_info()` | Get {url, title, viewport, scroll} |
| `js(expression)` | Execute JavaScript, return result as string |
| `click(x, y)` | Click at coordinates |
| `type_text(text)` | Type text |
| `screenshot(path)` | Take screenshot |
| `scroll(x, y, dy)` | Scroll page |
| `cdp(method, **params)` | Raw CDP call |
| `http_get(url)` | HTTP GET (no browser needed) |

### Stopping
```bash
python3 -c "from admin import stop_remote_daemon; stop_remote_daemon('work')"
```

---

## 15+ Use Cases for Your SaaS Business

### Lead Generation & Sales
1. **LinkedIn lead scraping** — Search for auto repair shop owners, extract names + companies + profiles. Use existing login cookies (sync via `profile-use`).
2. **Salesforce data extraction** — Pull lead lists, pipeline data, or reports from Salesforce dashboards that require login.
3. **G2/Capterra competitor reviews** — Scrape competitor reviews on G2, Capterra, Trustpilot. Track sentiment over time.
4. **Apollo/ZoomInfo scraping** — Extract contact lists from sales intelligence platforms.

### Competitive Intelligence
5. **Competitor pricing monitoring** — Regularly scrape competitor pricing pages (TireManagerPro competitors, etc.) and alert on changes.
6. **Product Hunt / Indie Hackers tracking** — Monitor new launches in your niche, extract feature lists and traction metrics.
7. **App store review monitoring** — Scrape Google Play / App Store reviews for competitor apps.

### Content & Marketing
8. **YouTube thumbnail grids** — What we did today. Build visual grids for competitor analysis, content inspiration, or portfolio showcases.
9. **Twitter/X thread extraction** — Scrape threads from specific accounts (requires login).
10. **Reddit/HN trend monitoring** — Track mentions of your products, competitors, or industry keywords across forums.

### Testing & QA
11. **End-to-end testing of your SaaS** — Test OttoManagerPro, TireManagerPro, CleanBuddyPro workflows in a real browser with real sessions.
12. **Visual regression testing** — Screenshot key pages, compare against baselines.
13. **Login flow testing** — Verify Clerk auth flows, Stripe checkout, Twilio SMS delivery in real browser.

### Operations & Automation
14. **Form submission automation** — Auto-fill government forms, permit applications, vendor registrations.
15. **Invoice/receipt scraping** — Extract data from vendor portals, bank dashboards, or accounting platforms.
16. **Job board monitoring** — Scrape Indeed, LinkedIn Jobs, Wellfound for relevant postings (e.g., auto repair shops hiring).
17. **Craigslist/Facebook Marketplace scraping** — Monitor listings for relevant items or leads in specific markets.

### Data Collection
18. **Zillow/real estate data** — Property data extraction for market analysis.
19. **SEC EDGAR filings** — Extract financial data from company filings.
20. **Wikipedia/open data extraction** — Structured data from sites that need JS rendering.

---

## Domain Skills Contributed

| Skill | Path | Content |
|-------|------|---------|
| Hacker News | `domain-skills/ycombinator.com/browser-scraping.md` | DOM selectors, js() extraction, gotchas |
| YouTube | `domain-skills/youtube/browser-scraping.md` | Channel scraping, thumbnails, search, watch pages |
| YouTube Grid | `domain-skills/youtube/grid_builder.py` | Reusable thumbnail grid builder |

---

## Free Tier Limits (Browser Use Cloud)
- **3 concurrent browsers**
- **Proxies included** (stealth, geo-targeting via `proxyCountryCode`)
- **Captcha solving included**
- **No credit card required**
- Browsers bill until timeout (default 2h, configurable 1-240 min)

---

## Next Steps
- [ ] Set up LinkedIn profile sync (`profile-use sync`) for lead gen
- [ ] Create competitor pricing monitoring cron job
- [ ] Build E2E test suite for TireManagerPro checkout flow
- [ ] Add more domain skills as we use browser-harness on new sites
