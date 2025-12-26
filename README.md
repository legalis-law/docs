# Clerra Mintlify Documentation

This directory contains the source files for Clerra's customer-facing documentation hosted on Mintlify.

## 📚 Documentation Structure

```
mintlify-docs/
├── mint.json              # Mintlify configuration
├── introduction.mdx        # Home page
├── quickstart.mdx         # Quick start guide
├── cases/                 # Case management docs
├── documents/             # Document management docs
├── billing/               # Billing & time tracking docs
├── ai/                    # AI features documentation
├── collaboration/         # Collaboration features
├── playbooks/             # Playbooks & automation
├── integrations/          # Third-party integrations
├── workspace/             # Workspace management
├── subscription/          # Plans & billing
├── security/              # Security & compliance
├── support/               # FAQs & troubleshooting
├── users/                 # User management
├── api-reference/         # API documentation
└── guides/                # How-to guides
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ installed
- Mintlify CLI (`npm install -g mintlify`)

### Local Development

1. **Install Dependencies**
   ```bash
   cd mintlify-docs
   npm install
   ```

2. **Start Dev Server**
   ```bash
   mintlify dev
   ```

3. **Preview Documentation**
   Open [http://localhost:3000](http://localhost:3000)

### Building for Production

```bash
mintlify build
```

## 📝 Writing Documentation

### Creating New Pages

1. Create a new `.mdx` file in the appropriate directory
2. Add frontmatter with title, description, and icon
3. Write content using MDX (Markdown + React components)
4. Update `mint.json` navigation to include the new page

Example:

```mdx
---
title: 'Page Title'
description: 'Brief description for SEO'
icon: 'icon-name'
---

## Your Content Here

Write using standard Markdown with Mintlify components.
```

### Available Components

Mintlify provides special components for rich documentation:

#### Cards
```mdx
<Card title="Card Title" icon="icon-name" href="/link">
  Card description
</Card>

<CardGroup cols={2}>
  <Card title="Card 1" icon="icon">Content</Card>
  <Card title="Card 2" icon="icon">Content</Card>
</CardGroup>
```

#### Accordions
```mdx
<AccordionGroup>
  <Accordion title="Question">
    Answer content here
  </Accordion>
</AccordionGroup>
```

#### Code Blocks
```mdx
<CodeGroup>
  ```javascript
  const example = "code";
  ```

  ```python
  example = "code"
  ```
</CodeGroup>
```

#### Callouts
```mdx
<Tip>Helpful tip</Tip>
<Warning>Important warning</Warning>
<Info>Informational note</Info>
<Check>Success message</Check>
```

#### Steps
```mdx
<Steps>
  <Step title="First Step">
    Content for step 1
  </Step>
  <Step title="Second Step">
    Content for step 2
  </Step>
</Steps>
```

#### Tabs
```mdx
<Tabs>
  <Tab title="Tab 1">
    Content for tab 1
  </Tab>
  <Tab title="Tab 2">
    Content for tab 2
  </Tab>
</Tabs>
```

## 🎨 Branding & Styling

### Colors

Brand colors are defined in `mint.json`:

- **Primary**: `#375DFB` (Clerra Blue)
- **Light**: `#6B8AFF`
- **Dark**: `#1E3A8A`
- **Background (Dark)**: `#0A0D14`

### Logo

Place logo files in the `/logo` directory:
- `light.svg` - Logo for light mode
- `dark.svg` - Logo for dark mode

### Favicon

Place `favicon.png` in the root directory.

## 📄 Configuration

The `mint.json` file contains:

- **Navigation** - Page organization and hierarchy
- **Branding** - Colors, logos, and styling
- **Integrations** - Analytics, feedback widgets
- **SEO** - Metadata and search configuration

### Navigation Structure

```json
{
  "navigation": [
    {
      "group": "Group Name",
      "pages": [
        "page-slug",
        "folder/page-slug"
      ]
    }
  ]
}
```

## 🔍 SEO Best Practices

- Use descriptive titles and descriptions in frontmatter
- Include relevant keywords naturally
- Use proper heading hierarchy (H1 → H2 → H3)
- Add alt text to images
- Include internal links between related pages

## 📊 Analytics

Analytics are configured in `mint.json`:

```json
"analytics": {
  "ga4": {
    "measurementId": "G-XXXXXXXXXX"
  }
}
```

## 🚢 Deployment

### Automatic Deployment

Mintlify automatically deploys when you push to your main branch.

1. Commit changes to git
2. Push to GitHub
3. Mintlify deploys automatically
4. View live at `https://docs.clerra.com` (or your custom domain)

### Custom Domain Setup

1. Go to Mintlify dashboard
2. Add custom domain
3. Update DNS records as instructed
4. Wait for SSL certificate provisioning

## 🧪 Testing

### Before Deploying

- [ ] Run local dev server and test all pages
- [ ] Check all links work correctly
- [ ] Verify images and assets load
- [ ] Test search functionality
- [ ] Review on mobile devices
- [ ] Proofread content for typos
- [ ] Validate code examples

### Link Checking

```bash
# Install broken-link-checker
npm install -g broken-link-checker

# Check for broken links
blc http://localhost:3000 -ro
```

## 📱 Mobile Optimization

All pages should be mobile-responsive. Test on:
- iPhone (Safari)
- Android (Chrome)
- iPad (Safari)

## 🤝 Contributing

### Documentation Standards

1. **Clarity**: Write for non-technical users
2. **Completeness**: Cover all features thoroughly
3. **Examples**: Include practical examples
4. **Accuracy**: Keep information up-to-date
5. **Consistency**: Follow style guide

### Style Guide

- Use active voice
- Write in second person ("you")
- Keep sentences concise
- Use bullet points for lists
- Include screenshots where helpful
- Bold important terms on first use

### Review Process

1. Create draft in separate branch
2. Self-review for quality
3. Test locally
4. Create pull request
5. Team review
6. Merge and deploy

## 🔧 Maintenance

### Regular Updates

- Update version numbers when features change
- Add new pages for new features
- Archive deprecated features
- Update screenshots periodically
- Refresh examples and use cases

### Content Audit

Quarterly review:
- Check for outdated information
- Verify all links still work
- Update statistics and examples
- Improve unclear sections
- Add missing documentation

## 📞 Support

### Documentation Issues

- Report issues: [GitHub Issues](https://github.com/clerra/docs/issues)
- Suggest improvements: [Feature Requests](https://github.com/clerra/docs/discussions)

### Mintlify Support

- [Mintlify Documentation](https://mintlify.com/docs)
- [Mintlify Community](https://mintlify.com/community)
- [Mintlify Support](mailto:support@mintlify.com)

## 📚 Resources

- [Mintlify Quickstart](https://mintlify.com/docs/quickstart)
- [MDX Documentation](https://mdxjs.com/)
- [Component Library](https://mintlify.com/docs/components)
- [SEO Best Practices](https://mintlify.com/docs/seo)

## 🎯 Next Steps

1. Complete all documentation pages (see sections below)
2. Add screenshots and images
3. Create video tutorials (optional)
4. Set up custom domain
5. Configure analytics
6. Launch documentation site

### Pending Pages

Pages that still need to be created:

**Cases:**
- [ ] case-workflow.mdx
- [ ] timelines.mdx
- [ ] checklists.mdx
- [ ] case-sharing.mdx
- [ ] case-intake.mdx

**Documents:**
- [ ] uploading-documents.mdx
- [ ] organization.mdx
- [ ] vault-system.mdx
- [ ] versioning.mdx
- [ ] search.mdx
- [ ] security.mdx

**Billing:**
- [ ] time-tracking.mdx
- [ ] creating-invoices.mdx
- [ ] approval-workflow.mdx
- [ ] payment-tracking.mdx
- [ ] billing-reports.mdx

**AI:**
- [ ] document-analysis.mdx
- [ ] case-insights.mdx
- [ ] playbook-guidance.mdx
- [ ] usage-analytics.mdx

(And many more... see mint.json for full list)

---

**Version**: 1.0
**Last Updated**: December 2025
**Maintained By**: Clerra Documentation Team
