# Media Production Website
## Overview
This project is a multi-page responsive website for a fictional Media Production Company. The purpose of the site is to present the company’s services, showcase media content (video and audio), provide company information, and allow visitors to contact the business through a structured form.

The website includes four pages:

## What's Included

- `Home(index.html)` - Introduction and hero section describing the company.
- `About (about.html)` – Information about the team and services.
- `Media (media.html)` – Video showcase, audio sample, and studio location.
- `Contact (contact.html)` – Contact form with validation and accessibility improvements.
- `css/styles.css` - Stylesheet 
- `images/` folder - Images
- `media/` folder - Video/Audio files

## Issues Found

The starter code contained several problems:

### 1.  HTML and CSS errors
  - Missing semantic HTML elements (`header`, `main`, `section`, `footer`)
  - Missing `<meta>` tags and accessibility attributes
  - Missing `<title>` validation requirement
  - Images missing `alt` attributes
  - Improper `<video>` setup (missing controls and fallback)
  - Missing audio and iframe elements
  - Form missing labels and proper input types
    
### 2. CSS Issues
  - No Flexbox layouts
  - No CSS Grid layout
  - No responsive design
  - No pseudo-classes
  - No transitions or animations
  - Low colour contrast in hero section
  - Poor navigation styling
    
### 3.Structural Issues
  - Missing service items
  - Missing portfolio grid
  - Media elements incomplete
  - No accessibility considerations


## Fixes and Implementations

The project was improved by:

  - Adding semantic HTML5 elements (`header`, `nav`, `main`, `section`, `article`, `aside`, `footer`)
  - Adding required metadata (`charset`, `viewport`, `description`, `author`)
  - Fixing validation errors and removing invalid attributes
  - Improving media elements with fallback text and multiple sources
  - Implementing a complete contact form with validation
  - Adding ARIA labels and descriptive alt text
  - Adding Maps iframe for the studio location
  - Implementing responsive layouts and styling improvements

## Screenshots

- All four pages (desktop view)
- Contact form with validation
- Media elements (video, audio, iframe)
- Flexbox layout demonstration
- CSS Grid gallery layout
- Browser compatibility comparison
- Two pages in mobile view
- Animations or hover effects

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
│   ├── sample1.webm
│   ├── sample2.mp4
│   ├── sample2.webm
│   ├── sample-audio.mp3
│   └── sample-audio.ogg
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

