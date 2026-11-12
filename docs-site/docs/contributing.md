---
id: contributing
title: Contributing to Documentation
sidebar_position: 8
slug: /contributing
---

# Contributing to Documentation

Help improve this documentation! We welcome contributions from the community.

## Quick Start

1. **Fork the repository**: [github.com/fnjlabs-arch/OSS-DocumentScanner](https://github.com/fnjlabs-arch/OSS-DocumentScanner)

2. **Clone your fork**:
   ```bash
   git clone https://github.com/YOUR_USERNAME/OSS-DocumentScanner.git
   cd OSS-DocumentScanner/docs-site
   ```

3. **Install dependencies**:
   ```bash
   npm install
   ```

4. **Start the dev server**:
   ```bash
   npm start
   ```

5. **Make your changes** to files in `docs-site/docs/`

6. **Submit a pull request**

## Documentation Structure

```
docs-site/
├── docs/                    # Documentation markdown files
│   ├── getting-started.md   # Document Scanner intro
│   ├── capture.md           # Capture features
│   ├── edit-and-enhance.md  # Editing features
│   ├── export.md            # Export options
│   ├── sync-and-backup.md   # Sync configuration
│   ├── settings.md          # All settings
│   ├── faq.md               # FAQ
│   ├── contributing.md      # This file
│   └── cardwallet/          # CardWallet-specific docs
│       ├── getting-started.md
│       ├── scanning-cards.md
│       └── managing-cards.md
├── src/
│   ├── pages/               # Homepage and custom pages
│   └── css/                 # Custom styles
├── static/img/              # Images and screenshots
├── docusaurus.config.js     # Site configuration
└── sidebars.js              # Sidebar structure
```

## How to Edit Pages

### Editing Existing Pages

1. Navigate to `docs-site/docs/`
2. Find the markdown file you want to edit
3. Make your changes
4. Preview with `npm start`
5. Submit a pull request

### Adding New Pages

1. Create a new `.md` file in `docs-site/docs/`
2. Add front matter:
   ```markdown
   ---
   id: my-page
   title: My Page Title
   sidebar_position: 5
   slug: /my-page
   ---

   # My Page Title
   
   Content goes here...
   ```
3. Add the page to `sidebars.js`

### Adding Screenshots

1. Take or generate screenshots (see [Maestro section](#maestro-screenshots))
2. Save to `docs-site/static/img/`
3. Reference in markdown:
   ```markdown
   ![Description](/img/my-screenshot.png)
   ```

## Maestro Screenshots

We use Maestro for automated screenshot generation:

```bash
# Generate all screenshots
./docs-site/maestro/generate-screenshots.sh android
```

Screenshots are saved directly to `docs-site/static/img/` with the correct filenames.

### Adding New Screenshot Flows

1. Create a new flow in `docs-site/maestro/screenshots/`:
   ```yaml
   # my-screenshot.yaml
   appId: com.akylas.documentscanner
   ---
   - launchApp
   - tapOn: "Some Button"
   - takeScreenshot: ../../static/img/my-screenshot
   ```

2. Add to `generate-screenshots.sh`

## Translations

### Translating Documentation

1. Generate translation files:
   ```bash
   npm run write-translations -- --locale fr
   ```

2. Copy docs to translate:
   ```bash
   mkdir -p i18n/fr/docusaurus-plugin-content-docs/current
   cp -r docs/* i18n/fr/docusaurus-plugin-content-docs/current/
   ```

3. Translate the copied markdown files

4. Test your translations:
   ```bash
   npm start -- --locale fr
   ```

### Supported Locales

| Locale | Language |
|--------|----------|
| `en`   | English (default) |
| `fr`   | French |
| `es`   | Spanish |
| `de`   | German |

### Using App Translations

The app has translations in JSON files at `app/i18n/` (e.g., `app/i18n/en.json`, `app/i18n/fr.json`). When documenting settings, you can reference the translation keys to ensure consistency:

```markdown
<!-- Reference app translation key for accuracy -->
**Setting**: `auto_scan` - "discover and add documents automatically"
```

## Style Guide

### Writing Style

- Use clear, concise language
- Write for users, not developers
- Use active voice
- Include practical examples

### Formatting

- Use headers hierarchically (H1 → H2 → H3)
- Use tables for comparing options
- Use code blocks for commands and paths
- Use admonitions for tips and warnings:

```markdown
:::tip
Helpful tip here
:::

:::warning
Important warning here
:::

:::info
Informational note here
:::
```

### Images

- Use descriptive alt text
- Optimize images for web
- Use consistent naming: `feature-action.png`
- Place in `static/img/`

## Building and Testing

### Local Development

```bash
npm start          # Start dev server
npm run build      # Build for production
npm run serve      # Serve production build locally
```

### Checking Links

```bash
npm run build      # Build will fail on broken links
```

### Checking Translations

```bash
npm run build -- --locale fr    # Build specific locale
```

## Pull Request Guidelines

1. **One topic per PR**: Keep changes focused
2. **Describe changes**: Explain what and why
3. **Test locally**: Ensure build passes
4. **Screenshots**: Include before/after for UI changes
5. **Link issues**: Reference related issues

### PR Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New documentation
- [ ] Documentation update
- [ ] Translation

## Testing
- [ ] Built locally with `npm run build`
- [ ] Tested on mobile viewport
- [ ] Checked links work

## Screenshots (if applicable)
```

## Getting Help

- **Questions**: Open a [GitHub Discussion](https://github.com/fnjlabs-arch/OSS-DocumentScanner/discussions)
- **Bugs**: Open a [GitHub Issue](https://github.com/fnjlabs-arch/OSS-DocumentScanner/issues)
- **Chat**: Join the community on GitHub

## Recognition

Contributors are recognized in:
- Git commit history
- Release notes (for significant contributions)
- This documentation's footer

Thank you for helping improve the documentation! 🙏
