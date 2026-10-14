---
name: eli5
description: >-
  Three-level plain-English explainer for when a user says "eli5," "ELI5," "pls eli5," "explain like I'm five," "explain like im five," "explain like I'm 5," "explain like im 5," "explain this simply," or asks to make a concept easier to understand. Always starts with three short levels: ELI5, Freshman, and adaptive Level 3 (Entry-Level CPA, Entry-Level Business, or College Grad). Then the user can reply 1, 2, or 3 to go deeper at that level, say "html" or "visual" for a simple one-page visual HTML of the idea, or "both" for a level plus the visual. Do NOT use this skill for authoritative GAAP/GAAS citations or conclusions, workpaper documentation, email drafting, voice-specific rewriting, or document/workpaper review.
metadata:
  author: Public adaptation
  version: "1.0.0-public"
  category: explanation
  updated: "2026-10-14"
  audited: "2026-10-14"
---

# ELI5

## Purpose

Explain one thing in plain English using a short three-level ladder. The first answer helps the reader choose the right altitude. Follow-up answers go deeper at the selected level without drifting into a different teaching style, or deliver a simple one-page visual HTML of the same idea when asked.

Read `references/style-guide.md` once per conversation for lightweight style context. Read `references/eli5-ladder.md` before answering. Read `references/example-output.md` when you need format calibration, especially for `1`, `2`, or `3` follow-ups. Read `references/eli5-visual-template.md` before building any visual HTML.

## Inputs and Outputs

**Required input:** one topic to explain, either stated by the user or inferable from recent context or pasted material.

**Optional inputs:** selected level (`1`, `2`, or `3`), a visual request (`html`, `visual`, `both`, or a combined reply like `2 and html`), a short command (`go deeper`, `simpler`, `examples`, `all three`, `reset`), target depth (`V=1` through `V=10`), or source text to explain.

**Output:** chat-only plain-English explanation by default. When the user replies `html`, `visual`, or `both`, also produce one self-contained visual HTML file built to `references/eli5-visual-template.md`. Do not create any other file unless the user separately asks for one.

## Default Behavior

- Infer the topic from the recent conversation or pasted material.
- If the topic is still unclear, ask one short question: "What do you want me to explain?"
- Default to all three levels every time `eli5` is invoked.
- Keep the first response compact so it is a ladder, not a lecture.
- End the first response with: `Reply 1, 2, or 3 to go deeper, "html" for a simple visual, or "both" for a level plus the visual.`
- Use small words, concrete examples, and direct sentences.
- Avoid jargon. If a term is needed, define it immediately.
- Do not add filler disclaimers like "this is a simplification." The skill is supposed to simplify.

## Output Modes

Use these exact headers:

```markdown
**1. ELI5**
[Actual child-simple explanation. Usually 2-4 short sentences.]

**2. Freshman**
[8th or 9th grade explanation. Usually 3-5 short sentences.]

**3. Entry-Level CPA** / **3. Entry-Level Business** / **3. College Grad**
[Topic-aware adult beginner explanation. Usually 4-7 sentences or tight bullets.]

Reply 1, 2, or 3 to go deeper, "html" for a simple visual, or "both" for a level plus the visual.
```

Use the Level 3 label rules in `references/eli5-ladder.md`.

## Follow-Up Behavior

Use `references/eli5-ladder.md` as the source of truth for `1`, `2`, `3`, `go deeper`, `simpler`, `examples`, `all three`, `reset`, and `test me` follow-ups.

## Visual HTML Mode

Triggered by `html`, `visual`, `both`, or a combined reply like `2 and html`. Rules:

- `html` or `visual`: build only the visual HTML. Skip the chat deep-dive entirely.
- `both`: deliver the deeper chat answer at the selected level, then the visual HTML. If no level is chosen yet, ask which level first. This is the only case where a follow-up question is allowed before building.
- A combined reply (`2 and html`) names the level, so build both with no follow-up question.
- The HTML is always pinned to ELI5-simple content, regardless of which chat level is in play. It is a fresh pass, never a re-render of the chat Level 1 text. The top half is a roughly 10-second glance; the whole thing fills one page, never more.
- Build to the locked template in `references/eli5-visual-template.md`: top half is headline phrase, one simple visual, 3-4 short callouts, and one "why it matters" line; bottom half is The story, Don't confuse it with, and Where you'll see it.
- Fully self-contained HTML (inline CSS and SVG, no external assets). Name the file `eli5-<topic-slug>.html`. It is a one-off deliverable for that session; do not archive or version it.
- The professional guardrails below apply to the visual exactly as they apply to chat text: the visual explains the concept and never presents an authoritative conclusion.

## Professional Guardrails

- If the explanation could affect GAAP, GAAS, SSARS, PCAOB, ERISA, EBITDA, working capital, tax, legal, audit evidence, or financial reporting conclusions, explain the concept but do not pretend to reach a sourced conclusion.
- For authoritative accounting or auditing treatment, exact citations, required accounting conclusions, or "what should we do under GAAP/GAAS," use an appropriate source-based review.
- For an internal workpaper note, use the appropriate workpaper-documentation workflow.
- For a review comment, use the appropriate review-comment workflow.
- For an email, use the appropriate approved email-drafting workflow.
- For voice-specific rewriting, use the appropriate voice-writing workflow.

## Style Rules

- Lead with the point.
- Prefer analogies over definitions when the topic is abstract.
- Use short paragraphs and one idea per paragraph.
- Keep the tone plain, calm, and useful. Do not talk down to the reader.
- Preserve important numbers, thresholds, dates, and facts. Do not invent missing facts.
- Avoid em dashes and semicolons.
- If the user sets `V=1` through `V=10`, adjust depth while preserving the selected ladder level.

## Edge Cases

- **Pasted dense text with no request:** explain the main idea and the part most likely to matter to the reader.
- **Multiple concepts at once:** explain the relationship first, then the two or three key pieces. If there are more than three, ask which one the user wants first.
- **Bad premise:** correct it plainly before explaining. Do not build an analogy around a false idea.
- **Topic requires current facts:** say if the concept is stable but the current fact needs verification.
- **User asks for "even simpler":** shorten and make the analogy more concrete. Do not merely repeat the same answer.
- **User asks to be tested:** ask 2-3 simple check-for-understanding questions at the sticky level. Do not turn every answer into a quiz by default.
- **Reference file cannot load:** continue from `SKILL.md`, state the limitation briefly if it affects the answer, and do not invent user-specific preferences from memory.

## Pre-Output Check

Before answering, confirm:

- The topic is clear or you asked one short question.
- The response uses the default three-level ladder unless the user is in a sticky selected-level follow-up.
- Any professional conclusion that needs authority is routed or caveated.
- Level 1 is truly simple enough for a child.
- Level 2 is plain enough for a freshman.
- Level 3 uses the right adaptive label for the topic.
- Any visual HTML follows the locked one-page template, stays ELI5-simple, and is self-contained.
- No unsupported facts, citations, or current-status claims were invented.
