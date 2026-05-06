# cantdraw roadmap

AI-powered graphic design for everyone. Start with logos, expand to merch, marketing, landing pages. Anyone can get professional-quality design assets — and real designers can plug in too.

---

## Core concept

You describe what you want. AI generates a few editable SVG concepts with proper layers. You share a Partiful-style poll, people vote, you ship the winner. No design skills required. The output is real SVG — not a raster image — so it works everywhere: web, print, merch, Figma.

---

## Why SVG over image generation (DALL-E, Stable Diffusion)

Image generators produce flat raster files (PNG/JPG). cantdraw uses LLMs (Claude / GPT-4o) to write SVG code directly. This means:
- Every element is a named, editable layer
- Colors, fonts, shapes are all swappable
- Output works at any scale (logos, billboards, favicons)
- Designers can open it in Figma or Illustrator and keep going

---

## Phase 0 — Logo generation MVP

Goal: describe a brand, get 3 logo SVG concepts, export with all layers intact.

- [ ] Input form: brand name, one-line description, style tags (minimal, bold, playful, techy, etc.)
- [ ] AI generates 3 SVG logo concepts with distinct visual directions
- [ ] Every concept is structured SVG: named layer groups for icon, wordmark, background, decorative elements
- [ ] In-app SVG preview with zoom
- [ ] Export as SVG (all layers/shapes preserved) and PNG flat export
- [ ] Share sheet so exported files can go straight to Figma, Illustrator, Messages, etc.

**AI backend:** Claude / GPT-4o writing structured SVG code with named layer groups
**Platform:** iOS + Android (Expo managed workflow)
**Collaboration / MCP:** deferred — keeping the exported SVG well-structured is the foundation for whatever collaborative layer comes later

---

## Phase 1 — Voting polls

Goal: share concepts, let people vote, see results.

- [ ] "Start a poll" from any generation → creates a shareable web link
- [ ] Voters see the SVG options side by side in browser (no app required)
- [ ] Vote with one tap, optionally leave a comment
- [ ] Creator sees live results and comments in-app
- [ ] Poll expires after X days or when creator closes it

**Requires:** lightweight hosted web page for poll voting (not in-app)

---

## Phase 2 — Editable layers

Goal: tap into the SVG and change anything.

- [ ] Layer panel: see all named groups in the SVG (icon, wordmark, background, etc.)
- [ ] Tap any layer to edit: color picker, font selector, scale/position
- [ ] Undo/redo history
- [ ] Variant generator: "make 3 color variations of this"
- [ ] Lock layers to prevent accidental edits

---

## Phase 3 — Designer access

Goal: professional designers can plug into cantdraw.

- [ ] Export to Figma (via Figma REST API or plugin)
- [ ] MCP integration: designers connect their tools and receive/edit assets directly
- [ ] Designer marketplace: clients can post briefs, designers respond with cantdraw-generated concepts
- [ ] Brand kit: lock in colors, fonts, logo variations for reuse across projects

**Open question:** MCP direction — does cantdraw expose an MCP server (designers connect their tools to it) or does it act as an MCP client (connects to Figma, Illustrator, etc.)?

---

## Phase 4 — Expand beyond logos

Goal: cantdraw handles all the visual assets a brand needs.

- [ ] Social media graphics (Instagram posts, stories, banners)
- [ ] Merch designs (t-shirt, hat, sticker layouts with bleed/safe zones)
- [ ] Landing page sections (hero, feature cards, CTA blocks)
- [ ] Marketing materials (pitch decks, sell sheets)

Each category follows the same pattern: describe → generate options → poll → edit → export.

---

## Architectural decisions

| Decision | Choice | Notes |
|---|---|---|
| SVG generation | LLM-written SVG code | Claude / GPT-4o, not image gen models |
| Voting polls | Hosted web page + link | No app required for voters |
| Storage | On-device for assets | Cloud needed for poll hosting |
| Platform | iOS + Android | Expo managed workflow |
| Designer integration | MCP — direction TBD | See Phase 3 open question |
| Apple Intelligence | Future consideration | On-device Foundation Models API — needs custom native module, no Expo support yet |

---

## What the default Expo template covers

Navigation and UI shell only. SVG generation, rendering, layer editing, and poll hosting are all custom additions — none are in the default template.
