---
name: ui-resource
description: Source and install prebuilt React UI from free shadcn-compatible resources instead of generating from scratch — official shadcn/ui components and blocks, the free subset of shadcnspace.com (isPro-filtered), React Bits animated components, animata.design motion components, and GSAP (free animation engine) for custom motion. Activate when building or extending UI in any React/Tailwind project (Next.js, Vite, Remix, TanStack Start), greenfield or existing.
---

# UI Resource — Sourcing Prebuilt React UI

## Overview

When building React UI, do not generate components from scratch. Source them from a known, free set and install them with the official shadcn CLI. Agents produce better UI working from a known component set than by improvising markup. When no prebuilt piece exists, write custom motion with the GSAP engine (below) rather than hand-rolled scroll listeners or ad-hoc keyframes.

**Free-only rule (hard boundary):** never recommend, install, or link paid-gated content. Excluded outright: shadcnspace Pro blocks, all shadcnspace Pages, the shadcnspace Admin Dashboard, and everything on React Bits' separate Pro site (pro.reactbits.dev, including its paid Agent Kit). Never suggest the user buy a license or walk them into a paywall. If an item's free status cannot be verified, treat it as paid and use another source.

## When to Activate

Activate when:
- Building or extending UI in any React project — greenfield included.
- The user asks for components, blocks, pages, landing sections, dashboards, forms, or animated UI.
- The project uses (or is adopting) Tailwind CSS with shadcn/ui-style components.

Do **not** activate for non-shadcn stacks — Material UI, Chakra, Mantine, or component systems outside the shadcn/Tailwind orbit. This skill's sources and CLI do not apply there.

## Prerequisites

- Node.js with `npx` (npm, pnpm, yarn, or bun all work with the shadcn CLI).
- A React project (Next.js, Vite, Remix, or TanStack Start).
- If the project has no `components.json`, run `npx shadcn@latest init` first — this scaffolds Tailwind CSS v4 and the base setup.

## Procedure

1. **Classify the need** using the Glossary below (component vs block vs page vs template). Searching the wrong category wastes the sourcing pass.
2. **Pick the source by hierarchy** — always try the earlier source first:
   1. Official shadcn/ui (backbone, 100% free, MIT)
   2. shadcnspace.com free subset (variants, when official doesn't have the look)
   3. React Bits (dramatic motion: animated text, WebGL backgrounds, 3D, micro-interactions)
   4. animata.design (everyday UI motion with accessibility, pure MIT)

   For motion needs, sources 3 and 4 are complementary — pick by character: decorative, dramatic effects → React Bits; functional UI motion with accessibility needs → animata. If no source has a prebuilt fit, build custom motion with GSAP — the animation engine below — not raw scroll listeners or keyframe soup.
3. **Install** via the source's mechanism (below).
4. **Verify**: imports resolve, dependencies installed, component renders in the page it was placed in.

## Source 1 — Official shadcn/ui (backbone)

~64 components plus blocks (sidebar, login, signup, dashboard categories). MIT licensed, free forever.

- Browse: https://ui.shadcn.com/docs/components and https://ui.shadcn.com/blocks
- Install: `npx shadcn@latest add <name>` — e.g. `button`, `dashboard-01`, `sidebar-07`, `login-03`
- The CLI copies full source into the project — no runtime dependency, no lock-in.

## Source 2 — shadcnspace.com free subset (variants)

~1000 components/blocks/pages/templates, but the large majority are Pro-gated. Use only after filtering:

1. Fetch the public registry index: `https://shadcnspace.com/r/registry.json`
2. Treat an item as free **only** if its metadata has `meta.isPro === false` (e.g. `hero-01`, `hero-02`, `hero-03`, `hero-33` are free; `hero-04`–`hero-52` are Pro).
3. Install free items with the URL registry form — no account or license needed:
   ```
   npx shadcn@latest add https://shadcnspace.com/r/<name>.json
   ```
   Example: `npx shadcn@latest add https://shadcnspace.com/r/hero-01.json`

A namespace form (`npx shadcn@latest add @shadcn-space/<name>`) is documented by the site but requires adding a `registries` entry to `components.json` whose exact snippet is not stable across their docs — if you use it, verify the current form at https://shadcnspace.com/docs/getting-started/how-to-use-shadcn-cli first. The URL form above always works without configuration.

Free templates (Crypgo, Typefolio, Resume) install the same way; all Pages require a license and are excluded by the free-only rule.

## Source 3 — React Bits (animated effects)

215 free animated React components in five categories — Text Animations, Animations, Components, Micro Interactions, Backgrounds — including WebGL/3D backgrounds (three.js) and GSAP-driven effects. Installs as source you own.

- Browse: https://reactbits.dev (repo: https://github.com/DavidHDev/react-bits)
- Install with the official shadcn CLI — React Bits is listed in the official registry directory, so the namespace resolves with no extra configuration:
  ```
  npx shadcn@latest add @react-bits/SplitText-TS-TW
  ```
- Every component has four slugs — JS/TS × CSS/Tailwind, chosen by suffix (`SplitText-JS-CSS`, `SplitText-JS-TW`, `SplitText-TS-CSS`, `SplitText-TS-TW`). In a TypeScript + Tailwind project use `-TS-TW`.
- Alternative CLI: `npx jsrepo@latest add https://reactbits.dev/r/SplitText-TS-TW` — same source, different installer.
- Per-component dependencies (motion, gsap, three, @hugeicons) are declared in each registry item and auto-installed by the CLI.
- Everything on reactbits.dev is free with no account; the Pro product is a separate site (pro.reactbits.dev) and is excluded by the free-only rule.
- If a slug 404s, take the exact name from the component's page on reactbits.dev — not every index name resolves as a registry slug.

## Source 4 — animata.design (everyday UI motion)

156+ hand-crafted animated React components for everyday UI — buttons, cards, widgets, lists, graphs, skeletons — with accessibility built in (keyboard focus, screen-reader labels, reduced-motion fallbacks). MIT licensed. Copy-paste first: copy the file into the project and it's owned from there.

- Browse: https://animata.design (19 categories)
- Setup: Tailwind CSS required; `motion` and Lucide/Radix icons optional per component.
- Source repo: https://github.com/codse/animata

## Animation Engine — GSAP (custom motion)

When none of the sources has a prebuilt fit, write custom motion with GSAP (GreenSock Animation Platform, https://gsap.com, repo https://github.com/greensock/GSAP) — the industry-standard JavaScript animation engine, powering 12M+ sites. Some React Bits components already run on it (their CLI auto-installs `gsap` when a component needs it).

**100% free since April 2025.** Webflow (which acquired GreenSock in late 2024) made GSAP entirely free — including every formerly paid Club GreenSock plugin: ScrollTrigger, ScrollSmoother, SplitText, MorphSVG, DrawSVG, Flip, Draggable, and the rest. Commercial use included, Webflow customer or not.

- Install: `npm install gsap` (or pnpm/yarn/bun). In React, also `npm install @gsap/react` and use its `useGSAP()` hook — a drop-in replacement for `useEffect`/`useLayoutEffect` that handles cleanup.
- Signature capabilities: timelines (sequence tweens with labels and offsets), ScrollTrigger (pinning, scrubbing, parallax, scroll-driven storytelling), SplitText (character/word/line reveal animations), SVG morphing and drawing.
- Docs: https://gsap.com/docs/v3 (includes a React guide covering `useGSAP` patterns).

## Glossary

shadcnspace's own taxonomy — classify before searching:

| Term | Meaning | Free status |
| :--- | :--- | :--- |
| **Component** | Single UI element + variants (button, card, input, navbar) | Many free; check `isPro` |
| **Block** | Multi-component section (hero, pricing, feature grid) in Marketing / Ecommerce / Dashboard UI / Applications groups | Some free; check `isPro` |
| **Animated block** | Block paired with motion-design prompts | Often unverifiable — apply the conservative rule |
| **Page** | Full pre-designed page (landing, blog, contact, error) | All require a license — excluded |
| **Template** | Complete starter site (12 total) | 3 free: Crypgo, Typefolio, Resume |
| **App block** | Pre-built interface (chat, Kanban, email) | Check `isPro` |
| **Dashboard** | The bundled Admin Dashboard kit | Premium-only — excluded |

Note: shadcnspace's MCP server uses a different internal taxonomy (14 categories: hero, features, pricing, testimonials, faq, cta, header, footer, stats, forms, content, ecommerce, ai, widgets) than the site's navigation. Match on item names and `isPro` flags, not category labels.

**GSAP terms:** a *tween* animates a target from one state to another; a *timeline* sequences tweens; *ScrollTrigger* ties playback to scroll position; *SplitText* splits text into characters/words/lines for staggered reveals.

## Optional — shadcnspace MCP Server

For live search/composition instead of static registry fetches, the MCP server is free to connect (PRO blocks and Pages require a token — never needed under the free-only rule):

```json
{ "mcpServers": { "shadcnspace-mcp": { "command": "npx", "args": ["-y", "shadcnspace-mcp@latest"] } } }
```

Claude Code: `claude mcp add shadcnspace-mcp -- npx -y shadcnspace-mcp@latest`

Useful tools: `listFreeBlocks` (free blocks only), `getBlockInstall` (install command + import path + JSX example for a given block).

Separately, the official shadcn MCP server (`npx shadcn@latest mcp init --client claude` — or `--client cursor` / `--client vscode`) can browse, search, and install any registry namespace, including `@react-bits`.

## Licensing

- **Official shadcn/ui** — MIT.
- **animata.design** — MIT.
- **React Bits** — MIT + Commons Clause: free for personal and commercial use, including selling apps built with the components; selling or redistributing the components themselves (alone, bundled, or ported) is not permitted (https://github.com/DavidHDev/react-bits/blob/main/LICENSE.md).
- **GSAP** — custom "Standard 'no charge' license" (https://gsap.com/standard-license): fully free including commercial use; not MIT.
- **shadcnspace.com** — a custom proprietary license (their homepage claims "MIT" but the license page at https://shadcnspace.com/license does not say that). Free resources may be used in personal, commercial, and client projects, including selling projects built with the code; retain the copyright notice; do not resell the resources as standalone products.

## Troubleshooting

- **No `components.json`** — run `npx shadcn@latest init`, then retry the add.
- **Registry URL 404s** — the item was renamed or removed; re-fetch `registry.json` and use the current name.
- **A paid item looks tempting** — stop. Do not recommend it or mention pricing. Pick the nearest free alternative from an earlier source in the hierarchy.
- **Radix vs Base UI variants** — shadcnspace offers both primitive styles; check which base the project uses (the `@shadcn-space` base-ui vs radix namespaces differ) and pick the matching variant, or use the URL form which serves the default style.
