# Working Plan — Elementary Category Theory

_This file is mutable. It accumulates plans, open questions, and integrated
feedback as the project evolves. See `history/` for the immutable record._

---

## Current state

- **Branch:** `claude/category-theory-book-mdgQ3`
- **Last build round:** v0.1 (initial scaffold)
- **Chapters written:** Preface, Chapter 1 (Things and Arrows)
- **Chapters planned:** 2–8 (see roadmap below)

---

## Process directives (from user)

1. Feedback is accumulative dialog — do not edit/rebuild the book in response
   to feedback alone.
2. History files are immutable — only add, never edit.
3. Notes files are mutable — update freely as plans evolve.
4. Before applying a batch of changes: ask/verify → create feature branch.
5. Before merging to main: ask for explicit review and commitment.

---

## Structural decisions pending (high priority)

### Cyclic return structure (v0.4) — MAJOR

The expansion arc needs a corresponding compression arc. Each section and
chapter should complete a full cycle: Core → expand out → compress back →
Axiomatic Core. The purpose is to train the reader to read the formal/axiomatic
form fluently by the time they finish a chapter.

**Proposed section shape:**
```
Core → Exp1 → Exp2 → Exp3 → [Compression2] → [Compression1] → [Axiomatic Core]
```

**Proposed chapter shape:**
- Sections follow the above cycle
- Chapter closes with a formal "Axiomatic Restatement" section:
  all definitions and laws in pure notation, no prose

**Open sub-questions before applying:**
1. Compression levels within sections, or only at chapter level?
   (Section-level = more granular; chapter-level-only = less repetitive)
2. Label names: "READING BACK" for section compressions?
   "FORMAL RESTATEMENT" for chapter-end?
3. Does the current summary box survive alongside the formal restatement?
   (Proposal: yes — summary = human recap, restatement = canonical form)

**Status:** Awaiting discussion/decision before any book edits.

---

## Open questions (accumulated)

_From v0.1 self-assessment:_

- [ ] Tone calibration: are Core sections accessible enough? The blunt opening
      ("Category theory is the study of things and arrows between things") may
      need one more sentence of context. Watch for reader feedback.
- [ ] Composition notation: use right-to-left ($g \circ f$, standard math) or
      also introduce left-to-right ($f ; g$, CS-friendly)? Deferred. Revisit
      when writing Chapter 3 (Functors).
- [ ] Commutative diagrams §1.5 Exp 1: the English/French sentence example may
      be too abstract. Consider a second, more concrete example.
- [ ] Appendix: "How to read a diagram" — a full annotated worked example.
- [ ] Appendix: Glossary.

---

## Planned chapter roadmap

| Ch | Title | Core concept |
|----|-------|-------------|
| 1  | Things and Arrows | Objects, morphisms, composition, identity, commutative diagrams |
| 2  | Categories | The full definition; small examples built from scratch |
| 3  | Functors | Maps between categories |
| 4  | Natural Transformations | Maps between functors |
| 5  | Universal Properties | Optimal solutions; initial and terminal objects |
| 6  | Limits and Colimits | Products, coproducts, equalizers, pullbacks |
| 7  | Adjunctions | The fundamental relationship between functors |
| 8  | Monads | Adjunctions that compose |

---

## Pending feedback to integrate

### preamble.tex — font size (v0.3)
- Change `\documentclass[11pt,oneside]{book}` → `[10pt,oneside]`.
- If still too large after render, escalate to 9.5pt via `fontsize` package.

### Ch 1 §1.2 Exp 1 — temperature notation (v0.2)
- Replace bare `$32°$` etc. with explicit `$32°\text{F}$` (Fahrenheit preferred;
  values 32/68/98/212 are distinctive and carry mnemonic anchors).
- Celsius alternative: 0/20/37/100 — equally valid, less US-centric.
- **Awaiting confirmation of F vs C preference before applying.**

---

## Decisions log

| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-05-11 | No borrowed math examples in Ch 1 | Core project constraint |
| 2026-05-11 | Four expansion levels with colored chip labels | Visually scannable |
| 2026-05-11 | `\CoreLabel` before subsection heading | First thing seen when skimming |
| 2026-05-11 | Right-to-left composition notation ($g \circ f$) | Standard math convention; revisit for CS audience |
| 2026-05-11 | Feedback = dialog, not trigger for immediate rewrite | User directive; expensive cycles to minimize |
