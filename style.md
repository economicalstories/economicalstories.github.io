# Style — The Eighteenth-Century Pamphlet

Design concept for economicalstories.com.

## The idea

The books on this site parody Adam Smith — *A Wealth of Narrations*, *A Theory of
Moral Sentences*. The site should be in on the joke. We design the whole page as a
**Scottish Enlightenment pamphlet**: the kind of title page printed in Edinburgh or
Glasgow around 1776 — long centred titles in mixed sizes, a rule, an ornament, the
author's name in small capitals, and the printer's imprint at the foot.

A modern visitor should get it within two seconds: this is a writer who plays with
old economics texts, and the site itself is one of the jokes. It must read as wit,
not as a costume — which means the period styling carries the *structure* of the
page while the content stays plain, modern, and brief.

## Tone rules

- **Witty, not twee.** One or two period flourishes per screen, never a wall of them.
  The long-form heading and the ornaments do the work; body copy is written normally.
- **A pamphlet, not a parchment.** No paper textures, no sepia photo filters, no
  faux-aged edges, no blackletter. Period feel comes from typography, spacing, and
  layout — the same way a Penguin classics cover does it.
- **Everything is typeset, nothing is decorated.** If an element needs a box, a
  shadow, or a coloured button to be noticed, re-set it in type instead.

## Layout

- **Single centred column**, max-width ~34em of body text (~620px). Pamphlets are
  narrow; let the margins breathe. No sidebars, no cards, no grid of tiles.
- **The masthead is a title page.** Replace the current header + nav with a composed
  block, centred, in mixed sizes — e.g.:

  > ECONOMICAL STORIES
  > *being a website of*
  > BOOKS, PROJECTS & DIVERS EXPERIMENTS
  > *by*
  > P. C. HUBBARD

  followed by a double rule. The nav becomes one centred line of small-caps text
  links separated by middots: `Books · Projects · Author · Blog · Contact`.
- **Section breaks are ornaments, not borders.** Between sections, a centred
  asterism (`⁂`) or a simple fleuron (`❧`), not the current 2px accent underline.
- **Sections open with small-caps headings**, centred, letterspaced
  (`font-variant: small-caps; letter-spacing: 0.08em`).
- **The footer is the printer's imprint.** Centred, small, in the period voice:
  *"Printed for the Author, and sold at economicalstories.com · MMXXVI"* — with the
  contact and Medium links beneath it as plain text links.
- **No sticky header.** Pamphlets don't follow you down the page.

## Typography

- **One serif family for everything**, in the Caslon tradition (Caslon was *the*
  18th-century British book face). Recommended stack, all free on Google Fonts:
  - Body & headings: **EB Garamond** (closest free workhorse; excellent small caps
    and oldstyle figures) — or **Libre Caslon Text** for a more literal Caslon.
  - Optional display-only accent for the masthead: **IM Fell English** (digitised
    from genuine Fell types, slightly rough). Use it for the title block *only*,
    if at all — it gets noisy at body sizes.
  - Fallback stack: `Georgia, 'Times New Roman', serif` (the current Georgia base
    means the site degrades gracefully without webfonts).
- **Oldstyle figures** where supported: `font-variant-numeric: oldstyle-nums`.
- **Italics carry emphasis and the "being a…" connective lines.** No bold in body
  copy; bold is a 19th-century invention and it shows.
- **Sizes:** body 18–19px, line-height 1.65; masthead lines range from ~1rem
  (connectives) to ~2.75rem (the title). Use a modest scale — pamphlet title pages
  get their drama from *contrast between lines*, not from any one huge line.
- **Drop cap** on the first paragraph of the Author section (`::first-letter`,
  3 lines tall). One per page, maximum.

## Colour

Restraint is the concept. Ink on paper, with one accent.

| Role | Colour | Notes |
| --- | --- | --- |
| Paper | `#faf6ee` | Warm off-white; not yellowed sepia |
| Ink | `#1d1a16` | Soft black, like letterpress impression |
| Accent / links | `#7a2e2e` | Oxblood red — period rubrication; replaces the current teal |
| Rules & ornaments | `#1d1a16` | Ornaments are ink, never accent-coloured |
| Muted / imprint | `#6b6259` | Footer, captions, connective lines |

Links are accent-coloured and underlined (`text-underline-offset: 2px`), darkening
slightly on hover. Rubrication — a second colour used sparingly for emphasis — is
the historically honest way to make links visible, so this concept *strengthens*
the link-visibility fix rather than fighting it.

## Components

- **Books.** Covers stay (they're the one modern image element that earns its
  place), but lose the card chrome: no white boxes, no border-radius, no shadows.
  Each book is cover + title in italics + a plain text link — *"Sold by Amazon"* —
  set as an underlined accent link, not a pill button.
- **Projects.** Already prose with inline links; that's exactly right for this
  concept. Optionally introduce the list with a period connective: *"In which the
  author also maintains…"*
- **Subscribe form.** The hardest element to period-set; don't try too hard. A
  single-line centred form: an underlined text input (border-bottom only, no box)
  and a plain small-caps text button — `[ Subscribe ]` — in accent colour. Strip
  every MailerLite visual default; keep its JS behaviour.
- **Buttons generally:** there are none. Any current `.button` becomes a text link.

## Implementation notes

- Pure CSS on the existing single `index.html`; no build step, no framework.
  Two webfont families maximum (EB Garamond + optionally IM Fell English), loaded
  with `font-display: swap`.
- Keep the page fully responsive: the centred narrow column is naturally
  mobile-friendly; just reduce masthead sizes under 600px.
- Ornaments are Unicode characters (⁂ ❧ ☙ —), not images or icon fonts.
- Accessibility: the ornament dividers should be `aria-hidden="true"`; maintain
  WCAG AA contrast (the palette above passes); don't letterspace lowercase body
  text, only small-caps headings.

## Don'ts

- No parchment/paper-grain background images.
- No blackletter, no ye-olde long-s (ſ) in real copy — at most one in the masthead
  as a wink, and only if it still reads instantly.
- No borders, cards, shadows, or coloured buttons.
- No more than one drop cap, one asterism style, and one accent colour per page.
- Don't write *all* the copy in period voice. The masthead, section connectives,
  and imprint are in voice; books and project descriptions stay modern and clear.
