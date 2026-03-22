# Changelog

All notable changes to the [RaptorQ Article](https://github.com/Dicklesworthstone/raptorq_article) are documented here.

This project has no formal release tags. The changelog is organized into logical development phases derived from the commit history. Every commit hash links to its GitHub diff.

---

## Development Phases

- [Phase 4: Repository Metadata](#phase-4-repository-metadata-2026-02-11--2026-02-22) — License, social preview, linting
- [Phase 3: Voice & Editorial Polish](#phase-3-voice--editorial-polish-2026-02-10-0048--0131) — De-slopification, prose tightening, research additions
- [Phase 2: Design System & Visualization Overhaul](#phase-2-design-system--visualization-overhaul-2026-02-10-0003--0047) — Visual redesign, all 5 viz upgrades, new content
- [Phase 1: Content Foundation](#phase-1-content-foundation-2026-02-09) — Initial article, PAR2 bridge, real-world deployments
- [Initial Commit](#initial-commit-2026-02-09) — Full project scaffold

---

## Phase 4: Repository Metadata (2026-02-11 -- 2026-02-22)

Housekeeping commits that do not change article content or visualizations.

### License

- Replaced plain MIT license with MIT + OpenAI/Anthropic Rider restricting use by OpenAI, Anthropic, and affiliates without express written permission — [`b95d7d9`](https://github.com/Dicklesworthstone/raptorq_article/commit/b95d7d9fbcc0e754d60099462ca94a3d891491d2)
- Updated README badge and license references to reflect the new license — [`5c86589`](https://github.com/Dicklesworthstone/raptorq_article/commit/5c86589e05ddfb20bde8271f6ba59572b934ece9)

### Social & Linting

- Added 1280x640 GitHub social preview image (`gh_og_share_image.png`) — [`72f451f`](https://github.com/Dicklesworthstone/raptorq_article/commit/72f451f15736d365d7cb081b73694ca7156806f7)
- Replaced bare f-strings (no interpolation) with plain strings in `02_lt_code_simulation.py` and `03_raptorq_precoding.py`, eliminating F541/W1309 lint warnings — [`fda0b81`](https://github.com/Dicklesworthstone/raptorq_article/commit/fda0b815865a19a4fd17ec47214826486370c09e)

---

## Phase 3: Voice & Editorial Polish (2026-02-10, 00:48 -- 01:31)

Seven commits in rapid succession that rewrote prose for voice consistency, removed AI writing artifacts, and folded in late-stage research material. No structural or layout changes.

### Research Content Additions

- Added 7 research items: feedback implosion, block size caveat, sqrt(K) permanent-inactivation scaling, capacity-achieving proof sketch, Digital Fountain Inc. history, Raptor etymology, and RaptorQ finite-length framing — [`ebcd7e6`](https://github.com/Dicklesworthstone/raptorq_article/commit/ebcd7e618f5146c6b49cb65f03ed6ca0f656e538)
  - Also re-applied voice edits (hero subtitle, section intros, heading rewrites) that had been partially reverted
  - Changed `visualizations.js` (263 lines) alongside 1,122 lines in `index.html`

### Voice & Copy Rewrites

- **De-slopify pass**: removed emdash overuse, "Here's why" patterns, "It's not X it's Y" formulas, performative headings, forced enthusiasm; rewrote to first-person conversational tone matching author's natural style — [`c4e3ba7`](https://github.com/Dicklesworthstone/raptorq_article/commit/c4e3ba73ad0c6d4b5e5f344f41dc4879a0dc8013)
- Restored 16 lines of intended working-tree text that were lost during commit splitting (a tooling artifact, not a content decision) — [`a122bf0`](https://github.com/Dicklesworthstone/raptorq_article/commit/a122bf07c8e1f5cf4e1db2ae97a205b75cb53f75)
- Minor prose cleanup: removed remaining throat-clearing, switched to active voice — [`6e4007d`](https://github.com/Dicklesworthstone/raptorq_article/commit/6e4007d8c21a1a8111a4bb2ed7f7607de0d1d9ff)
- Final prose tightening: shorter headings, cut meta-commentary ("Let's make it concrete" becomes just the example), reframed section intros as questions instead of proclamations — [`2dee0d1`](https://github.com/Dicklesworthstone/raptorq_article/commit/2dee0d17ef1d88796b4b732da34dc12f5fa92426)
- Thirty-four line-for-line copyedits: active voice, comma-for-emdash substitutions, tighter hero subtitle ("sparse matrix, dense core, precode -> fungible packets recoverable from K+2"), shorter footer thesis ("Sparse + Dense. Fast + Correct.") — [`de4a42a`](https://github.com/Dicklesworthstone/raptorq_article/commit/de4a42a127e4215c0d559cd93db614bc1e8f0846)

### Visualization Style Update

- Updated visualization interactions and color palette to match the editorial redesign — [`489bcc0`](https://github.com/Dicklesworthstone/raptorq_article/commit/489bcc042b1049c1cffa14152e10c60bdc0a6387)

---

## Phase 2: Design System & Visualization Overhaul (2026-02-10, 00:03 -- 00:47)

A coordinated redesign of the visual language and all five interactive visualizations, plus major content additions.

### Content: Worked Examples & Historical Context

- Added concrete worked XOR encoding example (A=5, B=3, C=7, D=2 with four coefficient vectors) to "Packets Are Equations" section — [`e7770af`](https://github.com/Dicklesworthstone/raptorq_article/commit/e7770afbceac9bddf5b6cb6513365514a36404bf)
- Added stopping set (2-core) example: five degree-2 equations forming a cycle where peeling fails, then a worked inactivation recovery showing how marking one variable as inactive triggers a full cascade
- Added K=1,000 coupon collector example (7,500 draws = 7.5x overhead) and "Dense = solvable but slow / Sparse = fast but broken" thesis statement
- Added 1997 Tornado Codes entry to the "How We Got Here" timeline
- Expanded Ideal Soliton fragility explanation with the "bathtub drain" metaphor

### Visualization Upgrades (all 5)

All five interactive visualizations were substantially reworked in a single commit — [`a08b105`](https://github.com/Dicklesworthstone/raptorq_article/commit/a08b1054ad2e9f5ada73af93e04430ec2a66fe34):

| Viz | Key Changes |
|-----|-------------|
| **GF(2) Matrix Rank Builder** | GSAP-driven cell animations with rotate:-45 entrance; "Linearly Independent/Dependent" labels per row; 6xl status with cyan glow on full rank |
| **Degree Distribution & Ripple** | Trimmed to degrees 1-12; explicit 12-element RFC 6330 probability vector; replaced O(K) bipartite simulation with O(1) parametric ripple model; stroke-dashoffset self-drawing animation |
| **Precode Repair** | Increased from K=24/P=4 to K=30/P=6; cleaner animation stages; 6,3 dash-pattern repair paths |
| **Toy Decode Walkthrough** | Horizontal pill-layout equations; enlarged symbol cards with active glow; "TRACE: STEP 1/6" status |
| **Peeling Cascade** | Expanded from K=8/M=12 to K=12/M=18; added degree-3 packets; replaced static layout with D3 force simulation (forceLink/forceManyBody/forceCenter); proper enter/update/merge pattern |

### Hero Animation Redesign

- Replaced "fountain droplet" particle system with calmer "data rain" aesthetic: 3,000 particles at lower opacity, per-particle velocity for depth parallax, THREE.GridHelper floor for spatial grounding, wider field of view — [`9238ebd`](https://github.com/Dicklesworthstone/raptorq_article/commit/9238ebd7e80bf5311fc7cdf838a36dc7daf53759)

### Design System Overhaul

- Overhauled CSS custom properties: removed redundant accent variables, kept --accent-cyan as sole interactive color, added typographic scale variables, capped paragraphs at 65ch with text-wrap:pretty — [`d5367df`](https://github.com/Dicklesworthstone/raptorq_article/commit/d5367dfb4e5277a3a9ec3ef0f0fb7f5f7fb7a69d)
- Switched headings from Bricolage Grotesque to Inter 900 at -0.05em tracking
- Added OpenType features ss03, cv05, tnum for numeral alignment
- Reduced border-radius globally, simplified section dividers, tightened button sizing
- Added utility classes: `.drop-cap`, `.data-grid-cell`, `.viz-overlay-stats`

### Visual Design Refresh

- Updated CSS custom properties (brighter cyan, lighter text), increased editorial spacing, refactored hero into "fountain droplet" metaphor — [`6e0b748`](https://github.com/Dicklesworthstone/raptorq_article/commit/6e0b748912fc66c8121dd1c557eae006018abed4)

---

## Phase 1: Content Foundation (2026-02-09)

Three commits that built the article's editorial structure on top of the initial scaffold.

### "RaptorQ in the Wild" Section

- Added 136-line section covering real-world RaptorQ deployments — [`1d58753`](https://github.com/Dicklesworthstone/raptorq_article/commit/1d58753c1187db3b3ce90d596c21384591030bdc)
  - **Cellular standards**: 3G/4G MBMS (KT Korea PyeongChang 2018, Verizon go90), 5G Broadcast (connected car firmware, IoT fleet provisioning), ATSC 3.0 NextGen TV (WHUT-TV datacasting, New Mexico PBS)
  - **Author's projects**: asupersync (RFC 6330 implementation, distributed state recovery at 1.2x storage), FrankenSQLite (WAL self-healing, database-level FEC, fountain-coded snapshots), Flywheel Connectors (symbol-first mesh protocol over Tailscale)
  - Each project card with distinct color scheme (emerald/amber/sky), gradient backgrounds, GitHub links

### PAR Files Bridge Section

- Added "What You Already Know" section bridging PAR2 repair files and RAID 5 to fountain codes — [`77f1d9b`](https://github.com/Dicklesworthstone/raptorq_article/commit/77f1d9bf330064633781e7eed7e87d5445eeb3ab)
  - Explains why Reed-Solomon's fixed-rate and O(K^2) encoding motivate rateless codes
  - Includes expanded mathematical notation, LT -> Raptor -> RaptorQ progression with complexity/overhead comparisons
- Softened heading to "What You **May** Already Know" for inclusivity — [`3ac2f15`](https://github.com/Dicklesworthstone/raptorq_article/commit/3ac2f15473b496e7e0caf81c86e1cc3e76b284cd)

---

## Initial Commit (2026-02-09)

[`3925004`](https://github.com/Dicklesworthstone/raptorq_article/commit/3925004b1487b0df2a91320909cf482ffa8ee229) — Full project scaffold: 8,091 lines across 17 files.

### Article (`index.html`)

Single-page interactive article covering the full RaptorQ (RFC 6330) construction from first principles through inactivation decoding. Sections: Packets Are Equations, Coupon Collector's Tax, LT Codes & The Ripple, The Precode Trick, Intermediate Symbols, Peeling & Inactivation, Engineering Tricks, The Deep Math.

### Visualizations (`visualizations.js`)

Five interactive visualizations built with D3.js, Three.js, and GSAP:
1. GF(2) Matrix Rank Builder
2. Degree Distribution & Ripple simulator
3. Precode Repair animation
4. Toy Decode Walkthrough (K=4, step-by-step)
5. Peeling Cascade (bipartite graph)

Plus a Three.js particle-stream hero animation and GSAP scroll-triggered transitions.

### Python Demos

Three standalone pedagogical scripts (Python 3.8+, NumPy):
- `01_xor_encoding_decoding.py` — XOR encoding/decoding with Gaussian elimination (312 lines)
- `02_lt_code_simulation.py` — LT code simulation with Robust Soliton + belief propagation (510 lines)
- `03_raptorq_precoding.py` — RaptorQ-style precoding: LDPC precode + LT fountain layer (647 lines)

### Research Notes

Six research/planning documents (3,534 lines total):
- `raptorq_article_research.md` — Primary research notes (2,927 lines)
- `raptorq_fountain_codes_research.md` — Fountain code family survey
- `raptorq_math_foundations.md` — Mathematical foundations deep-dive
- `raptorq_shamir_connection.md` — Shamir's Secret Sharing parallels
- `raptorq_precoding_section.md` — Precoding section draft notes
- `raptorq_blog_sections.md` — Section planning notes
- `raptorq_conclusion.md` — Conclusion draft notes
- `lt_codes_section.md` — LT codes section draft notes

### Tooling

- `tools/scroll_perf_probe.mjs` — Scroll performance diagnostic (323 lines)
- `.gitignore`, `README.md`, `TODO.md`

---

## File Inventory

| File | Role | Primary Phase |
|------|------|---------------|
| `index.html` | Single-page article (HTML + Tailwind + MathJax) | Phase 1-3 |
| `visualizations.js` | All 5 interactive visualizations + hero | Phase 2-3 |
| `01_xor_encoding_decoding.py` | Python demo: XOR + Gaussian elimination | Initial |
| `02_lt_code_simulation.py` | Python demo: LT codes + Robust Soliton | Initial, Phase 4 |
| `03_raptorq_precoding.py` | Python demo: precode + fountain composition | Initial, Phase 4 |
| `tools/scroll_perf_probe.mjs` | Scroll performance diagnostic | Initial |
| `gh_og_share_image.png` | GitHub social preview (1280x640) | Phase 4 |
| `LICENSE` | MIT + OpenAI/Anthropic Rider | Phase 4 |
| `raptorq_article_research.md` | Primary research notes | Initial |
| `raptorq_math_foundations.md` | Mathematical foundations | Initial |
| `raptorq_fountain_codes_research.md` | Fountain code family survey | Initial |
| `raptorq_shamir_connection.md` | Shamir's Secret Sharing parallels | Initial |
| `raptorq_precoding_section.md` | Precoding section draft | Initial |
| `raptorq_blog_sections.md` | Section planning | Initial |
| `raptorq_conclusion.md` | Conclusion draft | Initial |
| `lt_codes_section.md` | LT codes section draft | Initial |

---

## Technology Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| Layout & styling | Tailwind CSS (CDN) | Dark-theme editorial design |
| Typography | Inter, Crimson Pro, JetBrains Mono | Headings, body, code |
| 3D animation | Three.js | Data-rain hero |
| Charts | D3.js v7 | Bar/line charts, bipartite graphs, force layouts |
| Scroll animation | GSAP + ScrollTrigger | Section transitions |
| Math rendering | MathJax 3 | LaTeX equations |
| Python demos | Python 3.8+ / NumPy | Pedagogical simulations |
