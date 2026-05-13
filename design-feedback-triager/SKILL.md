---
name: design-feedback-triager
description: >
  Use this skill whenever a designer receives feedback on their work and needs help
  interpreting it before deciding what to do next. Trigger when a user shares stakeholder
  or reviewer comments, when they're stuck after a review session and don't know what to change.
  This skill is especially useful for designers working in mid-to-large companies who
  need to manage multiple stakeholders and navigate approvals.
---

# Design Feedback triager

Helps designers decode stakeholder and reviewer feedback before acting on it. The default
instinct — especially for early career designers — is to treat all feedback as a design
problem and go back to Figma. This skill breaks that reflex by diagnosing *what kind of
problem the feedback actually represents* before recommending a response.

---

## Step 1: Gather Context

Before diagnosing anything, collect the following inputs from the designer. Ask for all
of them upfront in a single message — don't drip questions one at a time.

**Required inputs:**

1. **The feedback** — exact words if possible, paraphrased if not
2. **Designer's goal for this review** — one of:
   - *Buy-in* — presenting a new concept or direction, seeking alignment on approach
   - *Sign-off* — presenting a near-final design, seeking approval to ship or move forward
3. **Who gave the feedback** — their role and their relationship to the project (decision
   maker, influencer, consulted, informed)
4. **Is this person the final decision maker?** — if not, who is, and were they in the room?
5. **What was presented and how** — static mockups, clickable prototype, live walkthrough,
   async Loom, etc.
6. **Was the feedback solicited or spontaneous** — did you ask for it, or did it come
   unprompted?
7. **Which round of feedback is this** — first time seeing it, or a revision cycle?

If the designer can't answer some of these, proceed with what's available and flag the
gaps in your output.

---

## Step 2: Triage the Feedback

Before suggesting any action, categorize the feedback using the triage system below.
A single piece of feedback can fall into more than one category — flag all that apply.

### The Four Categories

**1. Design Problem**
The feedback points to something in the UI that is genuinely unclear, broken, inconsistent,
or misaligned with user needs. This is the only category where going back to Figma is the
right first move.

*Signals:* Specific, observable, reproducible. "I couldn't find the save button." "The
steps feel out of order." "This label doesn't tell me what happens next."

**2. Communication Problem**
The design may be sound, but it wasn't presented in a way that built confidence. The
reviewer couldn't picture it working, didn't understand the rationale, or needed more
context to evaluate it fairly.

*Signals:* Vague or emotional language. "It doesn't feel right." "I'm not sure about
this." Feedback that disappears when you walk someone through it verbally. Common on
static mockups or async reviews.

**3. Organizational Problem**
The feedback is driven by territory, risk aversion, seniority performance, or departmental
priorities — not by the design itself. This cannot be fixed in Figma.

*Signals:* Feedback from a stakeholder who wasn't in scope but inserted themselves. "Legal
will never approve this." "My team won't be comfortable with that." A senior person saying
something critical in a room full of peers. Feedback that contradicts earlier alignment.

**4. Upstream Misalignment**
The design solved the wrong problem, or there are conflicting definitions of the goal
among stakeholders. No amount of iteration will resolve this — the brief needs revisiting.

*Signals:* Contradictory feedback from different reviewers. Feedback that questions the
fundamental premise ("why are we doing it this way?"). Scope creep disguised as feedback.
Feeling like the goalposts have moved.

---

## Step 3: Identify the Archetype

After categorizing, match the feedback to one of the named archetypes below. These
patterns repeat across organizations. Naming them helps the designer respond without
taking it personally or acting on it incorrectly.

### The Archetypes

**"Make It Pop"**
Category: Communication Problem
The reviewer is reacting emotionally to something they can't articulate. Usually means
the design feels low-confidence or unpolished in presentation, not that it's actually
broken.
→ Don't redesign. Ask what success looks like to them. Show the rationale behind the
current direction.

**"Can We Simplify This?"**
Category: Design Problem or Communication Problem — diagnose carefully
Often means "I'm overwhelmed" which is a hierarchy or information architecture issue.
But it can also mean the reviewer didn't understand the flow because it wasn't presented
well.
→ First ask: did they see a prototype or a static screen? If static, try walking them
through it before making changes.

**"It Doesn't Feel Like Us"**
Category: Communication Problem or Organizational Problem
Either the design genuinely departs from brand/product norms (design problem), or a
stakeholder is protecting perceived ownership of the product's identity.
→ Ask for a specific example of what "us" looks like to them. If they can't give one,
it's organizational.

**"Legal / Compliance Won't Like This"**
Category: Organizational Problem
Risk aversion dressed as feedback. May or may not reflect an actual constraint — often
the reviewer is pre-emptively protecting themselves from blame.
→ Don't redesign. Ask them to loop in the relevant team directly so you can get a
specific constraint to design against.

**"My Manager Won't Approve This"**
Category: Organizational Problem
Proxy opinion. The actual decision maker isn't in the room, and the reviewer is
anticipating their reaction — sometimes accurately, often not.
→ Get the decision maker in the room. Don't iterate based on speculation.

**"Can It Look More Like [Competitor]?"**
Category: Communication Problem
Usually means "I want this to feel as credible and polished as that product," not that
the design should literally copy it.
→ Identify what quality signal they're responding to (confidence, density, simplicity)
and address that specifically.

**"This Isn't What We Discussed"**
Category: Upstream Misalignment
Either the brief wasn't clear, the design drifted, or the reviewer's memory of the
brief is different from yours.
→ Go back to documented alignment artifacts (brief, prior sign-off, meeting notes)
before touching the design.

**The Room Opinion**
Category: Organizational Problem
A senior stakeholder says something critical primarily to demonstrate engagement. Others
in the room nod along even if they privately disagree.
→ Follow up 1:1. Room opinions often evaporate in direct conversation. Don't treat
group reactions as consensus.

---

## Step 4: Output Format

For each piece of feedback, produce the following. Keep it tight — three to five lines
per feedback item maximum.

```
FEEDBACK: [what they said]

CATEGORY: [Design / Communication / Organizational / Upstream — can be multiple]

ARCHETYPE: [name of the pattern, if it matches one]

DIAGNOSIS: [one to two sentences on what's actually happening]

RECOMMENDED MOVE: [specific next action — and importantly, whether or not it involves
opening Figma]
```

If the context inputs reveal gaps (e.g. decision maker wasn't in the room, first time
seeing it, async review), flag these as **Context Flags** at the top of the output.
These often explain more than the feedback itself.

---

## Guiding Principles

- **Not all feedback is design feedback.** Treat Figma as a last resort, not a first
  response.
- **The person speaking is not always the person who matters.** Always establish who
  the real decision maker is before deciding what to do.
- **Solicited feedback is more reliable than spontaneous feedback.** Weight it
  accordingly.
- **First impressions carry emotional noise.** Revision-round feedback is more
  calibrated but carries baggage. Account for both.
- **The goal of buy-in reviews is to not get blocked.** The goal of sign-off reviews
  is to get a clear yes. These require different responses to the same feedback.
- **Naming the pattern disarms it.** When a designer can say "this is a Room Opinion"
  they stop internalizing it as a personal failure and start treating it as a navigation
  problem.