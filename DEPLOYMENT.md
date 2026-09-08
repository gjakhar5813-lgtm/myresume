# GitHub & Deployment Setup Guide

## Step 1: Install Git

### Windows
Download and install Git from: https://git-scm.com/download/win

### After Installation
Verify git is installed:
```bash
git --version
```

## Step 2: Create GitHub Repository

1. Go to https://github.com/new
2. Enter repository name: `webpage` (or your preferred name)
3. Add description: "Web Calculator & Resume Portfolio"
4. Choose Public (for GitHub Pages) or Private
5. Click "Create repository"

## Step 3: Configure Git Locally

Open PowerShell and run:
```bash
cd d:\Projects\webpage

# Configure git user
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"

# Initialize repository
git init

# Add all files
git add .

# Create first commit
git commit -m "Initial commit: Web Calculator and Resume"

# Add remote (replace with your GitHub URL)
git remote add origin https://github.com/YOUR_USERNAME/webpage.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 4: Deploy to a Free Hosting Platform

**Note:** GitHub Pages only supports static sites. For your Flask app, use one of these platforms:

### Option A: Railway (Recommended - Easiest)

1. Go to https://railway.app
2. Click "Start Project"
3. Select "Deploy from GitHub"
4. Connect your GitHub account and select the `webpage` repository
5. Railway will auto-detect the Procfile and deploy automatically
6. Your app will be live at a Railway-generated URL

### Option B: Render

1. Go to https://render.com
2. Click "New +"  → "Web Service"
3. Connect your GitHub account
4. Select the `webpage` repository
5. Set:
   - Name: `webpage`
   - Environment: Python 3
   - Build: `pip install -r requirements.txt`
   - Start: `python app.py`
6. Deploy and get a live URL

### Option C: Heroku (Free tier limited)

1. Go to https://www.heroku.com
2. Create account and verify email
3. Install Heroku CLI
4. Run:
```bash
cd d:\Projects\webpage
heroku login
heroku create your-app-name
git push heroku main
```

## Alternative: GitHub Pages (Static Only)

If you want GitHub Pages hosting, you'll lose the Flask backend:
1. Rename `templates/index.html` to `docs/index.html`
2. Remove all Flask functionality
3. Go to Repository Settings → Pages → Select `docs/` folder
4. Your site will be live at `https://yourusername.github.io/webpage`

## After Deployment

Your web calculator and resume will be accessible at:
- **Railway**: `https://your-app-name.up.railway.app`
- **Render**: `https://your-app-name.onrender.com`
- **Heroku**: `https://your-app-name.herokuapp.com`

## Updating Your Site

After making changes:
```bash
git add .
git commit -m "Update description"
git push origin main
```

For Railway/Render: Auto-deploys on push to main branch
For Heroku: Deploy with `git push heroku main`

## Troubleshooting

- **Git not found**: Download from https://git-scm.com
- **SSH key errors**: Use HTTPS URLs instead of SSH
- **Port issues**: Platforms automatically detect and set the PORT environment variable
