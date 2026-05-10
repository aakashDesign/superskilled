---
name: ux-audit
description: Use when auditing or critiquing an existing UI — a screen, flow, component, or whole product — for usability, accessibility, and design quality. Triggers on requests like "review this screen", "what's wrong with this flow", "do a UX audit", "is this accessible", "critique this design", "find the issues with this onboarding", or when given a screenshot/URL/Figma and asked for feedback. Distinct from frontend-design (which builds) and ux-copywriting (which writes strings) — this skill diagnoses.
---

# UX Audit

The job is to look at an existing experience and report what's wrong, why it's wrong, and how serious it is — in a way the team can act on.

A good audit is not a list of opinions. It is a structured pass through known heuristics, prioritized by user impact, with each finding tied to a specific element and a concrete fix.

## How to run an audit

1. **Establish the user and the goal.** Who is using this, and what are they trying to accomplish? Most "design problems" are actually goal-mismatch problems. If the goal is unclear, ask before auditing.
2. **Walk the flow once without judging.** Note where you hesitated, re-read, or had to guess. Hesitation is data.
3. **Walk it again against the heuristics below.** This time, name what you see.
4. **Prioritize.** Not all findings are equal — sort by severity.
5. **Write it up.** One finding per item, in the format below. Don't bury three issues in one paragraph.

## The heuristic pass

Run through these in order. Each is a separate lens — don't blend them.

### 1. Nielsen's 10 (still works)
- **Visibility of system status** — does the user know what's happening, and what just happened?
- **Match with the real world** — does the language match how users think about this domain?
- **User control & freedom** — can the user undo, cancel, go back? Are escape hatches obvious?
- **Consistency & standards** — does the same thing look the same across the product? Does it follow platform conventions?
- **Error prevention** — is the system designed to avoid errors, or does it just handle them after?
- **Recognition over recall** — does the user have to remember things between screens?
- **Flexibility & efficiency** — are there shortcuts for power users without crowding the novice path?
- **Aesthetic & minimalist design** — is every element earning its place?
- **Help users recognize, diagnose, and recover from errors** — when things break, is the path forward obvious?
- **Help & documentation** — when help is needed, is it findable and contextual?

### 2. Information hierarchy
- What's the first thing the eye lands on? Is that the right thing?
- What's the primary action? Is there exactly one per screen, and is it visually unambiguous?
- Is anything important hidden below the fold or behind a click that shouldn't be?
- Is anything *un*important loud enough to compete with what matters?

### 3. Flow & friction
- How many steps from intent to completion? Is each step earning its existence?
- Where does the user have to provide information the system already has?
- Where does the user wait, and is that wait acknowledged?
- Where does the user have to make a decision they don't have context to make?

### 4. Accessibility (the non-negotiable layer)
- **Keyboard** — can every action be performed without a mouse? Is focus order logical? Is `:focus-visible` visible?
- **Contrast** — text/background pairs at WCAG AA (4.5:1 body, 3:1 large)? Verified, not eyeballed.
- **Screen reader** — do interactive elements have accessible names? Are images meaningfully alt-texted (or `alt=""` if decorative)?
- **Touch targets** — interactive elements ≥ 44×44px on touch surfaces?
- **Motion** — is `prefers-reduced-motion` honored?
- **Color alone** — is any state conveyed by color only, with no icon/label/shape?
- **Form labels** — every input has a visible, programmatically associated label (not just a placeholder)?
- **Zoom** — does it work at 200% browser zoom?

### 5. Copy
(Defer to the `ux-copywriting` skill for detailed rewrites, but flag at audit time.)
- Buttons named for actions, not mechanics?
- Errors specific and actionable?
- Empty states doing real work?
- Tone consistent across surfaces?

### 6. Trust & honesty
- Are there dark patterns? Pre-checked consent, hidden costs, fake urgency, confirmshaming, sneaking into baskets, hard-to-find unsubscribe?
- Is the user told what will happen before it happens — especially for destructive, paid, or shared-with-others actions?
- Is the privacy posture obvious, or buried?

### 7. Performance perception
- Skeleton screens or spinners where loads exceed ~300ms?
- Optimistic UI for actions that almost always succeed?
- Layout shift on load? (Things jumping after first paint is a UX issue, not just a perf one.)

## Severity levels

Tag every finding. Without severity, the team can't prioritize and the audit becomes wallpaper.

- **P0 — Blocker.** Users cannot complete the core task, or the product is inaccessible to a class of users (e.g. keyboard-only, screen reader). Fix before ship.
- **P1 — Major friction.** Users complete the task but with confusion, error, or drop-off. Fix this sprint.
- **P2 — Polish.** Inconsistencies, minor copy issues, visual nits. Fix as you touch the surface.
- **P3 — Opportunity.** Not broken, but a missed chance to delight or differentiate. Backlog.

## Finding format

Every finding should fit this template:

```
[P{0–3}] {short title}
Where: {specific element / screen / step}
What: {what the user experiences}
Why it matters: {what breaks for the user, ideally tied to a heuristic}
Suggested fix: {one concrete change, not three options}
```

Example:

```
[P1] Primary action competes with secondary
Where: Project settings → Delete project dialog
What: The "Cancel" button is filled and blue; "Delete" is a ghost link in red text.
Why it matters: Visual weight points the user toward Cancel, but that's the safe action by default — the styling is fighting the safety it's meant to provide. Worse, the destructive action looks like a hyperlink.
Suggested fix: Cancel as a ghost/text button, Delete as a filled button in the danger color. The visual hierarchy should match the consequence, not invert it.
```

## Output structure

When asked for an audit, return findings in this order:

1. **Summary** — 2–3 sentences naming the top 1–2 issues and overall posture.
2. **P0 findings** — listed using the format above.
3. **P1 findings**
4. **P2 findings**
5. **P3 findings** (optional; only if there's signal)
6. **What's working** — 2–4 things to keep. Audits without positives are demoralizing and miss the point: design is also about preserving what's good.

Aim for ~5–15 findings total for a single screen audit, ~15–40 for a flow. More than that and the team can't act on it; less and you probably haven't looked hard enough.

## Things that are not the audit's job

- **Don't redesign.** Suggest the smallest change that fixes the issue. Redesigns are a separate engagement.
- **Don't argue brand or strategy.** If the brief says "we want this to feel premium," audit *against* that brief, not against your taste.
- **Don't gold-plate.** Polish (P2) findings are real but should not crowd the P0/P1 list. A 40-item polish list with no P0s usually means the auditor avoided the hard problems.

## Anti-patterns to call out on sight

- Modal stacking — a modal that opens another modal
- Two primary buttons on one screen
- Disabled buttons with no explanation of why
- Forms that lose user input on validation error
- Destructive actions without confirmation, or with confirmation that doesn't name the consequence
- Critical functionality behind hover-only interaction (broken on touch)
- Infinite scroll on content the user needs to navigate back to
- Toast notifications for errors the user must act on (use inline, not transient)
- "Coming soon" labels on shipped UI
- Placeholder text doing the job of a label
