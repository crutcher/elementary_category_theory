# Volume IV Planning — Working Notes

_Mutable working notes. Created 2026-05-12 on `main` (`38fdb84`), after Vol III
completed (commits `337d812` foundational quartet, `553eadf` Ch 29–36, then
`38fdb84` TOC trim)._

This file scopes Volume IV before any drafting starts. It identifies what Vol III
already committed Vol IV to cover, sketches a candidate chapter map, and surfaces
the decisions the user must confirm before a feature branch is cut.

---

## 1. State of the book on the eve of Vol IV

- **Integration branch:** `main` (`38fdb84`)
- **Active feature branch:** none
- **Volumes complete:** I (Ch 1–12), II (Ch 13–24), III (Ch 25–36)
- **Chapter count:** 37 (Preface + 36 numbered)
- **Build:** `cd book && make` green; PDF builds clean.
- **Pending retrofits / appendices** (carried from earlier rounds, not blocking Vol IV):
  - Ch 1–5 v0.11 style retrofit (multi-line equations, `howtosay` callouts)
  - Appendix: "How to read a diagram"
  - Appendix: Glossary
  - Cosmetic: `tcolorbox nobreak` warning at `ch24:395`

---

## 2. What Vol III already promised Vol IV (ch36 §"What Remains")

Ch 36 §sec:beyond-vol3 (lines 165–215) names Vol IV's scope explicitly:

1. **∞-Categories** — develop ∞-categorical analogues of every Vol III theorem
   (∞-Yoneda, ∞-Kan extensions, ∞-monads, ∞-adjunctions). Quasi-categories,
   simplicial categories, complete Segal spaces named as models.
2. **Higher Algebra** — $\mathbb{E}_n$-algebras, $A_\infty$-algebras,
   $L_\infty$-algebras. Builds on Vol III operads (Ch 29), monads (Ch 32),
   distributive laws (Ch 35).
3. **Derived Algebraic Geometry** — stacks, derived schemes, formal moduli.
4. **Homotopy Type Theory** — univalence as the Yoneda philosophy.
5. **Applications to other branches** — explicitly framed as *after* Vol IV:
   "These appear after Volume IV's foundations are laid" (ch36:206).
   So the original v0.5 "connections to other math" promise becomes a
   potential Vol V, not Vol IV.

Ch 36's closing QA pointer: "Open Lurie's HTT or Riehl–Verity's
*Elements of ∞-Category Theory* to begin Volume IV" (ch36:332).

**Implication:** Vol IV is the *higher / homotopical* volume — the natural
∞-categorical extension of Vol III's formal spine — not the applications
volume.

---

## 3. Volume goal and exit criterion

**Goal (user-confirmed 2026-05-12):** A reader who completes Volume IV should be
able to step out of this book and into one of the existing introductions to
higher / ∞-category theory — Lurie's *Higher Topos Theory*, Riehl–Verity's
*Elements of ∞-Category Theory*, Cisinski's *Higher Categories and Homotopical
Algebra*, Land's *Introduction to Infinity-Categories*, or Kerodon — with a
**very strong foundation** for the existing material.

This reframes Vol IV as a **bridge**, not a self-contained complete treatment.
Selection principle: include what those references *assume* the reader knows,
plus enough of their first-few-chapters core that the reader is comfortable in
the working idiom — definitions, examples, characteristic proofs — but stop
short of full ∞-categorical infrastructure-building.

---

## 4. Revised chapter map — clusters of 1–3 chapters per topic

Volume IV is allowed to be significantly longer than Vols I–III (user
direction 2026-05-12). Topics that the literature consistently treats in
200+ pages are given 2–3 chapter clusters; lighter topics stay at 1.

### Cluster A — Simplicial Foundations (Ch 37–39)

| Ch | Title | Scope |
|----|---|---|
| 37 | The Simplex Category $\Delta$ | Combinatorics of $\Delta$; face and degeneracy maps; presentations |
| 38 | Simplicial Sets | $\mathbf{sSet}$ as $\mathbf{Set}^{\Delta^{\mathrm{op}}}$; standard simplices, boundaries, horns; skeleta; small examples |
| 39 | Geometric Realization, the Nerve, and Kan Complexes | $\lvert{-}\rvert \dashv \mathrm{Sing}$; nerve $N: \mathbf{Cat} \to \mathbf{sSet}$ and characterization of its image; Kan complexes |

### Cluster B — Homotopical Algebra (Ch 40–42)

| Ch | Title | Scope |
|----|---|---|
| 40 | Localization at Weak Equivalences | Categories with weak equivalences; Gabriel–Zisman localization; calculus of fractions |
| 41 | Model Categories: Axioms and Examples | Quillen's axioms; lifting properties; cofibrant/fibrant; $\mathbf{sSet}_{\mathrm{Quillen}}$ and $\mathbf{Top}_{\mathrm{Quillen}}$; the Quillen equivalence |
| 42 | Derived Functors and Quillen Equivalences | Left/right derived functors via cofibrant/fibrant replacement; Quillen adjunctions and equivalences |

### Cluster C — Quasi-Categories (Ch 43–45)

| Ch | Title | Scope |
|----|---|---|
| 43 | Quasi-Categories: Definition and First Examples | Inner Kan condition; nerves of ordinary categories; the homotopy category $\mathrm{ho}(\mathcal{C})$ |
| 44 | Mapping Spaces, Equivalences, and the Joyal Model Structure | Mapping anima $\mathrm{Map}_\mathcal{C}(x, y)$; equivalences of quasi-categories; Joyal model structure on $\mathbf{sSet}$ |
| 45 | Joins, Slices, and Limits in a Quasi-Category | Join $\star$ and slice $\mathcal{C}_{/x}$; (co)limit defined as terminal object in a slice; first $\infty$-(co)limit examples |

### Cluster D — Fibrations and Straightening (Ch 46–48)

| Ch | Title | Scope |
|----|---|---|
| 46 | Cartesian and coCartesian Fibrations | Definitions; relation to (op)fibrations of ordinary categories; first examples |
| 47 | Straightening and Unstraightening | The Lurie / Joyal–Lurie equivalence; idea of the proof; computational use |
| 48 | The ∞-Categorical Yoneda Lemma | $\mathcal{C} \hookrightarrow \mathcal{P}(\mathcal{C}) = \mathrm{Fun}(\mathcal{C}^{\mathrm{op}}, \mathcal{S})$; presheaves of spaces; free cocompletion in the $\infty$-setting |

### Cluster E — Universal Constructions, Revisited (Ch 49–51)

The direct higher-categorical successors of Vol III's spine.

| Ch | Title | Scope |
|----|---|---|
| 49 | ∞-Limits and ∞-Colimits | Diagrams; limit/colimit as terminal/initial in slice; preservation; cofinality |
| 50 | ∞-Adjunctions | Unit/counit up to coherent homotopy; relative-adjoint and mapping-space characterizations; ∞-RAPL/LAPC |
| 51 | ∞-Monads and ∞-Kan Extensions | Monads in a quasi-category; bar resolution and ∞-monadicity (statement-level); pointwise ∞-Kan extensions |

### Cluster F — Presentable and Stable ∞-Categories (Ch 52–54)

| Ch | Title | Scope |
|----|---|---|
| 52 | Presentable ∞-Categories | $\kappa$-filtered colimits; accessibility; the adjoint functor theorem in the presentable case |
| 53 | Stable ∞-Categories | Zero object, fiber/cofiber sequences, stabilization $\mathrm{Sp}(\mathcal{C})$ |
| 54 | Triangulated Categories and t-Structures | $\mathrm{ho}$ of a stable ∞-cat is triangulated; t-structures and hearts; derived category of an abelian category as an example |

### Cluster G — Higher Algebra (Ch 55–57)

| Ch | Title | Scope |
|----|---|---|
| 55 | ∞-Operads and Symmetric Monoidal ∞-Categories | Operads classically; Lurie's ∞-operad definition; tensor products of presentable ∞-cats |
| 56 | $\mathbb{E}_n$-Algebras and the Little Disks Operads | $\mathbb{E}_n$ as the little $n$-disks operad; $\mathbb{E}_1 =$ associative, $\mathbb{E}_\infty =$ commutative; Dunn additivity (statement) |
| 57 | $A_\infty$- and $L_\infty$-Algebras | Strong-homotopy associative and Lie algebras; bar/cobar duality; relation to $\mathbb{E}_1$ |

### Cluster H — Doorways (Ch 58–60)

| Ch | Title | Scope |
|----|---|---|
| 58 | Toward Derived Algebraic Geometry | $\mathbb{E}_\infty$-rings; spectral schemes and stacks; formal moduli problems — preview only |
| 59 | Toward Homotopy Type Theory | Univalence as Yoneda; identity types; $\infty$-groupoid models — preview only |
| 60 | The Higher Landscape | Synthesis of Vol IV; what a Vol V on applications would cover; reading-list table mapping Vol IV chapters to Lurie/Riehl–Verity/Cisinski/Kerodon sections |

**Total: 24 chapters (37–60), 8 clusters.**

The reader who completes Cluster D (Ch 48) has a working ∞-Yoneda and can already
open Riehl–Verity at chapter 1. The reader who completes Cluster E (Ch 51) has
the full higher-categorical spine of Vol III's content. Clusters F–G open the
door to Lurie's *Higher Algebra*. Cluster H points at the active frontier.

**Pure new clusters (no Vol I–III setup):** B, C, D, F, G.
**Higher-categorification of Vol III content:** E (49 ↔ 6/16/27; 50 ↔ 7/17/33; 51 ↔ 8/21/32 + 11/18/31).
**Foundational scaffolding / synthesis:** A, H.

---

## 5. Dependency / drafting order

The cluster boundaries are the natural drafting checkpoints. Each cluster lands
in one push with a review pause before the next.

| Phase | Clusters | Chapters | Rationale |
|---|---|---|---|
| Phase 1 | A + B | Ch 37–42 | Simplicial + model-cat foundations. Build the combinatorial and homotopical machinery before any ∞-cat appears. Pure prerequisites. |
| Phase 2 | C + D | Ch 43–48 | Quasi-categories + fibrations/straightening. Ends at ∞-Yoneda — the central theorem and the first "reader can open Riehl–Verity" milestone. |
| Phase 3 | E | Ch 49–51 | The higher-categorification of Vol III's spine. Tight three-chapter cluster. |
| Phase 4 | F + G | Ch 52–57 | Presentable, stable, and ∞-operadic structure. Opens the door to Lurie's *Higher Algebra*. |
| Phase 5 | H | Ch 58–60 | Doorways: DAG, HoTT, synthesis + reading-list mapping. Closing batch. |

A reviewer-friendly checkpoint after each phase: branch is push-ready and
buildable. If a phase reveals new scope or pedagogy decisions, those are
gathered, integrated into `working_plan.md`, and applied to subsequent phases —
not retroactively rewritten into the just-shipped phase (per the project's
"feedback is accumulative dialog" directive).

---

## 6. Pedagogy / style decisions to confirm

Vol III defaulted to "minimal prose, maximum proof density." Vol IV is denser
material on average. Key open questions:

1. **Primary ∞-category model.** Quasi-categories (Joyal/Lurie) recommended as
   the working model; complete Segal spaces and simplicial categories as
   side-bar comparisons. Confirm.

2. **Proof depth.** Three plausible levels:
   - (a) Full proofs as in Vol III. Cost: chapter lengths likely explode (∞-Yoneda
     alone is 50+ pages in Lurie/Riehl-Verity).
   - (b) Proof sketches + carefully chosen full proofs (e.g., Joyal lifting,
     ∞-Yoneda via straightening once, the rest by analogy). **Recommended default.**
   - (c) Theorem-statement-only with forward pointers to Lurie/Riehl-Verity. Risks
     feeling like a survey, not a textbook.

3. **Cycle stages.** Vol III used the cycle sparingly. Vol IV proposal:
   - Bookends (Overview / Restatement) still in every chapter.
   - Foundational chapters (37–40) use Informal → Formalizing → Formally lightly.
   - Theorem-heavy chapters (41–46) skip Informal, lead with Formalizing.
   - Confirm or override.

4. **Chapter length target.** Vol I avg ~600, Vol II ~430, Vol III ~400 lines.
   Proposal: Vol IV target **350–450 lines per chapter** with hard cap ~550.
   Confirm or override.

5. **Exercises.** Continue ~30 Q/A pairs/chapter? At Vol IV's density, 30 Q/A
   may bloat chapters. Plausible alternatives: 20/chapter, or 30 only for
   foundational chapters (37–40, 48) and 15–20 for the rest.

6. **Borrowed math examples.** The "no borrowed math" rule (v0.5) was
   already softened in Vol II/III (homological algebra, simplicial sets used
   as examples). For Vol IV, propose: **freely use established math** —
   topological spaces, chain complexes, schemes, types — for examples.
   Confirm. This is a meaningful philosophical shift; user should explicitly
   sign off.

7. **prooflog usage.** Vol II/III workhorse. Plausibly the right tool for
   ∞-categorical lifting arguments. Plan: keep `prooflog` central for all
   multi-step arguments. Confirm.

8. **New environments?** Vol IV might benefit from:
   - A `diagchase` environment for explicit ∞-cell diagrams (or just reuse `prooflog`).
   - A `model` callout for "in model X, this looks like…" comparisons across
     quasi-cats / simplicial cats / complete Segal spaces.
   Confirm whether to add either.

9. **Notation.** Anima/spaces (Lurie's $\mathcal{S}$ vs Cisinski's `Ani`); $\infty$-categorical
   hom (mapping space `Map_C(x, y)`) — pick a convention up front.

---

## 7. Scope risks (after cluster expansion)

The 2–3 chapter clusters address the worst pre-revision risks (simplicial
sprawl, higher-algebra cramming). Remaining risks:

- **Straightening/unstraightening (Ch 47) full proof is enormous.** Plan: state
  the theorem cleanly, give a worked low-dimensional example, sketch the proof
  strategy, and pointer-forward to HTT §2.2 for the full machinery.
- **Presentable ∞-cats (Ch 52) needs cardinal-arithmetic.** Plan: assume the
  reader has seen accessible categories in passing (or sidebar a primer);
  keep emphasis on the working facts (adjoint functor theorem, accessible
  presentation).
- **Stable ∞-cats / triangulated (Ch 53–54) is itself a textbook topic.** Plan:
  cover the core (fiber/cofiber, stability, t-structures, the derived category
  example) — explicitly leave $\infty$-categorical $K$-theory and higher
  algebra applications to forward pointers.
- **Higher algebra (Ch 55–57) risks becoming a mini-Lurie HA.** Plan: definitions,
  statement-level results, one characteristic theorem per chapter proven in
  sketch. Forward-pointer everything else to HA.
- **DAG / HoTT (Ch 58–59) are entire fields.** Each chapter is explicitly a
  *preview* — orient the reader, name the main objects and theorems, point at
  Toën–Vezzosi / HAG II and the HoTT Book / Univalent Foundations Project.
- **Survey-vs-textbook risk.** Counter-measure: every chapter must (a) prove at
  least one non-trivial theorem from scratch, (b) provide ~5–10 concrete worked
  examples with computations, (c) avoid citation-only theorem statements.

---

## 8. Branch + push discipline (carries forward from v0.13 directive)

- v0.13 directive #2 ("Stop and push after each volume") is in effect.
- Within Vol IV, push after each phase: 37–42 (Phase 1), 43–48 (Phase 2),
  49–51 (Phase 3), 52–57 (Phase 4), 58–60 (Phase 5). Final merge after Ch 60.
- Proposed branch name: `feature/volume4-v0.15`. Confirm or override.

---

## 9. Forward pointers from earlier volumes that Vol IV honors

Quick survey of "Volume IV" mentions in the existing text — Vol IV should
substantively deliver each:

- **ch36:30** — "topics beyond our scope: ∞-categories, higher algebra,
  derived algebraic geometry, and applications" → Ch 37, 45–46, 47, (Vol V).
- **ch36:80** — "These rooms — the entire next floor — are Volume IV,
  never written here." → Whole volume framing.
- **ch36:178–180** — "∞-categorical analogues of every Vol III theorem:
  ∞-Kan, ∞-Yoneda, ∞-monads, ∞-adjunctions" → Ch 48 (∞-Yoneda), Ch 49 (limits),
  Ch 50 (adjunctions), Ch 51 (monads + Kan).
- **ch36:206** — Applications "appear after Volume IV's foundations are laid" →
  framed as Vol V; Ch 48 should restate this.
- **ch36:332** — "Open Lurie's HTT or Riehl–Verity to begin Vol IV" →
  Ch 37 should reference both as the canonical literature.

---

## 10. Decisions (consolidated)

All decisions confirmed 2026-05-12 unless noted; minor items marked **(default applied)**
are sensible defaults that user has implicit override rights on.

| ID | Decision | Status |
|---|---|---|
| D1 | Volume scope is ∞-categorical / higher algebra (not applications) | Confirmed |
| D1b | Vol IV framed as bridge to existing higher-CT introductions (Lurie, Riehl–Verity, Cisinski, Land, Kerodon) | Confirmed |
| D1c | Cluster-of-1-3 chapters per topic; volume length significantly larger than I–III | Confirmed |
| D2 | 24-chapter map in 8 clusters (§4) | Confirmed |
| D3 | Phased drafting order — 5 phases (§5) | Confirmed |
| D4 | Primary ∞-category model: **quasi-categories** (Joyal / Lurie). Simplicial categories and complete Segal spaces appear in sidebar comparisons only. | Default applied |
| D5 | Proof depth: **sketched + selective full proofs**. One or two characteristic full proofs per chapter; sketches + literature pointers for the rest. | Confirmed |
| D6 | Cycle stages: **bookends always (Overview/Restatement)**; foundational chapters (37–42, 60) use Informal → Formalizing → Formally lightly; theorem-heavy chapters skip Informal and lead with Formalizing. | Default applied |
| D7 | Chapter length target: **400–500 lines**, hard cap ~600. | Confirmed |
| D8 | Exercises: **~20 Q/A pairs per chapter**. | Confirmed |
| D9 | Borrowed math examples: **Gated** — math that itself uses CT essentially (algebraic topology, homological algebra, type theory, simplicial homotopy, derived categories OK; analysis, number theory, classical geometry not). | Confirmed |
| D10 | New environments: **none**. Reuse `prooflog` for multi-step arguments; `tcolorbox` variants already in preamble suffice. | Default applied |
| D11 | Notation: **Lurie/Cisinski convention** — $\mathcal{S}$ for anima/spaces; $\mathrm{Map}_\mathcal{C}(x,y)$ for mapping space; $\mathcal{P}(\mathcal{C}) = \mathrm{Fun}(\mathcal{C}^{\mathrm{op}}, \mathcal{S})$ for presheaves of spaces; $\mathrm{ho}(\mathcal{C})$ for the homotopy category; $\mathrm{N}(\mathcal{C})$ for the nerve. | Default applied |
| D12 | Branch: **`feature/volume4-v0.15`**, phase-by-phase cadence (push after each phase; final merge after Ch 60). | Confirmed |

---

## 11. Drafting will not begin until the user

1. Reviews this note,
2. Confirms (or revises) the architecture in §4 and the drafting order in §5,
3. Answers (or defers) the remaining decisions in §10,
4. Explicitly approves the feature branch creation.
