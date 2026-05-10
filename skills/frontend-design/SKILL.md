---
name: frontend-design
description: Use when translating design intent into frontend code — building UI components, implementing screens from mocks/Figma, refactoring styling for consistency, setting up design tokens or theming, fixing layout/spacing/responsive issues, or improving the visual quality of an existing component. Triggers on requests like "build this component", "match this Figma", "make this look right", "set up our design tokens", "fix the spacing", "make this responsive", "this UI looks off".
---

# Frontend Design

Bridging design and code. The job is not "make pixels match" — it's to encode the design system so that the next ten components are consistent without anyone trying.

## Mental model

Every UI surface has four layers. Work them in order; skipping forward causes most of the bugs you'll spot later.

1. **Tokens** — colors, type scale, spacing scale, radii, shadows, motion. The vocabulary.
2. **Primitives** — Button, Input, Stack, Card, Icon. The grammar.
3. **Patterns** — Form, Dialog, Table, EmptyState. Sentences.
4. **Screens** — composed from patterns. Paragraphs.

A common failure mode is hand-styling at the screen layer. Each screen then owns its own version of every primitive, and "consistency" becomes a meeting topic instead of a property of the code.

## Tokens, concretely

A useful token set is small. If your scale has 14 grays, you do not have a scale — you have a palette of mistakes.

- **Color**: foreground, background, border, surface, accent, danger, warning, success — each with a small set of semantic variants (e.g. `fg`, `fg-muted`, `fg-subtle`). Avoid naming colors after the color (`blue-500`); name them after the role (`accent`).
- **Spacing**: a geometric scale (`4, 8, 12, 16, 24, 32, 48, 64`). No `13px`. No `padding: 7px 11px`.
- **Type**: 5–7 sizes max, with paired line-heights. Don't expose font-size without its line-height — they travel together.
- **Radii**: 3–4 values (`sm, md, lg, full`). Pick one for inputs and stick with it.
- **Shadow / elevation**: 3 levels is plenty. Each level should be perceptually distinct in the dark theme too.
- **Motion**: 2–3 durations (`fast, base, slow`) and 2 easings. Most "feel" bugs are motion bugs.

If the project doesn't have tokens, propose them before writing component code. One hour of token work saves a week of refactor.

## Spacing & layout

- **Use the scale.** If a value isn't on the scale, the design is wrong or the scale is wrong — fix one of them, don't sneak `margin: 13px` in.
- **Prefer gap over margin** for layout. Margin collapses, leaks, and fights flex. Gap composes.
- **One direction at a time.** A `Stack` (vertical gap) and an `Inline` (horizontal gap) primitive eliminates 80% of layout bugs.
- **Padding belongs to the container, gap belongs to the layout.** A button has padding; a list has gap.
- **Don't center with margins** when flex/grid will do it cleanly.

## Type

- Set line-height as a unitless multiplier (`1.5`), never in `px`.
- Headings tighter (`1.1–1.3`), body looser (`1.5–1.7`).
- `font-feature-settings` for tabular numbers in tables and dashboards — misaligned digits in a numeric column is a tell.
- One typeface is fine. Two is a choice. Three is a problem.

## Color & contrast

- All text/background pairs must meet WCAG AA (4.5:1 for body, 3:1 for large). Verify, don't eyeball.
- Don't rely on color alone to convey state. Pair with icon, label, or shape.
- Build the dark theme by inverting *roles*, not values. `bg` and `fg` swap; accents shift slightly to retain contrast.
- Disabled ≠ low-contrast normal. Disabled means non-interactive, and should look it without becoming unreadable.

## Components: the shape of a good primitive

A well-built primitive has these properties. Use them as a checklist when writing one:

- [ ] **Themeable** — colors, spacing, radii come from tokens, never hardcoded.
- [ ] **Composable** — accepts `children` or slots; doesn't dictate what goes inside.
- [ ] **Polymorphic where it matters** — a Button can render as `<a>` when given an `href`. Don't fork into `LinkButton`.
- [ ] **Stateful styles complete** — `:hover`, `:focus-visible`, `:active`, `:disabled`, loading. Every one. `focus-visible`, not `focus`.
- [ ] **Accessible by default** — correct semantic element, label, role, keyboard behavior. ARIA only when no native option exists.
- [ ] **Forwarded ref & rest props** — so consumers can attach refs, ids, event handlers without you predicting every use case.
- [ ] **No layout opinions baked in** — a Button shouldn't set `margin`. Let the parent layout decide.

## Responsive

- **Mobile-first as a default**, but design the content breakpoints, not device breakpoints. Add a breakpoint where the layout breaks, not at `768px` because that's a tablet.
- **Container queries over media queries** for components that live in varying contexts (a card in a sidebar vs. a card in a grid).
- **Touch targets ≥ 44×44px** on touch surfaces. This is non-negotiable.
- **Test the awkward sizes.** 360px wide, 1440px wide, 320px tall. Real users have weird windows.

## Motion

- Motion exists to explain change — where something came from, where it went, what's now in focus. If it doesn't explain, it distracts.
- 150–250ms for most UI transitions. Longer feels sluggish, shorter feels janky.
- Ease-out for things entering, ease-in for things leaving, ease-in-out for things moving in place.
- Honor `prefers-reduced-motion`. Don't disable motion entirely — replace transforms with opacity fades.

## Implementing from a mock

When given a Figma/screenshot, work in this order:

1. **Identify the tokens.** What colors, spacing values, type sizes are in use? Are they on the scale?
2. **Identify the primitives.** Buttons, inputs, cards — do they exist? Reuse before you create.
3. **Build the layout skeleton** with Stack/Grid before any styling. Get the structure right.
4. **Apply tokens.** No raw values yet.
5. **Add states.** Hover, focus, active, disabled, loading, empty, error.
6. **Test responsive & dark theme.** If the design didn't include them, that's a design conversation, not a guess.
7. **Verify accessibility.** Tab through it. Use a screen reader for one pass. Run axe.

## Quality bar before declaring done

- [ ] Renders correctly at 320px, 768px, 1280px, 1920px
- [ ] Renders correctly in dark theme (or explicitly N/A)
- [ ] All interactive elements reachable by Tab, in a sensible order
- [ ] All interactive elements have a visible `:focus-visible` style
- [ ] No layout shift on load (`CLS` budget ~0)
- [ ] No raw color/spacing/radius values — all token references
- [ ] No `!important` (or, if there is, a comment explaining the cascade fight you lost)
- [ ] Works with browser zoom at 200%
- [ ] Loading, empty, and error states exist and look intentional

## Anti-patterns to flag on sight

- Pixel values inline (`style={{ marginTop: 13 }}`)
- `text-gray-500` repeated 40 times across a codebase — that's a token waiting to be born
- `<div onClick>` for anything a user clicks — use a button
- Custom focus rings that are less visible than the browser default
- Animations longer than 400ms on routine UI
- "Just one more breakpoint" — every new breakpoint is a maintenance tax
- Z-index numbers like `9999`, `99999` — set up a z-index scale (`dropdown, sticky, modal, toast`) and move on
