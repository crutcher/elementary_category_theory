# Working Plan — Elementary Category Theory

_This file is mutable. It accumulates plans, open questions, and integrated
feedback as the project evolves. See `history/` for the immutable record._

---

## Current state

- **Branch:** `claude/category-theory-book-mdgQ3`
- **Last build round:** v0.1 (initial scaffold)
- **Chapters written:** Preface, Chapter 1 (Things and Arrows)
- **Chapters planned:** 2+ (see roadmap below)

---

## Process directives (from user)

1. Feedback is accumulative dialog — do not edit/rebuild the book in response
   to feedback alone.
2. History files are immutable — only add, never edit.
3. Notes files are mutable — update freely as plans evolve.
4. Before applying a batch of changes: ask/verify → create feature branch.
5. Before merging to main: ask for explicit review and commitment.

---

## Book goal (confirmed v0.5)

Full formal understanding of category theory, its complete suite of theorems,
and then its connections to other branches of mathematics — in that order.

Not a popularization. The goal is an **incremental retraining ramp**: long,
smooth, mildly entertaining. Cyclic redundancy is a feature. Readers are
expected to restart frequently; concept acquisition is optimized over coverage
speed. Connections to other math fields appear only after CT foundations are
built from scratch.

---

## Confirmed structural design (v0.4 + v0.5)

### The learning cycle

Each concept is walked through a cycle of labels drawn from this vocabulary:

```
INFORMALLY → EXPANDING → FORMALIZING → REORGANIZING → SIMPLIFYING → FORMALLY
```

- **INFORMALLY**: Intuition, everyday-language statement
- **EXPANDING**: Examples, internal dialog, multiple modalities — walking in
- **FORMALIZING**: Precise definitions and notation introduced
- **REORGANIZING**: Earlier examples restated *in* the new formalism
- **SIMPLIFYING**: Annotated compression — substituting notation for prose
- **FORMALLY**: The CT-idiomatic form a trained reader reads fluently

Design rules:
- This is a pattern, not a rigid template. Use as many steps as the concept
  warrants; skip steps that add no value for a given concept.
- Labels come from the vocabulary above — don't invent new ones ad hoc.
- The cycle is acknowledged openly to the reader.

### Chapter bookends (when chapter has multiple cycles)

- **Overview** (chapter intro): Informal/intuitive starting point — where
  the reader is *before* the chapter. Collects the informal statements.
- **Restatement** (chapter conclusion): CT-idiomatic compressed form —
  where the reader arrives *after* all cycles. Collects the formal statements.
- Overview and Restatement are mirror images: same content, different language.
- When a chapter or section grouping has **only one cycle**, no bookends needed.

### Chapter ending structure

1. **Summary box** — human-language recap (for first-pass skimmers and review)
2. **Formal Restatement section** — CT-idiomatic definitions and laws in pure
   notation; no prose expansion; the conclusion of the chapter's cycle arc

---

## Implementation plan for next edit batch

This batch requires a **new feature branch**. Changes are significant enough
that the existing ch01 and preamble both need substantial revision.

### preamble.tex changes

1. **Font size**: `\documentclass[11pt]` → `[10pt]` (v0.3)
2. **New label commands** for the full cycle vocabulary:
   - `\InformalLabel` (replaces or aliases `\CoreLabel`)
   - `\ExpandingLabel` (replaces `\ExpOneLabel`)
   - `\FormalizingLabel` (replaces `\ExpTwoLabel` or `\ExpThreeLabel`)
   - `\ReorganizingLabel`
   - `\SimplifyingLabel`
   - `\FormallyLabel`
   - Keep old aliases for backward compat during transition
3. **New environments**:
   - `overviewbox` — chapter intro bookend
   - `formalrestatement` — chapter conclusion bookend (distinct from summarybox)

### ch00_preface.tex changes

- Update the description of the section structure to reflect the full cycle
  (expand + compress) and the re-reader optimization goal.
- Be explicit that the cycle is intentional and openly labeled.

### ch01_things_and_arrows.tex changes

1. **Temperature notation** (v0.2, v0.6): use Celsius —
   `$0°\text{C}$`, `$20°\text{C}$`, `$37°\text{C}$`, `$100°\text{C}$`
2. **Add chapter Overview** (intro bookend) — the informal statements of
   objects, morphisms, composition, identity, commutative diagrams in plain
   language, before the first section.
3. **Retrofit sections** to use cycle labels and add compression/return steps:
   - Each section that has 3+ expansion levels gets Reorganizing + Simplifying
     steps before the Formally step.
   - Sections with 1–2 expansion levels: add at minimum a Simplifying step.
4. **Add Formal Restatement** (conclusion bookend) — the axioms of a category
   stated in CT-idiomatic notation with commutative diagram form of the laws.
5. **Keep the existing summary box** before the Formal Restatement.

---

## Open questions (accumulated)

- [x] Temperature notation: Celsius confirmed (v0.6)
- [ ] Tone calibration: Core/Informal sections accessible enough? Watch for
      reader feedback after next revision.
- [ ] Composition notation: right-to-left ($g \circ f$) vs also introducing
      left-to-right ($f ; g$)? Deferred to Chapter 3.
- [ ] Commutative diagrams §1.5 Exp 1: English/French example may be too
      abstract; consider a second concrete example in next revision.
- [ ] Appendix: "How to read a diagram" — annotated worked example.
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
| 9+ | Theorems and connections | Yoneda, adjoint functor theorems, connections to algebra/topology/logic |

---

## Decisions log

| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-05-11 | No borrowed math examples until foundations built | Core project constraint |
| 2026-05-11 | Four expansion levels with colored chip labels | Visually scannable |
| 2026-05-11 | `\CoreLabel` before subsection heading | First thing seen when skimming |
| 2026-05-11 | Right-to-left composition ($g \circ f$) | Standard math; revisit Ch3 |
| 2026-05-11 | Feedback = dialog, not trigger for immediate rewrite | User directive |
| 2026-05-11 | Goal: full formal CT + theorems + math connections | User directive v0.5 |
| 2026-05-11 | Full cycle: Informally→Expanding→Formalizing→Reorganizing→Simplifying→Formally | User directive v0.5 |
| 2026-05-11 | Chapter bookends (Overview + Restatement) when multiple cycles | User directive v0.5 |
| 2026-05-11 | Summary box + Formal Restatement both kept | User directive v0.5 |
| 2026-05-11 | Cycle openly acknowledged to reader | User directive v0.5 |
