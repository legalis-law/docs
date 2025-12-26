# Clerra Mintlify Documentation Deployment Guide

This guide will help you deploy the Clerra documentation to Mintlify.

## Prerequisites

- [ ] GitHub account
- [ ] Mintlify account (sign up at [mintlify.com](https://mintlify.com))
- [ ] Access to your domain's DNS settings (for custom domain)

## Step 1: Prepare Repository

### 1.1 Create GitHub Repository

```bash
# Navigate to mintlify-docs directory
cd mintlify-docs

# Initialize git repository
git init

# Add files
git add .
git commit -m "Initial Clerra documentation"

# Create repository on GitHub and push
git remote add origin https://github.com/your-org/clerra-docs.git
git branch -M main
git push -u origin main
```

### 1.2 Verify Files

Ensure these files exist:
- ✅ `mint.json` - Configuration file
- ✅ `introduction.mdx` - Home page
- ✅ `quickstart.mdx` - Quick start guide
- ✅ `/logo/light.svg` - Light mode logo
- ✅ `/logo/dark.svg` - Dark mode logo
- ✅ All documentation pages referenced in `mint.json`

## Step 2: Connect to Mintlify

### 2.1 Sign Up for Mintlify

1. Go to [mintlify.com](https://mintlify.com)
2. Click **Sign Up** or **Get Started**
3. Sign up with GitHub account
4. Authorize Mintlify to access your repositories

### 2.2 Connect Repository

1. In Mintlify dashboard, click **New Documentation**
2. Select your `clerra-docs` repository
3. Mintlify will detect `mint.json` automatically
4. Click **Deploy Documentation**

### 2.3 Initial Deployment

- Mintlify will build and deploy your documentation
- You'll get a temporary URL: `https://[your-project].mintlify.app`
- Visit the URL to verify deployment

## Step 3: Configure Custom Domain

### 3.1 Set Up Domain in Mintlify

1. Go to Mintlify dashboard > **Settings** > **Domain**
2. Click **Add Custom Domain**
3. Enter your domain (e.g., `docs.clerra.com`)
4. Copy the DNS records provided by Mintlify

### 3.2 Update DNS Records

Add these records to your DNS provider:

**For Subdomain (docs.clerra.com):**
```
Type: CNAME
Name: docs
Value: [provided by Mintlify]
```

**For Apex Domain (clerra.com/docs):**
```
Type: A
Name: @
Value: [IP provided by Mintlify]

Type: CNAME
Name: www
Value: [provided by Mintlify]
```

### 3.3 Wait for SSL Certificate

- DNS propagation: 5-60 minutes
- SSL certificate issuance: 10-30 minutes
- Total wait time: Up to 90 minutes

## Step 4: Configure Settings

### 4.1 Update mint.json

Edit `mint.json` with production values:

```json
{
  "name": "Clerra Documentation",
  "logo": {
    "dark": "/logo/dark.svg",
    "light": "/logo/light.svg"
  },
  "favicon": "/favicon.png",
  "colors": {
    "primary": "#375DFB",
    "light": "#6B8AFF",
    "dark": "#1E3A8A"
  },
  "topbarCtaButton": {
    "name": "Get Started",
    "url": "https://app.clerra.com/signup"
  },
  "analytics": {
    "ga4": {
      "measurementId": "G-XXXXXXXXXX"
    }
  },
  "feedback": {
    "thumbsRating": true,
    "suggestEdit": true,
    "raiseIssue": true
  }
}
```

### 4.2 Add Favicon

1. Create a `favicon.png` (32x32 or 64x64)
2. Place in `mintlify-docs/favicon.png`
3. Commit and push

### 4.3 Set Up Analytics

**Google Analytics 4:**
1. Create GA4 property at [analytics.google.com](https://analytics.google.com)
2. Get measurement ID (format: `G-XXXXXXXXXX`)
3. Add to `mint.json` under `analytics.ga4.measurementId`

## Step 5: Complete Documentation

### 5.1 Create Missing Pages

Based on the navigation in `mint.json`, create all missing pages:

```bash
# Example: Create user roles page
cat > users/roles-and-permissions.mdx << 'EOF'
---
title: 'Roles & Permissions'
description: 'Understanding user roles in Clerra'
icon: 'shield'
---

## Overview
[Your content here]
EOF
```

### 5.2 Add Images and Screenshots

1. Take screenshots of key features
2. Optimize images (compress, resize)
3. Place in `/images` directory
4. Reference in MDX files:

```mdx
<img src="/images/screenshot.png" alt="Description" />
```

### 5.3 Add Code Examples

Include practical code examples for API documentation:

```mdx
<CodeGroup>
  ```javascript
  // JavaScript example
  ```

  ```python
  # Python example
  ```
</CodeGroup>
```

## Step 6: Set Up Automatic Deployment

### 6.1 GitHub Actions (Automatic)

Mintlify automatically deploys when you push to main:

```bash
# Make changes
git add .
git commit -m "Update documentation"
git push origin main

# Mintlify detects push and redeploys
```

### 6.2 Preview Deployments

For pull requests, Mintlify can create preview deployments:

1. Go to Mintlify dashboard > **Settings** > **Previews**
2. Enable **Preview Deployments**
3. Each PR will get a preview URL

## Step 7: SEO Optimization

### 7.1 Add Metadata

Ensure every page has proper frontmatter:

```mdx
---
title: 'Descriptive Page Title'
description: 'Clear description for search engines (150-160 chars)'
icon: 'icon-name'
---
```

### 7.2 Submit Sitemap

1. Mintlify auto-generates sitemap at `/sitemap.xml`
2. Submit to Google Search Console
3. Submit to Bing Webmaster Tools

### 7.3 Create robots.txt

Mintlify creates this automatically, but verify:

```
User-agent: *
Allow: /
Sitemap: https://docs.clerra.com/sitemap.xml
```

## Step 8: Testing

### 8.1 Local Testing

```bash
# Install Mintlify CLI
npm install -g mintlify

# Run local dev server
cd mintlify-docs
mintlify dev

# Test at http://localhost:3000
```

### 8.2 Production Testing

After deployment, test:
- [ ] All pages load correctly
- [ ] Navigation works
- [ ] Search functionality
- [ ] Code snippets display properly
- [ ] Images and logos show
- [ ] Links work (internal and external)
- [ ] Mobile responsiveness
- [ ] Dark/light mode switching

### 8.3 Performance Testing

- Run Lighthouse audit
- Check page load times
- Verify asset optimization
- Test from different locations

## Step 9: Monitoring & Maintenance

### 9.1 Set Up Monitoring

**Google Analytics:**
- Track page views
- Monitor search queries
- Analyze user behavior

**Mintlify Analytics:**
- View in Mintlify dashboard
- Track popular pages
- Monitor feedback ratings

### 9.2 Regular Maintenance

**Weekly:**
- [ ] Review user feedback
- [ ] Check for broken links
- [ ] Monitor analytics

**Monthly:**
- [ ] Update outdated content
- [ ] Add new feature documentation
- [ ] Review and improve popular pages

**Quarterly:**
- [ ] Full content audit
- [ ] Update screenshots
- [ ] Review SEO performance

## Step 10: Team Collaboration

### 10.1 Add Team Members

1. Go to Mintlify dashboard > **Settings** > **Team**
2. Invite team members
3. Assign roles (Admin, Editor, Viewer)

### 10.2 Documentation Workflow

```
1. Create branch for changes
2. Write/update documentation
3. Test locally
4. Create pull request
5. Team review
6. Merge to main
7. Auto-deploy to production
```

## Troubleshooting

### Common Issues

**Deployment Fails:**
- Check `mint.json` syntax
- Verify all pages in navigation exist
- Check for broken frontmatter

**Images Not Loading:**
- Ensure images are in `/images` directory
- Use relative paths: `/images/file.png`
- Check file extensions are lowercase

**Custom Domain Not Working:**
- Verify DNS records are correct
- Wait for DNS propagation (up to 24 hours)
- Check SSL certificate status in Mintlify dashboard

**Search Not Working:**
- Ensure content has proper headings
- Verify pages are indexed
- Wait 24-48 hours after deployment

## Rollback

If you need to rollback:

```bash
# Revert to previous commit
git revert HEAD
git push origin main

# Or rollback to specific commit
git reset --hard <commit-hash>
git push -f origin main
```

## Support

**Mintlify Support:**
- Documentation: [mintlify.com/docs](https://mintlify.com/docs)
- Community: [mintlify.com/community](https://mintlify.com/community)
- Email: support@mintlify.com

**Clerra Team:**
- Internal docs: Notion workspace
- Slack channel: #documentation
- Email: docs@clerra.com

## Checklist

Before going live:

- [ ] All navigation pages created
- [ ] Logos and favicon added
- [ ] Custom domain configured
- [ ] SSL certificate active
- [ ] Analytics set up
- [ ] All images optimized
- [ ] Code examples tested
- [ ] Links verified
- [ ] Mobile tested
- [ ] SEO metadata complete
- [ ] Sitemap submitted
- [ ] Team access configured
- [ ] Backup plan documented

## Next Steps

1. ✅ Complete all pending documentation pages
2. ✅ Add screenshots and visual aids
3. ✅ Set up custom domain
4. ✅ Configure analytics
5. ✅ Launch documentation site
6. ✅ Announce to users
7. ✅ Monitor and iterate based on feedback

---

**Last Updated**: December 2025
**Version**: 1.0
**Maintained By**: Clerra Documentation Team
