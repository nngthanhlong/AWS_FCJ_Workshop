# AWS FCJ Workshop - Internship Report

Static website generated from Hugo with complete English and Vietnamese translations of AWS internship workshop content.

## 📋 Contents

- **1-Worklog**: Weekly reports (Weeks 1-12) covering AWS services learning
- **2-Proposal**: Online Library - Serverless Content Platform proposal
- **3-BlogsTranslated**: Translated AWS technical blogs
- **4-EventParticipated**: Event attendance records
- **5-Workshop**: Serverless workshop with Lambda & API Gateway
- **6-Self-evaluation**: Self-assessment table
- **7-Feedback**: Feedback and suggestions

## 🚀 Build & Deployment

### Local Build
```bash
# Install Hugo (if not already installed)
# Download from https://gohugo.io/installation/

# Build static site
hugo

# Serve locally (development)
hugo server -D
```

### GitHub Pages Deployment

1. **Create GitHub Repository**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

2. **Enable GitHub Pages**
   - Go to Settings → Pages
   - Build and deployment: GitHub Actions
   - Save

3. **Automatic Deployment**
   - Every push to main/master branch will trigger automatic build and deployment
   - Check "Actions" tab to monitor build progress

## 📁 Directory Structure

```
AWS_FCJ_Workshop/
├── content/              # Markdown content
│   ├── 1-Worklog/
│   ├── 2-Proposal/
│   ├── 3-BlogsTranslated/
│   ├── 4-EventParticipated/
│   ├── 5-Workshop/
│   ├── 6-Self-evaluation/
│   └── 7-Feedback/
├── static/               # Static assets
├── themes/               # Hugo themes
├── public/               # Built static site (generated)
├── config.toml           # Hugo configuration
└── .github/workflows/    # GitHub Actions workflows
```

## 🌐 Live Site

Once deployed to GitHub Pages, your site will be available at:
- `https://YOUR_USERNAME.github.io/YOUR_REPO/`

## 🛠️ Technologies Used

- **Hugo**: Static site generator
- **hugo-theme-learn**: Documentation theme
- **GitHub Pages**: Free hosting
- **GitHub Actions**: CI/CD automation

## 📝 Languages

- English (primary)
- Vietnamese (Vi)

Both languages are available in the navigation menu.

## 📄 License

This project is part of AWS First Cloud Journey internship program.
