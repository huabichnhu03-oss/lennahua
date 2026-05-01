# Lenna Hua — Portfolio

A production-ready Next.js 14 portfolio with a built-in Admin CMS, designed for deployment on Vercel or GitHub Pages.

---

## ✦ Stack

| Layer | Technology |
|---|---|
| Framework | Next.js 14 (App Router) |
| Styling | Tailwind CSS + CSS Variables |
| Fonts | Cormorant Garamond (display) + DM Sans (body) |
| Content | JSON flat files in `/data` |
| Admin CMS | Built-in, password-protected `/admin` route |
| Deploy | Vercel (recommended) or GitHub Pages |

---

## ✦ Getting Started

```bash
# 1. Install dependencies
npm install

# 2. Copy env file and set your admin password
cp .env.example .env.local

# 3. Run dev server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) — the site should be live.

---

## ✦ Site Structure

```
/              → Homepage (hero, featured projects, about strip, CTA)
/work          → All projects with filter tabs (UX / Research / Visual)
/work/[slug]   → Individual project case study
/about         → Full bio, skills, experience, education
/studio        → Creative gallery (art direction, photography, etc.)
/contact       → Contact form (mailto) + info sidebar
/admin         → Password-protected CMS (see below)
```

---

## ✦ Admin CMS — How It Works

### Access
Navigate to `/admin` and enter your password (default: `lenna2025`).

### What you can edit
| Section | Fields |
|---|---|
| **Projects** | Title, subtitle, slug, type, tags, description, cover image, year, featured flag |
| **About** | Bio paragraphs, skill groups, tools list |
| **Experience** | Job title, company, period, bullet points |
| **Education** | Degree, school, period, description |
| **Studio/Gallery** | Title, role, image URL, link, type |

### Workflow: Edit → Deploy

1. **Edit** content in `/admin`
2. Click **Save Draft** — saves to browser localStorage (preview in same browser)
3. Click **Export JSON** — downloads all 5 JSON files
4. **Replace** the files in `/data/` with the downloaded versions
5. **Commit & push** to GitHub
6. **Vercel redeploys** automatically (takes ~60 seconds)

> This is the recommended workflow for a static portfolio. No database needed, no backend cost, and your content is version-controlled.

---

## ✦ Deployment on Vercel

### One-click deploy
1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → New Project → Import from GitHub
3. Vercel auto-detects Next.js — just click **Deploy**
4. Set your admin password under **Settings → Environment Variables**:
   ```
   NEXT_PUBLIC_ADMIN_PASSWORD = your_secure_password
   ```

### Custom domain (lennahua.ca)
1. Vercel → Project → Settings → Domains
2. Add `lennahua.ca` and `www.lennahua.ca`
3. Update your DNS registrar to point to Vercel's nameservers

---

## ✦ Deployment on GitHub Pages

```bash
npm run build
npm run export   # if using static export
```

Add to `next.config.mjs`:
```js
output: 'export',
basePath: '/repo-name',  // only if not using custom domain
```

---

## ✦ Customising Content Without the Admin

All content lives in `/data/`:
```
data/
  projects.json    ← All work/projects
  about.json       ← Bio, skills, tools
  experience.json  ← Work history
  education.json   ← Education history
  gallery.json     ← Studio/creative items
```

Edit these directly for batch updates.

---

## ✦ Adding a New Project (manual)

Add an object to `data/projects.json`:

```json
{
  "id": "7",
  "slug": "my-new-project",
  "title": "My New Project",
  "subtitle": "Short one-liner description",
  "type": "ux",
  "tags": ["UX Research", "Prototyping"],
  "description": "Full paragraph description shown on the project page.",
  "coverImage": "https://your-image-url.com/cover.jpg",
  "year": "2025",
  "featured": false,
  "link": "/work/my-new-project"
}
```

---

## ✦ Design Decisions

### Information Architecture — Fixes from original

| Before | After |
|---|---|
| 8 nav items (HOME, ABOUT, PROJECTS, EXPERIENCE, EDUCATION, GALLERY, PRODUCTION, CONTACT) | 4 nav items (Work, About, Studio, Contact) |
| Experience & Education as separate top-level pages | Consolidated into About page with clear sections |
| PRODUCTION as a standalone nav item | Moved into Studio (creative sub-section) |
| No admin role — editing requires going back to Framer | Full `/admin` CMS with export workflow |
| Framer CMS (no code access) | JSON flat files — version-controlled, editable anywhere |

### Animation Principles
- **Scroll reveals** — elements fade + slide up as they enter the viewport
- **Mask reveals** — headline text slides out of a hidden container
- **Custom cursor** — gold dot + lagging ring, scales on hover
- **Noise overlay** — subtle grain texture via CSS SVG filter
- **Project cards** — image scale on hover, overlay fade, border transition

### Typography Pairing
- `Cormorant Garamond` — editorial serif for all display/heading text
- `DM Sans` — clean grotesque for body, labels, navigation, UI

### Colour System
```css
--bg:           #0A0908   /* Near-black warm base */
--surface:      #141210   /* Card/section backgrounds */
--border:       #272421   /* Default rule/border */
--accent:       #C8A96E   /* Gold — primary accent */
--text-primary: #F2EDE5   /* Warm white */
--text-secondary: #8A8278 /* Muted body text */
```

---

## ✦ License

Personal use — Lenna Hua portfolio. Not for redistribution.
