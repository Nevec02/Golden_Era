# Golden Era Design System

> Target-state design reference for the Golden Era website. The system translates the editorial hierarchy, modular storytelling, and motion language observed on [Tonemaki](https://www.tonemaki.com/) into Golden Era's own gold-and-black identity. Tonemaki's copy, branding, illustrations, and media are reference material only and must not be reproduced.

## 1. Design direction

Golden Era should feel like a confident audiovisual studio: cinematic, experimental, precise, and premium. Every page should combine one oversized editorial idea with restrained supporting copy, high-impact media, and motion that helps tell the story.

Core principles:

1. **One dominant idea per viewport.** Each section has one unmistakable headline, visual, or interaction.
2. **Editorial scale over decoration.** Large typography and composition create impact; ornamental UI stays minimal.
3. **Darkness frames the work.** Near-black surfaces are the default canvas. Gold and warm cream guide attention.
4. **Media is content.** Video, stills, and motion work must feel integral to the layout, never like placeholders.
5. **Motion has narrative purpose.** Animation reveals hierarchy, connects sections, or demonstrates process.
6. **Contrast creates rhythm.** Alternate immersive dark sections with bright gold or warm-cream pauses.

### Reference-to-brand translation

| Observed reference pattern | Golden Era expression |
| --- | --- |
| Coral/orange oversized display type | Gold oversized display type |
| Warm-cream content surfaces | Pale-gold or cream surfaces |
| Neon-green primary CTA | Solid gold CTA with near-black text |
| Playful sushi/3D imagery | Cinematic production, motion, and abstract Golden Era imagery |
| Heavy condensed display face | `NewTitle` for impact; `Chillax` for readable headings |
| Long pinned storytelling sequences | Short, deliberate GSAP sequences tied to project and process narratives |

## 2. Foundations

### Color tokens

Use the existing gold scale as the brand spectrum. Semantic aliases should be preferred in components so the palette can evolve without component rewrites.

| Token | Value | Use |
| --- | --- | --- |
| `--color-bg` | `#0e0b02` | Default page background |
| `--color-surface` | `#171207` | Raised dark panels and cards |
| `--color-text` | `#ffffff` | Primary text on dark surfaces |
| `--color-text-soft` | `#faf1da` | Warm display text and secondary emphasis |
| `--color-text-muted` | `#b9b29f` | Supporting copy on dark surfaces |
| `--color-gold` | `#e0aa23` | Primary brand color and CTA fill |
| `--color-gold-light` | `#f0d491` | Hover, focus, and pale highlight |
| `--color-gold-dark` | `#977215` | Borders, inactive accents, depth |
| `--color-ink` | `#0e0b02` | Text and icons on gold/cream surfaces |
| `--color-danger` | `#c94b3c` | Errors only; never decorative |

Rules:

- Keep each section to one dominant background and one accent color.
- Use gold for emphasis, not for long paragraphs.
- Body copy must meet WCAG AA contrast against its surface.
- Gradients are allowed only to blend media into `--color-bg`; avoid decorative multicolor gradients.

### Typography

| Role | Font | Weight | Treatment |
| --- | --- | --- | --- |
| Impact display | `NewTitle`, `Chillax`, sans-serif | 100–400 | Uppercase, tight leading, used for short statements |
| Section heading | `Chillax`, `Inter`, sans-serif | 600–800 | Sentence case or controlled uppercase |
| Body/UI | `Inter`, `Segoe UI`, sans-serif | 400–600 | Clear, neutral, compact |
| Editorial accent | `Theonory`, serif | 400 | One short phrase or word; never long copy |

Recommended fluid scale, based on the existing `html { font-size: 62.5%; }` convention:

```css
--text-xs: clamp(1.2rem, 1.1rem + 0.15vw, 1.4rem);
--text-sm: clamp(1.4rem, 1.3rem + 0.2vw, 1.6rem);
--text-body: clamp(1.6rem, 1.45rem + 0.25vw, 1.9rem);
--text-lead: clamp(2rem, 1.6rem + 0.8vw, 3.2rem);
--text-h3: clamp(2.8rem, 2rem + 2vw, 5.6rem);
--text-h2: clamp(4rem, 2.4rem + 5vw, 10rem);
--text-display: clamp(6rem, 3rem + 10vw, 18rem);
```

- Impact display: line-height `0.82–0.92`, letter-spacing `-0.02em` to `-0.05em`.
- Section headings: line-height `0.95–1.05`, letter-spacing `-0.02em`.
- Body: line-height `1.45–1.65`, maximum line length `60–70ch`.
- Eyebrows and metadata: uppercase, `0.08em–0.14em` tracking.
- Do not simulate the reference site's letter-by-letter spacing with literal spaces in content. Use CSS and split text only when animation requires it.

### Spacing, grid, and shape

- Content maximum: `1440px`; full-bleed media may exceed it.
- Desktop gutters: `clamp(4rem, 5vw, 8rem)`.
- Tablet gutters: `3.2rem`.
- Mobile gutters: `1.6–2rem`.
- Section block spacing: `clamp(9.6rem, 14vw, 20rem)`.
- Internal section gap: `clamp(2.4rem, 5vw, 8rem)`.
- Use a 12-column desktop grid, 6-column tablet grid, and 4-column mobile grid.
- Default content radius: `2.4rem`; large gold panels may use `4–5rem`.
- CTA radius: fully rounded (`999px`). Media can be square, softly rounded, or clipped by a deliberate section shape.
- Borders are usually `1px solid` using gold at 35–60% visual intensity.

## 3. Layout and components

### Navigation

- Fixed above content with a transparent or near-black background and restrained blur.
- Desktop: brand mark left, primary routes centered/right, one high-priority contact action.
- Mobile: menu trigger remains visible; navigation opens as a full-height or near-full-height drawer.
- Current route and hover states use gold plus underline or directional motion. Never rely on color alone.
- The skip link must be the first focusable control.

### Hero

- Minimum height: `100svh`; allow `100dvh` only as progressive enhancement.
- One full-bleed showreel or cinematic background, darkened sufficiently for readable foreground content.
- Golden Era logo or a short two-line statement is the dominant element.
- Supporting copy is limited to one or two lines, followed by one primary CTA.
- Keep essential text inside the safe center area; video may crop at any breakpoint.
- Mobile removes nonessential background effects and uses a stable poster image when autoplay or bandwidth is constrained.

### Section-intro pattern

Use a consistent three-level hierarchy:

1. Small eyebrow that orients the visitor.
2. Oversized statement that carries the idea.
3. Short supporting paragraph or action.

Alignment may alternate between left, center, and split layouts, but the information order remains consistent.

### Buttons and links

- Primary: gold fill, ink text, minimum height `4.8rem`, horizontal padding `2.4–3.2rem`.
- Secondary: transparent, gold border/text on dark; ink border/text on light.
- Text link: inline arrow or underline with a visible focus state.
- Hover: small lift or scale (`1.02–1.04`) plus color shift; no dramatic bounce.
- Active: return toward the surface and reduce shadow.
- Focus-visible: `2px` gold-light outline with at least `3px` offset.
- Touch target: at least `44 × 44px`.

### Marquees and trust bands

- Use a horizontal band for project categories, clients, awards, or studio capabilities.
- Content must be duplicated only for seamless animation and the duplicate must be `aria-hidden`.
- Movement is slow and linear (`30–80s`) and pauses or becomes static under reduced-motion preferences.
- The band may switch to a light surface to create a strong transition between dark sections.

### Media and project cards

- Use real Golden Era work only. Never use Tonemaki's media or copy.
- Cards prioritize the visual; title, discipline, and year form a compact metadata row.
- Desktop may use asymmetric spans or horizontal storytelling. Mobile stacks cards in reading order.
- Videos use `muted`, `playsinline`, an intentional poster, and lazy loading when below the fold.
- Reserve aspect ratio before media loads to avoid layout shift.

### Process storytelling

- A short intro leads into the existing four process panels.
- On desktop, panels can pin for one viewport and transition as a controlled sequence.
- On mobile, default to a normal vertical flow unless pinning has been tested for touch scrolling and short screens.
- Each step needs a unique title, concise explanation, deliverables, and genuine project media.
- Alternating gold and dark panels create rhythm; text/icon colors must switch semantically with the surface.

### Footer/contact finale

- Treat the footer as the final campaign panel, not a utility afterthought.
- Lead with a large contact proposition and one primary CTA.
- Follow with route, social, legal, location, and copyright groups.
- The oversized Golden Era wordmark closes the composition.
- Mobile stacks groups with generous separation and preserves a clear focus order.

## 4. Motion system

Use CSS for simple transitions and marquees. Use GSAP/ScrollTrigger for sequencing, pinning, and scroll-linked effects already supported by the project.

### Motion vocabulary

| Pattern | Behavior |
| --- | --- |
| Page/hero reveal | Fade and rise `16–32px`; stagger text by line or word |
| Section reveal | Opacity plus small vertical translation as content enters |
| Media reveal | Clip-path or mask reveal; avoid simultaneous scale, blur, and rotation |
| Pinned process | One panel per viewport with deliberate crossfade/slide transition |
| Marquee | Continuous linear horizontal motion |
| Hover | `150–250ms` color, underline, or `1.02–1.04` scale |
| Route transition | Optional `300–500ms` fade/curtain using the gold surface |

Defaults:

- UI duration: `150–250ms`.
- Content reveal: `500–800ms`.
- Section transition: `800–1200ms` when scroll-controlled.
- Preferred ease: `power2.out` for entry, `power2.inOut` for state changes, `none` for marquees.
- Stagger: `40–80ms`; avoid long letter-by-letter waits.
- Never animate layout-critical `width`, `height`, `top`, or `left` when transform/opacity can achieve the effect.
- Respect `prefers-reduced-motion: reduce`: remove pinning, parallax, continuous transforms, and split-text reveals; show all content immediately.
- Animation cannot be required to discover content or understand navigation.

## 5. Responsive behavior

Use content-driven media queries, with these shared anchors:

| Range | Expected behavior |
| --- | --- |
| `>= 1280px` | Full editorial scale, 12-column compositions, optional pinned/horizontal stories |
| `1024–1279px` | Reduced display scale and gaps; keep split layouts when readable |
| `768–1023px` | Collapse complex grids, shorten pins, simplify overlapping media |
| `< 768px` | Four-column stack, drawer navigation, normal-flow process sections, 16–20px gutters |
| `< 480px` | Protect readable line breaks, compact CTAs, remove decorative duplicates |

Responsive rules:

- Never scale the desktop composition uniformly. Recompose it.
- Keep mobile body text at least `1.6rem` and controls at least `44px` high.
- Avoid horizontal scrolling except inside a clearly signaled carousel or marquee.
- Use `svh` for essential viewport-height layouts and test landscape mobile.
- Decorative video, high-density effects, and complex scroll scenes must have a lightweight fallback.

## 6. Current Astro component mapping

This document defines the target behavior; implementation may be incremental.

| Existing area | Target role |
| --- | --- |
| `src/layouts/Layout.astro` | Own global tokens, font roles, selection, base focus, spacing, and reduced-motion rules |
| `src/components/Nav.astro` | Fixed responsive navigation and accessible drawer |
| `src/components/atoms/Button.astro` | Primary, secondary, and text-link variants with shared states |
| `src/components/index/Hero.astro` | Cinematic hero with safe text/media composition and poster fallback |
| `AboutGolden.astro` | Marquee plus concise studio proposition |
| `Together.astro` | Three-column capability/value narrative that stacks on mobile |
| `GoldenTouch.astro` | Full-width editorial statement break |
| `OurProcess.astro` | Four-step pinned desktop story with normal-flow mobile fallback |
| `WorkNow.astro` | Contact finale leading into the footer |
| `src/components/Footer.astro` | Large conversion panel plus structured utility footer |

Shared visual rules should move toward global semantic tokens or reusable primitives rather than being independently redefined in every component.

## 7. Content, accessibility, and performance

- Keep interface and marketing copy in Spanish unless a route explicitly supports another locale.
- Fix mojibake such as `DISEÃ‘O`, `menÃº`, and `ContÃ¡ctanos`; all source files must remain UTF-8.
- Every image requires meaningful Spanish alt text unless it is decorative.
- Provide captions or transcripts for narrative video with spoken content.
- Preserve semantic heading order even when visual sizes differ.
- Menus, accordions, and carousels must work with keyboard and screen readers.
- Do not hide meaningful content solely inside hover states.
- Prefer AVIF/WebP images and WebM/MP4 video fallbacks; size media for its rendered use.
- Lazy-load below-the-fold media and avoid initializing every motion scene at page load.
- Target stable layout, responsive interactions, and a smooth experience on mid-range mobile hardware—not just high-end desktop devices.

## 8. Definition of done

A page follows this system when:

- It clearly uses Golden Era's palette, fonts, logo, voice, and original media.
- Every section has a dominant idea and follows the shared spacing/grid rules.
- Desktop and mobile are intentionally composed, not merely scaled versions of each other.
- Buttons, navigation, cards, process panels, and the footer use consistent states and tokens.
- Motion strengthens hierarchy, has a reduced-motion fallback, and does not block access to content.
- Text and interactive controls meet contrast, focus, semantics, and touch-target requirements.
- No Tonemaki-owned copy, logos, or media have been copied into the implementation.

---

Reference inspected: `https://www.tonemaki.com/` on 2026-08-01 at desktop (`1280 × 720`) and mobile (`390 × 844`) viewports. The live reference may change; this file is the source of truth for Golden Era.
