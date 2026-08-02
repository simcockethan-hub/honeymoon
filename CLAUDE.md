# Honeymoon itinerary — project context

This folder is a single-page HTML itinerary for Ethan & Brooke's honeymoon,
16 Aug – 20 Sep 2026. Built in a prior Claude.ai chat session; this file is
the handoff so a fresh Claude Code session has the context that chat had.

## Files

- `honeymoon-itinerary.html` — the working/master copy.
- `index.html` — identical content, filename chosen for GitHub Pages
  (serves automatically at the repo root).
- Keep these two in sync. Easiest approach: edit one, then
  `cp honeymoon-itinerary.html index.html` before committing.

## What's in the document

Single self-contained HTML file (no build step, no external JS libraries
except Google Fonts + live Google Maps `output=embed` iframes). Sections,
top to bottom:

1. Masthead — route summary, trip stats
2. Packing list — interactive checkboxes, organized by leg/climate
3. Leg 1 — Cape Town & Franschhoek (South Africa)
4. Leg 2 — Saseka Tented Camp (Kruger safari)
5. Leg 3 — Monate Game Lodge (the wedding)
6. Leg 4 — Slovenia → Croatia. This is the deep section: a nested
   two-column layout (`#leg4days`) with a day-by-day narrative on the left
   and a sticky live Google Map on the right that swaps `iframe src` per
   day via IntersectionObserver watching `.day[data-day]` elements. Map
   URLs and badges are hardcoded in a `<script>` block near the end of
   the file (`URLS` / `BADGES` arrays, indexed 0–14).
7. Leg 5 — Louisville / French Lick, Indiana (Turo rental, West Baden
   Springs Hotel, a second wedding — Brian & Josie)
8. Budget — every dollar/euro figure found in the doc, totaled, with
   explicit "not yet known" callouts rather than invented numbers
9. Money still owed — action items with real payment deadlines
10. Still open — non-financial to-dos

There's also a fixed section-jump nav: a left rail on wide screens
(`#jumpnav`, shown above 1360px), collapsing to a floating "≡" button +
sheet (`#jumptoggle` / `#jumpsheet`) on narrower screens. Both are driven
by anchor IDs on each major section (`#packing`, `#leg1` … `#leg5`,
`#budget`, `#money`, `#open`) plus an IntersectionObserver that highlights
the active one.

## Data provenance — do not invent figures

Every dollar/euro amount, confirmation number, date, and phone number in
this document was pulled from real confirmation emails or a shared Google
Doc, not estimated. If asked to fill in a gap (e.g. an unknown lodging
cost), do not guess a number — mark it the same way existing "unknown"
items are marked (see the Budget and Money sections for the pattern:
`<div class="m-amt unknown">Not shown</div>` etc.) and say so in prose.

## Known open items (as of last handoff)

- South Africa lodging (Cape Town Airbnb, Franschhoek Airbnb) confirmed
  but no price shown on the confirmation PDFs.
- The Saseka + Monate package (Africa Tailormade) has no total cost
  captured anywhere — likely the single biggest unknown in the budget.
- Ljubljana and Lake Bohinj nights are "planned" but not confirmed —
  no booking reference for either.
- Turo return time (noon Sunday) conflicts with the West Baden checkout
  (11am) + ~1h45 drive back to Louisville — flagged, not resolved.
- Korčula balance (€661.20) due 11 Aug — check whether it's been paid
  since this handoff.

## Deploying

Repo: `github.com/simcockethan-hub/honeymoon`, served via GitHub Pages
from `index.html` at the root. To publish a change:

```bash
cp honeymoon-itinerary.html index.html
git add index.html honeymoon-itinerary.html
git commit -m "describe the change"
git push
```

GitHub Pages will pick up the change automatically within a minute or two
of the push landing on the default branch.
