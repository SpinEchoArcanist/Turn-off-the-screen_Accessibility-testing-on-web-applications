# Turn Off the Screen: What I've Learned About Accessibility Testing on Web and Mobile

HTML slide deck for the itecor Geneva BrownBag of 27 November 2026 — Simone Coppo.
Version 0.13 (45 slides; content revised; Chapter 4 in four parts; slide list by chapter; Slide navigation region; skip link; Display options with an Animations switch; images embedded; slides always complete in the zoomable layouts).

## How to open

Open `index.html` in a current browser (Chrome, Edge, Firefox or Safari). No installation and no network access are needed: the deck is one self-contained HTML file — photos and logos are embedded in it, so it also works when opened straight from the zip.

## Navigation with a screen reader

Screen readers (NVDA, JAWS, Narrator scan mode, VoiceOver) keep the arrow keys and single letters for reading in browse mode, so the presenter keys below do not reach the deck. Use instead:

- a **Skip to main slide content** link (first Tab stop) and a folded **How to use this deck** section right after it;
- the **Previous** and **Next** buttons at the bottom right of each slide, in their own **Slide navigation** region right after the slide content (Enter or Space): their name says "Next step" or "Next slide" ("Previous step" / "Previous slide"), their description says what they will show, or why they are not available. A revealed step is announced and focus stays on the button; after a slide change, focus moves to the title of the new slide;
- the **chapter menu** on the left: each chapter tells its slide range, and the current one the position ("You are on slide 12 of 45");
- the **Slide list** button at the top of the chapter menu (chevron): lists every slide by chapter (each chapter list named, e.g. "Chapter 2, Principles and legislation: slides 10 to 16"; chapter slides announced as "chapter slide"), the current one marked; Up/Down arrows move in the list, Enter opens a slide, Esc closes it;
- **Display options** button, always visible at the top right: opens the keyboard help, the Speaker notes button, the Display choice, the single-key shortcuts setting and the **Animations** checkbox (short 0.15 s fades between slides and steps; unchecked = instant changes; unchecked by default when the system asks for reduced motion). **Display**, one choice among three:
  - **Presentation**: one slide at a time, scaled to fit the screen; switches to the zoomable layout by itself when the browser is zoomed in;
  - **Zoomable slides**: one slide at a time as a scrollable page, always complete (no step-by-step: Next goes to the next slide); browser zoom enlarges the text and the content reflows;
  - **All slides on one page**: every slide and step on one scrollable page, one heading per slide — the most comfortable way to read the deck with a screen reader or after the talk.

## Keyboard shortcuts (presenter)

| Key | Action |
|---|---|
| Right arrow, Space, Page Down | Next step (next slide after the last step) |
| Left arrow, Page Up | Previous step (previous slide before the first step) |
| Home / End | First / last slide |
| N | Show or hide the speaker notes |
| V | Next display: Presentation → Zoomable slides → All slides on one page |
| Esc | Close the open panel (Display options, slide list, speaker notes) and the chapter tooltips |
| Tab | First stops: Skip to main slide content, How to use this deck (folded), Display options, then the Slide list button and the seven chapters of the left rail, then the links of the current slide, then the Previous and Next buttons |
| Enter or Space on a chapter | Go to the first slide of that chapter |

Mouse: click the left or right edge of the slide for the previous or next step; click a chapter icon in the left rail.

The single-key shortcuts **N** and **V** can be turned off with the "Single-key shortcuts (N, V)" checkbox in Display options; the Speaker notes button and the Display choice do the same jobs without the keys.

## Speaker notes

Each slide carries notes (goal, what to say, audience question, transition, backup details) and its planned minutes. Press **N**: the notes panel opens at the bottom of the window and the slide is resized above it, so the notes never cover the slide. They are hidden by default.

## Zoom

In Presentation, the 1280 × 720 slide is scaled to fit the window. When the window is narrower than 1000 CSS pixels (for example 200 % zoom on a 1920 px screen) or the zoom level rises after loading, the deck switches by itself to the zoomable layout (CSS pixels): browser zoom then enlarges the text and the content reflows to the window width. Choose "Zoomable slides" to keep that layout at any size. In the zoomable layout every slide is shown complete; step-by-step reveal exists only in Presentation.

## Accessibility statement

This deck targets **WCAG 2.2 Level AA** (no AAA claim).

How it was tested (v0.13, 23 November 2026):

- axe-core 4 (WCAG 2.0/2.1/2.2 A and AA rules + best practices) on every slide and every reveal step, in Presentation, in the zoomable layout and with all slides on one page: 0 violations;
- keyboard only: the full path through every step of every slide, the deck controls, the chapter rail and the links; visible focus on every control;
- contrast ratios computed with the WCAG formula for every colour pair and every text element; on photo slides, against the worst case (navy scrim over a white photo pixel);
- browser zoom 200 % (1280 × 720 and 1920 × 1080 windows): zoomable layout, no horizontal scrolling, no content cut off;
- `prefers-reduced-motion`: fades and movements switched off;
- accessibility tree as exposed by Chromium to screen readers, on every slide: landmarks (one navigation, main, footer), one `h1` and one `h2` per slide with no heading level skipped, lists exposed as lists, no symbol read out as a name (›, →, ≠, ·), reading order of every flow, card grid and two-column layout equal to the visual order;
- HTML validation (Nu Html Checker): no errors (the 30 warnings "role list is unnecessary" are intentional: Safari/VoiceOver drops list semantics from lists styled without bullets); no console errors.

Not yet tested: screen readers (Narrator test by the author planned before the talk).

Accessibility features: landmarks `header` (deck title, how-to text, Display options, announcements), `nav` (chapters; its first item, for screen readers only, gives the position "Slide n of 45"), `main` (slides only), `nav` "Slide navigation" (Previous / Next) and `footer`, plus the speaker-notes panel; one `h1` for the deck and one `h2` per slide, `h3`/`h4` inside blocks; flows are ordered lists whose headings say "Step n of m"; cards are lists with one heading per card; term/description pairs are description lists; arrows and separators are shown but read as words; each chapter of the left menu tells its slide range, and the current one also the position ("You are on slide 12 of 44. Slides 9 to 16"); the footer reads "Slide 12 of 44"; announcements that say what happened: "Moved to slide n of 45: title", "Added on slide n, step 2 of 3: …", "Removed the last item on slide n …", "End of the deck", "Speaker notes opened", "Display changed to …"; reveal steps and hidden slides kept out of the accessibility tree until shown; chapter tooltips dismissible with Esc; no information conveyed by colour alone.

Feedback: please open an issue in this repository.

## Credits and licences

- Photos and logos: itecor (embedded in `index.html`, photos resized to at most 1920 px wide).
- Icons of the chapter rail: [Lucide](https://lucide.dev) v1.76.0 (monitor-off, accessibility, scale, pencil-ruler, search-check, flag, book-open), under the ISC License:

```
ISC License

Copyright (c) 2026 Lucide Icons and Contributors

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```
