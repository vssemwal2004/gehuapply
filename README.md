# GEHU Admissions 2027–28 – static landing page

Graphic Era Hill University (Dehradun · Bhimtal · Haldwani). Same design system as the GEU
admissions page (`D:\CP\visitpage`), with GEHU content and photos.

HTML + CSS, no build step, no server code. The only JavaScript is the EduLeap enquiry
widget and the small file that themes it.

```
index.html              the page
assets/css/style.css    all styles (mobile-first; breakpoints 560 / 861 / 1100px)
assets/js/enquiry-theme.js  restyles the EduLeap widget to match the hero (presentation only)
assets/fonts/           Sora + Inter (woff2)
assets/brand/           GEHU logo (logo-color.png = official full-colour logo, header; logo.svg = official white logo, footer)
assets/img/<section>/   images, named <name>-<width>.webp (used via srcset); brand/ holds the favicon PNGs
```

## Cache busting
`index.html` loads `style.css?v=N` and `enquiry-theme.js?v=N`. Bump `N` whenever either file
changes, or returning visitors keep the old cached copy.

## Preview
Serve the folder over http (webfonts are blocked on `file://`), e.g.
`npx serve .` or `python -m http.server`. All paths are relative, so it works from any sub-folder.

## Sections
Hero · Tapes · 01 About · 02 Why GEHU · 03 Programmes · 04 Placements ·
05 Campus · 06 Admissions & scholarships · 07 FAQs · CTA · Footer

## Enquiry form (EduLeap CRM widget)
The right side of the hero (`<div class="hero__slot" id="apply">`) holds the EduLeap lead
widget, loaded from `staff-crm.vsilabs.co`. Every "Apply" button and programme link points to
`#apply`. Submissions go straight from the widget to the EduLeap CRM
(`data-api-url`); this site stores nothing.

- **Fields, title, colour** are set in the CRM admin for widget key `gehu-apply`. The live CRM
  config overrides the `data-*` attributes in `index.html`, so change fields there.
- **Look**: the widget renders in a Shadow DOM, so page CSS cannot style it.
  `assets/js/enquiry-theme.js` injects a stylesheet into that shadow root: navy header band
  (contour rings, ridge edge, badge, fact chips), white body, two fields per row, placeholders
  instead of labels, blue submit button. The gold offset slab behind the card is page CSS
  (`.hero__slot`). It never touches field names, validation or the request, so leads are
  unaffected.
  It relies on the vendor's class names (`.el-card`, `.el-input`, …); if EduLeap renames them,
  the form falls back to the vendor's own styling but still works.

## Where the content comes from
- **Placements**: GEHU student placement cards on gehu.ac.in (Batch 2024–2026). Top offer
  ₹66.01 L, Gunjan Bhanwal, B.Tech CSE, Batch 2026, Atlassian.
- **Programmes (79, shown as "70+")**: programme lists on gehu.ac.in/dehradun, /bhimtal and
  /haldwani, with the campuses that list each programme.
- **Scholarships, GECET, ₹1,500 fee, admission steps**: apply.gehu.ac.in.
- **Est. 2011, UGC Section 2(f), 20+ international tie-ups, 25% Uttarakhand-domicile concession**: gehu.ac.in.
- **Photos**: gehu.ac.in galleries (Bhimtal, Haldwani, Dehradun labs, university life) and the
  GEHU campus images in `D:\geu\gehu\frontend\src\assets` (bg, bg2, g). The GEU photos that
  apply.gehu.ac.in reuses were deliberately not used.

## Re-check before going live
- NIRF rank and NAAC grade are **not shown**: gehu.ac.in attributes its rankings to Graphic Era
  (Deemed to be University), so add them only once GEHU's own figures are confirmed.
- The recruiter logo strip is the group list that apply.gehu.ac.in shows ("Graphic Era").
- Scholarship percentages and GECET are from the 2026 intake; confirm the 2027–28 policy.
- Programme lists come from the campus enquiry lists; confirm with each school, especially
  which campus runs which programme.
- No phone number or email is shown: gehu.ac.in lists two different toll-free numbers
  (1800 890 6027 and 1800 270 1280). Confirm which one to publish.
- Bhimtal PIN is 263136 (gehu.ac.in); apply.gehu.ac.in shows 263132.
