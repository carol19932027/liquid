---
name: LiquiKit site
description: Documentation and marketing site for liquid-glass React components, on a black canvas.
colors:
  canvas: "#000000"
  ink: "#ffffff"
  ink-muted: "rgba(255, 255, 255, 0.7)"
  ink-quiet: "rgba(255, 255, 255, 0.6)"
  hairline: "rgba(255, 255, 255, 0.08)"
  surface-whisper: "rgba(255, 255, 255, 0.07)"
  accent-neon: "#2160ff"
  accent-neon-hot: "#a8ccff"
  accent-neon-deep: "#03103f"
  glass-accent: "#7774ff"
  glass-pane-tint-dark: "#0b1540"
  danger: "#ff6369"
typography:
  hero:
    fontFamily: "Geist Variable, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif"
    fontSize: "clamp(34px, min(8.4svh, 7.4vw), 96px)"
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: "-0.035em"
  page-title:
    fontFamily: "Geist Variable, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif"
    fontSize: "40px"
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: "-0.03em"
  section-title:
    fontSize: "24px"
    fontWeight: 600
    letterSpacing: "-0.02em"
  subsection-title:
    fontSize: "18px"
    fontWeight: 600
    letterSpacing: "-0.01em"
  lead:
    fontSize: "17px"
    lineHeight: 1.6
  body:
    fontSize: "15.5px"
    lineHeight: 1.75
  nav:
    fontSize: "14px"
    lineHeight: 1.4
  label:
    fontSize: "12.5px"
    fontWeight: 500
  mono:
    fontFamily: "Geist Mono Variable, ui-monospace, SF Mono, Menlo, monospace"
rounded:
  nav-item: "9px"
  note: "14px"
  pane: "28px"
  hero-pane: "30px"
  dialog: "36px"
  pill: "999px"
spacing:
  xs: "8px"
  sm: "12px"
  md: "16px"
  lg: "24px"
  xl: "32px"
  section: "56px"
components:
  nav-link:
    textColor: "{colors.ink-quiet}"
    typography: "{typography.nav}"
  nav-link-active:
    textColor: "{colors.ink}"
  sidebar-item-active:
    backgroundColor: "rgba(255, 255, 255, 0.08)"
    textColor: "{colors.ink}"
    rounded: "{rounded.nav-item}"
    padding: "7px 12px"
    typography: "{typography.nav}"
  chip:
    backgroundColor: "{colors.surface-whisper}"
    textColor: "{colors.ink-muted}"
    rounded: "{rounded.pill}"
    padding: "4px 12px"
    typography: "{typography.label}"
  note-callout:
    backgroundColor: "color-mix(in oklab, #2160ff 12%, transparent)"
    textColor: "{colors.ink-muted}"
    rounded: "{rounded.note}"
    padding: "16px"
  glass-pane:
    backgroundColor: "rgba(255, 255, 255, 0.07)"
    rounded: "{rounded.pane}"
    padding: "20px"
  button-glass:
    textColor: "{colors.ink}"
    rounded: "{rounded.pill}"
    padding: "8px 16px"
---

# Design System: LiquiKit site

## Overview

**Creative North Star: "The Black Studio"**

A dark room with a single key light: the only things in it are glass objects and the light refracting through them. Every page starts from pure black so the material has something to be seen against; white type is the label on the instrument, and the one saturated colour in the room is the neon blue that lights the glass edges.

The system is quiet on purpose. There is no card chrome, no gradient page background, no decorative illustration: depth comes from the glass itself (a lit rim, a soft resting shadow, refraction while in use) and from hairline rules at 8% white. Copy sets the rhythm, not boxes. The site is an Operate/Read surface with a Persuade landing page, so the landing page is allowed one full-bleed scroll-driven scene, and every page after it is typography and glass only.

Provisional: this record was extracted in scan mode; the North Star name and palette adjectives are a proposal, not a ratified creative direction.

**Key Characteristics:**
- Pure black canvas (`#000000`), never near-black grey.
- White type on a five-step alpha scale (100 / 80 / 70 / 60 / 50%).
- Hairlines at `rgba(255,255,255,0.08)`, 1px, never a shadow.
- Neon blue (`#2160ff`) as the only saturated colour, used for light and emphasis, never for large fills.
- Geist, semibold, tight negative tracking on every heading; body never bolder than 500.
- Glass is the elevation system: no conventional elevated cards.

## Colors

Near-black and white carry the whole interface; the palette is about light, not hue.

- **Canvas** `#000000` — page background everywhere, including the landing hero and the docs shell.
- **Ink scale** — `#ffffff` for headings and active states, `rgba(255,255,255,0.8)` for callout copy, `0.7` for body and primary nav, `0.6` for secondary nav and page descriptions, `0.5` for sidebar group labels, `0.3` for list markers.
- **Hairlines** `rgba(255,255,255,0.08)` — the only borders in the system: header bottom, sidebar divider, heading underline, section separators.
- **Whisper fills** `rgba(255,255,255,0.07)` for chips and inactive buttons, `0.08` for the active sidebar item, `0.12` on hover.
- **Neon** `#2160ff`, with `#a8ccff` as its hot highlight and `#03103f` as its deep end. Used for the landing glow, focus/emphasis accents, and a 12% wash inside note callouts (`ring` at 40%).
- **Glass accent** `#7774ff` is the component default; the site overrides switch/checkbox/focus accents to the neon blue through `--glass-accent`.
- **Dark pane tint** `#0b1540` — the deep navy that all dark glass panes are tinted with, set via `--glass-pane-tint`.
- **Danger** `#ff6369` only inside components (destructive menu items, invalid fields), never as page chrome.

## Typography

One family, Geist Variable, with Geist Mono for code and the wordmark's monospace treatment. Hierarchy comes from size and weight steps, not from a second face.

- **Landing hero** — `clamp(34px, min(8.4svh, 7.4vw), 96px)`, 600, `1.1`, `-0.035em`. Sized to the viewport height as much as the width, so the hero always fills the fold.
- **Page title** — 34px on small screens, 40px from `sm`, 600, `1.1`, `-0.03em`; description directly below at 17px/1.6 in 60% white.
- **Section heading (h2)** — 24px, 600, `-0.02em`, with a hairline rule under it and 56px of space above.
- **Subheading (h3)** — 18px, 600, `-0.01em`.
- **Body** — 15.5px, `1.75` line-height, 70% white, max 800px measure. Prose is never full-bleed.
- **UI text** — 14px nav, 12.5px labels and chips, 14px tables.
- **Mono** — code blocks and inline code only.

## Layout

- **Shell** — 1440px max width, 56px tall header (`h-14`), 16–24px side padding (`px-4 sm:px-6`).
- **Docs** — 260px sticky sidebar + fluid content column from `lg`; the article itself is capped at 800px inside a 1fr column, with a 220px outline rail from `xl`. Article padding: 20px on small screens, 32px at `sm`, 48px at `lg`; 40px top, 96px bottom.
- **Landing** — full-bleed, 100svh scenes; the hero pins for a 210svh scroll track. Vertical rhythm is expressed in `svh` units so it holds on short laptop viewports.
- **Density** — roomy for reading, compact for navigation: 8px gaps inside the sidebar list, 20–24px between sidebar groups, 12px between chips.

## Elevation & Depth

Depth is material, not shadow. There are no elevated cards and no layered panels.

- **Glass** — every raised surface is a `GlassPane` (or a glass control) tinted toward the dark navy (`#0b1540`) over the black canvas, with a lit rim from the light model and a resting shadow of `0 1.5px 4px rgba(0,0,0,0.14), 0 0 1px rgba(0,0,0,0.06)`. While a control is in use the resting shadow is swapped for the lifted one and the lens opens; at rest the surface is flat and stable.
- **Blur** — `backdrop-blur-xl` is used only for the sticky docs header (`bg-black/80`), never for content cards.
- **Neon light** — the landing scene's glow is the only emissive element; it sits behind glass, never on top of type.

## Shapes

- **Pills** — every control that is a pill is fully round (`999px`): buttons, switches, segmented controls, chips, search fields.
- **Panes** — large surfaces default to `28px` (hero panes `30px`, dialogs `36px`); the radius scales down with the surface, never below the 9px of a nav item.
- **Nav items and small labels** — `9px` radius; callouts `14px`.
- **Corners are the only ornament**: no borders on glass, no double strokes, no icon frames, no drop-shadowed cards.

## Components

- **Site header** — 56px, logo left, 14px nav links at 60% white turning white on hover/active, GitHub link pushed right. Docs variant is sticky, `bg-black/80` with `backdrop-blur-xl` and a hairline bottom border; landing variant is absolute over the hero, no background.
- **Docs sidebar** — 12.5px medium group labels at 50% white, 14px items with 7px/12px padding and a 9px radius; active item gets an 8% white fill and full white text.
- **Chips** — pill, 7% white fill, 12.5px label, optional 14px icon, flipping to 12% fill and white text on hover.
- **Note callout** — 14px radius, 12% neon wash, 1px neon-40% ring, 14.5px/1.65 text at 80% white with a hot-blue icon.
- **Glass buttons** — a glass track with an ink label, pill radius, `8px 16px` padding; primary emphasis comes from the accent inside the material, not from a filled brand button.
- **Code blocks** — mono, dark surface from the Shiki theme, never inside a glass pane.

## Do's and Don'ts

- **Do** start every new page from black and add glass, not a container.
- **Do** keep headings semibold with negative tracking; never letterspace display type.
- **Do** express hierarchy with the white alpha scale before reaching for a new size.
- **Do** let neon stay light: washes under 15%, rings, glows, focus accents.
- **Do** give glass a busy or meaningful backdrop (artwork, code, a product scene); flat colour wastes it.
- **Don't** introduce a second accent hue, gradients on text, or a coloured page background.
- **Don't** put content cards on glass panels on cards; the glass is the card.
- **Don't** use grey borders above 8% white or any border-with-shadow card treatment.
- **Don't** animate layout properties; motion is spring-based transform and opacity only.
