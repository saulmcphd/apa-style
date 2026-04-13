# APA Style Checker — Claude SKILL.md

A comprehensive APA 7th edition proofreading skill for Claude AI that produces a Grammarly-style interactive report with inline corrections, a scoring dashboard, and a sidebar with rule-by-rule explanations.

![APA Style Checker Dashboard](screenshots/apa-dashboard-strip.png)

## What It Does

Upload an academic paper (or paste text) and Claude produces an HTML artifact that:

- **Scores your paper 0–100** against APA 7th edition rules
- **Highlights every error inline** with red strikethrough and green corrections
- **Shows a sidebar** with detailed correction cards citing specific APA manual sections
- **Renders your tables as-is** so you can see structural mistakes, with the correctly formatted version shown in the sidebar
- **Categorises issues** across six colour-coded categories: Correctness, APA Compliance, Citations & References, Style, Statistical Notation, and Tables & Figures

![Two-panel layout](screenshots/apa-two-panel-layout.png)

## Why It Exists

Existing APA tools cover narrow slices of the problem:

- **Scribbr / Reciteworks** check citations and references only
- **Grammarly** covers grammar but knows nothing about APA heading levels, number formatting, *p*-value conventions, or bias-free language rules
- **Citation Machine / BibMe** generate references but don't proofread manuscripts
- Most tools silently correct your text — you never learn what was wrong

This skill checks everything in a single pass, shows your original errors, and teaches you the rule behind each correction.

![Comparison](screenshots/apa-comparison-grid.png)

## How It Was Built

The rule set comes directly from the *Publication Manual of the American Psychological Association, Seventh Edition* (2020), cross-referenced with:

- APA's Student Paper Checklist and Professional Paper Checklist
- The Style and Grammar Guidelines at [apastyle.apa.org](https://apastyle.apa.org)
- Purdue OWL APA formatting guide (for common student error patterns)

Every rule in the SKILL.md includes the relevant APA manual section number so Claude can cite it in the sidebar cards.

## Categories Checked

| Category | Colour | What It Covers |
|---|---|---|
| **Correctness** | 🔴 Red | Grammar, spelling, punctuation, serial comma, hyphenation |
| **APA Compliance** | 🔵 Blue | Heading levels, number rules, abbreviations, title/sentence case, page layout |
| **Citations & References** | 🟣 Purple | In-text format, reference list format, cross-matching, et al. rules |
| **Style** | 🟠 Orange | Wordiness, passive voice, bias-free language, hedging, "subjects" vs "participants" |
| **Statistical Notation** | 🟢 Green | Leading zeros, italicisation, *p*-value formatting, effect sizes |
| **Tables & Figures** | 🩵 Teal | Border rules, labels, titles, notes, shading, numbering |

## Scoring

The score starts at 100 and deducts points per issue:

- **Critical** (−3): missing references, heading hierarchy errors, statistical notation, citation mismatches
- **Major** (−2): verb tense, number rules, bias-free language, serial commas, table structure
- **Minor** (−1): wordiness, passive voice, capitalisation, minor punctuation

## Usage

### In Claude.ai

1. Add `SKILL.md` to your Claude skills directory
2. Upload a paper or paste text
3. Ask Claude to proofread for APA style
4. Claude generates the interactive HTML artifact

### With the Claude API

Send the SKILL.md as the system prompt with JSON output instructions. See the [blog post](https://saulmcleod.com) for the full API integration guide and SaaS architecture.

## File Structure

```
apa-style-checker/
├── SKILL.md              # The complete APA proofreading skill
├── README.md             # This file
└── screenshots/
    ├── apa-dashboard-strip.png
    ├── apa-two-panel-layout.png
    └── apa-comparison-grid.png
```

## Who It's For

- **Students** writing dissertations and theses — catch formatting errors before submission
- **Researchers** preparing journal submissions — avoid desk rejections for APA violations
- **Academic editors and supervisors** — provide consistent, structured feedback
- **Psychology educators** — the sidebar cards with section references turn proofreading into a teaching tool

## Limitations

- Claude analyses the text you provide; it cannot check physical page formatting (margins, font size, page numbers) from pasted text. Upload a .docx for best results.
- Scoring has slight variance (±2–3 points) across runs due to the nature of LLM-based analysis.
- The skill is optimised for psychology and social sciences but works for any APA-formatted paper.

## Author

**Dr. Saul McLeod, CPsychol, PhD**
Founder, [Simply Psychology](https://www.simplypsychology.org) · [saulmcleod.com](https://saulmcleod.com)

## License

MIT
