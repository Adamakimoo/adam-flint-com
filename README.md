# adam-flint.com

Portfolio site for Adam Flint — Lead Instructional Designer, Sydney.

Single static page, no build step. `index.html` contains everything (styles and
script inline; fonts from Google Fonts).

## Local preview

    python3 -m http.server 8899

Then open http://localhost:8899

## Design

Direction is "the authoring canvas": the page ground is the cool grey of an
Articulate Storyline/Rise canvas, content sits on white screen surfaces with
storyboard-style mono marginalia. Highlighter yellow marks emphasis, biro blue
marks anything interactive.

- Hero is a learning objective, with the three verbs as anchor links.
- The timeline is a two-track proportional chart on a month-accurate CSS grid,
  so bar length is tenure and the parallel tracks are real geometry. Row maths
  is in the `grid-row` values — see the comment block below before editing.
- Light and dark are both first-class. `data-theme` on `<html>` wins over the
  system preference; the choice is stored in `localStorage` under `af-theme`.

## Timeline row maths

Rows run one per month, newest at top. Row 1 is the sticky header; Aug 2026 is
row 2. For any month:

    row = 24321 - (year * 12 + month) + 1

Year bands and role spans both use that formula, so adding a role means
computing its start and end rows and setting `grid-row: endRow / startRow`.

## Deploy

Hosted on Cloudflare Pages. Production deploys come from `main`.
