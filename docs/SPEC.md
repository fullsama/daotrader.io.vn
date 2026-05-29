# daotrader.io.vn Landing Page MVP Plan

**Date:** 2026-05-29
**Status:** PLANNED
**Owner:** Sophia (Orchestrator) → subagent execution
**Domain:** daotrader.io.vn (Cloudflare managed)
**Repo:** github.com/fullsama/daotrader.io.vn

---

## 1. Clarity

**Goal:** Landing page giới thiệu ĐẠO TRADER AI LAB + 2 sản phẩm, lead contact qua external links.

**Scope:**
- Static HTML/CSS/JS landing page (no backend DB)
- Cloudflare Pages hosting
- Cloudflare Workers API route cho contact form (POST → Telegram message)
- No blog/case studies
- Contact: click-to-external Facebook/Telegram/Zalo

**Products:**
- Backtest: 50k/run
- Demo Bot: 200k/tháng

**Brand:**
- ĐẠO TRADER AI LAB
- Colors: Navy #0A1628 | Gold #D4AF37 | Cyan #00D4FF
- Logo: D+A monogram (có trong brain/SHARED/brand/)
- Slogan: "Ứng dụng AI & Trading Mindset để Tự Do Tài Chính & Làm Chủ Cuộc Chơi"

**Constraints:**
- Cloudflare Pages (Wrangler CLI deploy)
- Oscar will provide Facebook/Telegram/Zalo links
- Demo Bot: text description only (no live demo video)
- Landing is v1: product showcase + contact

---

## 2. Tech Stack

| Component | Choice | Reason |
|-----------|--------|--------|
| Hosting | Cloudflare Pages | Domain already on Cloudflare |
| Contact API | Cloudflare Workers | Sends Telegram message to Oscar |
| Frontend | Vanilla HTML/CSS/JS | Simple, no framework needed |
| Icons | Heroicons or FontAwesome CDN | External links icons |
| Assets | Brand assets from brain/SHARED/brand/ | Logo, brand poster |

---

## 3. File Structure

```
website_daotrader/
├── src/
│   ├── index.html          # Main landing page
│   ├── css/
│   │   └── style.css       # All styles
│   └── js/
│       └── main.js         # Contact form handler, smooth scroll
├── workers/
│   └── contact-api/
│       ├── wrangler.toml
│       └── index.js        # Cloudflare Worker: POST /api/contact
├── docs/
│   └── SPEC.md             # This file
├── .gitignore
└── README.md
```

---

## 4. Landing Page Sections

### Section 1: Hero
- Logo + Brand name: ĐẠO TRADER AI LAB
- Tagline: "Ứng dụng AI & Trading Mindset để Tự Do Tài Chính & Làm Chủ Cuộc Chơi"
- CTA: "Bắt Đầu Ngay" → scroll to products

### Section 2: Products
- **Backtest** card: icon, "Kiểm Thử Chiến Lược", 50k/run, feature bullets
- **Demo Bot** card: icon, "Trading Tự Động", 200k/tháng, feature bullets

### Section 3: How It Works
- 3-step: Chọn Chiến Lược → Backtest → Triển Khai Bot

### Section 4: Why Us
- 3 value props: AI-powered, Transparent, Professional

### Section 5: Contact
- 3 icons: Facebook | Telegram | Zalo (click to external, Oscar provides links)

### Section 6: Footer
- Brand name, copyright, "Made with ĐẠO TRADER AI LAB"

---

## 5. Tasks

### Phase 1: Setup + Structure
- [ ] Init git repo in workspace_daotrader
- [ ] Connect to GitHub repo (fullsama/daotrader.io.vn)
- [ ] Add brand assets (copy logo from brain/SHARED/brand/ to src/)

### Phase 2: Frontend (src/)
- [ ] index.html — all sections skeleton
- [ ] css/style.css — full styling with brand colors
- [ ] js/main.js — smooth scroll, contact form handler

### Phase 3: Contact Worker (workers/contact-api/)
- [ ] wrangler.toml — Workers project config
- [ ] index.js — POST /api/contact → send Telegram message to Oscar (chat_id: 1398796734)
- [ ] Test worker locally with wrangler dev

### Phase 4: Deployment
- [ ] Deploy to Cloudflare Pages (wrangler pages deploy)
- [ ] Create Cloudflare Worker: contact-api
- [ ] DNS: ensure daotrader.io.vn points to Cloudflare Pages
- [ ] Test live: open daotrader.io.vn

### Phase 5: Contact Links (Oscar provides)
- [ ] Update contact section with real Facebook/Telegram/Zalo URLs

---

## 6. Notes

- Oscar will provide Facebook/Telegram/Zalo links before Phase 5
- Logo file: brain/SHARED/brand/ (D+A monogram)
- Brand poster: brain/SHARED/brand/ (zen trader, for reference)
- Telegram bot token for contact worker: 8643603303:*** (same as demo_auto bot)
- Target chat_id for contact notification: 1398796734

---

## 7. Success Criteria

- [ ] daotrader.io.vn loads correctly (all sections visible)
- [ ] Brand colors (#0A1628, #D4AF37, #00D4FF) applied throughout
- [ ] Product cards display Backtest 50k + Demo Bot 200k
- [ ] Contact icons link to Oscar's provided URLs (Facebook/Telegram/Zalo)
- [ ] POST /api/contact sends Telegram message to Oscar's chat
- [ ] No console errors
- [ ] Mobile responsive