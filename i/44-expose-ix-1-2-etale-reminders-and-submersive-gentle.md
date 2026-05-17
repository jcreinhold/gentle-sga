# Exposé IX §§IX.1–IX.2 (gentle): reminders on étale morphisms and submersive morphisms

## What this file is about

An étale map is the algebraic version of a covering: it spreads each point of the base out into a small constellation of
points above it, with no folding, no branching, and no infinitesimal smearing. Étale maps are unusually rigid, and much
of the geometry built on them — fundamental groups, Galois theory in families, comparison with topology — depends on
that rigidity. This file collects the reminders that the next stretch of the book will rely on, repackaged so they work
without the noetherian assumptions earlier proofs used.

A second piece of vocabulary enters here. A map can fail to be a covering and still convey enough topological
information that any sensible question about its image lifts cleanly to the source. Maps with that property are called
submersive, and they are the right setting for the gluing theorems of the next file.

## Opening: from descent of schemes to descent of étale schemes

File 43 closed Exposé VIII with the five effectivity criteria: faithfully flat quasi-compact `g : S′ → S` is an
unconditional descent morphism in `Sch`, but the descent datum on `X′ → S′` is effective for the *underlying scheme*
only when one of five hypotheses holds (radicial; finite locally free with affine fibres; ample invertible sheaf with
descent datum; quasi-affine; quasi-finite separated noetherian). Outside those cases there are honest counterexamples of
Serre and Hironaka.

Exposé IX takes the same machinery and asks a sharper question: what happens if we restrict the fibred category from
*all* `S`-preschemes to the **fibred subcategory of étale `S`-preschemes**? The étale hypothesis is rigid — sections are
open subsets, morphisms are determined by their graphs, the cotangent complex is zero — and rigidity should turn the
Exposé VIII counterexamples into effective descent statements. That is exactly what happens, and it happens for a wider
class of base morphisms `g : S′ → S`: every *universally submersive* `g` is an unconditional descent morphism for étale
morphisms (file 45, IX.3), and effective descent holds under five sharper hypotheses (file 45, IX.4), including the
conceptual gem **IX.4.10: a finite radicial surjective base change induces an equivalence between étale categories** —
*topological invariance of the étale site*.

This file is the preparatory pass for that machinery. We collect the étale reminders we need from file 11 (§I.5–8) and
file 12 (§I.9–11), dropping noetherian hypotheses where descent forces us to handle non-noetherian bases such as
`Spec(Â ⊗_A Â)`; and we introduce the topological vocabulary — **submersive** and **universally submersive morphisms** —
that file 45 builds on. The next file is the heart of the matter.

## §IX.1 — Reminders on étale morphisms

<!-- source: IX.1 -->

Exposé I's definition of an étale morphism `f : X → S` (file 11 §I.4) required `S` to be locally noetherian, and so did
all the proofs in the body of Exposé I. Descent forces us out of that setting. If `A` is a noetherian local ring, `Â`
its completion, and we want to apply faithfully flat descent along `Spec(Â) → Spec(A)`, the fibre product
`Spec(Â ⊗_A Â)` enters the argument — and `Â ⊗_A Â` is *not* noetherian in general. The first step of Exposé IX is
therefore to repackage étale morphisms in a way that works on arbitrary preschemes.

### Mini-introduction: finite presentation

A morphism `f : X → S` is **of finite presentation at `x ∈ X`** when, near `x`, the morphism factors as

```text
Spec(B) → Spec(A)    with    B = A[t_1, ..., t_n] / (f_1, ..., f_m),
```

i.e. `B` is generated over `A` by finitely many variables modulo finitely many relations. *Finite presentation* is the
non-noetherian analogue of *finite type*: when `S` is locally noetherian the two notions coincide (every ideal in a
noetherian ring is already finitely generated, so any finite-type relation set generates a finitely-presented ideal),
but on a general base the relation-finiteness matters. File 41 (§VIII.3.6) gave the working definition; we use the same
convention here.

### IX.1.1 — Definition (étale without noetherian hypotheses)

<!-- source: IX.1.1 -->

**Definition IX.1.1.** Let `f : X → S` be a morphism of preschemes and `x ∈ X`. We say `f` is **étale at `x`** (or `X`
is **étale over `S` at `x`**) when there exist an affine open neighbourhood `U` of `s = f(x)` in `S`, an affine open
neighbourhood `V` of `x` over `U`, a **noetherian** affine scheme `U_0`, an affine `U_0`-scheme `V_0` which is étale
over `U_0` *in the sense of file 11 §I.4*, a morphism `U → U_0`, and a `U`-isomorphism

```text
V ≃ V_0 ×_{U_0} U.
```

We say `f` is **étale** when it is étale at every `x ∈ X`.

*This definition says:* every point of `X` has an affine neighbourhood that comes by base change from an étale morphism
over a noetherian affine. The noetherian case is the only one we ever defined, and we use base change to extend it to
non-noetherian bases.

When `S` is locally noetherian, IX.1.1 agrees with file 11 (§I.4)'s definition: take `U_0 = U` and `V_0 = V`. For a
general `S`, the definition is *designed* so that the propositions of file 11 (§I.5–I.8) and file 12 (§I.9–I.10) reduce
immediately to the noetherian case. EGA IV §17 carries out this reduction systematically. We invoke that EGA section as
a black box; for the gentle reader, "everything that worked over a locally noetherian base in file 11–12 still works on
arbitrary preschemes" is the working summary.

### IX.1.2 — Remarks on the consequences

<!-- source: IX.1.2 -->

**Remark IX.1.2.** If `f` is étale at `x`, then `f` is of **finite presentation at `x`** (file 41 VIII.3.6), the local
ring of `x` in the fibre `f⁻¹(s)` is a **finite separable extension** of `κ(s)`, and `f` is **flat at `x`**.

The converse is true: a morphism that is of finite presentation, flat at `x`, and with finite separable fibre is étale
at `x`. The proof is delicate (a Krull-dimension argument together with the rigidity statement of file 11 §I.4); we
follow Grothendieck and *not* take this characterisation as the definition. The black-box reference is EGA IV §17.6.

### IX.1.3 — Base change preserves étaleness

<!-- source: IX.1.3 -->

**Proposition IX.1.3.** If `f : X → S` is étale, then for every morphism `S′ → S` the base change `f′ : X ×_S S′ → S′`
is étale.

This is automatic from IX.1.1: base change commutes with the noetherian template. ∎

Consequently, étale morphisms form a **fibred subcategory** of the category of arrows of `Sch` (file 35 §VI.5). The
remainder of Exposé IX is the study of its descent properties.

### IX.1.4 — Open immersion = étale + radicial

<!-- source: IX.1.4 -->

**Proposition IX.1.4.** A morphism `f : X → S` is an **open immersion** iff it is **étale** and **radicial**.

*Recall.* A morphism `f` is **radicial** when the induced map on points is injective and, for every `x ∈ X`, the residue
extension `κ(f(x)) → κ(x)` is purely inseparable (file 11 I.5.1 calls this *injective + radicial on residues*; see also
file 10 §I.3 for the definition).

The forward direction is immediate; the converse is file 11 I.5.1, restated here without noetherian hypotheses via
IX.1.1. ∎

It follows that for `X` étale over `S`, every section `s : S → X` of `f` is an **open immersion**.

### IX.1.5 — Sections of étale morphisms

<!-- source: IX.1.5 -->

**Corollary IX.1.5.** Let `X` be étale over `S`. Then there is a one-to-one correspondence between sections of
`X over S` and **radicial surjective opens `Γ ⊂ X`**, i.e. open subsets `Γ ⊂ X` such that the structural morphism
`Γ → S` is radicial and surjective.

*Proof sketch.* A section `s : S → X` has image an open subset (IX.1.4) on which `s` is an isomorphism. Conversely a
radicial surjective open `Γ → S` is an isomorphism by IX.1.4 again, so its inverse provides a section. ∎

If `X` is moreover **separated over `S`**, then `Γ` is automatically open *and closed* in `X`; this strengthening is not
needed for what follows.

> **Slogan.** *Sections of an étale `S`-prescheme are exactly the saturated open subsets that are radicial and
> surjective onto `S`.*

### IX.1.6 — Graphs of `S`-morphisms with étale target

<!-- source: IX.1.6 -->

**Corollary IX.1.6.** Let `Y → S` be étale, and let `X` be any `S`-prescheme. The map sending an `S`-morphism
`f : X → Y` to its graph

```text
Γ_f = {(x, f(x)) : x ∈ X} ⊂ X ×_S Y
```

is a **bijection** from `Hom_S(X, Y)` onto the set of open subsets `Γ ⊂ X ×_S Y` such that the projection `pr_1 : Γ → X`
is **radicial and surjective**.

*Proof.* Make the base change `Y / S ↝ (X ×_S Y) / X`. Then `X ×_S Y → X` is étale (by IX.1.3), and an `S`-morphism
`f : X → Y` corresponds to a section of `pr_1 : X ×_S Y → X`. Apply IX.1.5 to the latter. ∎

This single corollary is the **key technical lemma** of Exposé IX. File 45 §IX.3 uses it three times:

1. *Injectivity of pull-back on `Hom`s* (IX.3.1) — a morphism is determined by its graph.
1. *Descent of `Hom`s along universally submersive `g`* (IX.3.2) — graphs descend along submersive `g` because saturated
    opens descend (IX.2.3).
1. *Full faithfulness of pull-back when `g` has geometrically connected fibres* (IX.3.4) — connected fibres force the
    graph to descend uniquely.

The geometric content is the **rigidity of étale morphisms**: an `S`-morphism with étale target is detected by the
topology of its graph alone.

### IX.1.7 — Lifting across a nil-ideal thickening

<!-- source: IX.1.7 -->

**Proposition IX.1.7.** Let `S_0 ⊂ S` be the closed subscheme defined by a **quasi-coherent nil-ideal** `𝒥 ⊂ 𝒪_S` — i.e.
`𝒥^n = 0` Zariski-locally, and the closed immersion `S_0 → S` is a homeomorphism on underlying spaces. Then the functor

```text
X  ↦  X ×_S S_0
```

from étale `S`-preschemes to étale `S_0`-preschemes is an **equivalence of categories**.

*Proof.* The full-faithfulness comes from IX.1.6: a morphism `X → Y` of étale `S`-preschemes is determined by the open
subset of its graph in `X ×_S Y`, and the closed immersion `S_0 → S` is a homeomorphism, so the same open subset detects
morphisms over `S_0`. Essential surjectivity (lifting an étale `X_0 → S_0` to an étale `X → S`) is file 11 I.8.3
restated without noetherian hypotheses, again via EGA IV §17. ∎

The geometric content: **étale topology does not see nilpotents.** An étale cover of `S_0 = S_{red}` (or of any
infinitesimal thickening's underlying reduced scheme) lifts canonically to an étale cover of `S`.

### IX.1.8 — Complete-local: finite étale lifts from the residue field

<!-- source: IX.1.8 -->

**Corollary IX.1.8.** Let `A` be a **complete noetherian local ring** with residue field `k`. The functor

```text
B  ↦  B ⊗_A k
```

is an **equivalence** from the category of **finite étale `A`-algebras** to the category of finite étale `k`-algebras
(i.e. finite direct products of finite separable extensions of `k`).

*Proof sketch.* Apply IX.1.7 to the sequence of artinian thickenings `Spec(A / 𝔪^n) ⊃ Spec(k)` and pass to the inverse
limit using **Grothendieck's existence theorem** for coherent sheaves on a proper scheme over a complete local base (EGA
III §5, recorded in the appendix as [`grothendieck-existence`](appendix-black-boxes.md) and used already in files 18,
21, 22, 43). The existence theorem says formal sheaves algebraise on a proper scheme; "proper" includes "finite", so
finite étale `A_n`-algebras assembled along an inverse system of thickenings algebraise to a finite étale `A`-algebra. ∎

*Geometric content.* The étale fundamental group `π₁(Spec(A), \bar k) = π₁(Spec(k), \bar k) = Gal(\bar k / k)` for `A`
complete local; in particular **completion does not change the étale fundamental group of a complete local base**. This
is the local analogue of the topological-invariance theorem IX.4.10 (file 45).

### IX.1.9 — Finite étale = locally free with separable fibres

<!-- source: IX.1.9 -->

**Proposition IX.1.9.** A morphism `f : X → S` is an **étale covering** of `S` (i.e. finite and étale) iff
`X = Spec_S(𝒜)` for some **𝒪_S-algebra 𝒜** that is

1. **locally free** of finite type as an `𝒪_S`-module, and
1. fibrewise **separable**: for every `s ∈ S`, the algebra `𝒜_s ⊗_{𝒪_s} κ(s)` is a finite product of finite separable
    extensions of `κ(s)`.

This restates file 12 I.9.1/I.10.1 in the non-noetherian form. The proof is unchanged: locally free + separable fibre
algebra = flat + finite fibres + unramified = finite étale; conversely a finite étale `f` is flat with finite separable
fibres, so `f_*𝒪_X` is locally free with separable fibre algebra. ∎

### IX.1.10 — Proper + complete-local: étale coverings descend from the special fibre

<!-- source: IX.1.10 -->

**Theorem IX.1.10.** Let `S = Spec(A)` with `A` a **complete noetherian local ring** with residue field `k`. Let `X` be
a **proper `S`-scheme** and `X_0 = X ×_S Spec(k)` its special fibre. Then the **restriction functor**

```text
X′  ↦  X′ ×_X X_0
```

is an **equivalence** from the category of étale coverings of `X` to the category of étale coverings of `X_0`.

This is the deepest step of §IX.1. Two parts:

- **Fully faithful.** A morphism between étale coverings of `X` is determined by its restriction to `X_0`, by IX.1.6
    applied to the graph in `X′ ×_X Y′ → X′`, since `X_0 → X` is a homeomorphism modulo nilpotents *on each artinian
    thickening*. The Theorem on Formal Functions (EGA III §4) is invoked here to assemble the artinian thickenings into
    the proper map `X_n → X`; this part of IX.1.10 does **not** require the existence theorem of EGA III §5. The cleaner
    statement: any *formal* isomorphism of étale coverings comes from a global isomorphism, by formal functions alone.
- **Essential surjective.** Given an étale covering `X_0′ → X_0`, the artinian thickenings `X_0′ → X_0 ⊂ X_n` lift
    uniquely (by IX.1.7) to a *formal* étale covering of `X̂`. The **Grothendieck existence theorem** (EGA III §5) is
    needed *here* to algebraise that formal covering to a global étale `X′ → X`.

> **Caveat (load-bearing in file 45).** The proof of IX.4.12 in file 45 — descent of finite étale coverings along proper
> surjective `g : S′ → S` — only uses **the fully-faithful direction** of IX.1.10. So IX.4.12 does **not** require the
> EGA III §5 existence theorem; it requires only the Theorem on Formal Functions. We will flag this when we get there.

## §IX.2 — Submersive and universally submersive morphisms

<!-- source: IX.2 -->

The descent of Exposé VIII for *schemes* was driven by a topological fact: a faithfully flat quasi-compact `g` makes `S`
a *quotient topological space* of `S′` (VIII.4.3, file 41). That is the topological half of "descent works." In Exposé
IX we extract this topological half as a self-standing definition — **submersive morphism** — and prove descent of étale
morphisms relative to *any* universally submersive `g`, not only faithfully flat quasi-compact ones.

### IX.2.1 — Definition

<!-- source: IX.2.1 -->

**Definition IX.2.1.** A morphism `g : S′ → S` of preschemes is **submersive** when

1. `g` is **surjective** (every point of `S` is hit), and
1. `S` carries the **quotient topology** from `S′`: a subset `U ⊂ S` is open iff `g⁻¹(U) ⊂ S′` is open.

We say `g` is **universally submersive** when, for every morphism `T → S`, the base change `g_T : S′ ×_S T → T` is
submersive.

The set-theoretic intuition: a *quotient map* in topology is a continuous surjection that *generates* the topology of
the target — every open of the target is the image of a saturated open of the source. **Submersive** is the schematic
word for the same thing.

The properties one immediately checks:

- The **composition** of two submersive (resp. universally submersive) morphisms is submersive (resp. universally
    submersive).
- A **base change** of a universally submersive morphism is universally submersive (built into the definition).
- If `fg` is submersive (resp. universally submersive) then so is `f`. (The reverse implication can fail.)

> **Slogan.** *A submersive morphism is a continuous surjection that generates the topology of the target from the
> topology of the source. A universally submersive morphism is one that does the same after any base change.*

### IX.2.2 — Examples

<!-- source: IX.2.2 -->

The two examples we will use throughout files 45–47:

**Example (a).** A surjective morphism that is **open**, or **closed**, is submersive: if `g⁻¹(U)` is open then
`U = g(g⁻¹(U))` is open. In particular every *surjective universally closed* or *surjective universally open* morphism
is universally submersive. As a concrete case, every **proper surjective** morphism is universally submersive.

**Example (b).** A **faithfully flat quasi-compact** morphism is universally submersive. This is the content of VIII.4.3
(file 41): faithfully flat quasi-compact `g` makes `S` a quotient of `S′`, and faithful flatness is stable under
arbitrary base change. So `g` is universally submersive.

These are the two main classes that supply descent morphisms in §IX.4: example (a) feeds IX.4.7 (finite surjective) and
IX.4.12 (proper surjective), example (b) feeds IX.4.1 (faithfully flat quasi-compact) and IX.4.11 (faithfully flat
quasi-compact radicial).

### IX.2.3 — Saturated opens descend along submersive `g`

<!-- source: IX.2.3 -->

**Proposition IX.2.3.** Let `g : S′ → S` be submersive, and set `S″ = S′ ×_S S′`. Then the diagram

```text
Open(S)  →  Open(S′)  ⇉  Open(S″)
```

is an **equaliser**: an open subset `U′ ⊂ S′` is of the form `g⁻¹(U)` for a (necessarily unique) `U ⊂ S` iff its two
pull-backs `p_1⁻¹(U′)` and `p_2⁻¹(U′)` to `S″` agree.

*Proof.* Uniqueness of `U` is surjectivity of `g`. For existence: if the two pull-backs agree, then `U′` is the inverse
image of its set-theoretic image `U := g(U′) ⊂ S` (because `g` is surjective and `U′` is *saturated for the fibre
relation*), and `g⁻¹(U) = U′` is open, so `U` is open by the quotient-topology property. ∎

This is the categorical underpinning of all of §IX.3 in file 45. Graphs of `S`-morphisms with étale target are saturated
opens (by IX.1.6); IX.2.3 says they descend along submersive `g` whenever they descend on the level of underlying sets.
The rest is bookkeeping.

> **Slogan.** *Open subsets of `S` descend from saturated open subsets of `S′` along any submersive `g`.*

### IX.2.4 — Descent of properties of morphisms

<!-- source: IX.2.4 -->

**Proposition IX.2.4.** Let `g : S′ → S` be universally submersive, and let `f : X → Y` be an `S`-morphism with base
change `f′ : X′ → Y′` along `g`.

- For `f` to be **open** (resp. **closed**), it suffices that `f′` be so.
- For `f` to be **universally open** (resp. **universally closed**, **separated**), it is necessary and sufficient that
    `f′` be so.
- If `g` is moreover **quasi-compact** and `f` is **locally of finite type**, then `f` is **proper** iff `f′` is proper.

*Proof.* The open / closed half is IX.2.3 applied to the underlying topological spaces. For the universal half, run the
same argument after an arbitrary base change `T → Y`; universality of `g` survives this base change. The properness
statement: if `f′` is proper then `f′` is quasi-compact, hence (since `g` is quasi-compact) `f` is quasi-compact
(VIII.3.3, file 41), hence of finite type; combined with separatedness and universal closedness of `f` from the prior
bullets, `f` is proper. ∎

This proposition is what makes §IX.4's reductions work: properties like "open," "closed," "proper" descend along
universally submersive `g`, so the *property* of being a finite étale covering — which is closed under base change — can
be checked after pulling back to `S′`.

### IX.2.5 — Local-finite test over a complete local base

<!-- source: IX.2.5 -->

**Proposition IX.2.5.** Let `S = Spec(A)` with `A` a **complete noetherian local ring**, let `S′ → S` be of finite type,
and assume that the fibre `S′_s` over the closed point `s ∈ S` is **finite**. Form `S″ → S′` as the sum scheme

```text
S″  :=  ⨿_{s′ ∈ S′_s} Spec(𝒪_{S′, s′}),
```

a finite `S`-scheme. Then `g : S′ → S` is universally submersive iff the natural morphism `S″ → S′` is **surjective**.

*Proof.* `(⇐)` *Sufficiency.* The map `S″ → S′` is a local isomorphism at every closed point of `S′_s`, hence open;
combined with surjectivity it makes `S″ → S′` universally submersive by IX.2.2 (a), and the composite `S″ → S′ → S` is
finite surjective, hence universally submersive. The "if `fg` is universally submersive then so is `f`" implication in
IX.2.1 gives `g` universally submersive.

`(⇒)` *Necessity.* Suppose `S″ → S′` is **not** surjective. We construct a base change witnessing failure of universal
submersiveness. Pick a point `t ∈ S′` not in the image of `S″`; let `T = Spec(B)` be the spectrum of a discrete
valuation ring with image `\{s, t\}` in `S` (this exists by an EGA IV §7 construction: pull back to the local ring at
`s` along `S → S` and lift `t` along the generic point). Set `T′ = S′ ×_S T`. The image of `S″ → S′` is open (local
isomorphism on a finite cover of the closed fibre) and **contains** the closed fibre `S′_s` but **misses** the open
fibre `S′_t`. Pulling back: the inverse image of the open image in `T′` is open and identical to the inverse image of
the *closed point* of `T`. Hence `T′ → T` is not submersive, and `g` is not universally submersive. ∎

We use IX.2.5 once, in §IX.4.8 (file 45), to reduce "universally submersive + finite type + quasi-finite" to "finite
surjective."

### IX.2.6 — Valuative criterion for universal submersion

<!-- source: IX.2.6 -->

**Proposition IX.2.6.** Let `g : S′ → S` be of **finite type** with `S` locally noetherian. Then `g` is **universally
submersive** iff for every `S`-scheme `T = Spec(B)` with `B` a discrete valuation ring, setting `T′ = S′ ×_S T`, the
inverse image of the **closed point** of `T` in `T′` is **non-open**.

*Proof sketch.* `(⇒)` Reverse the construction in the proof of IX.2.5: if there is some DVR `B` whose closed point has
an open inverse image in `T′`, this exhibits a base change after which `g` fails submersion.

`(⇐)` Suppose `g` is not universally submersive. Then some base change `T → S` makes the pull-back `T′ → T`
non-submersive; we find a `T` for which the closed-point inverse image is open. Using **constructibility** of opens
under finite-type morphisms (file 27 IV.6.3) we may reduce `T` to the spectrum of a DVR. ∎

This is the valuative criterion that lets us *test* universal submersion on a single DVR base — the analogue of the
valuative criterion for properness (file 14 II.1.5) and for separatedness.

## Closing pointer to file 45

The two technical inputs that file 45 §IX.3 (descent of étale morphisms) and §IX.4 (effectivity criteria) need from this
file:

1. **The graph theorem IX.1.6.** Every `S`-morphism `X → Y` with étale target `Y / S` is encoded by an open subset of
    `X ×_S Y` with radicial-surjective first projection.
1. **The saturated-opens equaliser IX.2.3.** Saturated open subsets of `S′` descend uniquely along any submersive
    `g : S′ → S`.

Combining these two: an `S`-morphism with étale target is an open subset on `X ×_S Y` satisfying a topological condition
that descends along submersive base change. That is the engine of §IX.3.

The two étale facts that file 45 §IX.4 needs:

1. **The lifting theorem IX.1.7** (étale across a nil-ideal): used in IX.4.10 (topological invariance) to bridge `S′`
    and `S` whose underlying spaces coincide but whose structure sheaves differ by a nil-ideal.
1. **The proper-complete-local theorem IX.1.10** (étale coverings descend from the special fibre): used in IX.4.12
    (descent of finite étale along proper surjective `g`).

With these in hand, file 45 establishes that universally submersive `g` is unconditionally a descent morphism for étale
preschemes (§IX.3), and that effectivity holds under five sharper hypotheses (§IX.4), the most striking of which is the
topological invariance IX.4.10. File 46 then re-reads the descent equivalence as a calculation of `π₁(S, a)`, and file
47 turns the descent equivalence for proper surjective with geometrically connected fibres into the fundamental exact
sequence `1 → π₁(X̄_0) → π₁(X) → π₁(S) → 1`.
