---
theme: white
transition: fade
transitionSpeed: fast
slideNumber: true
separator: "---"
width: 1280
height: 720
margin: 0
center: false
---


<style>
/*
   COLOR TOKENS
   */
:root {
  --accent1: #FE5000;   /* main accent (orange) — titles, chevrons, highlights */
  --accent3: #00C19F;   /* secondary accent (light green/teal) — callout box */
  --dark2: #333F48;     /* dark neutral — body text */
  --lt2: #E7E6E6;       /* light neutral — code background */
  --obs: #7C3AED;       /* Obsidian brand purple — small logo mark */

  /* LAYOUT CALIBRATION - the only numbers you should need to touch to adjust vertical spacing. Everything else derives from these, so changing them here updates every slide consistently. */
  --title-push: 0em;    /* gap between the pinned title and the body content below it (was 4.8em, then 2.8em - 3.2em avoids body text touching the title's underline while keeping more room than 2.8em) */
  --n: 32;  /* TOTAL slide count in the deck (32 as of v7.14: v7.11 inserted the third Demo slide, v7.14 added slide 4, the Chapter 6 divider and the synthesis slide - count includes the cover, dividers, and all Demo slides - even though those do not show the rail themselves, they still count toward "how far through the deck" the audience is). THE single number to change here if slides are added or removed; see CHAPTER RAIL block below for what else needs touching. Feeds both the marker's position and the line's orange/gray split (v7.9). */
  --footer-line: 14px;    /* shared bottom offset for the footer logo, footer text, reveal's page number, AND the corner triangle - kept in px (not em) on purpose: em is relative to each element's OWN font-size, so the same em value gave different real offsets on differently-sized elements. One px value here keeps all four bottom edges visually aligned regardless of how tall the slide's content is. */
  --body-size: 0.8em;   /* v7.15 - body text size on regular content slides (paragraphs, chevron lists, callouts). 1em = reveal's default 42px, which looked cramped. Lower this one number for more white space; footnotes (.note-gray) follow at 80% of it. Cover, dividers, demo slides and inline-sized statements (thesis, navy panel) are not affected. */
  --block-gap: 0.9em;   /* v7.17 - vertical space below each paragraph, chevron list and callout on regular content slides (list items get 70% of it). Raise it for airier slides, lower it if a dense slide overflows above its title. Uses margin-BOTTOM on purpose: margin-top on direct children is already forced to --title-push by the "no-push" rule below. */
  --sectionnum-offset: -0.7em; /* moves the big chapter number (e.g. "02") up/down on chapter slides - negative = move up, positive = move down */
}

/*
   GLOBAL FONT
   */
.reveal, .reveal h1, .reveal h2, .reveal h3, .reveal p, .reveal li {
  font-family: Arial, Helvetica, sans-serif;
}

/*
   1. SLIDE POSITIONING RESET
   Every slide is pinned to the top-left corner and stretched to fill
   the full 1280x720 area, instead of relying on reveal's default
   translateY centering. This keeps titles/footers/logos at identical
   pixel positions on every slide regardless of content height.
   IMPORTANT: this reset is scoped to ":not(.overview)" so that when the
   user presses ESC to open the slide overview, reveal's own grid
   layout (which relies on inline transforms) is left alone. Without
   this scoping, the forced "transform:none" / "position:absolute;
   top:0;left:0" below would collapse every slide on top of the first
   one in overview mode, which is the bug that was reported.

   NOTE: there used to be a ".reveal .slides { height: 100% !important }"
   rule here. Removed — inspecting the live DOM showed reveal.js sets an
   INLINE style on .slides (height:720px + transform:scale(...)) that is
   its own reliable, JS-computed canvas size. Our 100% override was
   silently replacing that 720px with 100% of .reveal (the actual browser
   window height) instead, which doesn't match the scale factor reveal.js
   computed for it — that mismatch is the likely root cause of the
   footer/title-push coupling, the demo-slide height gap, and the
   "footer too low in fullscreen" issue, since every bottom/bottom-fixed
   offset in this file was ultimately being measured against that wrong,
   viewport-sized box instead of the true 720px one.
   */

.reveal:not(.overview) .slides section {
  position: absolute !important;
  top: 0 !important;
  left: 0 !important;
  width: 100% !important;
  height: 100% !important;
  padding: 0 2.2em 2.2em 2.2em !important;
  box-sizing: border-box !important;
  transform: none !important; /* disables JS translateY shifts in normal/present mode */
}

.reveal .slides section.present {
  display: block !important;
}

/*
   2. PINNED SLIDE TITLE ("content-title")
   Every regular content slide's heading is pinned at the exact same
   top/left position so titles line up perfectly slide to slide.
   */
.content-title {
  position: absolute !important;
  top: 1em !important;        /* EXACT TOP POSITION - change to move all titles up/down */
  left: 2.8em !important;     /* EXACT LEFT POSITION - moved right (v7.4, retuned v7.6/v7.7, unchanged in v7.8) to clear the chapter rail (see CHAPTER RAIL block below) */
  max-width: 80% !important;  /* prevents titles from overflowing off the right edge */
  text-align: left !important; /* keeps 2-line titles aligned to the left */
  color: var(--accent1);
  font-weight: 700;
  font-size: 1.5em;
  line-height: 1.2;
  margin: 0 !important;
  padding-bottom: 0.2em;
  border-bottom: 3px solid var(--accent1);
  display: inline-block;
  z-index: 10;
}

/* Push all slide body content down below the pinned title.
   Elements that must stay fixed regardless of content height opt out
   via a single "no-push" class rather than a long chain of :not()
   selectors - a long :not() chain is what likely triggered the
   "Invalid string length" preview crash (the renderer's own
   preprocessor appears to be regex-based and fragile on this kind of
   pattern, similar to its documented crash on Obsidian internal note
   links). Add
   "no-push" to any new element you want excluded from this spacing. */
.reveal .slides section:not(.panel-demo) > *:not(.no-push) {
  margin-top: var(--title-push) !important;
}

/* Left/right centering on regular slides — fix confirmed working by
   direct testing (the earlier CSS-only attempt in v5 didn't work; this
   targets the actual wrapper the renderer generates for absolutely
   positioned content, rather than the <section> itself). */
.reveal .slides section > div[absolute="true"] {
  align-items: center !important;
}

/*SIC adding this - the centering now happens in the real Available center. GOOD*/
.reveal .slides section > div[absolute="true"]::before {
  content: "";
  height: calc(var(--title-push) + 2em);  /* title zone + buffer */
  order: -1;  /* ensure it appears first */
}

/* Reserve room for the chapter rail (v7.4, retuned v7.6/v7.7, unchanged
   in v7.8) on regular content slides, so its line/chevron column
   doesn't sit under body content. The rail's label is vertical text and
   sits on the OTHER side (toward the true left edge), so it doesn't
   factor into this margin - only the line/chevron column itself needs
   clearing. Targets the same wrapper div as the two rules just above
   (the actual box the renderer positions content in), not the <section>
   itself or its plain padding, since neither of those reliably moves
   this wrapper's content. Scoped to :not(.cover):not(.divider) because
   the rail doesn't appear on those slide types at all (nor on the
   .panel-demo slides, excluded by index instead - see CHAPTER RAIL block
   below). */
.reveal .slides section:not(.cover):not(.divider) > div[absolute="true"] {
  padding-left: 2.8em;
  box-sizing: border-box;
}


/*
   TYPOGRAPHY & GENERAL ELEMENTS
   */
.reveal p, .reveal li { color: var(--dark2); font-weight: 400; }
.subtitle2 { color: #6b7280; font-size: 0.7em; font-weight: 400; }
code { background: var(--lt2); color: var(--dark2); padding: 0.1em 0.4em; border-radius: 4px; font-size: 0.85em; }

/* Reusable "muted footnote" / "orange payoff" text styles.
   Used to style the smaller supporting lines that appear at the end of
   a slide (previously hand-styled inline on individual slides — now a
   single class each so they stay consistent and are easy to reuse). */
.note-gray   { font-size: 0.8em; color: #6b7280 !important; }                       /* muted grey footnote line - !important needed since ".reveal p" is more specific than a bare class */
.note-accent { font-size: 1em; font-weight: 500; color: var(--accent1) !important; } /* orange payoff / answer line - !important needed since ".reveal p" is more specific than a bare class */

/* BODY TEXT SIZE (v7.15) - driven by --body-size on :root.
   Scoped to regular content slides only. The callout's inner <p> is
   reset to 1em so it isn't shrunk twice (box and paragraph). An inline
   style="font-size:..." on any element still wins over these rules. */
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo) p,
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo) ul.chevlist,
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo) .calloutbox { font-size: var(--body-size); }
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo) .calloutbox p { font-size: 1em; }
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo) p.note-gray { font-size: calc(var(--body-size) * 0.8); }

/* VERTICAL SPACING (v7.17) - driven by --block-gap on :root. */
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo):not(.panel-navy) p,
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo):not(.panel-navy) ul.chevlist,
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo):not(.panel-navy) .calloutbox { margin-bottom: var(--block-gap); }
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo):not(.panel-navy) .calloutbox p { margin-bottom: 0; }
.reveal .slides section:not(.cover):not(.divider):not(.panel-demo):not(.panel-navy) ul.chevlist > li { margin-bottom: calc(var(--block-gap) * 0.7); }

/* ACCENT WORD (v7.16) - highlights the key word of a slide in the
   accent orange, bold. Usage: <span class="accent">word</span>.
   !important because ".reveal p" would otherwise force the body colour. */
.accent { color: var(--accent1) !important; font-weight: 700; }

/* CHAPTER MAP (v7.16) - slide 5 "Where we're headed". Each row is a
   3-column grid: number | chapter name | grey subtitle. A wide list so
   names start further left and subtitles further right, instead of one
   narrow centred column.
   - font-size: overall size of the map
   - width: total width of the map (wider = more spread out)
   - grid-template-columns: widths of number / name / subtitle columns */
ul.chapter-map {
  list-style: none;
  padding: 0;
  margin: 0 auto;
  width: 1000px;
  max-width: 100%;
  text-align: left;
  font-size: 0.7em;
}
ul.chapter-map > li {
  display: grid;
  grid-template-columns: 1.4em 1fr 1.4fr;
  column-gap: 0.8em;
  align-items: baseline;
  padding: 0.45em 0;
  border-bottom: 1px solid #e5e7eb;
}
ul.chapter-map > li:last-child { border-bottom: none; }
ul.chapter-map .cm-num  { color: var(--accent1); font-weight: 700; }
ul.chapter-map .cm-name { color: var(--dark2); font-weight: 700; }
ul.chapter-map .cm-sub  { color: #6b7280; font-size: 0.85em; }

/* Chevron bullet list — always flush-left regardless of slide centering. */
ul.chevlist { list-style: none; padding-left: 0; text-align: left; }
ul.chevlist > li { position: relative; padding-left: 1.3em; margin-bottom: 0.5em; }
ul.chevlist > li::before { content: "›"; color: var(--accent1); font-weight: 700; position: absolute; left: 0; }

/*
   COVER / DIVIDER (CHAPTER) SLIDE SHARED SCRIM
   */
.cover, .divider { color: #ffffff; }

/* Force white text on cover/divider slides by default (they sit on a
   photo background) — but carve out exceptions for the elements that
   must be accent-orange: the cover's main title (.cover-title) and a
   chapter slide's big title (.sectiontitle). */
.cover .content-title, .divider .content-title,
.cover h1:not(.cover-title), .divider h1,
.cover h2:not(.sectiontitle), .divider h2:not(.sectiontitle),
.cover p, .divider p { color: #ffffff !important; }

.cover .cover-title { color: var(--accent1) !important; } /* main title on slide 1 */
.divider .sectiontitle { color: var(--accent1) !important; } /* chapter title on chapter slides */

.cover::before, .divider::before {
  content: "";
  position: absolute;
  inset: 0;
  background: rgba(10,10,15,0.45); /* darkening scrim so white text stays readable over the photo */
  z-index: 0;
}
.cover > *, .divider > * { position: relative; z-index: 1; }

/*
   TITLE SLIDE (SLIDE 1) — name/date block, bottom right
   */
.title-meta {
  position: absolute;
  right: 3em;              /* v7.11: was 1.2em (19px) - the block sat under reveal's next-slide arrow. 3em = 48px, i.e. ~29px further left, about 30% of the block's own ~95px width. Increase if it still touches the arrow. */
  bottom: 1.2em;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;         /* Arial 16, as requested */
  font-weight: 400;
  color: #ffffff;
  text-align: right;
  line-height: 1.4;
  z-index: 1;
}

/*
   CHAPTER (DIVIDER) SLIDE LAYOUT
   */
.divider-wrap { position: absolute; inset: 0; display: flex; align-items: center; justify-content: space-between; padding: 0 1.6em; }
.divider-left { max-width: 56%; }
.sectiontitle { font-size: 2.2em; font-weight: 400; margin: 0 0 0.2em 0; text-align: left; } /* color set above via .divider .sectiontitle */
.sectionsub   { font-size: 1.05em; font-weight: 400; color: #fff; opacity: 0.92; margin: 0; text-align: left; }

/* Big chapter number, e.g. "02" — sized to the equivalent of Arial 287 Bold. */
.sectionnum {
  font-size: 287px;
  font-weight: 700;
  color: #fff;
  opacity: 0.85;
  line-height: 1;
  flex-shrink: 0;
  transform: translateY(var(--sectionnum-offset)); /* negative = move up, positive = move down */
}

/* Small chevron badge, bottom-right of every slide that uses it (cover, chapter dividers, closing slide). */
.chevron-badge { position: fixed; bottom: 0.9em; right: 0.9em; width: 1.7em; height: 1.7em; color: #fff; z-index: 1; }
.chevron-badge svg { width: 100%; height: 100%; }

/* On chapter slides specifically (a chevron-badge that follows a divider-wrap),
   the badge is accent-orange and doubled in size ("100% bigger"). Scoped with
   the sibling selector so it does NOT affect the cover slide or the closing
   "thesis" divider slide, which don't have a divider-wrap. */
.divider-wrap ~ .chevron-badge { color: var(--accent1); width: 3.4em; height: 3.4em; }

/* image7.png placed bottom-right specifically on chapter slides, positioned
   above the (now larger) chevron badge so the two don't overlap. Adjust
   "height" below to resize either one. */
.chapter-logo { position: fixed; right: 0.9em; bottom: 4.6em; height: 2em; z-index: 1; }

/*
   CALLOUT BOX
   Background = accent3 (light green), inner text = white. Horizontal
   centering comes for free from the section-level text-align:center
   rule above, since the box is display:inline-block.
   */
.calloutbox {
  border: 2px solid var(--accent3);
  background: var(--accent3);
  border-radius: 14px;
  padding: 0.8em 1.2em;
  display: inline-block;
  max-width: 900px;
  color: #ffffff;
}
.calloutbox p { color: #ffffff !important; } /* override the default dark body-text color inside the box */

/*
   NAVY STATEMENT PANEL (big standalone quote slide)
   */
.panel-navy { background: var(--dark2); color: #fff; }
.panel-navy .content-title, .panel-navy h2, .panel-navy p, .panel-navy li { color: #fff !important; border-bottom-color: #fff !important; }
.panel-navy .bigchevron { position: absolute; opacity: 0.15; right: -0.6em; top: 50%; transform: translateY(-50%); width: 7.5em; height: 7.5em; color: #fff; z-index: 0; }

/* Decorative hexagon watermark, fixed position so it never affects slide height. */
.bighex { position: absolute; right: -1em; top: 50%; transform: translateY(-50%); width: 9em; height: 9em; opacity: 0.10; color: var(--dark2); z-index: 0; pointer-events: none; }

/*
   FOOTER BAR (bottom, now horizontally centered) + LOGO (bottom-left)
   */
.footerbar {
  position: fixed; /* was position:absolute — anchored to the SECTION's box, which turned out not to have a truly fixed height in the actual renderer (its effective height quietly grows/shrinks with --title-push), so the footer drifted whenever title-push changed. position:fixed anchors to the true slide/viewport frame instead, same as the corner triangle below, which never had this problem. */
  left: 50%;
  bottom: var(--footer-line);
  margin: 0 !important; /* safeguard: can never inherit the title-push margin-top */
  transform: translateX(-50%);
  font-size: 0.4em;
  font-weight: 700;
  color: var(--dark2);
  text-align: center;
  z-index: 1;
  white-space: nowrap;
}
.footerbar .chev { color: var(--accent1); margin: 0 0.15em; }
.divider .footerbar, .cover .footerbar { color: #fff !important; }
.divider .footerbar .chev, .cover .footerbar .chev { color: #fff !important; }

/* Two footer-logo variants:
   - .footer-logo-dark  (image1.png) - dark mark, for slides with a
     light/white background (the regular content slides).
   - .footer-logo-light (image7.png) - white mark, for slides on a
     photo or dark background (cover, chapter dividers, the demo
     slide's grey half, the navy panel, the closing/questions slides).
   Adjust "height" below to resize either one. */
.footer-logo-dark, .footer-logo-light {
  position: fixed; /* see note on .footerbar above — same fix, same reason */
  left: 0.8em;
  bottom: var(--footer-line);
  margin: 0 !important;
  height: 1em;
  z-index: 1;
}

/*
   SLIDE NUMBER
   */
.reveal .slide-number { color: var(--dark2) !important; background: transparent !important; font-family: Arial, Helvetica, sans-serif !important; font-size: 0.4em !important; right: 2.4em !important; bottom: var(--footer-line) !important; }

/*
   BOTTOM-RIGHT CORNER TRIANGLE
   Rebuilt so its vertical edge sits flush with the slide's right border
   and it points left/west (rather than the old south-east-pointing
   corner-fold shape). Vertically nudged to line up with the slide
   number. Tweak "bottom" / the two 15px values / the 22px value to
   fine-tune size and vertical alignment.
   */
.reveal::after {
  content: "";
  position: fixed;
  right: 0;
  bottom: var(--footer-line);
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 15px 22px 15px 0;                                  /* top right bottom left */
  border-color: transparent var(--accent1) transparent transparent; /* only the right-hand "border" is filled -> flat edge on the right, point on the left */
  z-index: 30;
  pointer-events: none;
}

/*
   OBSIDIAN LOGO MARK / BACKGROUND WATERMARKS
   */
.obsmark { width: 2.2em; height: 2.2em; background: var(--obs); clip-path: polygon(50% 0%, 90% 25%, 100% 70%, 60% 100%, 20% 90%, 0% 45%); display: inline-block; vertical-align: middle; margin-right: 0.4em; }

.obs-bg {
  position: absolute !important;
  right: -1em !important;
  top: 50% !important;
  transform: translateY(-50%) !important;
  width: 8em !important;
  opacity: 0.8 !important;
  z-index: 0 !important;
  pointer-events: none !important;
}

/*
   BACKGROUND IMAGES FOR SLIDES (from 5b)
   */
.hex-bg {
  position: absolute !important;
  top: 50% !important;
  transform: translateY(-45%) !important;
  width: 22em !important;
  opacity: 1 !important;
  z-index: -1 !important;
  pointer-events: none !important;
}
.hex-bg-mask {
  position: absolute !important;
  right: -1em !important;
  top: 50% !important;
  transform: translateY(-45%) !important;
  width: 27em !important;   /* slightly wider than hex-bg's 22em */
  height: 24em !important;  /* square to cover vertical spread */
  background: #ffffff !important;
  opacity: .66 !important;
  z-index: 0 !important;
  pointer-events: none !important;
}

/* .img-bg - faint watermark image on the right edge.
   To make ONE slide's image bigger without creating a new class, add an
   inline style on that <img>, e.g. style="width:12em !important;" - an
   inline !important beats this class's !important (used on slides 8
   and 9 since v7.11). */
.img-bg
{
  position: absolute !important;
  right: -1em !important;
  top: 50% !important;
  transform: translateY(-50%) !important;
  width: 8em !important;
  opacity: 0.15 !important;
  z-index: -1 !important;
  pointer-events: none !important;
}

.img2-bg
{
  position: absolute !important;
  right: -1em !important;
  top: 50% !important;
  transform: translateY(-40%) !important;
  width: 10em !important;
  opacity: 0.45 !important;
  z-index: -1 !important;
  pointer-events: none !important;
}
/*
   DEMO SLIDE — recreated from scratch.
   Left half grey (same --dark2 grey used on the navy statement panel),
   right half white. Big orange chevron centered on the seam. "Demo"
   title left-aligned and vertically centered on the grey side; chevlist
   on the white side.
   */
.reveal .slides section.panel-demo { padding: 0 !important; } /* belt-and-braces: also remove the global slide padding, though the fixed-position fix below no longer depends on it */
.panel-demo { position: relative; width: 100%; height: 100%; }
/* NOTE: demo-left/demo-right/demo-chevron-big below use position:fixed,
   not position:absolute. They were previously position:absolute anchored
   to THIS section, but the section's own rendered height turned out not
   to be a reliable, truly-fixed 720px in the actual renderer (same
   underlying issue that made the footer drift with --title-push) — that
   is what left a gap at the bottom instead of the grey/white halves
   reaching full height. position:fixed anchors directly to the true
   slide/viewport frame instead, same fix as the footer, and sidesteps
   the section-height question entirely. */

.panel-demo .demo-left {
  position: fixed;
  top: 0; bottom: 0; left: 0;
  width: 50%;
  background: var(--dark2);
  display: flex;
  align-items: center;         /* vertical centering */
  justify-content: flex-start; /* left alignment */
  box-sizing: border-box;
  padding-left: 1.6em;
  z-index: 0; /* explicit, so footer/logo/chevron (z-index 1-2 below) are guaranteed to paint above it regardless of DOM order */
}
.panel-demo .demo-right {
  position: fixed;
  top: 0; bottom: 0; right: 0;
  width: 50%;
  background: #ffffff;
  display: flex;
  align-items: center;
  box-sizing: border-box;
  padding-left: 2.6em; /* v7.17: was 3.2em, moved the demo list further left. Still clears the big chevron, which overlaps ~2.2em into this half — increase if the chevron size below changes */
  z-index: 0;
}
.panel-demo .demo-label { font-size: 2.6em; font-weight: 800; letter-spacing: 0.02em; color: var(--accent1); margin: 0; }

/* Big orange chevron, centered on the seam between the two halves.
   Vertical centering uses top:0 + bottom:0 + margin:auto (rather than
   top:50%/translateY(-50%)) — immune to the same height quirk noted
   above. */
.panel-demo .demo-chevron-big {
  position: fixed;
  left: 50%;
  top: 0;
  bottom: 0;
  margin: auto 0;
  transform: translateX(-50%);
  width: 4.5em;
  height: 4.5em;
  color: var(--accent1);
  z-index: 2;
}
.panel-demo .demo-chevron-big svg { width: 100%; height: 100%; }

.panel-demo .demo-list { list-style: none; padding: 0; margin: 0; text-align: left; font-size: 0.85em; color: var(--dark2); } /* v7.17: was 1.1em - one size for all three demo slides */
.panel-demo .demo-list li { margin-bottom: 0.4em; }
.panel-demo .demo-list li::before { content: "›"; color: var(--accent1); font-weight: 700; margin-right: 0.5em; }

.panel-demo .footerbar, .panel-demo .footerbar .chev { color: var(--dark2) !important; }

/*
   CHAPTER RAIL (v7.8 → v7.11) — a plain progress line, no checkpoints.

   v7.17 changes (text + spacing - no slides added/removed, rail
   numbers unchanged): new --block-gap token (vertical spacing), demo
   lists unified (0.85em, further left), slide 10 callout removed and
   tags promoted, slide 15 rewritten as short lines, slide 16 callout,
   slide 17 last line grey, slide 25 reordered, slide 29 tags line,
   slide 31 "without worrying".

   v7.16 changes (text + layout - no slides added/removed, rail
   numbers unchanged): new .accent class (key word in orange) used on
   slides 9, 10, 11, 15, 17, 19; new .chapter-map layout for slide 5;
   slide 19 tool lines back to regular text; smaller demo lists on
   slides 20 and 27; slide 25 opens with "AI is not included by
   default"; slide 29 links line = several MOCs; slide 31 standard
   footer and text shifted left.

   v7.15 changes (text + sizing - no slides added/removed, rail
   numbers unchanged): new --body-size token (body text 0.8em), slide 5
   subtitles under each chapter in small grey, slide 9 simplified, slide
   15 "One note per subject" with "note" in accent colour, slide 17
   simplified to one emphasis style, slide 18 callout turned into a
   plain line, slide 22 footnote, slide 29 list and callout smaller, and
   every dash/hyphen removed from slide text, menu titles and speaker
   notes (except markdown syntax shown as code on slide 9).

   v7.14 changes (structure round - 3 slides added, rail renumbered):
   1) New slide 4 "Then I found a way out" (Intro).
   2) Chapter 4 renamed "Organisation" (divider, menu title, rail
      labels, map).
   3) AI chapter: the two content slides replaced by "Just ask, in plain
      words" (24→25) and "Better answers through the structure" (26).
   4) New Chapter 6 "Conclusion": divider (slide 28, reuses the cover
      photo image4.jpeg - swap if you have a dedicated one) and the
      synthesis slide "Several ways back to every note" (29); cons now
      come before the navy payoff (30, 31), then Questions (32).
   5) Slide 17 (Type) rewritten: Type = the WHAT, Templater = the HOW.
   --n went 29 → 32 and every --i was renumbered to its new position.

   v7.13 changes (text only - no slides added/removed, rail numbers
   unchanged): slide 7 rewritten ("Notes that stay yours"), slide 10
   YAML example, slide 13 closing fragment, slide 17 layout (one
   template per Type + callout), Chapter 2 and 5 subtitles (+ map),
   slide 28 plugin-security bullet.

   v7.12 changes (text only - no slides added/removed, rail numbers
   unchanged): comparisons with other note apps removed (slides + notes), slide 6
   bullets trimmed, slide 8 retitled + one body line, slide 9 callout
   reworded, slide 13 bullets removed, slide 14 MOC definition, slide 18
   split into one line per tool, Chapter 4 subtitle, slide 22 rewritten,
   personal-anecdote references removed from speaker notes.

   v7.11 changes (content round - rail logic untouched, only the numbers
   a new slide always requires):
   1) Inserted a third Demo slide ("Demo — Folders, daily note & AI") as
      slide 26, right after "Why it actually works". --n went from 28 to
      29, and --i was renumbered on the two rail slides after it (navy
      panel 26→27, cons 27→28). Also corrected the stale "30" in the
      earlier comments: the deck actually had 28 slides in v7.10.
   2) Text changes (no layout impact): cover title size and "I" typo,
      name/date block moved left, bigger watermark images on slides 8-9,
      backlinks introduced on slide 9, properties rewritten on slide 10,
      Chapter 3 re-framed as retrieval (divider subtitle + slide 13),
      Bases vs Dataview sentence on slide 18, typo fixes on slides 8/16.

   v7.10 changes (menu-title fixes + one new slide - no rail-logic
   changes beyond the numbers a new slide always requires):
   1) Added data-menu-title to the four chapter dividers ("Chapter 2:
      Foundation" etc., matching the chapter numbers already used in the
      speaker notes and the on-slide .sectionnum badge). The
      Questions? slide already has a real <h1> the menu picks up
      correctly, so it was left alone.
   2) Demo slides carry a data-menu-title too ("Demo — Foundation" /
      "Demo — Structure") - .panel-demo slides use a plain
      <div class="demo-label"> for their on-slide "Demo" text, not a
      heading, so the menu previously had nothing to read there either.
   3) Inserted the Structure Demo slide as slide 19, immediately before
      the Architecture divider.

   v7.9 changes (two small additions, no structural changes):
   1) The line is two-tone now - orange from the top down to the current
      slide, plain gray below it - so the rail reads as a filled
      progress bar rather than just a marker on a track. This piggybacks
      on the exact same --i/--n calc() already driving the marker's
      position (see below); --i moved from the marker up to the outer
      .chapter-rail div so both the line's gradient and the marker's
      "top" can read it (a custom property set inline is only visible to
      the element it's set on and that element's descendants - the line
      is a sibling of the old marker-only placement, so it could not
      have seen it there).
   2) The plugin's own built-in slide-menu button (bottom-left by
      default) was overlapping the itecor logo down there, so it's
      pinned to the top-left instead - see ".slide-menu-button" at the
      bottom of this block. That button belongs to the menu plugin
      itself, not to this file's own markup, so it's targeted purely by
      the class name the plugin renders it with.

   v7.1 shipped this as a JS-built rail: a <script> block that scanned the
   deck for .divider slides with a .sectiontitle, built the dots, and kept
   them in sync on 'slidechanged'. That script never ran in practice.
   Checked against this plugin's actual documented options: it strips
   inline <script> tags from slide content, and — contrary to what v7.1
   assumed — there's no "scripts:" frontmatter property here either (only
   "css:" for extra stylesheets); that property belongs to a different,
   similarly-named fork. So there's no supported way to run custom JS in
   a slide deck on this plugin.

   v7.8 is a full rebuild, dropping the dots/chapters-as-checkpoints
   design entirely after several rounds of chasing chevron/dot alignment
   bugs that kept recurring: the underlying problem was that dots and
   chevron were two independent position systems (chapter-based spacing
   for dots, slide-index-based math for the chevron) that had to be kept
   in sync by hand, and every deck change - or even just an uneven
   chapter length - knocked them back out of alignment.
   v7.8 removes that coupling instead of re-fixing it again: there is
   now exactly ONE position, computed ONE way. The rail is just a
   vertical line; a single marker (the orange chevron, with the current
   chapter's name as a vertical label attached to it) travels down it.
   No dots, no per-chapter interpolation, no click-to-jump links (that
   was only ever wired to the dots, which are gone) - and so also no
   more need for "hash: true" in the frontmatter either.
   THE ONLY TWO NUMBERS involved:
     --n   : total slide count in the whole deck (32, as of v7.14) - set
             ONCE, on :root, above. Change it there if slides are
             added/removed.
     --i   : this slide's own 1-indexed position in the deck (matches
             the number Reveal's own slideNumber counter would show) -
             set per-slide, inline, on the outer .chapter-rail div
             below (moved there in v7.9 so the line's gradient and the
             marker's position can both read it).
   The marker's vertical position is plain CSS: calc(var(--i) / var(--n)
   * 100%) - the browser computes it, nothing is pre-computed by hand or
   baked in as a percentage. This is deliberately the SAME arithmetic a
   live "current slide / total slides" progress bar would use - it's
   just fed by two static numbers instead of Reveal's live state, since
   (as established back in v7.2) there's no supported way to run custom
   JS in a slide deck on this plugin.
   WHAT THIS MEANS FOR MAINTENANCE:
   - Reordering slides without changing the total: --n is unchanged;
     renumber each moved slide's --i to match its new position - that's
     a plain sequential renumbering, not a recomputed percentage.
   - Adding or removing slides: update --n once on :root, and renumber
     --i sequentially (1, 2, 3, ...) on every slide from the change point
     onward. Still manual, still no live recalculation - but it's
     literally counting, and it's the only thing left to touch.
   - Changing which chapter a slide belongs to, or adding a new chapter:
     just the label text in that slide's <span class="chapter-rail-label">
     - nothing positional depends on chapter boundaries anymore.
   The rail does NOT appear on: the cover slide, the .divider-class
   slides (five chapter openers plus the Questions slide - full-bleed
   photo backgrounds), or the three .panel-demo slides (custom
   full-bleed layout, no room reserved for a left rail at all).
   */
.chapter-rail {
  position: fixed;
  left: 1.2em;
  top: 16%;
  bottom: 22%; /* stays clear of the footer/page-number zone */
  width: 1.1em;
  z-index: 40; /* above footer/logo/chevron; wins over ".cover > *, .divider > *" (position:relative reset above) since it's a later, equally-specific class rule - same reasoning that already lets .chevron-badge stay position:fixed on those slides */
}
.chapter-rail::before {
  /* the whole progress line - full height, no gaps for dots to leave.
     Two-tone (v7.9): orange above the current position, gray below it -
     a hard cutoff at the same calc(var(--i)/var(--n)*100%) the marker
     itself sits at, so the two are always exactly in sync (same
     expression, same source values - there's nothing here to fall out
     of alignment the way the old dots could). */
  content: "";
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(
    to bottom,
    var(--accent1) 0%,
    var(--accent1) calc(var(--i) / var(--n) * 100%),
    #dcdcdc calc(var(--i) / var(--n) * 100%),
    #dcdcdc 100%
  );
  transform: translateX(-50%);
  z-index: 0;
}
.chapter-rail-marker {
  /* the one moving unit: chevron + its label. Sized to match the
     chevron exactly (see width/height below) so centering THIS box on
     the line via left:50%/translateX(-50%) puts the chevron itself
     exactly on the line - the label is pulled out of this box's own
     layout via position:absolute below, so it never affects that
     centering math or gets centered along with the chevron. --i and --n
     are read from .chapter-rail (its ancestor) via normal CSS custom
     property inheritance - nothing set directly on this element. */
  position: absolute;
  left: 50%;
  top: calc(var(--i) / var(--n) * 100%);
  transform: translate(-50%, -50%);
  width: 0.7em;
  height: 0.7em;
  z-index: 2;
  pointer-events: none;
}
.chapter-rail-chevron {
  display: block;
  width: 100%;
  height: 100%;
  color: var(--accent1);
}
.chapter-rail-label {
  /* Vertical (rotated) text, to the LEFT of the chevron - toward the
     true screen edge, away from both the line and body content. Its
     footprint is about one line-height wide regardless of the chapter
     name's length (length becomes vertical extent instead). */
  position: absolute;
  right: 100%;
  top: 50%;
  margin-right: 0.3em;
  writing-mode: vertical-rl;
  transform: translateY(-50%) rotate(180deg); /* reads bottom-to-top */
  white-space: nowrap;
  max-height: 6em;      /* defensive cap - a much longer chapter name would get clipped; widen this or shrink font-size if that happens */
  overflow: hidden;
  font-size: 0.42em;
  font-weight: 700;
  letter-spacing: 0.03em;
  color: var(--dark2);
  background: rgba(255, 255, 255, 0.85);
  padding: 0.3em 0.18em;
  border-radius: 4px;
}

@media print {
  .chapter-rail { display: none !important; } /* position:fixed elements are unreliable in PDF export - hide it there */
}

/* MENU BUTTON REPOSITION (v7.9) - the menu plugin's own built-in
   slide-out-menu button renders bottom-left by default, which sits
   right on top of the itecor logo/footer down there. Moved to top-left
   instead, which is clear on every slide type. This is the plugin's own
   injected element (class name per its own CSS, not ours), so
   !important guards against its stylesheet loading after this one. */
.slide-menu-button {
  bottom: auto !important;
  top: 8px !important;
  left: 8px !important;
}

</style>

<!-- .slide: data-background-image="image4.jpeg" data-background-size="cover" class="cover" -->

<!-- SIC Added a Div around to resize and center the Itecor logo-->
<div style="position:absolute; bottom:515px; left:500px; max-width:26%;">
<img src="image7.png">
</div>


<!-- v7.11: main title 100px → 88px ("slightly smaller"); subtitle unchanged at 32px -->
<div style="position:absolute; bottom:1.6em; left:1em; max-width:75%;">
<h1 class="cover-title" style="font-weight:700; font-size:88px; text-align:left; margin-bottom:0.15em;">Finding what I wrote, when I need it</h1> 
<p class="subtitle2" style="color:#f0f0f0; text-align:left; font-size:32px;">How I built my notes to be found, powered by Obsidian</p>
</div>
<div class="title-meta">Simone Coppo<br>02.10.2026</div>


note: Goal: set the frame: this is a personal workflow talk, not a generic "note taking apps" overview. Welcome the room, one line on why you switched. 30 minute core = Chapters 1, 2, 3, 5, 6, skip Chapter 4 entirely by pressing → once on its divider. Full hour = all six, slower demo pacing.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 2;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Intro</span>
</div>
</div>


<h3 class="content-title no-push">The thesis</h3>


<p style="font-size:1.5em; font-weight:700; max-width:900px;">A note taking app is only as good as <span style="color:var(--accent1);">getting information back out.</span></p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: plant the one sentence the entire talk answers, so everything after this has a clear "why." Say it slowly, let it sit for a second before moving on. Optionally add: "not how it looks, not how fast you write, how fast you retrieve."

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 3;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Intro</span>
</div>
</div>


<h3 class="content-title no-push">The familiar pain</h3>


<div class="calloutbox">
<p style="margin:0;">The app makes <i>you</i> adapt to its structure, not the other way around.</p>
</div>
<p class="fragment fade-up" style="margin-top:0.6em;">So if you don't already remember <i>where</i> you filed it, you will never find it again.</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: make the problem feel familiar and personal before offering any solution. Tell your own story here in one or two sentences: you know you wrote something down, but unless you remember the exact page/section, it's gone. Keep it short, don't dwell.
• You need to adjust your way of thinking to the note app structure and not the opposite.
• So it started my quest to find a note app that whould actually allow me to find my notes.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 4;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Intro</span>
</div>
</div>


<h3 class="content-title no-push">Then I found a way out</h3>

<p><span class="accent">OBSIDIAN</span></p>
<p>A tool where I build the structure myself, around how I look for things, <br> not where I filed them.</p>
<div class="calloutbox fragment fade-up">
<p style="margin:0; font-weight:700;">More than one way back to every piece of information.</p>
</div>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: turn the pain into a promise, without explaining anything yet. One sentence of relief: I found a way out. The callout is the intention of the whole system; it gets paid off in the Conclusion chapter ("Several ways back to every note"). Don't name the paths here.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 5;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Intro</span>
</div>
</div>


<h3 class="content-title no-push">Where we're headed</h3>

<ul class="chapter-map">
<li class="fragment fade-up"><span class="cm-num">2</span><span class="cm-name">Foundation</span><span class="cm-sub">preparing information to be found</span></li>
<li class="fragment fade-up"><span class="cm-num">3</span><span class="cm-name">Structure</span><span class="cm-sub">how I get it back out</span></li>
<li class="fragment fade-up"><span class="cm-num">4</span><span class="cm-name">Organisation</span><span class="cm-sub">folders &amp; daily rhythm</span></li>
<li class="fragment fade-up"><span class="cm-num">5</span><span class="cm-name">AI</span><span class="cm-sub">asking your notes directly</span></li>
<li class="fragment fade-up"><span class="cm-num">6</span><span class="cm-name">Conclusion</span><span class="cm-sub">how it all fits, and its limits</span></li>
</ul>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: give the room a map so the build makes sense as it happens, not just in hindsight. Point at the list, don't read it verbatim.

Chapter cheat sheet, for your own structuring:
Ch.2 Foundation: what Obsidian even is, then the bedrock ideas, plain text/markdown, links + backlinks, properties.
Ch.3 Structure: the retrieval tools, MOCs + backlinks, the Type property, Templater/QuickAdd to keep notes consistent, and Bases/Dataview to query at scale.
Ch.4 Organisation (optional): how the vault stays organized across clients (folders) and alive day to day (daily/GTD rhythm).
Ch.5 AI: how you connected an AI to the vault (MCP + OpenCode), why that combination actually works, and a live question to the vault.
Ch.6 Conclusion: how all the ways back fit together, the honest tradeoffs, then the payoff line.

---

<!-- .slide: data-background-image="image16.jpg" data-background-size="cover" class="divider" data-menu-title="Chapter 2: Foundation" -->

<div class="divider-wrap no-push">
<div class="divider-left">
<h2 class="sectiontitle" style="font-weight:700; font-size:90px;">Foundation</h2>
<p class="sectionsub">preparing information to be found</p>
</div>
<div class="sectionnum">2</div>
</div>
<img src="image7.png" class="footer-logo-light no-push">

<div class="chevron-badge no-push">
<svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

note: Goal: mark the tone shift into "building the system" and set up that the audience may not know the tool yet. Say explicitly: "I'll introduce the tool itself first, then build the system layer by layer."

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 7;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Foundation</span>
</div>
</div>


<h3 class="content-title no-push">What is Obsidian?</h3>

<!-- Obsidian logo-->
<!-- <p><span class="obsmark"></span><b>Obsidian</b> — a free, local-first note-taking app.</p>-->

<!-- Background Logo --> 
<img src="Obsidian_Logo.jpg" class="img-bg">

<p><b>Obsidian</b>: <br> a free note taking app that keeps everything on your own machine.</p>

<ul class="chevlist">
<li class="fragment fade-up">Notes link to each other, like web pages</li>
<li class="fragment fade-up">Extensible through community plugins</li>
<li class="fragment fade-up">Even this presentation is built in it</li>
</ul>


<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: give the audience the bare minimum context before anything else makes sense: what the tool is, in three sentences. Don't assume anyone in the room has heard of it. The "even this deck" line is a nice concrete proof point, pause on it if it lands.
• Demo the basic view of Obsidian.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 8;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Foundation</span>
</div>
</div>


<h3 class="content-title no-push">Notes that stay yours</h3>

<p>Every note is a markdown file on your own disk.</p>

<ul class="chevlist">
<li class="fragment fade-up"><b>Always accessible</b>: plain files, no app or account needed to open them</li>
<li class="fragment fade-up"><b>Durable</b>: readable in 20 years, by anything</li>
<li class="fragment fade-up"><b>Private</b>: on your machine, not in someone else's cloud</li>
</ul>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: establish plain text as the foundation everything else depends on. No proprietary format, no cloud dependency, if Obsidian disappeared tomorrow, your notes are still just files you can open in anything. This is what makes every later layer trustworthy long term.
You can arrange them as you want. But filesystem structure is not your main organisation asset. Is just one of them.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 9;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Foundation</span>
</div>
</div>


<h3 class="content-title no-push">Structure while you type</h3>

<!-- SIC added Background Logo - v7.11: enlarged 8em → 12em via inline style (tweak the number to resize) --> 
<img src="MarkdownNote_image.png" class="img-bg" style="width:12em !important;">


<p><span class="accent">Markdown</span> is just text with light formatting marks.</p>
<p class="fragment fade-up"><code># Heading</code> &nbsp; <code>**bold**</code> &nbsp; <code>- list item</code> <br><code>- &#91; &#93; checkbox</code> <code> &gt; &#91;!callouts&#93; </code> </p>
<p class="fragment fade-up">Headings, lists and checkboxes structure the information inside the note itself.</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: explain markdown concretely, since it's been implied but never actually shown until now. Point at the three examples on screen, say each one out loud with what it renders as. This is the syntax layer underneath everything else in the talk.
• Headings helps structure your information easily; taks helps you 
• you can quickyl dump information and is already structured.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 10;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Foundation</span>
</div>
</div>


<h3 class="content-title no-push">Connect ideas as you write</h3>

<!-- SIC added Background Logo - v7.11: enlarged 8em → 12em via inline style (tweak the number to resize) --> 
<img src="LinkNote_image.png" class="img-bg" style="width:12em !important;">


<p>Type <code>&#91;&#91;note name&#93;&#93;</code> and two notes are <span class="accent">linked</span>.</p>
<p class="fragment fade-up">Obsidian adds the way back automatically: every note shows its <b>backlinks</b>, all the notes that point to it.</p>
<p class="fragment fade-up">Add a <code>#tag</code> for a topic that cuts across subjects: <code>#automation</code>, <code>#performance</code>. One search lists every note on that topic, in every project.</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: introduce the link AND its automatic backlink as the first retrieval path. Writing a link is the only action; the backlink is free. This is what sets Obsidian apart, and it's what will make MOCs (Chapter 3) usable without any upkeep. Tags are a third, looser path: a topic label that cuts across projects and MOCs; one tag search gathers them all. Show a tag search in the demo.
• This is the second most powerfull tool provided by Obsidian: connecting ideas beyond their file placement
• Bases and Dataview (Chapter 3) query even further, but natively, the backlink is the first step.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 11;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Foundation</span>
</div>
</div>


<h3 class="content-title no-push">Classify every note</h3>

<p>Every note can carry <span class="accent">properties</span>: simple key : value pairs at the top of the file (YAML frontmatter).</p>
<p class="fragment fade-up"><code>type: meeting</code> &nbsp; <code>participants: &#91;&#91;Anna&#93;&#93;, &#91;&#91;Marc&#93;&#93;</code> &nbsp; <code>project: &#91;&#91;Website&#93;&#93;</code></p>
<div class="calloutbox fragment fade-up">
<p style="margin:0; font-weight:700;">Find a note by <i>what it is</i>, not by where you saved it.</p>
</div>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>


note: Goal: explain what properties are with a real example, and why they matter for retrieval: they describe WHAT a note is (a meeting, on which project, when), so you can find it without remembering where it lives. Read the example aloud: "this note is a meeting, with Anna and Marc, about this project", none of that is something the file system could know. Point out that participants are links, so each person's note lists, through its backlinks, every meeting they attended. The actual querying (Bases, Dataview) comes in Chapter 3; just promise it here.
• After folder structure, and linking, this is the third powerfull tool provided by obsidian to classify and find notes.

---

<!-- .slide: class="panel-demo" data-menu-title="Demo: Foundation" -->

<div class="demo-left">
  <div class="demo-label">Demo</div>
</div>
<div class="demo-right">
  <ul class="demo-list">
    <li>Markdown</li>
    <li>Links, backlinks and tags</li>
    <li>Properties</li>
  </ul>
</div>

<div class="demo-chevron-big">
  <svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

<img src="image7.png" class="footer-logo-light no-push">


note: Goal: pause here and actually screen share Obsidian. Live demo whatever this chapter just covered before moving on. Show the backlinks panel on a note that others link to. This slide is your placeholder to come back to if you get pulled off track mid demo.

---

<!-- .slide: data-background-image="image11.jpeg" data-background-size="cover" class="divider" data-menu-title="Chapter 3: Structure" -->

<div class="divider-wrap no-push">
<div class="divider-left">
<h2 class="sectiontitle" style="font-weight:700; font-size:90px;">Structure</h2>
<p class="sectionsub">how I get it back out</p>
</div>
<div class="sectionnum">3</div>
</div>
<img src="image7.png" class="footer-logo-light no-push">
<!-- <img src="image7.png" class="chapter-logo no-push"> -->
<div class="chevron-badge no-push">
<svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

note: Goal: signal the shift from preparing information (Chapter 2: links, backlinks, properties) to getting it back out. Chapter 2 was the raw materials; this chapter is the retrieval tools I built on top of them.



---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 14;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Structure</span>
</div>
</div>

<h3 class="content-title no-push">The way back is yours to build</h3>

<p>Links, tags, properties: Obsidian imposes no structure on them.</p>
<div class="calloutbox fragment fade-up">
<p style="margin:0; font-weight:700;">You choose how you'll get information back.</p>
</div>

<p class="fragment fade-up">Here's the way back I built.</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: frame the whole chapter: these are the retrieval tools I use, each one built on a raw material from Chapter 2. Contrast with the pain slide: here the app adapts to me, not the other way around. Name the tools out loud as a preview if you like (MOCs + backlinks, Bases, Dataview), each gets its own slide. Templater also appears in this chapter: it's what keeps properties consistent so these tools never miss a note.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 15;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Structure</span>
</div>
</div>


<h3 class="content-title no-push">One note per subject</h3>


<!-- SIC To Do - make this logo gigger anw less transparent without creating a new class --> 
<!-- SIC added Background Logo --> 
<img src="MOC.png" class="img2-bg">

<p>A <b>MOC</b> (Map of Content) is just a <span class="accent">note</span>, one per subject.</p>
<p class="fragment fade-up">One for each project, each person, each release.</p>
<p class="fragment fade-up">Every note about that subject links to it.</p>

<div class="calloutbox fragment fade-up">
<p style="margin:0; font-weight:700;">Follow relationships, not folder paths.</p>
</div>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: show what links become at scale: a navigable structure, not just isolated connections. Explain your own recall habit, when someone asks about a person or project, you think "who / what" first, then open that MOC. Bridge into the live demo next.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 16;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Structure</span>
</div>
</div>


<h3 class="content-title no-push">Every mention finds its way back</h3>

<!-- SIC To Do - make this logo gigger anw less transparent without creating a new class --> 
<!-- SIC added Background Logo --> 
<img src="MOC.png" class="img2-bg" style="opacity: 0.15 !important;">


<p>Link any note to a MOC and it appears in the MOC's backlinks, with no manual upkeep.</p>
<p class="fragment fade-up">Open the MOC → every meeting, note, mention that ever pointed to it.</p>
<div class="calloutbox fragment fade-up">
<p style="margin:0; font-weight:700;">Every MOC I create is one more way back to my information.</p>
</div>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: cash in the backlink from Chapter 2: a MOC is where backlinks pay off, because every note about that subject links to it. You don't maintain the hub by hand. And one note can link to several MOCs (its project, its people, its product), so every MOC you create adds another way back. This is the first proof point of the whole talk, switch to Obsidian and demo a real MOC live, click through to a linked meeting note, then back. Don't rush.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 17;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Structure</span>
</div>
</div>


<h3 class="content-title no-push">One property to rule them all</h3>

<!-- Background Logo --> 
<img src="Ring.jpg" class="img-bg">

<p>Every note gets a <span class="accent">Type</span>:<br> meeting, person, release, project, action, wiki, test plan.</p>
<p class="fragment fade-up">Choosing a Type forces you to classify every note you write.</p>
<p class="fragment fade-up">The Type decides which other properties the note needs: a meeting gets participants, a release gets a version.</p>
<p class="fragment fade-up note-gray">Well organised, well filled properties make your notes easier to find afterwards.</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: show the specific, highest leverage property in your system. Type is the WHAT: it forces a classification, and the classification decides which other properties a note carries, a cleaner, more ordered vault. The next slide (Templater) is the HOW. Show the meeting note schema live if you can: attendants (linked to person MOCs), object, Release/Project/Product links, date, tags. Point out that these properties link straight back into the MOCs, the two layers reinforce each other, that's the key insight here.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 18;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Structure</span>
</div>
</div>


<h3 class="content-title no-push">Every note starts prebuilt</h3>

<!-- SIC added Background Logo --> 
<img src="Templater image.png" class="img2-bg">


<p>Build one template per Type. <b>Templater</b> fills it in, every time.</p>

<ul class="chevlist">
<li class="fragment fade-up">Already filled in</li>
<li class="fragment fade-up">Right structure</li>
<li class="fragment fade-up">Right folder</li>
<li class="fragment fade-up">At your fingertip</li>
</ul>

<p class="fragment fade-up">Same properties every time, so no note slips through a query.</p>

<p class="fragment fade-up note-gray">Templater and <b>QuickAdd</b> are free community plugins; one shortcut triggers it all.</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: make clear Templater is the actual engine (automated, structured note creation) and QuickAdd is a minor convenience on top, not the point itself. Demo the shortcut live if you can, press it, a fully formed note appears. Make the point explicit: without this, filling in a rich property schema every time would be a chore you'd eventually stop doing. This is what makes Chapter 3 sustainable day to day.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 19;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Structure</span>
</div>
</div>


<h3 class="content-title no-push">Search across the whole vault</h3>

<p>Turn your notes into tables you can sort and filter.</p>
<p class="fragment fade-up"><span class="accent">Bases</span>: a native tool to filter by properties, point and click.</p>
<p class="fragment fade-up"><span class="accent">Dataview</span> is a query language that can use anything: properties, links, tags, file details.</p>
<div class="calloutbox fragment fade-up">
<p style="margin:0; font-weight:700;">Query the whole vault at once.</p>
</div>

<p class="fragment fade-up note-gray">Your vault becomes a real note database</p>
<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: name and briefly define these two tools before showing the payoff. The one line difference: Bases only reads properties but needs no code; Dataview is a query language that can combine properties, links, tags and file info, more power, more to learn. Show your dashboard new tab view, prepared Base views per note type (meetings, projects, releases, people). This is retrieval path #3: ask a question across everything at once, instead of navigating one link at a time.

---

<!-- .slide: class="panel-demo" data-menu-title="Demo: Structure" -->

<div class="demo-left">
  <div class="demo-label">Demo</div>
</div>
<div class="demo-right">
  <ul class="demo-list">
    <li>MOC and Type</li>
    <li>Templater</li>
    <li>Bases and Dataview Queries</li>
  </ul>
</div>

<div class="demo-chevron-big">
  <svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

<img src="image7.png" class="footer-logo-light no-push">


note: Goal: pause here and actually screen share Obsidian. Live demo whatever this chapter just covered before moving on. This slide is your placeholder to come back to if you get pulled off track mid demo.

---

<!-- .slide: data-background-image="image10.jpeg" data-background-size="cover" class="divider" data-menu-title="Chapter 4: Organisation" -->

<div class="divider-wrap no-push">
<div class="divider-left">
<h2 class="sectiontitle" style="font-weight:700; font-size:80px;">Organisation</h2>
<p class="sectionsub">folders &amp; daily rhythm</p>
</div>
<div class="sectionnum">4</div>
</div>
<img src="image7.png" class="footer-logo-light no-push">
<!-- <img src="image7.png" class="chapter-logo no-push"> -->
<div class="chevron-badge no-push">
<svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

note: Goal: flag this chapter as skippable so you can make a live time check decision here. OPTIONAL CHAPTER for the 30 minute cut, press → once to skip straight to Chapter 5 (AI) if you're short on time.


---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 22;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Organisation</span>
</div>
</div>


<h3 class="content-title no-push">Hexagonal Architecture</h3>

<!--
<div class="bighex">
<svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg"><polygon points="25,5 75,5 100,50 75,95 25,95 0,50" fill="currentColor"/></svg>
</div>
-->

<img src="HexagonalArchi_v4_color_w.png" class="hex-bg">
<div class="hex-bg-mask fragment fade-up" ></div>


<ul class="chevlist">
<li class="fragment fade-up">Business specific: projects, products, test plans</li>
<li class="fragment fade-up">Business independent: daily notes, mail, people, tools</li>
<li class="fragment fade-up">Change clients → only one folder moves</li>
</ul>

<p class="fragment fade-up note-gray">People, tools and daily notes keep all their links when the client changes.</p>

<!-- SIC To Do : add aopacity layer to have the entire chevlist behind disappear behing the image-->

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: explain the problem this solves: at scale, hundreds of structured notes need a boundary or a client change becomes a mess. Hexagonal inspired split. Compress to one sentence if you're tight on time.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 23;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Organisation</span>
</div>
</div>


<h3 class="content-title no-push">Capture now, link later</h3>

<p>The daily note is my dumping ground: <br>every meeting and task starts there.</p>
<p class="fragment fade-up">I add the links and tags and move notes to the right folder later on,<br> so they can be found.</p>
<p class="fragment fade-up note-gray">Rhythm borrowed from GTD (Getting Things Done).</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>


<img src="GTD.png" class="img2-bg">


note: Goal: show the temporal counterpart to the previous slide's spatial structure: capture fast in the daily note, then the daily and weekly reviews add links, tags and folder moves so everything stays findable. Keep this brief, it's the least essential slide in the deck.

---

<!-- .slide: data-background-image="image15.jpeg" data-background-size="cover" class="divider" data-menu-title="Chapter 5: AI" -->

<div class="divider-wrap no-push">
<div class="divider-left">
<h2 class="sectiontitle" style="font-weight:700; font-size:110px;">AI</h2>
<p class="sectionsub">asking your notes directly</p>
</div>
<div class="sectionnum">5</div>
</div>
<img src="image7.png" class="footer-logo-light no-push">
<!-- <img src="image7.png" class="chapter-logo no-push"> -->
<div class="chevron-badge no-push">
<svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

note: Goal: big beat: change your pace and tone here. Frame the AI as a separate, extra way to ask your notes: it works on plain text alone, and gets better with the structure built so far.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 25;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">AI</span>
</div>
</div>


<h3 class="content-title no-push">Just ask, in plain words</h3>

<p>AI is not included by default, but you <b>can</b> connect it to your own local LLM.</p>
<p class="fragment fade-up">It works because every note is a plain markdown file, which any AI tool reads well.</p>
<p class="fragment fade-up" style="font-weight:700;">Because the model is local, my notes never leave my machine.</p>
<p class="fragment fade-up note-gray">Ask a question → the AI reads your notes → answers with sources.</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: first make clear that Obsidian has no AI built in; it's something you choose to connect, here to a local LLM. Then show the AI as an independent, extra way back: even with no structure at all, a local model can read plain markdown notes and answer in plain words. Stress LOCAL: nothing leaves the machine, consistent with Chapter 2's "notes that stay yours".

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 26;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">AI</span>
</div>
</div>


<h3 class="content-title no-push">Better answers through the structure</h3>

<p>An Obsidian plugin exposes the vault through an <span class="accent">MCP</span>;<br> <b>OpenCode</b> connects to it.</p>
<div class="calloutbox fragment fade-up">
<p style="margin:0; font-weight:700;">Now the AI also uses links, tags and properties: it follows the structure, not just the text.</p>
</div>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

<img src="MCP.png" class="img-bg">

note: Goal: explain the extra layer: MCP (Model Context Protocol) lets the AI use Obsidian's own features, follow links and backlinks, filter on properties, read tags, so answers get more precise and efficient. The AI works without it; it works better with the structure built in Chapters 2 and 3.

---

<!-- .slide: class="panel-demo" data-menu-title="Demo: Folders, daily note & AI" -->

<!-- v7.11: new final Demo slide (slide 26). Same layout as the two
     earlier Demo slides; no chapter rail on demo slides. -->

<div class="demo-left">
  <div class="demo-label">Demo</div>
</div>
<div class="demo-right">
  <ul class="demo-list">
    <li>Hexagonal folder structure</li>
    <li>A daily note with GTD</li>
    <li>AI connected to the vault</li>
  </ul>
</div>

<div class="demo-chevron-big">
  <svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

<img src="image7.png" class="footer-logo-light no-push">


note: Goal: last live stop, before the close. Show the folder tree (business specific vs business independent), open today's daily note to show the GTD rhythm, then ask the AI a real question live and let it answer with sources. If you skipped Chapter 4 for the 30 minute cut, skip the first two items and go straight to the AI.

---

<!-- .slide: data-background-image="image4.jpeg" data-background-size="cover" class="divider" data-menu-title="Chapter 6: Conclusion" -->

<!-- v7.14: new Chapter 6 divider. Background reuses the cover photo (image4.jpeg) as a bookend - swap for a dedicated image if you have one. -->

<div class="divider-wrap no-push">
<div class="divider-left">
<h2 class="sectiontitle" style="font-weight:700; font-size:90px;">Conclusion</h2>
<p class="sectionsub">how it all fits, and its limits</p>
</div>
<div class="sectionnum">6</div>
</div>
<img src="image7.png" class="footer-logo-light no-push">

<div class="chevron-badge no-push">
<svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

note: Goal: mark the close as its own chapter: first how everything fits together to find information, then the honest limits, then the payoff line.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 29;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Conclusion</span>
</div>
</div>


<h3 class="content-title no-push">Several ways back</h3>

<ul class="chevlist" style="font-size:0.7em;">
<li class="fragment fade-up"><b>Links</b> → several MOCs &amp; backlinks:  <i> <br>reach one note from its project, its people or its product</i></li>
<li class="fragment fade-up"><b>Properties</b> → Bases &amp; Dataview: <i>what kind of note is it?</i></li>
<li class="fragment fade-up"><b>Tags</b> → search &amp; Dataview: <i>every note on #automation, across all projects</i></li>
</ul>

<div class="calloutbox fragment fade-up" style="font-size:0.65em; padding:0.5em 1em;">
<p style="margin:0; font-weight:700;">If one path doesn't find it, another one will.</p>
</div>

<p class="fragment fade-up note-gray">And the AI can walk all of them at once.</p>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: pay off the promise from slide 4 ("more than one way back"). Each line ties one Chapter 2 raw material to its Chapter 3 retrieval tool, phrased as the question you'd ask. This is the answer to the title question: I find it because I never depend on a single path. The AI line is a one sentence nod, not a new topic.

---
<div class="chapter-rail no-push" aria-hidden="true" style="--i: 30;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Conclusion</span>
</div>
</div>


<h3 class="content-title no-push">Honestly: the cons</h3>

<ul class="chevlist">
<li class="fragment fade-up">Needs admin rights to install</li>
<li class="fragment fade-up">Real learning curve to set up</li>
<li class="fragment fade-up">Total freedom = easy to get lost</li>
<li class="fragment fade-up">No native Outlook calendar sync</li>
<li class="fragment fade-up">Community plugins have full access: install only the ones you trust</li>
</ul>

<img src="image1.png" class="footer-logo-dark no-push">
<div class="footerbar no-push">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: build credibility by being honest about tradeoffs before the close, rather than ending on an unqualified sales pitch. Mention briefly that the learning curve investment paid off fast for you specifically.


---

<!-- .slide: class="panel-navy" -->

<div class="chapter-rail no-push" aria-hidden="true" style="--i: 31;">
<div class="chapter-rail-marker">
<svg class="chapter-rail-chevron" viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
<span class="chapter-rail-label">Conclusion</span>
</div>
</div>


<div class="bigchevron">
<svg viewBox="0 0 340.16 340.16" xmlns="http://www.w3.org/2000/svg"><path d="M105.8 338.06 61.38 286.75 168.23 169.47 61.38 52.19 105.8 1.53 284.37 169.47Z" fill="currentColor"/></svg>
</div>

<p style="font-size:1.6em; font-weight:700; max-width:700px; margin-left:1.5em; margin-right:auto; text-align:left;">I write more, faster and without worrying. Because I know I'll find it again.</p>

<img src="image7.png" class="footer-logo-light no-push">
<div class="footerbar no-push" style="color:#fff;">itecor Geneva <span class="chev">›</span> Finding what I wrote, when I need it <span class="chev">›</span> 02.10.2026 </div>

note: Goal: deliver the emotional core of the whole talk, as its own beat, not folded into the previous slide. Don't rush past it, this is the actual payoff, more than any single feature: knowing retrieval works means you capture information freely instead of curating it in the moment.

---

<!-- .slide: data-background-image="image17.jpg" data-background-size="cover" class="divider" -->

<img src="image7.png" class="footer-logo-light no-push">

<img src="image21.png" style="position:absolute; top:36%; left:50%; transform:translate(-50%,-50%); width:130px; z-index:1;">
<h1 style="position:absolute; bottom:1.8em; left:1em; color:#fff; font-weight:400; z-index:1;">Questions?</h1>

note: Goal: open discussion with momentum instead of an awkward silence. 30 minutes left on the clock (or however much time discussion allows), use them. Have two or three follow up demo ideas ready in case the room is quiet at first (e.g. show a property filtered Base, or ask the AI another live question).
