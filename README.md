# Media Production Website
## Overview
This project is a multi-page responsive website for a fictional Media Production Company. The project involved debugging a 70%-complete starter codebase, fixing all semantic and validation errors, and implementing advanced layout, animation, and accessibility features — without JavaScript.  The website represents a fictional media production company offering video production, audio recording, and post-production services. It consists of four fully linked pages: a home page, an about/services page, a media gallery, and a contact form. The site demonstrates professional-grade HTML structure, responsive CSS layouts using Flexbox and Grid, CSS animations and transforms, embedded media elements, and accessible form design.

The website includes four pages:

## What's Included

- `Home(index.html)` - Introduction and hero section describing the company.
- `About (about.html)` – Information about the team and services.
- `Media (media.html)` – Video showcase, audio sample, and studio location.
- `Contact (contact.html)` – Contact form with validation and accessibility improvements.
- `css/styles.css` - Stylesheet 
- `images/` folder - Images
- `media/` folder - Video/Audio files
  
---

## Issues Found

The starter code contained several problems:
 
- `<meta name="description">` missing on 3 of 4 pages
- `<iframe>` had no `title` attribute — a W3C validation error and accessibility failure
- Second `<video>` element had no `poster` attribute
- `contact.html` had no `<footer>` element
- Only 3 `<figure>/<figcaption>` image pairs (6+ required)
- Only 2 radio button options (3 minimum required)
- `type="number"` and `type="url"` inputs were absent entirely
- `min`, `max`, and `maxlength` validation attributes missing from form
- No ID selector (`#`) used anywhere in the CSS
- No adjacent sibling selector (`+`) used
- `:focus`, `:nth-child()`, `:first-child`, `:last-child`, `:not()` pseudo-classes all absent
- `grid-template-rows` never defined; no grid positioning (`grid-column: span`) used
- `align-items` used only once; only 2 flexbox layouts instead of 3
- `@keyframes slideIn` had only 2 stops (`from`/`to`) instead of 3+
- Only 2 CSS transforms on the same element; a third independent transform was missing
- No gradient text effect; only `text-shadow` used
- Only 1 named `@keyframes` animation; second was missing
- No `<address>`, `<aside>`, `aria-label`, `aria-labelledby`, or `aria-current` attributes used anywhere
 
See `design/issues-identified.md` for the complete line-by-line inventory.
 
---

## Fixes and Implementations

Every HTML page was restructured with the complete set of semantic elements. Metadata was completed on all four pages. The CSS was rebuilt section-by-section to satisfy every quantitative requirement. Specific changes:
 
- Added `<meta name="description">` and `<meta name="author">` to all pages
- Added `title`, `referrerpolicy`, `loading="lazy"`, and `allowfullscreen` to the `<iframe>`
- Added `poster` to the second `<video>` element and a WebM fallback source to both videos
- Added an OGG fallback source to the `<audio>` element
- Added `<footer>` to `contact.html`
- Expanded portfolio to 6+ `<figure>/<figcaption>` image pairs across the site
- Added a third radio option (Video Call) to the contact form
- Added `type="url"` and `type="number"` inputs with `min`, `max`, `step` attributes
- Added `maxlength` to all text inputs
- Added `<aside>` sections with `<address>` elements to all four pages, including the studio address (123 Studio Lane, Sandton, ZA 2094) and phone number (072-012-3456)
- Added `aria-label`, `aria-labelledby`, and `aria-current` to navigation and sections
 
---

## Flexbox Layouts
 
**Layout 1 — Site header (`.top`):** `display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap`. The company logo and navigation sit on opposite ends of the header bar. On screens below 768px, `flex-direction: column` stacks them vertically.
 
**Layout 2 — Services section (`.flex-container`):** `display: flex; justify-content: center; align-items: stretch; flex-wrap: wrap`. Each service card uses `flex: 1 1 280px` so cards grow to fill space and wrap gracefully to a new row on smaller screens, with all cards stretching to equal height.
 
**Layout 3 — Site footer (`.bottom`):** `display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap`. Copyright text and contact address sit on opposite ends. On mobile it collapses to a column with centred text.
 
---
 
## CSS Grid Layout
 
The portfolio gallery (`.grid-gallery`) uses `display: grid` with `grid-template-columns: repeat(auto-fit, minmax(280px, 1fr))` and `grid-template-rows: auto`. The `gap` property spaces all cells at 28px. Grid positioning is demonstrated by applying `grid-column: span 2` to the first `<figure>` element, causing it to span the full width of the grid on desktop. On screens below 768px, the responsive media query collapses the span back to 1 column.
 
---
 
## Selectors and Pseudo-classes
 
**Selector types used (7):** element (`body`, `nav`, `video`, `audio`, `h2`, `p`), class (`.top`, `.nav`, `.hero`, `.service-card`, `.grid-gallery`), ID (`#contact-form-area`), attribute (`input[required]`, `iframe[title]`, `input:not([required])`), descendant (`.nav a`, `.bottom a`), child (`section > h2`, `.service-card > h3`, `article > p`), adjacent sibling (`h2 + p`, `input[type="radio"] + label`).
 
**Pseudo-classes used (7):** `:hover` (nav links, service cards, grid images, CTA button, footer links), `:focus` (nav links, all form inputs, submit button), `:focus-visible` (submit button keyboard indicator), `:nth-child()` (alternating service card backgrounds, odd nav items), `:first-child` (service card accent border, article paragraphs, grid first figure), `:last-child` (last service card border, footer paragraph alignment), `:not()` (grid captions, optional input borders, radio/checkbox exclusion from text-input styles).
 
**Combination selectors (3+):** `.nav a.active` (class + class), `article > p` (element + child combinator), `h2 + p` (adjacent sibling), `.grid-gallery figure:not(:first-child) figcaption` (descendant + pseudo-class).
 
---
 
## Animations, Effects, Transforms, and Transitions
 
**Text effects:** `text-shadow` on `.hero h2` with a dual-layer shadow including a pink glow. Gradient text via `-webkit-background-clip: text` and `background-clip: text` on the `.gradient-text` utility class, creating a pink-to-orange gradient across text.
 
**Transforms (4):** `scale(1.08)` on grid images on hover; `rotate(0.8deg)` on the same images; `translateY(-3px)` on the CTA button and `translateY(-6px)` on service cards on hover; `rotate(0deg → 360deg)` on the `.loading-spinner` element via `@keyframes spin`.
 
**Transitions (6):** nav link colour and border-bottom; CTA button background and transform; service card transform and box-shadow; grid image scale; form input border-colour and box-shadow on focus; submit button background and transform.
 
**@keyframes animations (4):** `slideIn` — 3 stops (0%, 60%, 100%) — hero heading bounces in from above. `fadeUp` — 3 stops — hero paragraph rises from below with a 0.3s delay. `pulse` — continuous loop — first service card glows with a pink shadow ring. `spin` — continuous 360° rotation — loading spinner element.
 
---
 
## Accessibility Improvements
 
- `lang="en"` on all `<html>` elements
- `aria-label="Main navigation"` on all `<nav>` elements
- `aria-current="page"` on the active navigation link per page
- `aria-labelledby` linking all `<section>` elements to their heading IDs
- `aria-label` on both `<video>` elements and the `<audio>` element
- `title` attribute on `<iframe>` (also a W3C validation requirement)
- `role="radiogroup"` and `aria-labelledby` on the radio button group
- `aria-hidden="true"` on asterisk (`*`) symbols so screen readers don't read them as "star"
- `<address>` elements used for all contact information
- All form inputs have explicit `<label for="...">` associations
- `:focus` and `:focus-visible` styles ensure keyboard-navigable interactive elements are always visually indicated
- `autocomplete` attributes on personal information fields
 
---
 
## Cross-Browser Compatibility
 
Tested in **Google Chrome 124** and **Mozilla Firefox 125**. Both browsers rendered all layouts, animations, and form elements consistently.
 
Browser-specific CSS used:
- `-webkit-background-clip: text` — required for Safari and older Chrome to enable gradient text clipping. The standard `background-clip: text` is written immediately after for all other browsers.
- `-webkit-text-fill-color: transparent` — required alongside `background-clip: text` for the gradient text effect to display correctly in WebKit browsers.
- `accent-color` — used on radio and checkbox inputs for brand-coloured controls. Supported in all modern browsers; older browsers fall back to the system default appearance with no functional loss.
 
No layout differences were observed between Chrome and Firefox. The sticky header, grid gallery, flexbox services, and form all rendered identically.
 
---
 
## How to View
 
**Option 1 — Live Server (recommended for Codespaces/VS Code):**
1. Install the "Live Server" extension by Ritwick Dey from the VS Code Extensions panel
2. Right-click `index.html` in the file explorer and choose "Open with Live Server"
3. The site opens automatically in your browser on port 5500
 
**Option 2 — Python local server:**
```bash
python3 -m http.server 5500
```
Then open `http://localhost:5500` in your browser. In GitHub Codespaces, go to the Ports tab and click the globe icon next to port 5500.
 
**Option 3 — Direct file open:**
Open `index.html` directly in any browser. Note: the Google Maps iframe may be blocked by some browsers when opened as a local file due to mixed-content rules; use a local server for full functionality.
 
**File structure required:**
```
project/
├── index.html
├── about.html
├── media.html
├── contact.html
├── css/
│   └── styles.css
├── images/
│   ├── hero.jpg
│   ├── work1.jpg … work6.jpg
│   ├── video-thumb1.jpg
│   └── video-thumb2.jpg
├── media/
│   ├── sample1.mp4
│   ├── sample2.mp4
│   
└── design/
    ├── wireframe.html
    └── issues-identified.md
```
 
---
 
## Known Issues / Limitations
 
- All image and media file paths are set up correctly but the actual image and video files (`work1.jpg` through `work6.jpg`, `hero.jpg`, `sample1.mp4`, etc.) need to be placed in the `images/` and `media/` folders respectively. The HTML and CSS are complete; only the asset files need to be supplied.
- The Google Maps iframe `src` URL uses a placeholder embed. Replace the `pb=...` parameter in `media.html` with a real Google Maps embed URL from maps.google.com → Share → Embed a map to display an actual location.
- The `novalidate` attribute on the contact form was added during development to allow custom styling of validation states. Remove it if you want the browser's native validation tooltips to appear when the form is submitted incomplete.
- The `.gradient-text` CSS class and `.loading-spinner` element are implemented in the stylesheet. Add `class="gradient-text"` to any heading text span, and `<div class="loading-spinner"></div>` to any page section to activate these effects visually.
 
---
 
## Reflection
 
The most challenging part of debugging this project was the selector and pseudo-class coverage. The starter code appeared functional on the surface but was using fewer than 3 selector types and only 1 pseudo-class, which required a ground-up audit of every CSS rule to identify gaps rather than just fixing obvious errors.
 
The grid positioning requirement was easy to miss — `display: grid` with `auto-fit/minmax` alone doesn't demonstrate positioning techniques. Adding `grid-column: span 2` to the first figure, and handling the responsive collapse of that span in the media query, required careful testing at multiple screen widths to ensure the layout didn't break when the column count changed.
 
The `novalidate` attribute on the form was a deliberate trade-off: it enables clean CSS-controlled focus states and custom styling, but suppresses the browser's built-in validation UI. Understanding when to use it versus leaving native validation active was a useful lesson in the difference between HTML5 constraint validation and browser-rendered validation UI.
 
The iframe `title` attribute was the single most overlooked error in the starter code — it's a small attribute but it fails W3C validation and breaks screen reader accessibility entirely. It was the first thing caught when running the page through the W3C validator.

