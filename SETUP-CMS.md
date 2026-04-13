# Staff Upload Feature — One-Time Setup Guide

This guide turns on the admin panel at **`yoursite.com/admin`** where shop staff can add, edit, and delete before/after photo pairs themselves — no developer, no code, just a login.

Setting it up takes about **15 minutes** and only needs to be done once.

---

## What you'll end up with

- A login page at `drivewayautorepair.ca/admin` (or whatever domain you use)
- Staff logs in with email + password
- Clicks **"Manage Gallery Entries"** → drags in before/after photos, types car model + description, clicks **Publish**
- Site rebuilds automatically in ~60 seconds, new pair appears in the gallery
- Same dashboard lets staff edit or delete any existing entry

---

## Step 1 — Create a free GitHub account (2 min)

GitHub is where the website's files will live. It's free and you won't need to touch it again after this step.

1. Go to https://github.com/signup
2. Sign up with your email (use the shop email if you like)
3. Verify your email

## Step 2 — Put the website on GitHub (5 min)

1. While logged into GitHub, go to https://github.com/new
2. **Repository name:** `driveway-website`
3. Set it to **Private** (your files stay yours)
4. Click **Create repository**
5. On the next page, click **"uploading an existing file"**
6. Drag **all the files** from the unzipped `driveway-website` folder (from your computer) into the upload area
   - Make sure you include the `admin/` folder and `gallery.json`
7. Click **Commit changes**

## Step 3 — Switch Netlify from drag-drop to GitHub (3 min)

1. Go to https://app.netlify.com and log in
2. Click your current Driveway site (e.g. `tourmaline-sable-d7ba93`)
3. Go to **Site configuration → Build & deploy → Link repository**
4. Pick **GitHub** → authorize → pick `driveway-website` → click **Deploy site**

From now on, anything you or the CMS pushes to GitHub auto-deploys in about a minute.

## Step 4 — Turn on Netlify Identity (2 min)

This is the free login system.

1. Inside your Netlify site, click **Integrations** (or **Identity** on older UI)
2. Click **Enable Identity**
3. Under **Registration**, change to **Invite only** (so random visitors can't sign up)
4. Scroll down to **Services → Git Gateway**, click **Enable Git Gateway**

## Step 5 — Invite your staff (1 min per person)

1. Still in Netlify → **Identity** tab → **Invite users**
2. Type the email address of each staff member who should be able to add photos
3. They'll get an email — they click the link, pick a password, and they're in

## Step 6 — Use it!

1. Anyone invited goes to **`drivewayautorepair.ca/admin`** (replace with your actual domain or Netlify URL)
2. They log in with their email + password
3. Click **Before & After Gallery → Manage Gallery Entries**
4. Scroll to the bottom of the list and click **+ Add Gallery Entries** to create a new pair
5. Fill in:
   - **Car** — e.g. "Honda Civic 2020"
   - **Before photo** — drag/drop the damaged car photo
   - **After photo** — drag/drop the repaired photo
   - **Description** — one or two sentences
   - **Tags** — short labels (e.g. Collision, Insurance claim)
6. Click **Publish**
7. Wait ~60 seconds — new pair is live on the website

To **edit** or **delete** an existing pair, they just click on it in the list.

---

## Notes

- Photos get saved automatically to `images/uploads/` on the site — no renaming needed
- The CMS runs entirely in the browser, free, no monthly fee
- Netlify Identity's free tier covers 5 invited users per month (more than enough for the shop)
- If you ever want to move off Netlify, the content is all in plain Git files (portable)

---

## Troubleshooting

**"I log in but the admin page says 'No collections found'"**
→ Git Gateway isn't enabled. Go back to Step 4 → Services → enable Git Gateway.

**"New entries don't show up on the site"**
→ Wait 2 minutes. Netlify needs to rebuild. Check the **Deploys** tab in Netlify to see if the build succeeded.

**"Photos uploaded but broken image icon on site"**
→ Photo filenames with spaces sometimes break. Rename the file (no spaces, no special characters) and re-upload.

**"I want to remove a staff member's access"**
→ Netlify → Identity → find their email → click **Delete user**.
