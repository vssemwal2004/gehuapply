# GEHU Admissions 2027–28 – static landing page

Graphic Era Hill University (Dehradun · Bhimtal · Haldwani). Same design system as the GEU
admissions page (`D:\CP\visitpage`), with GEHU content and photos.

Pure HTML + CSS. No JavaScript, no build step, no server code.

```
index.html              the page
assets/css/style.css    all styles (mobile-first; breakpoints 560 / 861 / 1100px)
assets/fonts/           Sora + Inter (woff2)
assets/brand/           GEHU logo (logo-color.png = official full-colour logo, header; logo.svg = official white logo, footer)
assets/img/<section>/   images, named <name>-<width>.webp (used via srcset); brand/ holds the favicon PNGs
```

## Preview
Serve the folder over http (webfonts are blocked on `file://`), e.g.
`npx serve .` or `python -m http.server`. All paths are relative, so it works from any sub-folder.

## Sections
Hero · Tapes · 01 About · 02 Why GEHU · 03 Programmes · 04 Placements ·
05 Campus · 06 Admissions & scholarships · 07 FAQs · CTA · Footer

## No form (by design, for now)
There is no application form on the right of the hero, and the side "Apply" tab from the GEU
page has been removed. Every "Apply" button and every programme link points to `#apply`, an
empty `<div class="hero__slot" id="apply">` at the bottom of the hero (search for `FORM SLOT`).
To add a form later, put it in that slot; or, to send students to an existing portal, replace
`href="#apply"` with the portal URL.

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
