# Volume III Planning — Working Notes

_Mutable working notes. Last updated 2026-05-12, on branch `main`._

This file consolidates the state of the book on the eve of writing Volume III,
identifies what Vol III's actual contribution must be given the scope of Vols I–II,
and flags decisions needed from the user before drafting starts.

---

## 1. Current state of the repo

### Branches and history
- **Integration branch:** `main` (currently checked out, up to date with `origin/main`)
- **Active feature branch:** none — v0.13 merged at `25620d1`
- **Notable side branches still present:** `feature/volumes-v0.13` (origin matches), `crutcher/fix` (build fix; merged via the v0.13 round), `claude/category-theory-book-mdgQ3` (early dev), various earlier feature branches
- **Recovered-session note (2026-05-12):** the latest fast-forward (`4c3f51b..25620d1`) fused two branches that couldn't land via the remote runner due to API issues. The `crutcher/fix` build-fix branch addressed a malformed tabularx column spec in `preamble.tex` (`>{}\foo}X` → `>{\foo}X`) that broke every chapter using the `qa`/`prooflog` environments.

### Build
- `cd book && make` produces `build/main.pdf` cleanly: **193 pages, 1.48 MB**, no undefined references after the rerun pass.
- One latent warning: `Package tcolorbox Warning: Using nobreak failed` near `ch24:395` (Formal Restatement box). Cosmetic; safe to defer.

### main.tex status
- Vol I `\part` active, Ch 1–12 wired.
- Vol II `\part` active, Ch 13–24 wired.
- Vol III `\part` and Ch 25–36 inputs **commented out** (lines 48–62) — confirmed correct by the user; chapters do not exist yet.

### Chapter sizes (lines)
- Vol I: 474–983 lines/chapter. Ch 1 longest (foundations); Ch 5 second longest.
- Vol II: 183–585 lines/chapter. Ch 16 shortest (limits as representable); Ch 20 longest (enriched CT).
- Vol II is roughly **half** the per-chapter length of Vol I — consistent with the "recapitulation at half familiarity" directive.

---

## 2. Pedagogy/style state at end of Vol II

Cumulative directives in effect when Vol III starts:
- 8pt body via `fix-cm`; A4 paper; `parskip`-style paragraphs; cycle-step labels are no-ops (carried by subsection titles).
- Cycle vocabulary: `Informally → Expanding → Formalizing → Reorganizing → Simplifying → Formally`. Use what the concept warrants; don't pad.
- Chapter bookends: Overview at top; Exercises + Summary + Formal Restatement at bottom.
- Vol II distinctive: `prooflog` environment (step | justification, two-column tabularx). Used heavily in ch17–23.
- Exercises: Q/A pairs in `qa` environment (~30/chapter), 0.3em+rule+0.6em spacing.
- `\sayit{...}` inline and `howtosay` callouts for notation pronunciation.
- No borrowed math examples; Celsius for temperature.

Vol III directive (from working_plan):

> _"High familiarity assumed; rotating toward formal/terse presentation. Minimal prose expansion. Maximum proof density. Advanced CT constructions."_

So Vol III chapters will look denser still — possibly even shorter per chapter (~150–350 lines?), heavier use of `prooflog`, fewer cycle stages, fewer everyday-language sections.

---

## 3. What Vol II actually covered (and what remains for Vol III)

Survey of Vol II chapters, focused on overlap with the planned Vol III chapter list.

### Ch 13 — Categories as Algebra
- Algebraic taxonomy (monoid/groupoid/preorder), Ab-categories, biproducts.
- **No** forward-pointers. Foundational vocabulary; Vol III consumes silently.

### Ch 14 — Functors as Structure Maps
- Profunctors and their composition via coend.
- **Explicit promise:** ch14:145 says "Coends are introduced formally in Volume III." Coends used here only as notation.

### Ch 15 — Representability and the Yoneda Philosophy
- **Full** proof of ordinary Yoneda lemma, Yoneda embedding, category of elements.
- No enriched/weighted version.

### Ch 16 — Limits as Representable Constructions
- Limits via representability; completeness from products + equalizers; pointwise limits in functor categories (statement-level).
- No weighted limits.

### Ch 17 — Adjunctions: A Deeper Account
- Triangle identities ↔ hom-bijection; uniqueness via Yoneda; comma-category characterization; **adjoint triples**.
- Forward-pointers to Ch 18 only (intra-Vol II).

### Ch 18 — Kan Extensions as Universal Adjoints
- Adjoint triple `Lan ⊣ p* ⊣ Ran` with full proof.
- **Coend formula** `(Lan_p F)(e) = ∫^c E(p(c),e)·F(c)` stated (coend itself still informal).
- Pointwise / absolute Kan extensions; nerve/realization; free cocompletion.
- Promised "every right adjoint is a right Kan extension along Yoneda."

### Ch 19 — Monoidal Categories as Categorified Monoids
- Pentagon + triangle axioms; **Mac Lane's coherence theorem with proof** (normal-form strategy via prooflog); lax/oplax/strong monoidal functors; monoids in monoidal categories; Eckmann–Hilton; monads as monoids in `[C, C]`.
- Substantially complete for monoidal foundations.

### Ch 20 — Enriched Category Theory (longest Vol II chapter)
- **Enriched Yoneda lemma** with full prooflog. Ends introduced informally in the proof (`∫_c V(G(c), H(c))`).
- V-adjunctions.
- **Weighted limits and colimits**: definition of `{W, F}`, Yoneda reduction (ordinary limits as ΔI-weighted), cotensor as weighted limit, mentions of homotopy limits.
- Change of base via lax monoidal `Φ: V → W`.
- Self-enrichment of closed symmetric monoidal categories; tensors and cotensors.

### Ch 21 — Monads: Algebraic Theory and Beck's Theorem
- Kleisli, Eilenberg–Moore, comparison functor; **Beck's monadicity theorem with full prooflog**.
- F-split coequalizers, absolute coequalizers, crude monadicity, applications.
- No distributive laws.

### Ch 22 — Natural Transformations as 2-Morphisms
- $\mathbf{Cat}$ as a 2-category; vertical/horizontal composition; whiskering; **interchange law with proof**.
- Strict 2-categories defined; bicategories introduced.
- **Explicit forward-pointer:** ch22:25 — "prepares the ground for enriched category theory (Volume III)."
- No pseudofunctors / lax functors / modifications; no example bicategories beyond `Mon` and brief mention of `Span`/`Prof`.

### Ch 23 — Adjoint Functor Theorems: Complete Treatment
- Universal arrow recap; **GAFT** with solution-set condition; **SAFT** with cogenerating sets; applications (free algebras, sheafification, Stone–Čech, geometric morphisms).

### Ch 24 — The Representable Universe (Vol II synthesis)
- Representability thread through every Vol I/II construction.
- Co-Yoneda / density theorem; presheaf category as free cocompletion; universal property of $\hat{\mathcal{C}}$.
- Final table reading every construction as representability-or-adjointness.
- **Volume III preview** section (§sec:vol3-preview): enriched cats, weighted limits, ends/coends, 2-categorical structure.

---

## 4. Vol III chapter map — what's actually new

| Ch | Planned title | Setup in Vol II | Vol III contribution | Recap : new |
|----|---|---|---|---|
| 25 | 2-Categories and Bicategories | Ch 22 introduces Cat as 2-cat + interchange | Pseudofunctors, modifications, biequivalences, example bicategories (Span, Prof, Rel) | 30 : 70 |
| 26 | Ends and Coends | **Promised but undefined** in Ch 14, 18, 20 | Foundational chapter: define rigorously, dinatural transformations, Fubini, examples | 0 : 100 |
| 27 | Weighted Limits and Colimits | Ch 20 §3 has definitions + Yoneda reduction | Composition of weighted limits, weighted Kan extensions, end/coend characterization | 25 : 75 |
| 28 | The Formal Yoneda Lemma | Ch 15 (ordinary) + Ch 20 (enriched) prove their versions separately | Yoneda via ends ("ninja Yoneda"), weighted Yoneda, unified statement | 50 : 50 |
| 29 | Monoidal Categories: Coherence | Ch 19 proves Mac Lane coherence | Coherence for monoidal functors, free monoidal categories, strictification theorem proof | 60 : 40 |
| 30 | Enriched Categories: Day Convolution | Ch 20 develops enriched CT broadly | **Day convolution** (monoidal structure on `[C, V]`); tensor product of V-cats; enriched Kan extensions via coends | 30 : 70 |
| 31 | Kan Extensions: The General Theory | Ch 18 is thorough | Enriched Kan extensions; pointwise in V-Cat; absolute case in enriched setting; applications | 40 : 60 |
| 32 | The Formal Theory of Monads | Ch 21 covers EM, Kleisli, Beck | Monads in a 2-category; the "formal theory" (Street); algebraic theories | 30 : 70 |
| 33 | Adjunctions: The Full Formal Account | Ch 17 + Ch 23 | Adjunctions in 2-categories / bicategories; enriched adjunctions formally | 30 : 70 |
| 34 | Adjoint Functor Theorems: Unified | Ch 23 proves GAFT + SAFT | Unified framing (Freyd's reduction?); enriched AFT; locally presentable case | 50 : 50 |
| 35 | Distributive Laws and Composed Monads | **Not in Vol II** | Distributive laws, composed monads, Beck's distributive-law theorem | 0 : 100 |
| 36 | The Formal Landscape | Ch 24 is Vol II synthesis | Final synthesis: enriched/2-categorical landscape, forward pointers | 30 : 70 |

**Pure new chapters:** 26 (Ends/Coends), 35 (Distributive Laws).
**Mostly new with Vol II setup:** 25, 27, 30, 31, 32, 33, 36.
**Synthesis/unification chapters:** 28, 29, 34.

---

## 5. Dependency order for drafting

Vol II made promises that constrain Vol III's drafting order. **Coends and ends are the
foundational missing piece** — Ch 26 has to come early because Ch 27, 28, 30, 31 all
build on it. Suggested order:

1. **Ch 25 (2-cats/bicats)** — extends Ch 22 directly; lowest-risk warm-up; provides 2-categorical language for later chapters.
2. **Ch 26 (Ends/Coends)** — prerequisite for everything weighted/enriched-formal.
3. **Ch 27 (Weighted Limits)** — uses Ch 26.
4. **Ch 28 (Formal Yoneda)** — uses Ch 26 (ninja Yoneda) and Ch 27 (weighted version).
5. **Ch 29 (Monoidal Coherence)** — independent; can slot in anytime.
6. **Ch 30 (Day Convolution)** — uses Ch 26, 27.
7. **Ch 31 (Kan Extensions General)** — uses Ch 26, 27.
8. **Ch 32 (Formal Theory of Monads)** — uses Ch 25.
9. **Ch 33 (Adjunctions Formal)** — uses Ch 25.
10. **Ch 34 (AFTs Unified)** — uses Ch 31, 33.
11. **Ch 35 (Distributive Laws)** — uses Ch 32.
12. **Ch 36 (Formal Landscape)** — synthesis last.

A natural sub-batch boundary: after Ch 28 the "foundational quartet" is in place; the remaining eight chapters could be a second batch with a mid-volume push.

---

## 6. Open decisions before drafting

These should be confirmed with the user before Ch 25 begins. Convert pending items
to decisions in `working_plan.md` once answered.

1. **Vol III pedagogy environment.** Vol II uses `prooflog` for proofs. Should Vol III
   default to `prooflog` even more aggressively (every multi-step argument), or introduce
   a still-denser environment (e.g., a "diagram chase" environment) for the highest-density chapters?
2. **Cycle stages in Vol III.** The directive says "minimal prose expansion." Should
   Informally/Expanding be skipped routinely in Vol III, leaving most chapters as
   Formalizing → (Reorganizing) → Formally? Or only for some chapters?
3. **Chapter length target.** Vol I averaged ~600 lines, Vol II ~430 lines. Vol III target:
   propose ~250–350 lines per chapter? Or let topic length drive it freely?
4. **Ch 28 vs. Ch 15+20 redundancy.** Ch 28 ("Formal Yoneda") risks restating Ch 15 and
   Ch 20. Should it be re-scoped — e.g., explicitly "Yoneda via ends and weighted Yoneda
   in V-Cat" — to avoid recap-feel?
5. **Ch 29 vs. Ch 19 redundancy.** Mac Lane coherence is done in Ch 19. Ch 29's value is
   probably enriched/higher coherence + strictification; confirm scope to avoid recap-feel.
6. **Ch 31 vs. Ch 18 redundancy.** Ch 18 covers Kan extensions thoroughly in `Set`-enriched
   terms. Confirm Ch 31's scope is the enriched/V-Cat generalization.
7. **Ch 34 vs. Ch 23 redundancy.** Confirm Ch 34's "unified" framing is enriched AFT and/or
   the locally-presentable case, not a re-proof of GAFT/SAFT.
8. **Exercises in Vol III.** Continue ~30 Q/A pairs/chapter? Or scale down since the audience
   is expected to be high-familiarity?
9. **Examples policy.** Vol II already used homological algebra, simplicial sets, etc., as
   examples (within enriched CT). Is borrowed-math freely available in Vol III? Or still
   gated to "examples from CT itself + foundations established"?
10. **Pre-flight: retrofit of Ch 1–5.** Still pending from v0.11/v0.12. Block Vol III on it
    or proceed in parallel?
11. **Branch convention for Vol III.** `feature/volume3-v0.14` or similar? Per-volume push
    confirmed by v0.13 directive 2 ("Stop and push after each volume").

---

## 7. Forward pointers from Vols I–II already on the page

Honoring these in Vol III avoids breaking the reader's expectations. Each should be
delivered at the location it was promised:

- **ch14:145** — "Coends are introduced formally in Volume III." → Ch 26.
- **ch22:25–27** — Bicategory-ground preparation. → Ch 25.
- **ch24:288–369** — Preview lists enriched cats, weighted limits, ends/coends, 2-categorical structure as Vol III scope. All four must be substantively delivered (Ch 26, 27, 30, 25 respectively).
- **ch24:127** — "in Volume III, a monad is itself a Kan extension — the left Kan extension along the unit." → Ch 31 or Ch 32 should include this identification.
- **ch24:356–364** — Lists Vol III revisits: limits → weighted; adjunctions → enriched; Yoneda → enriched Yoneda; Kan → enriched Kan via coends; Beck → enriched monadicity. → Ch 27, 33, 28, 31, 32.

---

## 8. Build-discipline reminders (from `CLAUDE.md`)

- Don't rewrite the book on feedback alone — accumulate, then ask for a feature branch.
- `history/` is append-only — write a new `v0.14_*.md` only when a Vol III round closes.
- `notes/` is fair game — update this file and `working_plan.md` freely.
- All book edits go to a named feature branch, reviewed, merged. Confirm the branch name
  with the user when Vol III drafting starts.
