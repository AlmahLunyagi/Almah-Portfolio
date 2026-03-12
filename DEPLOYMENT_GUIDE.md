# 🚀 Almah Lunyagi Portfolio — Deployment & Customization Guide

## Overview

Your portfolio is a single `index.html` file. This guide walks you through:
1. Setting up GitHub to host your images
2. Deploying to Netlify (free)
3. Updating your Web3Forms API key
4. Adding your photos to the site

---

## STEP 1 — Set Up Your GitHub Image Repository

Your photos will live on GitHub so they load fast and maintain quality.

### Create an image repo
1. Go to [github.com/AlmahLunyagi](https://github.com/AlmahLunyagi)
2. Click **New repository**
3. Name it: `portfolio-assets`
4. Set it to **Public** (required for images to load on your site)
5. Click **Create repository**

### Upload your photos
1. Inside the repo, click **Add file → Upload files**
2. Organize your images like this:
   ```
   portfolio-assets/
   ├── profile.jpg          ← Hero section photo
   ├── about.jpg            ← About Me section photo
   └── travels/
       ├── kenya.jpg
       ├── qatar.jpg
       ├── usa.jpg
       └── [country].jpg
   ```
3. Click **Commit changes**

### Get the raw image URL
For any image you upload, the URL format is:
```
https://raw.githubusercontent.com/AlmahLunyagi/portfolio-assets/main/[filename]
```

Example:
```
https://raw.githubusercontent.com/AlmahLunyagi/portfolio-assets/main/profile.jpg
https://raw.githubusercontent.com/AlmahLunyagi/portfolio-assets/main/travels/kenya.jpg
```

---

## STEP 2 — Add Your Photos to index.html

Open your `index.html` file and find these placeholder sections:

### Hero photo (homepage)
Find this block (~line 195):
```html
<div class="hero-photo-placeholder">
  ...placeholder content...
</div>
```
Replace the entire `<div class="hero-photo-placeholder">...</div>` with:
```html
<img src="https://raw.githubusercontent.com/AlmahLunyagi/portfolio-assets/main/profile.jpg" alt="Almah Lunyagi" />
```

### About Me photo
Find the similar block inside `<div class="about-photo-frame">` and replace it the same way:
```html
<img src="https://raw.githubusercontent.com/AlmahLunyagi/portfolio-assets/main/about.jpg" alt="Almah Lunyagi" />
```

### Travel cards
Each travel card has a `<div class="travel-img-placeholder">` section. Replace each one with:
```html
<img class="travel-img" src="https://raw.githubusercontent.com/AlmahLunyagi/portfolio-assets/main/travels/kenya.jpg" alt="Kenya" />
```
Adjust the filename and alt text for each country.

---

## STEP 3 — Get Your Web3Forms API Key

Web3Forms lets your contact form send emails for free — no backend needed.

1. Go to **[web3forms.com](https://web3forms.com)**
2. Enter your email: `lunyagialmah@gmail.com`
3. Click **Create Access Key**
4. Check your email and copy the key (looks like: `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`)

### Add the key to your site
In `index.html`, find this line (~line 395):
```html
<input type="hidden" name="access_key" value="YOUR_WEB3FORMS_ACCESS_KEY" />
```
Replace `YOUR_WEB3FORMS_ACCESS_KEY` with your actual key:
```html
<input type="hidden" name="access_key" value="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" />
```

---

## STEP 4 — Deploy to Netlify

### Option A — Drag & Drop (Fastest, 2 minutes)
1. Go to **[netlify.com](https://netlify.com)** and create a free account
2. On your dashboard, look for the **"drag and drop"** zone
3. Drag your `index.html` file directly onto it
4. Netlify will give you a URL like: `https://random-name-123.netlify.app`
5. Click **Site settings → Change site name** to rename it to something like `almahlunyagi`

Your site will be live at: `https://almahlunyagi.netlify.app` ✨

### Option B — GitHub Integration (Recommended for updates)
This method means every time you edit `index.html` on GitHub, your site updates automatically.

**Set up a GitHub repo for your site:**
1. Create a new repo called `portfolio` (or `almahlunyagi`)
2. Upload your `index.html` to it
3. The repo can be **private** (Netlify can still access it)

**Connect Netlify to GitHub:**
1. On Netlify, click **Add new site → Import an existing project**
2. Choose **Deploy with GitHub**
3. Authorize Netlify to access your GitHub account
4. Select your `portfolio` repo
5. Leave build settings blank (it's just HTML)
6. Click **Deploy site**

**Every future update:**
- Edit `index.html` on GitHub (or use GitHub Desktop)
- Netlify auto-deploys within ~30 seconds

---

## STEP 5 — Add a Custom Domain (Optional)

If you want `www.almahlunyagi.com` instead of the Netlify subdomain:

1. Purchase a domain at [Namecheap](https://namecheap.com) or [Google Domains](https://domains.google)
2. In Netlify: **Site settings → Domain management → Add custom domain**
3. Follow Netlify's DNS instructions (they walk you through it step by step)
4. Netlify provides **free HTTPS** automatically

---

## Quick Reference — What to Update

| What | Where in index.html | What to change |
|------|-------------------|----------------|
| Hero photo | `<div class="hero-photo-placeholder">` | Replace with `<img src="...">` |
| About photo | `<div class="about-photo-placeholder">` | Replace with `<img src="...">` |
| Travel photos | `<div class="travel-img-placeholder">` | Replace with `<img class="travel-img" src="...">` |
| Contact form key | `value="YOUR_WEB3FORMS_ACCESS_KEY"` | Your Web3Forms key |
| Countries visited | `<div class="chip">` section | Add/edit country chips |
| Testimonials | `<div class="tcard">` blocks | Update with real quotes/names |

---

## Tips

- **Image sizes**: Keep photos under 500KB for fast loading. Use [squoosh.app](https://squoosh.app) to compress before uploading.
- **Photo dimensions**: Profile photos: tall/portrait (3:4 ratio). Travel photos: landscape (4:3 ratio).
- **Testing**: After deploying, test on your phone to check the mobile layout.
- **Analytics**: Add Google Analytics by pasting the GA script just before `</head>` — Netlify also offers built-in analytics.

---

*Questions? Email: lunyagialmah@gmail.com*
