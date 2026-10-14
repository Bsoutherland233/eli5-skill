# ELI5 Ladder Reference

Use this file to keep the three levels consistent.

## Default First Response

Always provide all three levels when the user invokes `eli5`.

Use this shape:

```markdown
**1. ELI5**
[Actual child-simple explanation.]

**2. Freshman**
[Slightly more precise explanation.]

**3. Entry-Level CPA** / **3. Entry-Level Business** / **3. College Grad**
[Topic-aware adult beginner explanation.]

Reply 1, 2, or 3 to go deeper, "html" for a simple visual, or "both" for a level plus the visual.
```

## Level Definitions

**1. ELI5**

- Audience: a real child.
- Use everyday objects, simple cause and effect, and concrete pictures.
- Avoid technical terms unless the term itself is the thing being explained.
- Usually 2-4 short sentences.
- Goal: the reader understands the basic idea.

**2. Freshman**

- Audience: an 8th or 9th grader.
- Add basic vocabulary and simple why-it-matters context.
- Define terms as they appear.
- Do not assume business, accounting, audit, or finance knowledge.
- Usually 3-5 short sentences.
- Goal: the reader can explain the concept back in normal words.

**3. Adaptive Adult Beginner**

Pick the label based on the topic:

- `Entry-Level CPA`: accounting, audit, TAS, GAAP, SSARS, tax, EBITDA, working capital, financial reporting, audit evidence, trial balances, workpapers.
- `Entry-Level Business`: business, marketing, operations, sales, management, strategy, pricing, client service, firm operations.
- `College Grad`: general topics, hobbies, personal questions, science, technology, health concepts, sports, miscellaneous subjects.

Assume an educated beginner, not an expert. For accounting topics, assume a staff accountant who knows basic accounting words but still needs the concept made practical.

## Sticky Follow-Up Rules

If the user replies `1`, `2`, or `3`, continue on the same topic at that selected level. Treat the selected level as sticky until the reader:

- changes topic,
- replies with a different level,
- asks for `all three`, or
- says `reset`.

Selected-level follow-up structure:

1. Quick recap in one sentence.
2. Deeper explanation at the selected level.
3. One concrete example.
4. One common mistake, trap, or watch-out.
5. Optional next prompt: `Say "example", "simpler", or "go deeper" if you want the next pass.`

## Short Commands

- `go deeper`: continue at the sticky level. If no sticky level exists, ask whether the user wants `1`, `2`, or `3`.
- `simpler`: move one level simpler, or rewrite the current level with smaller words if already at Level 1.
- `examples`: give 2-3 examples at the sticky level.
- `all three`: show the three-level ladder again.
- `reset`: clear the sticky level and ask for the next topic.
- `test me`: ask 2-3 simple questions at the sticky level.
- `html` or `visual`: build the simple visual HTML only (see SKILL.md Visual HTML Mode and eli5-visual-template.md).
- `both`: deeper chat answer at the selected level plus the visual HTML; ask for the level only if none is chosen yet.

## Accounting Boundary

ELI5 explains the concept. It does not own authoritative accounting conclusions.

Stay in ELI5 when the reader asks:

- what a concept means,
- why something exists,
- how to think about a topic,
- what an accounting word means at a high level.

Route to an authoritative accounting or auditing review when the reader asks:

- what GAAP or GAAS requires,
- whether a specific treatment is correct,
- for ASC, AU-C, AR-C, or other citations,
- for workpaper language tied to authoritative guidance,
- for a conclusion that could affect audit evidence, financial reporting, EBITDA, or working capital.
