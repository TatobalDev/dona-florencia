# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static HTML website for **Jardines Doña Florencia**, a garden services business in Patagonia, Chile. No build system, no package manager, no server-side code — all files are served as-is.

Contact: jardinesflorencia2014@gmail.com | +569 91423597  
Facebook: https://www.facebook.com/jardinesflorenciapatagonia/

## Development

Open any HTML file directly in a browser, or serve with any static file server:

```bash
python3 -m http.server 8080
# or
npx serve .
```

There is no build step, linter, or test suite.

## Repository structure

- **Root-level HTML**: `index.html`, `contact.html`, `404.html` — the active site pages. The git status shows many other HTML files were deleted; only these three remain.
- **`donaflorencia/`** — an alternate/duplicate copy of the site (also `index.html` + `style.css`). The root version is the canonical one (`lang="es"`); the `donaflorencia/` copy still has `lang="en"` from the original template.
- **`style.css`** — main stylesheet (based on the "WS Garden" ThemeForest template by WordPress Showcase Team). Sections: import, skeleton, header, sections, page styles, footer, slider, modules, shopping, blog, contact, gallery, others, pricing, testimonials, colors, responsive.
- **`css/custom.css`** — override file for color customizations; add site-specific styles here rather than editing `style.css`.
- **`js/custom.js`** — site JS: accordion toggling, dropdown menu behavior, page loader fade-out, tooltips, WOW.js scroll animations, Owl Carousel.
- **`js/contact.js`** — AJAX contact form submission against the form's `action` URL; collects name, email, phone, datepicker, gardenservice, gardener, comments, verify fields.
- **`upload/`** — all editable/replaceable images (sliders, gallery, team, testimonials, shop, SVG icons). These are the images to swap when updating content.
- **`images/`** — UI chrome assets (logo, favicon, loader gif, background textures). Not typically changed.
- **`rs-plugin/`** — Revolution Slider (ThemePunch) plugin assets; treat as read-only vendor code.
- **`fonts/fontawesome/`** — Font Awesome icon font; treat as read-only vendor.

## Key conventions

- Custom styles go in `css/custom.css`, not `style.css`.
- New images belong in `upload/`, not `images/`.
- The contact form uses jQuery AJAX — a server-side script must exist at the form's `action` attribute URL to process submissions (not included in this repo).
- WOW.js controls scroll-triggered animations via the `wow` CSS class on elements. Animate.css provides the animation classes.
- The slider is powered by Revolution Slider (`rs-plugin/`); slider configuration lives inline in the HTML markup.
