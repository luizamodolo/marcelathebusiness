# M4Melo Dance — Website Guide

This is a plain-language walkthrough of what the website does, followed by step-by-step instructions for getting the latest version live on GitHub.

## What the website does

**One file runs everything.** The whole site — pages, styling, and all the logic — lives in a single file called `index.html`. There's no separate database by default: every sign-up, payment, and cancellation is remembered inside that file's memory while someone has it open. (See "Optional: connecting a real Google Sheet" below for how to make that data persist across devices.)

### For visitors (the public site)

- **Bilingual** — a button in the corner switches the whole site between English (🇺🇸) and Portuguese (🇧🇷). The choice is remembered on that visitor's browser.
- **Instructor section** — Marcela's photo and bio.
- **Class schedule and pricing** — First Class (for new students), Drop-in, 2-Class Pack, and Monthly Membership, shown per location (San Francisco, Richmond, Santa Clara).
- **Sign-up form** — a visitor picks a class date and a plan, fills in their name/email/phone, and submits.
  - Before anything is created, a **rules pop-up** appears summarizing exactly what they're agreeing to for that plan (payment deadline, cancellation/refund policy, and — for Memberships — how credits work). They have to click "I understand, continue" before the sign-up is actually made.
  - After confirming, they land on a **pay box** with Venmo and Zelle info to send payment, and a reminder of the policies.
  - A "+ Sign up for another class" button lets them add a second person (like a friend) without losing the first sign-up — the form reopens blank.
- **Cancel a Class page** — anyone can look up their sign-up(s) by email or phone and cancel. The refund shown follows the 2-hour rule (see below).
- **Check Your Credits page** (Membership members) — look up by email or phone to see:
  - Their current class-credit balance per location.
  - Every upcoming class date at their location, with a "Book" button that uses 1 credit to reserve that specific date (also behind a rules pop-up first).
  - A "Save remaining credit(s) for next month" button — lets them explicitly acknowledge they're not using a credit this month; a message explains that next month's dates open on the 1st.
  - A "Cancel this class" button on any date they've already booked.
- **Class Request form** — for someone in an area without a class yet, or requesting a private class.
- **Invite a Friend** — a quick share link.

### The 2-hour rule (used everywhere)

- Cancel (or a membership credit-booked class) **2+ hours before** the class starts → full refund / credit returned.
- Cancel **less than 2 hours before**, or don't show up → 50% refund (regular sign-ups) or the credit is forfeited (membership bookings).
- If a regular (non-membership) sign-up is never marked paid and the 2-hour mark passes, it's **auto-canceled** — staff can reactivate it later if the person actually did pay.

### For Marcela (Staff Portal)

Reached via the "Staff" link in the footer, gated by a **passcode** (`m4studio444` by default — change this any time by searching for it in the file). The passcode is **not remembered** — closing the tab or refreshing the page always asks for it again. A "Refresh" button inside the panel updates the data without needing the passcode again.

Inside the Staff Portal:
- **All sign-ups**, grouped by location — mark paid/unpaid, fix the exact paid time, reactivate an auto-canceled entry.
- **Membership Credits panel**, one card per member:
  - "− Log class attended" — manually subtract 1 credit (disabled once balance hits 0 — it can never go negative).
  - "+ Add credit" — fix a mistake by 1.
  - "+ Renew (4 classes)" — the button to use when someone pays for a new month; adds the standard 4 credits without needing a new sign-up.
- **Class Requests** — everything submitted through the request form.
- A **printable roster** for a physical sign-in sheet.

### Optional: connecting a real Google Sheet

By default, all the data above only lives in that one browser tab and resets on reload — fine for testing, not for real use across devices. `Code.gs` is a companion file that turns a free Google Sheet into a simple shared database, so sign-ups/payments/credits show up for Marcela on any device. Open `Code.gs` and follow the setup notes at the very top of that file (roughly 5 minutes, no coding needed) — it also has an optional weekly email reminder for members running low on credits.

---

## Publishing to GitHub

You already have the repo `luizamodolo/m4-melo-dance-studio` on GitHub — these steps update it with the latest file, entirely through the GitHub website (no command line needed).

1. **Download the latest file.** Make sure you have the newest `index.html` I sent you saved somewhere easy to find, like your Downloads folder.
2. **Go to your repo.** Open [github.com](https://github.com) in a browser, sign in, and open `luizamodolo/m4-melo-dance-studio`.
3. **Open the existing `index.html`.** Click on it in the file list.
4. **Edit/replace it:**
   - Click the pencil ("Edit this file") icon in the top right of the file view, **or**
   - Go back to the repo's main page, click **Add file → Upload files**, then drag your new `index.html` in — GitHub will ask if you want to replace the existing file of the same name; confirm that you do.
5. **Commit the change.** Scroll down to "Commit changes," add a short message like "Update site," and click **Commit changes** (or **Propose changes** → **Merge** if it asks).
6. **Check that GitHub Pages is turned on** (only needs doing once):
   - In your repo, click **Settings** (top menu) → **Pages** (left sidebar).
   - Under "Build and deployment," Source should be set to **Deploy from a branch**, Branch set to **main** and folder set to **/ (root)**. Click **Save** if you had to change anything.
   - GitHub will show your site's address at the top of that page, something like `https://luizamodolo.github.io/m4-melo-dance-studio/`.
7. **Wait about a minute**, then visit that address (or refresh it if you already had it open) — your changes will be live.

**Important:** the file must stay named exactly `index.html` — that's the name GitHub Pages automatically serves as the homepage. Don't rename it.

### Updating it again later

Any time I send you a new version of the site, just repeat steps 1, 4, and 5 above (upload the new `index.html`, replacing the old one, and commit). Steps 2, 3, and 6 only need to happen once, the first time.
