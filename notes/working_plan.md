# Working Plan — Elementary Category Theory

_This file is mutable. It accumulates plans, open questions, and integrated
feedback as the project evolves. See `history/` for the immutable record._

---

## Current state

- **Integration branch:** `main` (at `38fdb84`)
- **Feature branch in progress:** `feature/volume4-v0.15` (Vol IV drafting; Phase 1 = Ch 37–42 starting 2026-05-12)
- **Last merged round:** v0.14 (Vol III Ch 25–36 complete + TOC trim); landed on main 2026-05-12
- **Chapters written:** Preface, Ch 1–36 (Vols I, II, III complete)
- **Unwritten:** Ch 37–60 (Vol IV: 24 chapters in 8 clusters, see `notes/vol4_planning.md`)
- **Build:** `cd book && make` is green from main.
- **Vol IV preparation:** see `notes/vol4_planning.md` — bridge to higher-CT literature; 24-chapter map; 5-phase drafting cadence; decisions D1–D12 recorded.
- **Merged PRs**: #1 (v0.7), #2 (v0.10 typography), #3 (undefined ref fix),
  #4 (v0.10 → main), #5 (Ch 2+3), #7 (v0.11 Ch 4-5), #8 (v0.12)

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

### Chapter ending structure (v0.12 onward)

1. **Exercises section** — ~30 Q/A pairs in Little Schemer two-column style
2. **Summary box** — human-language recap (for first-pass skimmers and review)
3. **Formal Restatement section** — CT-idiomatic definitions and laws in pure
   notation; no prose expansion; the conclusion of the chapter's cycle arc

---

## Style directives in effect (cumulative)

These apply going forward; existing chapters may be retrofitted in batches.

- **Font size**: 8pt body via `fix-cm` + redefined size commands (book class)
  (v0.11 + v0.11 patch)
- **Paper**: A4 with 25/25/30/25mm margins (v0.10)
- **Multi-line equations**: use `align*` / `gather` for grouped equations
  and multi-stage proofs (v0.11)
- **"How to say this" callouts**: use `\sayit{...}` inline for single
  readings, `howtosay` tcolorbox for notation with multiple conventions (v0.11)
- **Cycle vocabulary**: Informally → Expanding → Formalizing → Reorganizing
  → Simplifying → Formally; carried by subsection headings, no chip labels (v0.7/v0.9)
- **Chapter bookends**: Overview at top, Exercises + Summary + Formal Restatement at bottom (v0.12)
- **Examples**: no borrowed mathematical examples until foundations are built
- **Temperature notation**: Celsius (0°C, 20°C, 37°C, 100°C)
- **Exercises**: Little Schemer-style Q/A in a two-column `qa` environment
  (v0.12). ~30 Q/A pairs per chapter, ramping from trivial to probing.

---

## Pending: retrofit of Ch 1-5 style

The v0.11 style directives (multi-line equations, `howtosay` callouts) apply
to new content. The existing chapters (1, 2, 3, preface) contain material
that would benefit from a retrofit pass:

- Multi-equation passages that could combine into `align*` blocks
- Notation introductions that could carry `howtosay` callouts

Defer to its own batch; do not mix retrofits with new-content writing.

---

## Open questions (accumulated)

- [x] Temperature notation: Celsius confirmed (v0.6)
- [ ] Tone calibration: Core/Informal sections accessible enough? Watch for
      reader feedback after next revision.
- [ ] Composition notation: right-to-left ($g \circ f$) vs also introducing
      left-to-right ($f ; g$)? Decided in Ch 3: stayed with $g \circ f$.
      Could revisit if a CS-oriented appendix is added.
- [ ] Commutative diagrams §1.5 Exp 1: English/French example may be too
      abstract; consider a second concrete example in next revision.
- [ ] Is 8pt too small for body text? (v0.11) — pending render check.
- [ ] `howtosay` callout length calibration — currently varies by notation
      richness. Watch for reader feedback.
- [ ] Q/A layout calibration — two-column tabularx; visual check needed.
- [ ] Appendix: "How to read a diagram" — annotated worked example.
- [ ] Appendix: Glossary.
- [ ] Vol III pedagogy: confirm prose density / cycle stages / chapter length
      target before drafting Ch 25. See `vol3_planning.md` §6.
- [ ] Vol III chapter scoping: confirm intended depth for Ch 28 (Formal Yoneda),
      Ch 29 (Coherence), Ch 31 (Kan extensions), Ch 34 (AFTs unified) — each
      risks recap of an already-thorough Vol II chapter. See `vol3_planning.md` §6.
- [ ] Cosmetic: `tcolorbox nobreak` warning at `ch24:395` — defer.

---

## Multi-volume structure (v0.13 directive)

The book is organized into three volumes via LaTeX `\part{}`, with `\partname` set to "Volume".
Connections to other math fields are deferred beyond Volume III.

### Volume I — The Architecture of Categories (Ch 1–12)

Full cycle pedagogy from scratch. Connections deliberately excluded.

| Ch | Title | Core concept |
|----|-------|-------------|
| 1  | Things and Arrows | Objects, morphisms, composition, identity, commutative diagrams |
| 2  | Categories | The full definition; small examples built from scratch |
| 3  | Functors | Maps between categories |
| 4  | Natural Transformations | Maps between functors (v0.11) |
| 5  | Universal Properties | Initial/terminal, the universal pattern, products/coproducts preview (v0.11) |
| 6  | Limits and Colimits | Diagrams, cones, completeness, preservation (v0.12) |
| 7  | Adjunctions | Hom-set bijection, unit/counit, RAPL/LAPC (v0.12) |
| 8  | Monads | Adjunctions give monads, Eilenberg–Moore, Kleisli (v0.12) |
| 9  | The Yoneda Lemma | Hom-functors, representability, the Yoneda embedding (v0.12) |
| 10 | Adjoint Functor Theorems | GAFT, SAFT, existence of adjoints (v0.12) |
| 11 | Kan Extensions | Left/right Kan extensions, colimit/limit formulas, density (v0.13) |
| 12 | Monoidal and Enriched Categories | Tensor products, coherence, V-categories (v0.13) |

### Volume II — The Architecture Revisited (Ch 13–24)

Recapitulation assuming ~half familiarity. Same pedagogy, interior math focus.
Arguments use two-column `prooflog` environment (step | justification).
Chapter ordering rotated to reframe coverage.

| Ch | Title | Rotation angle |
|----|-------|---------------|
| 13 | Categories as Algebraic Structures | Via monoids, groupoids, thin categories |
| 14 | Functors as Structure Maps | Profunctors; bicategory of relations |
| 15 | Representability and the Yoneda Philosophy | Yoneda first as organizing principle |
| 16 | Limits as Representable Constructions | Limits via the Yoneda perspective |
| 17 | Adjunctions: A Deeper Account | Triangle identities; adjoints of adjoints |
| 18 | Kan Extensions as Universal Adjoints | Lan/Ran as adjoints to precomposition |
| 19 | Monoidal Categories as Categorified Monoids | Strict vs. weak; coherence |
| 20 | Enriched Category Theory | V-Cat in depth; self-enrichment |
| 21 | Monads: Algebraic Theory and Beck's Theorem | Monadicity; Beck's monadicity theorem |
| 22 | Natural Transformations as 2-Morphisms | The 2-category Cat; whiskering |
| 23 | Adjoint Functor Theorems: Complete Treatment | Full proofs with justification logs |
| 24 | The Representable Universe | Volume II synthesis |

### Volume III — The Formal Spine (Ch 25–36)

High familiarity assumed; rotating toward formal/terse presentation.
Minimal prose expansion. Maximum proof density. Advanced CT constructions.

| Ch | Title | Theme |
|----|-------|-------|
| 25 | 2-Categories and Bicategories | Cat as 2-category; strict vs. weak |
| 26 | Ends and Coends | Dinatural transformations; the coend calculus |
| 27 | Weighted Limits and Colimits | V-limits; weighted colimit formula |
| 28 | The Formal Yoneda Lemma | Yoneda via ends; ninja Yoneda |
| 29 | Monoidal Categories: Coherence | Mac Lane's coherence theorem; strictification |
| 30 | Enriched Categories: Day Convolution | Day convolution; enriched Kan extensions |
| 31 | Kan Extensions: The General Theory | Pointwise; Kan in enriched setting |
| 32 | The Formal Theory of Monads | Eilenberg–Moore objects; Beck's monadicity |
| 33 | Adjunctions: The Full Formal Account | Adjunctions in 2-categories |
| 34 | Adjoint Functor Theorems: Unified | GAFT + SAFT from a single perspective |
| 35 | Distributive Laws and Composed Monads | Compatibility of monads |
| 36 | The Formal Landscape | Volume III synthesis and forward pointers |

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
| 2026-05-11 | A4 paper, chip labels removed (no-ops) | User directive v0.8/v0.9 |
| 2026-05-12 | Font size 10pt → 8pt via fix-cm size redefinitions (not extsizes) | v0.11 + patch |
| 2026-05-12 | Multi-line equation environments preferred | User directive v0.11 |
| 2026-05-12 | `howtosay` callouts / `\sayit` inline for notation pronunciation | User directive v0.11 |
| 2026-05-12 | Defer retrofit of Ch 1–5 to its own batch | Avoid mixing retrofit with new-content writing |
| 2026-05-12 | Little Schemer Q/A exercises in every chapter | User directive v0.12 |
| 2026-05-12 | Ordering: Ch 8 = Monads, Ch 9 = Yoneda, Ch 10 = AFT | Natural progression: monads from adjunctions, Yoneda before AFT |
| 2026-05-12 | Three-volume structure using `\part{}` | Vol I = core CT; Vol II = recapitulation at half familiarity; Vol III = formal spine |
| 2026-05-12 | Vol II uses prooflog (2-col step/justification) format | Written proof + parallel annotation |
| 2026-05-12 | Exercise spacing: 3× vertical gap + thin horizontal rule between Q/A pairs | User directive v0.13 |
| 2026-05-12 | Connections to other math fields deferred beyond Vol III | Build CT foundations first |
| 2026-05-12 | Vol IV scope = ∞-categories + higher algebra (Ch 37–60, 24 chapters in 8 clusters) | Per Ch 36 §"What Remains" framing; applications to other branches deferred to potential Vol V |
| 2026-05-12 | Vol IV is a bridge to existing higher-CT introductions (Lurie/Riehl–Verity/Cisinski/Land/Kerodon), not a self-contained complete treatment | User directive — reader should be ready to step into the literature with a strong foundation |
| 2026-05-12 | Vol IV uses 1–3 chapter clusters per topic; volume length is significantly larger than I–III | User directive — single-chapter constraint was too restrictive |
| 2026-05-12 | Vol IV ∞-cat model: quasi-categories (Joyal/Lurie) as primary | Standard in the literature; matches HTT and Riehl–Verity convention |
| 2026-05-12 | Vol IV proof depth: sketched + selective full proofs (one or two per chapter) | Bridge function over completeness; full proofs available in the named literature |
| 2026-05-12 | Vol IV chapter length: 400–500 lines, ~20 Q/A pairs | Higher density per topic; smaller exercise count keeps total length manageable |
| 2026-05-12 | Vol IV borrowed math: Gated — only math that itself uses CT essentially (algebraic topology, homological algebra, type theory, derived categories OK) | Middle ground between v0.5 strict restriction and full openness |
| 2026-05-12 | Vol IV cadence: phase-by-phase pushes on `feature/volume4-v0.15` (Phase 1 = Ch 37–42, Phase 2 = 43–48, Phase 3 = 49–51, Phase 4 = 52–57, Phase 5 = 58–60) | Mirrors Vol III's two-batch split, scaled to 24 chapters |
