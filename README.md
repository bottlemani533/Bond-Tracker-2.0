# Bond Payout Tracker — Install Guide

Your app, unchanged in every feature — I only added what's needed to make it
installable on Android and to work offline: a manifest, a service worker,
app icons, and self-hosted fonts (previously pulled from Google's CDN).

## Install on your phone (~5 min)

**Option A — GitHub Pages (free)**
1. Create a new public GitHub repo, e.g. `bond-payout-tracker`.
2. Upload every file in this folder (keep the `fonts` folder as-is) to the repo root.
3. Settings → Pages → Source: "Deploy from branch" → `main` → `/ (root)` → Save.
4. Wait ~1 min, then open the given `https://<you>.github.io/bond-payout-tracker/` URL.
5. On your phone, open that URL in **Chrome** → **⋮ menu → "Add to Home screen"**.

**Option B — Netlify Drop (no account, drag-and-drop)**
1. On a computer, go to `https://app.netlify.com/drop`.
2. Drag this whole folder onto the page → get an instant live URL.
3. Open it in Chrome on your phone → **Add to Home screen**.

Once installed it opens full-screen with its own icon and works with data off —
your bonds, calendar, and Form 121 tracker are all stored locally on the
device, exactly as before.

## One feature that needs a heads-up: AI cashflow parsing

The "Parse Cashflow Statement" upload (in Add Bond → cashflow section) calls
`api.anthropic.com` directly from the browser with no API key attached.
That only works inside Claude.ai's Artifact environment, which auto-injects
a key — it will **not** work once this is hosted standalone (GitHub Pages,
Netlify, or installed as a PWA). It already fails gracefully: you'll see
"Parse failed — use manual entry below" and can enter payouts by hand, which
still works exactly as before.

If you want AI parsing to work in the standalone app, that needs a small
backend proxy holding your own Anthropic API key (the browser can never hold
it directly — anyone could read it from the page source). Happy to build
that proxy if you want this feature live outside Claude.ai — just say the word.

## Everything else — unchanged

Portfolio, Payments calendar, Form 121 tracker, TDS tracking, bond
add/edit, manual cashflow entry, export data, NSE/IndiaBonds quick links —
all identical to what you built, just now installable and offline-capable.
