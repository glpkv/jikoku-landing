# Jikoku — landing page

Bilingual (EN/RU) landing page for **Jikoku**, a native macOS app that brings your
**Apple Calendar, Apple Reminders, and a work Exchange calendar** together in one
window — with reminders you can drag onto the day and give a real duration for
time-blocking. One-time price, no subscription.

**Live:** https://glpkv.github.io/jikoku-landing/

This is a pre-launch validation page: it gauges interest via an email waitlist and a
small "what should we build next?" poll.

## Features of the page
- **Bilingual** EN / RU with a one-click language switch (remembers your choice; screenshots
  swap per language).
- **Light, minimal design** with on-scroll reveal animations.
- **Real app screenshots** (not mockups), including a cropped close-up of drag-and-drop
  time-blocking.
- **Email waitlist** that writes straight to a private Google Sheet (see below).
- **Interest poll** (in-app email, share-free-slots) tracked as analytics events.
- **Privacy-friendly analytics** via GoatCounter (no cookies).

## Tech
Plain static HTML/CSS/JS — no build step, no framework. Everything lives in `index.html`
(styles and scripts inline). Hosted on GitHub Pages.

```
.
├── index.html          # the whole page
├── assets/
│   ├── icon.png        # Jikoku app icon
│   ├── og.png          # social share / OG preview card
│   ├── screenshot.png        # app screenshot (RU UI)
│   ├── screenshot-en.png     # app screenshot (EN UI)
│   ├── dragdrop.png / -en.png   # close-up of reminder time-blocking
│   └── app-*.png       # Reminders / Calendar / Exchange icons
└── README.md
```

## How the waitlist works
The signup form posts the email to a **Google Apps Script web app**, which appends a row to
a private Google Sheet (`Date · Email · Lang · Source`). The endpoint is set in `index.html`
as `SHEET_ENDPOINT`. No secrets live in the page — the endpoint can only *append* a row, not
read the sheet. A hidden honeypot field (`company`) filters out bots.

## Analytics
GoatCounter (`jikoku.goatcounter.com`) records visits and three events:
`cta-notify` (waitlist button), `want-email` and `want-slots` (poll votes).

## Run locally
```bash
python3 -m http.server 8000
# open http://localhost:8000
```
(GoatCounter ignores localhost, so visit stats only appear on the live domain.)

## Deploy
Hosted on GitHub Pages from `main` / root. Pushing to `main` redeploys automatically.

---
Made on a Mac, for Mac.
