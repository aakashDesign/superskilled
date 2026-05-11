---
name: ux-writing
description: Use when writing or reviewing interface copy — button labels, form errors, empty states, onboarding, tooltips, confirmation dialogs, system notifications, marketing surfaces inside the product. Triggers on requests like "write copy for…", "what should this button say", "rewrite this error", "the empty state feels off", "make this less wordy", or when reviewing screens/mocks for tone and clarity.
---

# UX-writing

Interface copy is part of the interface. It should make the product feel obvious, honest, and human — not loud, clever, or apologetic.

## Operating principles

1. **Clarity over cleverness.** If a user has to re-read a sentence, the sentence is wrong. Wit is fine; ambiguity is not.
2. **Verb + object for actions.** Action labels describe what the user is doing to what: Save changes, Delete project, Copy key. Not Submission, not Save, not OK. Navigation items can stay nounal (Settings, Billing) — they describe a place, not an action.
3. **Specific over generic.** "Couldn't reach Stripe" beats "Something went wrong." Name the thing.
4. **Front-load meaning.** First two or three words carry the load. Users scan; they don't read.
5. **Don't apologize for the product working correctly.** "Sorry, you need to verify your email" — no, you don't. State the next step.

## The checklist

Before shipping any string, verify:

- [ ] **Length** — could half the words be removed without losing meaning?
- [ ] **Voice** — second person ("you"), active, present tense by default
- [ ] **Capitalization** — sentence case for everything except product names; consistent across the surface
- [ ] **Punctuation** — no periods on buttons, labels, or short single-line items; periods on full sentences
- [ ] **Specificity** — does this string tell the user what just happened or what to do next?
- [ ] **Tone fit** — would this sentence be at home in the rest of the product, or does it sound like a different writer?
- [ ] **Accessibility** — screen readers will read this; does it still make sense out loud?

## Patterns by surface

### Buttons & primary actions
A button is a promise about what happens next. The label should let the user predict the result without reading the surrounding context.
- Verb + object: `Create project`, `Invite teammate`, `Cancel subscription`.
- Avoid `Submit`, `OK`, `Yes` — they describe the form mechanic, not the user's intent.
- Destructive actions name the thing being destroyed: `Delete invoice`, not `Delete`.
- Users scan buttons, not titles. `Create` inside a "Create API Key" dialog forces the eye back up to remember what's being created; `Create key` doesn't.
- Pair commit and dismiss asymmetrically. The commit button is specific (`Save changes`, `Delete project`, `Send invite`). The dismiss button stays generic (`Cancel`, `Close`). Don't write `Don't save` or `Keep editing` unless the consequence of dismissal isn't obvious.
- Match the verb to the user's situation. `Go to X` for chosen navigation (empty states, settings, dialogs). `Back to X` for recovery from errors or dead ends (404 pages, broken flows). 
- A leading icon can repeat the label's meaning if it speeds up scanning (`+ New template`, `↑ Upload JSON`). Trailing arrows (`Go to Integration →`) signal navigation away. Use them for that, not for emphasis.

### Form errors
- Inline, next to the offending field, in the moment the user can fix it.
- Format: **what's wrong** → **how to fix**. "Password needs at least 8 characters" beats "Invalid password."
- Never blame the user. Replace "You entered an invalid email" with "That doesn't look like an email address."

### Empty states
- Three jobs: explain what lives here, show one concrete next step, hint at the value.
- Avoid stock illustrations carrying the meaning. The text should work alone.
- Bad: "No projects yet." Better: "You haven't started a project. Create one to begin tracking time."

### Confirmation dialogs
Confirmation dialogs have one job: make sure the user meant to do this. The copy pattern depends on what kind of action you're confirming. Use confirmation dialog only if the action is irreversible, like destructive action which cannot be undone, something is lost. Removing a user, permanently deleting an account, unlink a project.
- Title states the action as a question: `Remove John Smith?`
- Body names what's lost and when it takes effect: "They'll lose access to all projects and data in this workspace immediately."
- Confirm button repeats the verb and object: `Remove member`, not `OK` / `Yes`.
- Don't add "This cannot be undone" if the body already makes that clear. Say it once.

### System notifications & toasts
- Past tense for completion (`Invoice sent`), present-progressive for ongoing (`Uploading 3 files`).
- One sentence. If it needs two, it's not a toast — it's a screen.
- Always pair errors with a recovery path (`Undo', 'Restore`) or a "see details" affordance.


## Anti-patterns to flag on sight

- "Oops!", "Whoops!", "Uh oh!" — performative apology
- "Please" on every action — empty politeness; reserve for genuine asks
- "Click here" — link text should describe the destination
- "Are you sure?" with no specifics — what am I being un-sure about?
- "Successfully" — redundant; if the toast appeared, it succeeded
- "Invalid input" — name what's invalid
- Em-dash padding, exclamation marks, sparkles ✨ — usually a sign the copy is hiding weak meaning behind decoration
