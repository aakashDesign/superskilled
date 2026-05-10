---
name: ux-copywriting
description: Use when writing or reviewing interface copy — button labels, form errors, empty states, onboarding, tooltips, confirmation dialogs, system notifications, marketing surfaces inside the product. Triggers on requests like "write copy for…", "what should this button say", "rewrite this error", "the empty state feels off", "make this less wordy", or when reviewing screens/mocks for tone and clarity.
---

# UX Copywriting

Interface copy is part of the interface. It should make the product feel obvious, honest, and human — not loud, clever, or apologetic.

## Tone and voice

- Direct, not blunt. Warm, not friendly.
- Never apologetic, never cheerful.
- Address the user as "you". Refer to the product by name when relevant, not as "we" or "the system".
- No exclamation marks. No filler words (just, simply, easily, quickly).
- Sentence case everywhere. Proper nouns are always capitalised.
- Never use passive voice if active is possible.

## Operating principles

1. **Clarity over cleverness.** If a user has to re-read a sentence, the sentence is wrong. 
   Wit is fine; ambiguity is not.
2. **Verbs over nouns.** Buttons, CTAs, and nav labels describe an action 
   ("Save changes", "Delete project"), not a category ("Submission", "Settings").
3. **Name the thing.** "Couldn't reach Stripe" beats "Something went wrong." 
   Specific error sources, specific items, specific consequences.
4. **User's words, not yours.** Don't make the user learn your data model. 
   Say "team" if they say team, even if the table is called `organizations`.
5. **Front-load meaning.** First two or three words carry the load. Users scan; they don't read.
6. **When in doubt, cut.** No copy is better than copy that states the obvious. 
   If removing a line doesn't change what the user understands, remove it.
7. **Don't apologize for the product working correctly.** "You need to verify your email" — 
   not "Sorry, you need to verify your email." State the situation, not your feelings about it.

## The checklist

Before shipping any string, verify:

- [ ] **Length** — could half the words be removed without losing meaning?
- [ ] **Person** — is it second person ("you"), not first ("we") or third ("the user")?
- [ ] **Voice** — active and present tense? ("Settings saved", not "Your settings have been saved")
- [ ] **Capitalization** — sentence case throughout; proper nouns and product names only
- [ ] **Punctuation** — no periods on buttons, labels, or short single-line items; periods on full sentences
- [ ] **Specificity** — does the string name the thing? (item, action, error source — not "something", "this", "it")
- [ ] **Headline vs. body** — does the body add new information, or does it restate the headline?
- [ ] **State fit** — is this written for this specific state, or borrowed from another context?
- [ ] **Tone fit** — would this sentence be at home in the rest of the product, or does it sound like a different writer?
- [ ] **Localization risk** — no idioms, no English-dependent wordplay, no hardcoded plurals (`1 items`)
- [ ] **Accessibility** — does every interactive element have a text label? Does the string make sense without surrounding visual context?

## Structure rules (all states)

Headline = situation or value prop. Never a command or instruction.
Body = one new piece of information. Never restate the headline.
CTA = specific action, not a generic label.

Do not use: "Get started", "Learn more", "Click here", "No [thing] yet".

## Zero state

Zero state = the user has never done this action. The feature exists but has no content yet. Focus on possibility, not absence.

Formula:
- Headline: what this feature gives the user (outcome or value), stated as fact
- Body: one concrete detail about how it works or what to expect
- CTA: the first action that gets them there

Example:
✓ "Tasks give your team a single place to track work"
  "Create a task to assign it, set a due date, and track progress."
  [+ New task]

✗ "No tasks yet"
  "You haven't created any tasks."
  [Create your first task]

## Empty state

Empty state = the user has been here before, but the list or view is currently empty due to filters, search, or cleared content. Focus on why nothing is showing, not on onboarding.

Formula:
- Headline: name the reason nothing is showing
- Body: how to fix it or what to try instead (one sentence)
- CTA: only include if there is a clear recovery action

Example:
✓ "No tasks match this filter"
  "Try removing a label or changing the date range."
  [Clear filters]

✗ "Nothing here"
  "Try adjusting your search."

## Error state

Error state = something went wrong, a page is missing, or the user lacks permission. Focus on clarity and next step.

Formula:
- Headline: name the situation plainly, not the technical cause
- Body: one sentence — what happened or what it means. If there is a clear action, state it. If not, omit the body.
- CTA: only if there is a meaningful recovery action

Do not use: "Oops", "Uh oh", "Something went wrong" (be specific), "Please try again" (only if retrying actually helps)

Examples:
✓ "Task not found" — "This task doesn't exist or may have been moved."
✓ "You don't have access to this page" — "This page is only available to admins."
✓ "404" — "This page doesn't exist or may have been moved." [Go to home]

Validation errors:
- State the constraint, not just the violation
- Keep it one sentence, no period needed for short inline errors
- ✓ "Must be 3 characters or fewer"
- ✗ "Must be 3 characters or fewer. You entered 4."


## Patterns by surface

### Buttons & primary actions
- Verb + object: `Create project`, `Invite teammate`, `Cancel subscription`.
- Avoid `Submit`, `OK`, `Yes` — they describe the form mechanic, not the user's intent.
- Destructive actions name the thing being destroyed: `Delete invoice`, not `Delete`.

### Form errors
- Inline, next to the offending field, in the moment the user can fix it.
- Format: **what's wrong** → **how to fix**. "Password needs at least 8 characters" beats "Invalid password."
- Never blame the user. Replace "You entered an invalid email" with "That doesn't look like an email address."

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


## Anti-patterns to flag on sight

- "Oops!", "Whoops!", "Uh oh!" — performative apology
- "Please" on every action — empty politeness; reserve for genuine asks
- "Click here" — link text should describe the destination
- "Are you sure?" with no specifics — what am I being un-sure about?
- "Successfully" — redundant; if the toast appeared, it succeeded
- "Invalid input" — name what's invalid
- Em-dash padding, exclamation marks, sparkles ✨ — usually a sign the copy is hiding weak meaning behind decoration
