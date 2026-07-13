# DoctorMasood.com
# DoctorMasood.com

Static website - the digital home of Dr Masood. Pure HTML/CSS + minimal vanilla JS. No build step, no backend.

## Deploy (GitHub → Cloudflare Pages)

1. Create a new GitHub repository and push the entire contents of this folder to the root (so `index.html` sits at the top level of the repo).
2. In Cloudflare → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**, select the repo.
3. Build settings: **Framework preset = None**, **Build command = (leave blank)**, **Build output directory = `/`**.
4. Deploy. Then add the custom domain `doctormasood.com` under the Pages project's **Custom domains** tab.

That's it - every push to the repo redeploys automatically.

## Before you go live - replace these placeholders

Search the whole project for each token and paste in the real link. Every placeholder appears in the page footers and on the relevant path page.

| Placeholder | Where | What it is |
|---|---|---|
| `CALCOM_STUDENT_INTAKE_LINK` | future-doctor | Cal.com booking link for the £100 consultation, with Stripe payment attached in Cal.com |
| `CALCOM_EXECUTIVE_APPLICATION_LINK` | executive-advisory | Cal.com application/enquiry form for advisory |
| `CALCOM_PRIVATE_COUNSEL_APPLICATION_LINK` | private-counsel | Private enquiry route (Cal.com form or a mailto:) |
| `CALCOM_SPEAKING_ENQUIRY_LINK` | index (#speaking) | Speaking enquiry form |
| `SUBSTACK_URL` | ghla | Substack publication URL (free + Inner Circle) |
| `LINKEDIN_URL` / `INSTAGRAM_URL` / `TIKTOK_URL` / `YOUTUBE_URL` | footers | Social profile URLs |

Quick way to find them all: `grep -rn "CALCOM\|SUBSTACK_URL\|_URL" .`

## Also before launch

- Add a **portrait photo**: replace the placeholder box on `about/index.html` (`.portrait`) with `<img src="/assets/images/masood.jpg" alt="Dr Masood Ahmed">`.
- Add a **favicon** and an **Open Graph image** (`assets/images/`), then reference the OG image in each page's `<head>`.
- Complete **privacy** and **terms** - both are placeholders and must be finalised (ideally checked by a solicitor) before taking payments. The not-medical-care clause matters for your GMC registration.
- Set up **Stripe inside Cal.com** so the student consultation takes the £100 at booking.

## Configuration notes

- **Payments** run through Cal.com's Stripe integration, so no payment code lives in this site.
- **Private Counsel** is set to `noindex` and disallowed in `robots.txt` - it is discreet by design.
- **The Doctor's Method** (Investigate · Diagnose · Decide · Act · Review) is the through-line: it appears on the homepage and the student page, and the same language runs through every path. Keep it consistent everywhere.
- Pricing appears **only** on the Future Doctor page. Executive Advisory and Private Counsel quote fees privately, after a conversation - do not add prices to those pages.

## Structure

```
/
├── future-doctor/          Student path - the only page with public pricing
├── privacy/  terms/        Placeholders - finalise before launch
├── executive-advisory/     Application-based
├── private-counsel/        Discreet, noindex
├── ghla/                   Community + Inner Circle (Substack)
├── 404.html
├── robots.txt  sitemap.xml
└── assets/css  assets/js  assets/images
```
