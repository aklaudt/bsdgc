# BSDGC Website

Static website for the disc golf club, built with Jekyll and hosted on GitHub Pages.

## Quick Start

The site will automatically build and deploy via GitHub Actions when you push to the `main` branch.

## Customizing Your Site

### Updating Club Information

Edit `_config.yml` to update:

- **Site title and description**: Change `title` and `description`
- **Contact information**: Update email, Facebook, Instagram under `contact:`
- **Google Drive links**: Update the folder URLs under `documents:`

```yaml
contact:
  email: "yourclub@example.com"
  facebook: "https://facebook.com/yourclub"
  instagram: "https://instagram.com/yourclub"

documents:
  meeting_minutes_folder: "https://drive.google.com/drive/folders/YOUR_FOLDER_ID"
  financial_reports_folder: "https://drive.google.com/drive/folders/YOUR_FOLDER_ID"
```

### Changing Colors

All colors are centralized in `_config.yml` under `theme_colors`. Update these values to match your branding:

```yaml
theme_colors:
  primary: "#2d5016"        # Main brand color (headers, nav)
  secondary: "#7cb342"      # Accent color (highlights)
  accent: "#ff6f00"        # Call-to-action color (buttons)
  background: "#ffffff"     # Page background
  text: "#333333"          # Main text color
  link: "#2d5016"          # Link color
```

After changing colors in `_config.yml`, you'll need to update the CSS variables in `assets/css/style.css` to match. Look for the `:root` section at the top of the file.

### Editing Page Content

All pages are markdown files in the root directory:

- `index.md` - Home page
- `membership.md` - Membership information
- `documents.md` - Document links

Edit these files to update content. Use markdown syntax for formatting.

### Adding New Pages

1. Create a new `.md` file in the root directory (e.g., `events.md`)
2. Add front matter at the top:
   ```yaml
   ---
   layout: default
   title: Events
   ---
   ```
3. Add the page to navigation in `_config.yml`:
   ```yaml
   navigation:
     - name: Events
       link: /events/
   ```

## Google Drive Document Setup

To link your documents:

1. Upload files to Google Drive
2. Create a shared folder for each document type
3. Right-click the folder → Share → Get link
4. Set permissions to "Anyone with the link can view"
5. Copy the link and paste it into `_config.yml`

## Local Development

To test the site locally before pushing:

```bash
# Install dependencies
bundle install

# Run local server
bundle exec jekyll serve

# View at http://localhost:4000
```

## Deployment

The site automatically deploys to GitHub Pages when you push to `main`.

### First-time Setup

1. Push your code to GitHub
2. Go to your repository Settings → Pages
3. Under "Build and deployment", select Source: **GitHub Actions**
4. The site will build automatically

After the first deployment, your site will be available at:
`https://aklaudt.github.io/bsdgc/`

If you have a custom domain, you can configure it in GitHub's Settings → Pages.

## File Structure

```
.
├── _config.yml              # Site configuration
├── _layouts/
│   └── default.html        # Main page layout
├── assets/
│   └── css/
│       └── style.css       # Site styles
├── .github/
│   └── workflows/
│       └── jekyll.yml      # GitHub Actions workflow
├── index.md                # Home page
├── membership.md           # Membership page
├── documents.md            # Documents page
└── Gemfile                 # Ruby dependencies
```

## Common Tasks

### Update Membership Pricing
Edit `membership.md` and replace `$XX` with actual prices.

### Add a New Document Link
Edit `documents.md` and add to the document list:
```markdown
<li>
  <a href="https://drive.google.com/..." target="_blank">Document Name</a>
</li>
```

### Change Navigation Order
Edit the `navigation` section in `_config.yml`.

## Troubleshooting

### Site not updating after push
- Check GitHub Actions tab to see if build succeeded
- Builds typically take 2-3 minutes
- Make sure GitHub Pages is set to deploy from "GitHub Actions" in Settings

### Styling looks broken
- Make sure all color variables match between `_config.yml` and `assets/css/style.css`
- Clear your browser cache

### Google Drive links not working
- Verify folder sharing is set to "Anyone with the link can view"
- Check that you copied the full folder URL

## Support

For Jekyll documentation: https://jekyllrb.com/docs/
For GitHub Pages help: https://docs.github.com/en/pages
