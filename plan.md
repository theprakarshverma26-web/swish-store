# SWISH STORE implementation plan

## Product scope
A responsive, client-side e-commerce demo for the fictional SWISH STORE basketball footwear and gear brand. The experience prioritizes the home hero, shoes catalogue, product details, interactive filtering/search, shoe finder, cart/wishlist, and honest demo checkout. All inventory, prices, promotions, policies, newsletter submissions, and order confirmations are explicitly presented as demo data/interactions.

## Implementation approach
- Use a lightweight React + Vite client application with no server or database capability enabled; cart, wishlist, and recently viewed state persist in localStorage for the demo session.
- Keep all catalogue entries in one central TypeScript data module. Each item carries category, brand, price, colors, sizes, play-style, court, cushioning, tags, demo stock messaging, and related-product identifiers so filters and the shoe finder never rely on unsupported attributes.
- Use a small route/state layer based on `window.history` and `popstate` for `/`, `/shop`, `/shoes`, `/apparel`, `/accessories`, `/new-arrivals`, `/best-sellers`, `/product/:id`, `/cart`, `/wishlist`, `/checkout`, `/about`, and `/help`. Query strings represent search/filter state where useful; all in-app links remain functional without a backend.
- Serve a static `public/manus-routes.json` route manifest before the dev server starts. Include meaningful HTML metadata, Open Graph tags, and a clear demo disclosure in `index.html`; client navigation updates document title and description.
- Use the project runtime port 3000, bind the dev server to `0.0.0.0`, and include a production build command/output declaration once the app is stable.

## Design direction
- **Design movement:** premium basketball editorial / modern streetwear lookbook, combining hard court geometry with boutique sneaker-retail restraint.
- **Core principles:** (1) one decisive focal point per section, (2) orange used as a court-line signal rather than a gradient effect, (3) typography carries the attitude, (4) utility is always visible and tactile.
- **Color philosophy:** near-black, clean white, and neutral greys create a quiet premium gallery-like base; white is used as the signature contrast signal for actions and match highlights; charcoal and silver support technical product information.
- **Layout paradigm:** asymmetric editorial bands, oversized type, split hero composition, horizontal product rails, and offset image/text blocks. Avoid a centered template feel by letting sections break the grid and by using strong full-bleed moments.
- **Signature elements:** white “court line” rules that bend around key blocks, a compact SWISH wordmark with a curved swoosh underline, and small technical labels that read like scouting notes.
- **Interaction philosophy:** every interaction should feel like a quick move—fast feedback, clear state, and no hidden dead ends. Cart/wishlist actions use short confirmations, drawers keep context, and filters expose their current state.
- **Animation:** 180–360ms transform/opacity transitions, hover image lift/zoom, staggered reveal for hero/product rows, drawer slide transitions, and reduced-motion fallbacks that preserve all state changes.
- **Typography system:** use `Barlow Condensed` for display/labels and `DM Sans` for body/UI, with uppercase display hierarchy, tight tracking on utility labels, and generous line-height for long copy.
- **Brand essence:** India’s fictional basketball destination for gear that moves from hardwood to street; bold, precise, restless.
- **Brand voice:** direct, energetic, player-aware. Example lines: “Find your next possession.” and “Demo stock. Real attitude. No fake promises.”
- **Wordmark & logo:** text-based SWISH wordmark in condensed capitals paired with an original orange curved mark that echoes a ball seam and a fast crossover.
- **Signature brand color:** signal white `#ffffff`.

## Main modules
- `src/data/catalogue.ts`: central catalogue and helper types.
- `src/App.tsx`: route shell, header, footer, global overlays, and screen selection.
- `src/components/`: hero, product cards/grid, filters, product detail, finder, cart drawer/page, checkout, editorial, and shared UI.
- `src/lib/store.ts`: localStorage-backed cart/wishlist/recent helpers and cart totals.
- `src/styles/`: tokens, layout, component styles, responsive breakpoints, reduced-motion rules.
- `public/`: route manifest, favicon/logo assets, and any generated/curated visual assets.

## Asset strategy
Use the user-supplied catalog crops as clearly labelled reference/lookbook imagery, plus original monochrome basketball visuals generated for SWISH STORE. Exact third-party product names are not used as real stock claims; the demo catalogue uses fictional SWISH-branded product naming and explicitly labels catalog/reference imagery as illustrative with no affiliation or inventory claim. Generate a small set of cohesive hero/editorial/product visuals with black, white, concrete, and grey direction, then reuse only where the image job is appropriate. Keep images lazy-loaded below the fold and use responsive object-position crops.

## Delivery workflow
Implement the plan, enable TypeScript diagnostics through `webdev.config` before the first code batch, run a local build/typecheck, start the managed preview on port 3000, verify `/manus-routes.json` and representative page URLs, inspect key desktop/mobile screenshots, fix confirmed issues, then commit/push to the canonical `main` checkpoint. Do not enable auto-publish and do not add real payment, customer messaging, account auth, or live inventory services.
