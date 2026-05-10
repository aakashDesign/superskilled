---
name: ux-copywriting
description: Use when writing or reviewing interface copy — button labels, form errors, empty states, onboarding, tooltips, confirmation dialogs, system notifications, marketing surfaces inside the product. Triggers on requests like "write copy for…", "what should this button say", "rewrite this error", "the empty state feels off", "make this less wordy", or when reviewing screens/mocks for tone and clarity.
---

# UX Copywriting

Interface copy is part of the interface. It should make the product feel obvious, honest, and human — not loud, clever, or apologetic.

## Operating principles

1. **Clarity over cleverness.** If a user has to re-read a sentence, the sentence is wrong. Wit is fine; ambiguity is not.
2. **Verbs over nouns.** Buttons describe an action the user is taking ("Save changes", "Delete project"), not a category ("Submission", "Deletion").
3. **Specific over generic.** "Couldn't reach Stripe" beats "Something went wrong." Name the thing.
4. **User's words, not yours.** Don't make the user learn your data model. Say "team" if they say team, even if the table is called `organizations`.
5. **Front-load meaning.** First two or three words carry the load. Users scan; they don't read.
6. **Don't apologize for the product working correctly.** "Sorry, you need to verify your email" — no, you don't. State the next step.

## The checklist

Before shipping any string, verify:

- [ ] **Length** — could half the words be removed without losing meaning?
- [ ] **Voice** — second person ("you"), active, present tense by default
- [ ] **Capitalization** — sentence case for everything except product names; consistent across the surface
- [ ] **Punctuation** — no periods on buttons, labels, or short single-line items; periods on full sentences
- [ ] **Specificity** — does this string tell the user what just happened or what to do next?
- [ ] **Tone fit** — would this sentence be at home in the rest of the product, or does it sound like a different writer?
- [ ] **Localization risk** — no idioms, no puns that depend on English, no hardcoded plurals (`1 items`)
- [ ] **Accessibility** — screen readers will read this; does it still make sense out loud?

## Patterns by surface

### Buttons & primary actions
- Verb + object: `Create project`, `Invite teammate`, `Cancel subscription`.
- Avoid `Submit`, `OK`, `Yes` — they describe the form mechanic, not the user's intent.
- Destructive actions name the thing being destroyed: `Delete invoice`, not `Delete`.

### Form errors
- Inline, next to the offending field, in the moment the user can fix it.
- Format: **what's wrong** → **how to fix**. "Password needs at least 8 characters" beats "Invalid password."
- Never blame the user. Replace "You entered an invalid email" with "That doesn't look like an email address."

### Empty states
- Three jobs: explain what lives here, show one concrete next step, hint at the value.
- Avoid stock illustrations carrying the meaning. The text should work alone.
- Bad: "No projects yet." Better: "You haven't started a project. Create one to begin tracking time."

### Confirmation dialogs (destructive)
- Title states the action as a question or fact, not a warning. `Delete this project?`
- Body names the consequences and what survives. ("All 12 tasks will be permanently deleted. Time entries will be kept.")
- Confirm button repeats the verb: `Delete project`, not `OK` / `Yes`.

### Loading & progress
- If under ~1s: nothing. A spinner that flashes is worse than no spinner.
- 1–10s: indeterminate spinner with a label naming the work. ("Importing your CSV…")
- 10s+: progress, what's happening, ability to leave and come back.

### System notifications & toasts
- Past tense for completion (`Invoice sent`), present-progressive for ongoing (`Uploading 3 files`).
- One sentence. If it needs two, it's not a toast — it's a screen.
- Always pair errors with a recovery path or a "see details" affordance.

### Onboarding
- One thought per screen. Don't stack three benefits on one slide.
- Show the product, don't describe it. "Here's where you'll see your projects" + a real screenshot beats a paragraph of features.

## Tone calibration

When stuck, place the string on this spectrum and ask: does it match the rest of the product?

```
playful  ──  warm  ──  neutral  ──  formal  ──  clinical
```

A banking app sliding into "Whoops! 🙈" feels off. A hobby app saying "Operation could not be completed" feels off in the other direction. Tone is consistency, not personality.

## Review pattern

When asked to review existing copy, return:

1. **The string as-is**
2. **What's wrong** (in one phrase — clarity, tone, length, voice, etc.)
3. **One rewrite** (not three options unless explicitly asked)
4. **Why it's better** (one line)

Example:

> **Before:** "Oops! It looks like something might have gone wrong on our end. Please try again later."
> **Issue:** Apologetic, vague, no recovery.
> **After:** "We couldn't load your projects. Retry"
> **Why:** Names what failed, offers the next action as a button.

## Anti-patterns to flag on sight

- "Oops!", "Whoops!", "Uh oh!" — performative apology
- "Please" on every action — empty politeness; reserve for genuine asks
- "Click here" — link text should describe the destination
- "Are you sure?" with no specifics — what am I being un-sure about?
- "Successfully" — redundant; if the toast appeared, it succeeded
- "Invalid input" — name what's invalid
- Em-dash padding, exclamation marks, sparkles ✨ — usually a sign the copy is hiding weak meaning behind decoration
