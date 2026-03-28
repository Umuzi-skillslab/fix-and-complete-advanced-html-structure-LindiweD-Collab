# Media Production Co. Website — Issues Identified Report

## Overview

This document provides a detailed identification of HTML, CSS, and feature-related issues found in the starter code of the Media Production Co. website. The report includes all errors, missing features, and recommendations for fixes and enhancements.

**Total issues identified: 35**
HTML errors: 14 | CSS errors/omissions: 16 | Missing features: 5

---

## HTML Errors

### index.html (4 errors)

1. **Missing `<meta name="description">` for SEO** — No description metadata present. Required for search engine indexing and meets the metadata completeness requirement.
2. **Missing `<meta name="author">`** — Author metadata absent on this page and all others.
3. **No `<aside>` or secondary semantic structure** — Only a bare `<article>` with no real semantic hierarchy. The page used fewer than 7 distinct semantic tag types.
4. **No `<figure>` / `<figcaption>` markup** — Images were referenced with plain `<img>` tags only. Semantic figure markup was completely absent on this page.

### about.html (3 errors)

5. **Missing `<meta name="description">`** — No description tag present.
6. **Only 3 `<figure>` elements** — The requirement is 6+ across the site with proper `<figure>` / `<figcaption>` markup. Only 3 existed in the entire starter codebase.
7. **Service cards use generic `<div>` instead of `<article>`** — Service cards contained structured, self-contained content that semantically belongs in `<article>` elements.

### contact.html (5 errors)

8. **Missing `<meta name="description">`** — No description tag present.
9. **Only 2 radio button options** — The requirement specifies a minimum of 3. Only "Email" and "Phone" existed; a third option such as "Video Call" was missing.
10. **Missing `<input type="number">` and `<input type="url">`** — The requirement calls for 4+ input types beyond the basics. Both were absent entirely.
11. **No `min`, `max`, or `maxlength` attributes on inputs** — HTML5 validation attributes were incomplete. Only `required`, `pattern`, and `minlength` were used.
12. **Missing `<footer>` element** — `contact.html` was the only page without a footer, making the structure inconsistent across the site.

### media.html (2 errors)

13. **`<iframe>` missing `title` attribute** — A W3C validation error and an accessibility failure. Screen readers cannot identify the purpose of an untitled iframe. The `title` attribute is mandatory for both compliance and usability.
14. **Second `<video>` missing `poster` attribute** — Only the first video had a poster image. The second video element had no poster, leaving a blank black box before playback begins.

---

## CSS Errors & Omissions

### Selector Coverage (4 missing)

15. **No ID selector used** — The CSS contained zero `#id` selectors despite `#contact-form-area` existing in the HTML. This left a required selector type category completely absent.
16. **No adjacent sibling selector (`+`)** — Required as a combination selector type. Absent from the entire stylesheet.
17. **No `:focus` pseudo-class** — Only `:hover` was used for interactive states. `:focus` is required for keyboard accessibility and the pseudo-class minimum count.
18. **No `:nth-child()`, `:first-child`, `:last-child`, or `:not()` pseudo-classes** — All four were missing. The starter code used only `:hover` and `.active`, falling far short of the 5 pseudo-class minimum requirement.

### Grid Layout (2 missing)

19. **`grid-template-rows` never defined** — The CSS Grid used only `grid-template-columns`. `grid-template-rows` was omitted entirely despite being a required grid property.
20. **No grid positioning used** — No `grid-column: span`, `grid-row`, or `grid-area` properties were present anywhere. The requirement calls for demonstrated grid positioning techniques.

### Flexbox Coverage (2 missing)

21. **`align-items` used only once** — The requirement calls for 2+ uses in distinct flex contexts. Only the `.top` header used it.
22. **Only 2 flexbox layouts implemented** — The footer had no `display: flex`. A third distinct flexbox layout was required.

### Animations & Effects (4 missing)

23. **`@keyframes slideIn` used only 2 steps (`from` / `to`)** — The requirement specifies multiple steps. A 3-stop animation using named percentages (0%, 50%, 100%) was required instead of the shorthand `from`/`to`.
24. **Only 2 CSS transforms on the same element** — `scale` and `rotate` were applied together on a single element. A third independent transform (`translateY`, `skew`) on a separate interactive element was missing.
25. **No gradient text effect** — Only `text-shadow` was used as a text effect. A second text effect such as gradient text via `background-clip: text` was absent.
26. **Only one `@keyframes` animation** — Only `slideIn` existed. A second named animation such as `fadeUp`, `pulse`, or `spin` was required.

### Code Quality (4 errors)

27. **No CSS custom properties (`--variables`) defined** — The starter CSS used hardcoded colour and spacing values throughout (e.g. `#1a1a1a`, `#ff009d`, `0.3s ease`). No `:root` block with custom properties was present, making the code difficult to maintain and update consistently.
28. **No `box-sizing: border-box` reset** — The starter CSS had no universal reset rule. Without `box-sizing: border-box`, padding and borders add to element widths unexpectedly, causing layout inconsistencies across browsers.
29. **Duplicate `video` CSS rule** — The `video` element was targeted twice in separate rules within the same stylesheet. The duplicate `video { width: 100%; height: auto; }` rule was redundant and indicated a lack of code organisation.
30. **No meaningful CSS comments or section structure** — The starter stylesheet had no section headings, grouping comments, or organisational structure. Related rules were scattered throughout the file with no logical order.

---

## Missing Features (5)

31. **No `<address>` element anywhere** — The semantic `<address>` element for contact information was never used across any page. Plain paragraphs were used for contact details instead.
32. **No `<aside>` element** — Secondary and complementary content sections used generic `<section>` or `<div>` elements instead of the semantic `<aside>`.
33. **`<iframe>` missing `referrerpolicy` attribute** — Good practice for embedded third-party content. The attribute controls what referrer information is sent with the iframe request and was absent from the starter.
34. **`<iframe>` missing `loading="lazy"` attribute** — A performance best practice that defers loading the iframe until it is near the viewport. Missing from the starter code.
35. **No ARIA attributes anywhere** — `aria-current`, `aria-label`, `aria-labelledby`, and `role` attributes were entirely absent from navigation, sections, and form elements, making the site inaccessible to screen reader users.

---

## Recommendations

- Restructure all HTML pages using the full set of semantic elements: `header`, `nav`, `main`, `section`, `article`, `aside`, `figure`, `figcaption`, `address`, and `footer`.
- Add all missing metadata tags (`description`, `author`) to every page for SEO and authoring compliance.
- Enhance the CSS by introducing a `:root` block with custom properties, a universal `box-sizing` reset, ID selectors, combination selectors, advanced pseudo-classes, additional flexbox and grid layouts, and multiple animations and transforms.
- Update forms with proper HTML5 input types, explicit labels, full validation attributes (`required`, `min`, `max`, `minlength`, `maxlength`, `pattern`), and ARIA attributes for accessibility.
- Apply best practices for all media elements: add `poster` images to videos, `title` and `referrerpolicy` to iframes, `loading="lazy"` for performance, and fallback content for unsupported browsers.
- Organise the CSS file with clear section comments, remove duplicate rules, and use custom properties for all repeated values.
- Test across multiple browsers and devices for cross-browser compatibility and verify all pages pass W3C HTML and CSS validation with zero errors.

---

## Conclusion

Addressing the 35 identified issues transforms the starter code from a partially functional prototype into a professional, standards-compliant website. The fixes ensure the site passes W3C HTML and CSS validation, meets WCAG accessibility guidelines, renders consistently across browsers, and demonstrates all required advanced HTML and CSS techniques. Implementing proper semantic structure, responsive layouts, and accessible form design results in a website that is maintainable, inclusive, and ready for real-world use.
