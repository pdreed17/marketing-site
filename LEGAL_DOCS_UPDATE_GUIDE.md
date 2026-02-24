# Legal Documents Update Guide

**Last Updated:** February 24, 2026

## Current Versions
- **Terms of Service:** Last updated February 17, 2026
- **Privacy Policy:** Last updated February 17, 2026

## Hosted Legal Documents (Source of Truth)

Legal docs are hosted on **Vercel** and live at:
- **Privacy Policy:** https://musickollab.app/privacy
- **Terms of Service:** https://musickollab.app/terms

**Repository:** `/Users/petahdacheetah/Developer/kollab-legal-docs/`

This is the **ONLY place** you need to update legal documents. All other sites link to these URLs.

## Where Legal Docs Are Referenced

### 1. Marketing Site (Links to Hosted Docs)
**File:** `/Users/petahdacheetah/Developer/kollabmarketing-site/public/index.html`
**Lines ~2413-2415:**
```html
<a href="https://musickollab.app/privacy" target="_blank">Privacy Policy</a>
<a href="https://musickollab.app/terms" target="_blank">Terms of Service</a>
```
✅ **No updates needed** - Links directly to hosted docs

### 2. Web Uploader (Links to Hosted Docs)
**Location:** `/Users/petahdacheetah/Developer/kollabMusicApp/web/public/legal/`
- Check if the web uploader also links to the hosted docs or has local copies

### 3. Mobile App
**Location:** `/Users/petahdacheetah/Developer/kollabMusicApp/`
- Check if settings or legal screens link to the hosted docs

## Update Process (Simplified!)

**You only need to update ONE repository now:**

### Step 1: Edit the Master Files
```bash
cd /Users/petahdacheetah/Developer/kollab-legal-docs/

# Edit these files:
# - privacy-policy.html
# - terms-of-service.html
```

### Step 2: Update the "Last Updated" Date
Look for the line with class `update-date` in both files and change the date.

### Step 3: Deploy to Vercel
```bash
cd /Users/petahdacheetah/Developer/kollab-legal-docs/
git add .
git commit -m "Update legal docs - [describe changes]"
git push origin main
```

Vercel will automatically deploy the changes to:
- https://musickollab.app/privacy
- https://musickollab.app/terms

**That's it!** All sites linking to these URLs will automatically show the updated versions.

## Local Testing (Before Deploying)

To test locally before deploying:
```bash
cd /Users/petahdacheetah/Developer/kollab-legal-docs/
npx serve .
```

Then visit:
- http://localhost:3000/privacy-policy.html
- http://localhost:3000/terms-of-service.html

## Benefits of This Approach

✅ **Single source of truth** - Update once, applies everywhere
✅ **No manual copying** - No need to sync files across projects
✅ **Consistent versioning** - Everyone sees the same version
✅ **Easy updates** - Push to git, Vercel deploys automatically

## Checklist When Updating

- [ ] Edit files in `kollab-legal-docs/` repository
- [ ] Update "Last updated" date in both files
- [ ] Test locally if desired (`npx serve .`)
- [ ] Commit and push to git
- [ ] Verify deployment on Vercel
- [ ] Test links from marketing site work
- [ ] Update this document's "Last Updated" date at top

## Important Notes

- **Never edit copies** in other projects - edit the master in `kollab-legal-docs/`
- **All sites should link** to `https://musickollab.app/privacy` and `/terms`
- **Vercel auto-deploys** on push to main branch
- The `vercel.json` file handles URL rewrites (so `/privacy` works without `.html`)
