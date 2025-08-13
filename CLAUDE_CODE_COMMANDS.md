# Claude Code Commands - COPY AND PASTE THIS TO CLAUDE CODE

## Step 1: Initialize Git and Create GitHub Repository

```bash
cd C:\summerlin-pools-website
git init
git add .
git commit -m "Initial commit - Summerlin Pools website"

# Create GitHub repository
gh repo create summerlin-pools --public --source=. --remote=origin --push
```

## Step 2: If gh command doesn't work, use these manual steps:

```bash
cd C:\summerlin-pools-website
git init
git add .
git commit -m "Initial commit - Summerlin Pools website"

# After manually creating repo on GitHub.com, run:
git remote add origin https://github.com/YOUR_USERNAME/summerlin-pools.git
git branch -M main
git push -u origin main
```

## Step 3: Deploy to Cloudflare Pages

1. Go to: https://dash.cloudflare.com/
2. Click "Workers & Pages" in sidebar
3. Click "Create application" → "Pages" → "Connect to Git"
4. Select your GitHub account and the "summerlin-pools" repository
5. Configuration settings:
   - Project name: summerlin-pools
   - Production branch: main
   - Build command: (leave empty - it's static HTML)
   - Build output directory: /
6. Click "Save and Deploy"

## Step 4: Connect Your Domain

After deployment:
1. In Cloudflare Pages, go to your project
2. Click "Custom domains" tab
3. Click "Set up a custom domain"
4. Enter: summerlinpools.com
5. Follow DNS configuration instructions

## Step 5: Update Phone Number

Before going live, update all instances of XXX-XXXX with your actual phone number:

```bash
# In Claude Code, you can use:
sed -i 's/XXX-XXXX/YOUR-ACTUAL-NUMBER/g' index.html
git add index.html
git commit -m "Update phone number"
git push
```

## Quick Updates After Initial Deploy

```bash
# Make your changes to index.html, then:
git add .
git commit -m "Update: description of changes"
git push

# Cloudflare Pages will automatically redeploy
```

## Notes:
- Cloudflare Pages gives you free hosting
- Automatic SSL certificate
- Global CDN
- Automatic deployments on git push
- No build step needed for static HTML