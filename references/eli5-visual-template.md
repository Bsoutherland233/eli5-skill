# ELI5 Visual Template

The locked shape for every visual HTML this skill produces. Read this before building any visual. The page fills one full screen: the TOP HALF is the 10-second glance, the BOTTOM HALF adds three short sections that reward another minute. Nothing should require scrolling past one page.

## Top half: the 10-second glance (four pieces, in order)

1. **Headline phrase.** One big, plain-language sentence or phrase that IS the idea, not a title for it. Wrong: "Understanding Depreciation." Right: "Stuff wears out. We spread the cost over the years it's used."
2. **One simple visual.** Basic shapes, icons, or inline SVG built fresh for the topic. A before/after pair, a simple flow, or a tiny bar chart. Not photorealistic art, not a stock image, not a dense diagram. If the idea needs two visuals, it is not simple enough yet: cut until one works.
3. **Three to four short callouts.** Small labeled boxes, a few words each, not full sentences. Each callout carries one concrete fact or step. Use real numbers from the conversation when they exist; simple round examples when they do not.
4. **One "why it matters" line.** A single sentence connecting the idea back to something the reader would care about. This closes the top half.

## Bottom half: three short sections (always included)

5. **The story.** A tiny 2-4 step walk of one concrete example, numbered steps, one short line each. Real numbers from the conversation when they exist, simple round ones when they do not.
6. **Don't confuse it with.** One or two contrast rows: the idea next to the thing people mix it up with, each side in a phrase. (Depreciation is not cash leaving; it is not the thing losing market value.)
7. **Where you'll see it.** Two or three short bullets naming the real places this shows up (a financial statement line, a tax return, an EBITDA addback, a client conversation).

That is the whole page. No footers with disclaimers, no "learn more," no fourth bottom section.

## Content rules

- Always pinned to ELI5-simple, regardless of which chat level is in play.
- Written fresh for the glance, never a copy-paste of the chat Level 1 text.
- Small words in the callouts, big words only in the headline if the big word is the thing being explained.
- Preserve important real numbers; never invent facts.
- The professional guardrails in SKILL.md apply: the visual explains a concept and never presents an authoritative GAAP/GAAS/tax conclusion. A diagram can imply certainty that a sentence would hedge; do not diagram a conclusion the chat text would not state.
- No em dashes anywhere.

## Style rules

- Use a calm, readable palette: green #176B5B, dark green #0E4A3D, aqua #137C8B, ink #1C2B27, light background #F6F8F7, line #DFE6E2. Font stack: 'Aptos','Segoe UI',system-ui,sans-serif.
- Lighter, more playful touch inside that palette: bigger type contrast (headline 26-34px bold, callout labels small caps), generous whitespace, rounded corners. Simple and clear, never cartoonish.
- Fully self-contained: inline CSS and inline SVG only. No external assets, fonts, scripts, or CDNs.
- Fills one page; no scrolling needed at normal window size. If the bottom half forces a scroll, cut words, never sections. Max width around 700-800px, centered.
- File name: `eli5-<topic-slug>.html`. One-off deliverable; do not archive or version it.

## Skeleton

```html
<!DOCTYPE html><html lang="en"><head><meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>eli5: [Topic]</title><style>
body{margin:0;font-family:'Aptos','Segoe UI',system-ui,sans-serif;color:#1c2b27;background:#f6f8f7}
.wrap{max-width:760px;margin:0 auto;padding:40px 24px}
.headline{font-size:30px;font-weight:800;color:#0f4e3b;line-height:1.2;margin:0 0 24px}
.visual{display:flex;align-items:center;justify-content:center;gap:16px;margin:24px 0}
.callouts{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:20px 0}
.callout{background:#fff;border:1px solid #dfe6e2;border-radius:8px;padding:10px 14px;font-size:14px}
.callout b{display:block;font-size:12px;text-transform:uppercase;letter-spacing:.4px;color:#0f4e3b;margin-bottom:3px}
.why{background:#e9f4ef;border-left:4px solid #156A51;border-radius:8px;padding:12px 16px;font-size:15px;margin-top:22px}
</style></head><body><div class="wrap">
<div class="headline">[The idea, as a plain sentence]</div>
<div class="visual">[inline SVG built for this topic]</div>
<div class="callouts">
  <div class="callout"><b>[Label]</b>[few words]</div>
  <div class="callout"><b>[Label]</b>[few words]</div>
  <div class="callout"><b>[Label]</b>[few words]</div>
  <div class="callout"><b>[Label]</b>[few words]</div>
</div>
<div class="why">Why it matters: [one sentence].</div>
<div class="section"><h2>The story</h2><ol><li>[step]</li><li>[step]</li><li>[step]</li></ol></div>
<div class="section"><h2>Don't confuse it with</h2>
  <div class="contrast"><span>[the idea, as a phrase]</span><span>[the mix-up, as a phrase]</span></div>
</div>
<div class="section"><h2>Where you'll see it</h2><ul><li>[place]</li><li>[place]</li><li>[place]</li></ul></div>
</div></body></html>
```

Add matching CSS for the bottom half: `.section{margin-top:22px} .section h2{font-size:15px;color:#0f4e3b;text-transform:uppercase;letter-spacing:.5px;margin:0 0 6px;border-bottom:2px solid #156A51;padding-bottom:4px;display:inline-block} .contrast{display:grid;grid-template-columns:1fr 1fr;gap:10px}` with the two contrast cells styled like callouts (the idea side tinted green, the mix-up side neutral).

## Worked example: "What is depreciation?"

Headline: "Stuff wears out. We spread the cost over the years it's used."
Visual: a truck shape, an arrow, and a 5-bar declining chart (three simple SVGs in a row).
Callouts: The truck / Costs $50,000 today. The years / Used for 5 years. Each year / $10,000 counted as cost. The catch / No new cash leaves the bank.
Why it matters: profit looks smaller each year even though nothing new was paid, because the truck is quietly "using itself up."
The story: 1. Buy the truck for $50,000. 2. It will work for about 5 years. 3. Each year, $10,000 shows up as an expense. 4. After 5 years the truck is "used up" on paper.
Don't confuse it with: cash going out (that happened once, on day one) or the truck's resale value (the books do not track what a buyer would pay).
Where you'll see it: the P&L (depreciation expense), the balance sheet (accumulated depreciation), and every EBITDA calculation (it gets added back).

The shipped calibration anchor in `assets/` is the rendered version of this example. Match its density and restraint: if your draft has more text than the anchor, cut.
