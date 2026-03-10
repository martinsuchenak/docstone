# Docstone

A clean Hugo theme for documentation sites with dark/light/system theme modes, responsive layout, and accessible components.

**Requires Hugo:** 0.120.0+

## Installation

Add as a git submodule:

```bash
git submodule add https://github.com/martinsuchenak/docstone themes/docstone
```

Set the theme in your `hugo.yaml`:

```yaml
theme: docstone
```

## Configuration

```yaml
# hugo.yaml
baseURL: https://example.com
languageCode: en-us
title: My Docs

params:
  description: Short site description
  themeKey: my-site-theme       # localStorage key for theme preference
  themeColor: "#0F172A"         # browser theme-color meta tag
  author: Your Name
  warning: Optional warning banner text shown on the homepage

  # Homepage hero buttons
  heroActions:
    - name: Get Started
      url: /docs/
    - name: GitHub
      url: https://github.com/you/repo
      external: true

  # Homepage feature cards
  features:
    - title: Fast
      description: Built on Hugo, one of the fastest static site generators.
      icon: ⚡
      url: /docs/performance/
    - title: Accessible
      description: Keyboard navigable with proper ARIA roles throughout.
      icon: ♿
      url: /docs/accessibility/

# Navigation
menus:
  main:
    - name: Docs
      url: /docs/
      weight: 1
    - name: GitHub
      url: https://github.com/you/repo
      weight: 2
      params:
        external: true

  footer:
    - name: Resources
      weight: 1
      children:
        - name: Documentation
          url: /docs/
        - name: Changelog
          url: /changelog/
```

## Overriding Logos

Copy the partial into your site and replace the SVG:

```
layouts/partials/logo.html       # nav + footer logo (32×32)
layouts/partials/hero-logo.html  # homepage hero logo (96×96)
```

## Custom CSS

Create `assets/css/custom.css` in your site — it's automatically loaded after the theme styles.

## Search

Docstone includes Pagefind search integration. To enable:

1. Add Pagefind to your project:
```bash
npm install -D pagefind
```

2. Update your build script in `package.json`:
```json
"scripts": {
  "build": "hugo --minify && npx pagefind --site public"
}
```

3. The search box appears automatically in the header on desktop. Pagefind indexes your site after Hugo builds it.

## Shortcodes

### Notice

```
{{</* notice type="info" title="Note" */>}}
Content here supports **markdown**.
{{</* /notice */>}}
```

Types: `info`, `warning`, `tip`, `danger`

### Tabs

```
{{</* tabcontainer */>}}
{{</* tab name="npm" */>}}
npm install my-package
{{</* /tab */>}}
{{</* tab name="yarn" */>}}
yarn add my-package
{{</* /tab */>}}
{{</* /tabcontainer */>}}
```

## Front Matter

```yaml
---
title: Page Title
description: Shown below the title in docs pages
toc: true   # set false to hide table of contents (default: true)
---
```

## License

MIT — see [LICENSE](LICENSE)
