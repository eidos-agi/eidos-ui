# Technique: Shipr multi-surface defaults

**Why this exists.** Shipr watches shipments on phone, Mac, tablet, and a
Chrome add-in. Argue density, context binding, and status color **here** before
MV3 / Electron / RN. Tokens live in `/brand.css` (retroactive). Each version
fixes one surface failure and stays online.

Dogfood product: [Shipr](https://shipr.eidosagi.com/). Pattern origin: same
ladder idea as `product-shell-mock/` (Knox), specialized for fleet + page context.

## When to use

| Use this | Don't use this |
|----------|----------------|
| Chrome side panel width / density | Final extension packaging |
| Page-context binding (repo · PR · Actions) | Real GitHub / Railway data |
| Status chips shared with Mac / phone | Production a11y audit |
| Dock badge semantics | Replacing chat-event demos |

## Recipe

1. **One file per version** — CSS + tiny JS data model; link `/brand.css`.
2. **Host + surface** — fake GitHub (or Mac / phone frame) beside the Shipr UI.
3. **Shared state** — clicking a run on the host selects the same shipment in Shipr.
4. **Chrome floor** — side panel mock width = `--panel-side-min` (360px). Comfort target `--panel-side-comfort` when the user widens.
5. **Status from tokens** — `--ship-inflight` / `--ship-ok` / `--ship-blocked` / `--ship-failed` only.
6. **Callout** under the stage lists the ship checklist for implementers.
7. **Version ladder** — `v0/` Chrome, then phone, Mac dock, tablet.

## Anti-patterns

- Hex colors outside `brand.css`.
- Cards stacked inside the 360px panel.
- Global nav that fights the page URL context.
- Happy path only (always show empty / unpaired / error).
- Emoji in chrome (Lucide SVG, stroke 2).
