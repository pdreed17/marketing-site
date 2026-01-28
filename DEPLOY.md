# Music Kollab Marketing Site — Deployment Guide

## Step 1: Create GitHub Repo

Go to https://github.com/new and create a new repo:
- Name: `marketing-site`
- Private or Public (your choice)
- Don't initialize with README (we have one)

## Step 2: Push to GitHub

Run these commands from the marketing-site folder:

```bash
cd marketing-site

git init
git add .
git commit -m "Initial landing page"
git branch -M main
git remote add origin https://github.com/pdreed17/marketing-site.git
git push -u origin main
```

## Step 3: Connect to Vercel

1. Go to https://vercel.com/new
2. Click "Import Git Repository"
3. Select `marketing-site`
4. Vercel will auto-detect settings from vercel.json
5. Click "Deploy"

## Step 4: Configure Domain

1. In Vercel dashboard, go to your marketing-site project
2. Click "Settings" → "Domains"
3. Add `musickollab.app` (root domain)
4. Follow DNS instructions if needed

## Step 5: Update Your Existing App Domain

Move your current uploader from `upload.musickollab.app` to `app.musickollab.app`:
1. Go to your kollabmusic-app project in Vercel
2. Settings → Domains
3. Add `app.musickollab.app`
4. Remove `upload.musickollab.app` (optional, can redirect)

## Final Domain Structure

| Domain | Points To |
|--------|-----------|
| musickollab.app | Marketing site (landing page) |
| app.musickollab.app | Web uploader / future web app |

---

## TODO After Deploy

- [ ] Connect form to ConvertKit (see FORM_SETUP.md)
- [ ] Create og-image.png (1200x630px) for social sharing
- [ ] Add analytics (Plausible or Vercel Analytics)
