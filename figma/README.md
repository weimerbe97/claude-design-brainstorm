# Figma Integration Package

Two things in here:

- `svg/` — nine notification states as clean, editable SVGs
- `design-tokens.json` — the full color / type / spacing system in Tokens Studio format

---

## Importing the SVGs

Figma imports SVG natively, so there's no plugin required:

1. In Figma, drag any `.svg` file from `svg/` directly onto the canvas — **or** use **File → Place image / Import** and select them
2. Each file lands as a frame containing editable vector shapes and **live text layers** (not outlined paths, so you can still edit copy)
3. The layers are named (`logo`, `btn-primary`, `btn-secondary`, `notification-card`, etc.) so the structure is easy to navigate

You can import all nine at once — select them all in the file picker and Figma will place them as separate frames.

### What comes in editable

- Text is real `<text>`, so you can re-type copy and it stays vector
- Colors map to fills you can swap or link to variables
- Rectangles, circles, and lines are native Figma shapes
- Groups preserve the logical structure

### What needs a quick touch-up after import

- **Fonts:** the SVGs reference Inter and JetBrains Mono. If those aren't installed/enabled in your Figma, you'll get a font-substitution prompt — install them (both are free on Google Fonts) or remap to your house fonts.
- **Drop shadows:** SVG shadows don't transfer perfectly. Re-apply the card elevation using the `boxShadow.notification` token after import (it's a subtle `0 4 16 rgba(0,0,0,0.06)`).
- **The pulsing live-dot and spinners** are static in SVG. They're placeholders for animated elements — see the prototype extension or the spec doc for the intended motion.

---

## Importing the design tokens

The `design-tokens.json` file is in **Tokens Studio** format (the most widely used token system for Figma):

1. Install the free **Tokens Studio for Figma** plugin (from the Figma community)
2. Open the plugin → **Settings / menu → Import** → load `design-tokens.json`
3. The tokens appear as a `global` set — colors, font sizes, spacing, radii, shadows, etc.
4. Use **"Create styles"** / **"Create variables"** in the plugin to turn them into native Figma styles and variables you can apply throughout your file

Once the tokens are variables, you can select any imported SVG shape and bind its fill to e.g. `color.navy` — so future color changes propagate everywhere.

### Token structure

- `color.*` — full palette with usage notes (navy is primary, red is logo-only, etc.)
- `fontFamily / fontWeight / fontSize / lineHeight / letterSpacing` — the type system
- `borderRadius.*` — container (12), card (8), pill (999), etc.
- `spacing.*` and `sizing.*` — layout measurements
- `borderWidth.*` — hairline (0.5) and accent (2)
- `boxShadow.*` — notification, pin, and tooltip elevations

Every token has a `description` explaining where it's used.

---

## Suggested workflow for a clean rebuild

If your team wants a fully native Figma component library rather than imported SVGs:

1. Import `design-tokens.json` first and create variables — this sets up your styles
2. Import the SVGs as visual reference (drop them on a scratch page)
3. Rebuild each state as a proper Figma component using the variables, using the SVGs as a pixel guide
4. The notification card → main component; states → variants

This gives you the cleanest result with real auto-layout and component variants, using the SVGs as the source of truth for layout and the tokens for styling.

### Alternative: html.to.design

If you'd rather skip the manual rebuild, the **html.to.design** plugin can ingest the `notification-redesign.html` file (from the earlier deliverable) and reconstruct the states as Figma layers with auto-layout — often a faster path to native components than rebuilding from the SVGs. The SVGs here are the better choice if you want lightweight, dependency-free vector reference.

---

## File list

```
figma/
├── README.md                         (this file)
├── design-tokens.json                (Tokens Studio format)
└── svg/
    ├── state-1-first-paint.svg
    ├── state-2a-rewards-only.svg
    ├── state-2b-codes-ready.svg
    ├── state-3a-3b-rewards-activated.svg
    ├── state-3c-testing-codes.svg
    ├── state-4a-code-rewards-win.svg
    ├── state-4b-codes-failed.svg
    ├── state-5-checkout-pin.svg
    └── state-6-post-purchase.svg
```
