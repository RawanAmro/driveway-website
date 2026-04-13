# Driveway Auto Collision — Deployment Guide

A start-to-finish walk-through to take your website **live in about 60 minutes**, with a working contact form and a real `.ca` domain. Free hosting, ~$15 CAD/year for the domain.

---

## Quick Overview

| Step | What | Time | Cost |
|------|------|------|------|
| 1 | Activate the contact form (Web3Forms) | 5 min | Free |
| 2 | Drop in your real before/after photos | 10 min | Free |
| 3 | Buy a `.ca` domain | 10 min | ~$15 CAD/yr |
| 4 | Host the site on Netlify (drag-and-drop) | 10 min | Free |
| 5 | Connect your domain | 15 min | Free |
| 6 | Set up Google Business Profile | 15 min | Free |
| 7 | Going-live checklist | 5 min | Free |

**Total cost to launch: ~$15 CAD for the first year.** Hosting and form backend are free forever on the basic tiers.

---

## Step 1 — Activate the contact form (5 minutes)

Your form is wired up to **Web3Forms**, a free service that emails every submission directly to your inbox (with photo attachments). You just need to plug in an access key.

1. Go to **https://web3forms.com**
2. Click **"Create Access Key"**
3. Enter the email where you want estimate requests delivered: `drivewayautoinc@gmail.com`
4. Confirm the email Web3Forms sends you — that activates the key.
5. Copy the access key string they show you (looks like `1a2b3c4d-5e6f-7890-abcd-ef1234567890`).
6. Open `index.html` in any text editor (Notepad, TextEdit, VS Code, etc.).
7. Find this line (around line 605):
   ```html
   <input type="hidden" name="access_key" value="YOUR_WEB3FORMS_ACCESS_KEY_HERE" />
   ```
8. Replace `YOUR_WEB3FORMS_ACCESS_KEY_HERE` with your real key. Save.

That's it — submissions will now arrive at your Gmail with all the customer details + uploaded photos attached.

> **Free tier**: 250 submissions/month — more than enough to start. Upgrade only if you outgrow it.

**Test it**: Open `index.html` in your browser, fill out the form, submit. You should get an email within a minute.

---

## Step 2 — Drop in your real before/after photos (10 minutes)

The site already looks great with stock images, but real customer photos build way more trust.

1. Open the `images/` folder.
2. Read `images/README.md` for the exact filenames (e.g., `jetta-before.jpg`, `jetta-after.jpg`).
3. Save your photos with those exact names — the site will pick them up automatically.

> **Tip**: Compress photos at https://tinypng.com first so the site stays fast on mobile.

---

## Step 3 — Buy a `.ca` domain (10 minutes)

A `.ca` domain looks more professional and trustworthy to Canadian customers than `.com`.

**Recommended Canadian registrars**:

| Registrar | Why | Approx. price |
|-----------|-----|--------------|
| **Namecheap** (namecheap.com) | Cheap, clean interface, great support | ~$15 CAD/yr |
| **GoDaddy.ca** | Most well-known, frequent sales | ~$20 CAD/yr |
| **Hover** (hover.com) | Clean, no upsells, Canadian-friendly | ~$22 CAD/yr |
| **CIRA Member Registrars** | Official `.ca` registry | varies |

**Suggested domain ideas (check availability):**
- `drivewayautocollision.ca` ← first choice
- `drivewayauto.ca`
- `drivewaycollision.ca`
- `drivewayautoinc.ca`

**To buy:**
1. Go to your chosen registrar.
2. Search for your domain.
3. Add to cart — *decline* the upsells (private registration is usually included free for `.ca`; you don't need their hosting, email, or SSL — Netlify gives you those free).
4. Check out. You'll need basic ID info — `.ca` domains require Canadian presence (you qualify as a Canadian business).

---

## Step 4 — Host the site on Netlify (10 minutes, free forever)

Netlify is the easiest path: drag a folder, get a live URL.

1. Go to **https://app.netlify.com/drop**
2. Sign up (free, Google sign-in works).
3. **Drag the entire `driveway-website/` folder** onto the page.
4. Wait ~30 seconds. Netlify gives you a temporary URL like `random-name-12345.netlify.app`.
5. **Test it** — visit the URL, click around, submit a test form.

That's your live site. Now to swap the temp URL for your real domain:

6. In Netlify, go to **Site settings → Site information → Change site name**.
7. Pick something memorable like `driveway-auto`. Your URL becomes `driveway-auto.netlify.app`.
8. Then **Domains → Add a domain you own → enter your `.ca` domain**.

**Alternative free hosts** (if you prefer):

- **Vercel** (vercel.com) — same drag-and-drop concept, equally good.
- **Cloudflare Pages** (pages.cloudflare.com) — free, fast, includes DDoS protection.
- **GitHub Pages** — free, but requires a GitHub account and is a bit more technical.

---

## Step 5 — Connect your `.ca` domain to Netlify (15 minutes, including DNS wait)

In Netlify after adding your domain, it will show you DNS records to add. There are two paths:

### Easiest: Use Netlify DNS (recommended)
1. Netlify will give you 4 nameservers (e.g., `dns1.p01.nsone.net`, etc.).
2. Log into your domain registrar (Namecheap/GoDaddy/etc.).
3. Find **"Nameservers"** in your domain settings.
4. Switch from "Default" to "Custom" and paste in Netlify's 4 nameservers.
5. Save.

### Alternative: Keep registrar's DNS, add records manually
1. In Netlify's DNS instructions, copy the `A` record IP and the `CNAME` for `www`.
2. In your registrar's DNS panel, add:
   - `A` record: `@` → Netlify's IP (e.g., `75.2.60.5`)
   - `CNAME` record: `www` → `[your-site].netlify.app`

**DNS takes 5 minutes to a few hours to propagate.** Check status at https://dnschecker.org

Once propagated, **HTTPS / SSL is automatic** — Netlify provisions a free Let's Encrypt certificate within a few minutes. You'll see the lock icon in browsers.

---

## Step 6 — Google Business Profile (15 minutes — biggest local-SEO move you can make)

This is what makes your shop show up in Google Maps and "auto body shop near me" searches.

1. Go to **https://www.google.com/business**
2. Sign in with the Gmail you want associated (`drivewayautoinc@gmail.com`).
3. Search for your business name. If it doesn't exist, click **"Add your business to Google"**.
4. Fill in:
   - **Name**: Driveway Auto Collision Inc.
   - **Category**: Auto body shop *(also add: Auto repair shop, Towing service)*
   - **Address**: 3095 Wolfedale Rd, Unit A3, Mississauga, ON L5C 1V8
   - **Service area**: Mississauga, Brampton, Etobicoke, Oakville, Toronto
   - **Phone**: 647-914-4176
   - **Website**: your new `.ca` domain
   - **Hours**: Mon–Fri 8am–7pm, Sat 9am–5pm, Sun by appointment, Towing 24/7
5. **Verify** your business — Google mails a postcard with a code (5–10 days). Some businesses can verify by phone or video instead.
6. Once verified, **upload 10–15 photos**: shop exterior, interior, your team, before/afters, equipment.
7. **Ask happy customers for Google reviews.** A simple text after pickup: *"Hey, glad we could help with your car. If you have 30 seconds, would you mind leaving us a Google review? Here's the link: [your review link]"*. Five-star reviews on Google Business is the single highest-ROI thing you can do for getting more customers.

---

## Step 7 — Going-live checklist

Before you start sharing the link, run through this:

- [ ] Form submits successfully and you receive the test email (with photo attached)
- [ ] All 6 before/after sliders work on mobile (drag finger left-right)
- [ ] Phone numbers tap-to-call on mobile
- [ ] "Get Directions" link opens Google Maps
- [ ] Google Reviews link in the testimonials section points to YOUR Google Business listing (update once it's verified — search `index.html` for `g.page/r/` and replace)
- [ ] Spell-check the page (especially business name, address, phone)
- [ ] Open the site on your phone — does it look good? Buttons big enough?
- [ ] Site loads in under 3 seconds (test at https://pagespeed.web.dev)
- [ ] HTTPS lock icon shows in the browser bar
- [ ] Domain redirects properly (try with and without `www.`)

---

## Step 8 — After launch (ongoing)

**Promote your site:**
- Add the URL to your business cards, invoices, signage
- Add it to your Google Business Profile, Instagram bio, Facebook page
- Put a small sign in the shop: "Get a free online estimate at drivewayautocollision.ca"
- Share before/after photos on Instagram + Facebook with the link

**Track results (free):**
- Add **Google Analytics 4** (analytics.google.com) — paste the tracking snippet just before `</head>` in `index.html`.
- Or use **Cloudflare Web Analytics** — privacy-friendly, no cookie banner needed.

**Update content:**
- Add new before/after photos every month or two
- Keep your shop hours accurate (especially around holidays)
- Reply to every Google review within 48 hours

---

## What it'll cost over time

| Item | Year 1 | Year 2+ |
|------|--------|---------|
| `.ca` domain | $15 CAD | $15 CAD/yr |
| Netlify hosting | $0 | $0 |
| Web3Forms (250 submissions/mo) | $0 | $0 |
| SSL certificate | $0 (auto via Netlify) | $0 |
| **Total** | **$15 CAD** | **$15 CAD/yr** |

If you ever exceed the free tiers (e.g., you start getting hundreds of estimate requests a month), Netlify Pro is $19 USD/mo and Web3Forms paid plans start at ~$5/mo. But you'd be a busy shop at that point.

---

## Help & troubleshooting

**Form not sending?**
- Make sure you replaced `YOUR_WEB3FORMS_ACCESS_KEY_HERE` with your real key.
- Check spam folder for the first test submission.
- Verify the email tied to your Web3Forms account is `drivewayautoinc@gmail.com`.

**Site looks broken on Netlify?**
- Make sure you uploaded the *folder*, not just `index.html`. The `images/` folder must come along too.

**Domain not pointing to the site after 24h?**
- Run https://dnschecker.org — paste your domain — should show Netlify's IP everywhere.
- Double-check nameservers / DNS records match what Netlify told you.

**Want to make changes?**
- Edit `index.html` locally, then drag the whole folder onto Netlify again. It'll update in seconds.
- Or hook Netlify up to a free GitHub repo for one-click deploys.

---

You're all set. Welcome to the internet, Driveway Auto Collision.
