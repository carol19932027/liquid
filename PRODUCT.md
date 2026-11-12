# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

React developers who want Apple-style liquid glass in a real product and will not trade away keyboard support, screen-reader semantics or Base UI behaviour for it. They arrive from a link, a shadcn registry search, or a Base UI project, read the docs, try a component in the demo pages, and install the source into their own app. Second audience: developers already on shadcn/ui who use `components.json` registries as their distribution model.

## Product Purpose

Give React 19 teams liquid-glass components whose refraction is a physical model rather than a painted effect, and ship them as source copied into the project so the team owns and can read every line. Success is a component that installs in one command, behaves like the Base UI primitive it wraps, bends the page convincingly while it is used, and costs nothing at rest.

## Positioning

The glass is traced, not styled: `packages/liquikit/src/glass/optics.ts` models a viewing ray refracting through a glass body (index of refraction, thickness, bevel, base) and bakes the displacement into a map, so the rim, magnification, Fresnel rim light and glints follow from the material instead of being hand-tuned. One SVG `feDisplacementMap` bends a live picture of the content, so text under the lens stays selectable and links stay clickable. No WebGL, no flags.

## Operating Context

- Bun + Turborepo monorepo: `packages/liquikit` (source of every registry item), `apps/www` (TanStack Start site: marketing, docs, component pages, examples, and the built registry served at `/r`), `apps/lumen` (Next.js sample product page, served at `/lumen` from the site's build).
- `bun run dev` builds the registry, then starts the site on :3000 and Lumen on :3200; `bun run build`, `bun run typecheck`, `bun run check` (Biome) are the other gates.
- Registry items link to each other by URL from `REGISTRY_URL` (default `https://liquikit.dev/r`); `packages/liquikit/scripts/registry.ts` derives each item's dependencies from its imports.
- Readers evaluate the components in the docs site and the example pages, so the site has to demonstrate the glass bending real content, not describe it.

## Capabilities and Constraints

- Every shipped component is a Base UI primitive with a glass surface; compound parts are exported both as named parts (`MenuRoot`, `MenuTrigger`, `MenuPopup`) for Server Components and as `Menu.Root` for client components.
- Also ships glass controls of its own: `GlassPane`, switch, slider, segmented control, toggle group, and `GlassScope` with the refraction engine.
- Not an npm dependency: the shadcn CLI copies source into `components/liquikit/`, with the engine in `components/liquikit/glass/`. React 19 peer; `@base-ui/react` and `motion` come along.
- Glass runs no filter at rest (backdrop blur plus a baked light image). It bends while pressed, dragged, focused, opening, or briefly after, unless `refraction="always"` (or `"backdrop"` on a scope) is opted into, which keeps a filter running while on screen.
- Browser limits are product truth, documented on `/docs/limitations`: Safari and Firefox cannot filter what is behind an element, so glass bends the content of the `GlassScope` instead; scopes do not nest; a `position: fixed` element inside a scope is fixed to the scope; in Safari and Firefox popups stay frosted; some Safari layers (video, `backdrop-filter`, `will-change`, 3D transform) are left unbent inside a scope; a switch, slider or segmented control inside a scope builds its lens maps on first use.
- The optics are physically based, not physically exact (no perspective, no second bend on the way out); `/docs/how-it-works` is the record of what the model leaves out.
- The site deploys to Cloudflare with a custom domain on `liquikit.dev` (`wrangler.jsonc`).

## Brand Commitments

The name LiquiKit, and the material itself: the interface is meant to read as iOS-style liquid glass, and the glass must have something real to bend (a photo, a gradient, content) rather than sit on flat colour. The demo pages are the shop window, so their restraint and craft are held to the same bar as the components.

## Evidence on Hand

- Docs in `apps/www/content/docs/` (introduction, installation, how-it-works, limitations, theming, glass-pane) and one page per component in `apps/www/content/components/`.
- Runnable examples in `apps/www/src/examples/` plus the Lumen sample product page in `apps/lumen/`.
- The engine's design notes in `packages/liquikit/GLASS.md`, engine source in `packages/liquikit/src/glass/`.
- `design/LiquiKit.icon/`, `apps/www/public/og.png` and the logo components.
- No customer logos, testimonials, benchmarks, download counts or pricing exist in the repository. Do not invent them.

## Product Principles

1. Behaviour comes from Base UI, appearance from LiquiKit; never regress keyboard, focus or ARIA behaviour for a visual effect.
2. The material is modelled, not painted: parameters stay physical (`ior`, `thickness`, `bevel`), and new effects earn their place through the model.
3. Restraint by default: no filter at rest, refraction is a response to touch, and long pages of glass stay smooth to scroll.
4. Source you own: the registry copies readable code into the project, so internal structure and naming are part of the product surface.
5. Be honest about the browser: limitations are documented as facts, not hidden behind a support matrix.

## Accessibility & Inclusion

Keyboard interaction, focus management and semantics are delegated to the Base UI primitive behind each component, and the glass itself never becomes the hit target for text or links. No product-specific conformance standard or assisted-technology support list has been established; do not claim WCAG conformance that has not been verified.
