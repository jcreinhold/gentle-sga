# Exposé IX §§IX.3–IX.4 (gentle): descent of étale morphisms and effectivity criteria

## What this file is about

Covering maps are rigid enough that knowing one over a covering of the base should be enough to recover it over the
base itself. The previous file laid out the étale vocabulary; this file delivers on the promise. When the base is
covered in any reasonable way — by something flat, finite, finite-type, or proper — a covering of the cover descends
without obstruction to a covering of the base. Where the corresponding statement for general geometric objects needed a
list of fine-print conditions, the étale version is essentially free.

One consequence is especially clean. A map that is finite and identifies points without separating their tangent
directions induces no change at all on the world of coverings above. The covering theory cannot tell two such bases
apart — a topological-invariance principle this file makes precise.

## Opening: from prerequisites to the geometric climax

File 44 collected the two technical inputs we need from Exposé I: the **graph theorem IX.1.6** ("`S`-morphisms with
étale target are open subsets of the fibre product with radicial-surjective first projection") and the **saturated-
opens equaliser IX.2.3** ("open subsets of `S` descend uniquely from saturated open subsets of `S′` along any
submersive `g`"). An open `U ⊆ X` is **saturated** relative to a morphism `f : X → S` when `U` is a union of fibres
of `f` — equivalently, `U = f^{-1}(f(U))`. Combined: an `S`-morphism with étale target is *exactly the data* of an
open subset of `X ×_S Y` that descends along submersive base change. This is the engine of §IX.3.

The present file extracts the consequences. §IX.3 proves that every **universally submersive** `g : S′ → S` is a
*descent morphism* for the fibred category of étale preschemes — unconditionally, and with no hypothesis on whether
the candidate `X′` is qf, finite, or finite type. §IX.4 then asks when this descent is *effective*: when does a
descent datum on `X′ → S′` actually come from an `X → S`? Five sufficient hypotheses give five effectivity theorems,
each subtler than the last:

- **IX.4.1** — `g` faithfully flat quasi-compact ⇒ effective for étale separated finite-type schemes.
- **IX.4.7** — `g` finite surjective of finite presentation ⇒ same.
- **IX.4.9** — `g` finite-type surjective universally open + `S` locally noetherian ⇒ same.
- **IX.4.10** — `g` finite radicial surjective ⇒ **equivalence** of étale categories.
- **IX.4.12** — `g` proper surjective of finite presentation ⇒ effective for *finite étale* coverings.

The fourth, **IX.4.10**, is the **topological invariance of the étale site**: a universal homeomorphism (finite +
radicial + surjective) induces an equivalence of étale categories. This unpacks the load-bearing black-box row
[`univ-homeo-equiv`](appendix-black-boxes.md#univ-homeo-equiv) that we have been citing since file 06.

## §IX.3 — Descent of morphisms of étale preschemes

<!-- source: IX.3 -->

### IX.3.1 — Injectivity of `f ↦ f′` for étale target

<!-- source: IX.3.1 -->

**Proposition IX.3.1.** Let `g : S′ → S` be a **surjective** morphism of preschemes, let `X` and `Y` be two
preschemes over `S`, and let `X′`, `Y′` be their inverse images over `S′`. If `Y / S` is **unramified**, then the
canonical map

```text
Hom_S(X, Y)  →  Hom_{S′}(X′, Y′),    f ↦ f′ = f ×_S id_{S′},
```

is **injective**.

*This result says:* a morphism with unramified target is *uniquely* determined by its base change to `S′`, provided
`S′ → S` is surjective.

*Proof.* By IX.1.6 (file 44), an `S`-morphism `f : X → Y` with `Y / S` étale is encoded by its graph `Γ_f`, an open
subset of `Z = X ×_S Y` whose first projection to `X` is radicial and surjective. More generally, for `Y / S` only
*unramified* the same conclusion holds: the graph is a *locally closed* subset of `Z` with the same projection
properties (file 11 I.5.1; the radicial+surjective characterisation only uses unramifiedness, not étaleness).

Now `Z′ = Z ×_S S′ = X′ ×_{S′} Y′` and the projection `Z′ → Z` is the base change of `g`, hence surjective. So the
underlying set of `Γ_f ⊂ Z` is *determined* by the underlying set of its pullback `Γ_{f′} = Γ_f ×_S S′ ⊂ Z′`. Two
morphisms `f_1, f_2` with the same `f_1′ = f_2′` therefore have `Γ_{f_1} = Γ_{f_2}` as subsets of `Z`, hence by
IX.1.6 we conclude `f_1 = f_2`. ∎

### IX.3.2 — The descent diagram for `Hom`s

<!-- source: IX.3.2 -->

**Proposition IX.3.2.** Let `g : S′ → S` be a **universally submersive** morphism, set `S″ = S′ ×_S S′`, let `X` and
`Y` be `S`-preschemes, let `X′`, `Y′` be their inverse images over `S′`, and let `X″`, `Y″` be their inverse images
over `S″`. If `Y / S` is **étale**, then the canonical diagram of maps

```text
Hom_S(X, Y)  →  Hom_{S′}(X′, Y′)  ⇉  Hom_{S″}(X″, Y″)
```

is an **equaliser**: an `S′`-morphism `f′ : X′ → Y′` is the pullback of an `S`-morphism `f : X → Y` iff the two
pullbacks `p_1^*(f′)` and `p_2^*(f′)` from `Hom_{S″}(X″, Y″)` agree.

*This result says:* **every universally submersive morphism is a descent morphism for the fibred category of étale
preschemes.** Descent data on a single `S′`-morphism with étale target are *automatically effective*.

*Proof.* Injectivity of `Hom_S(X, Y) → Hom_{S′}(X′, Y′)` is IX.3.1 (using `g` surjective, which follows from
universal submersion).

For the surjectivity onto the equaliser: given `f′ : X′ → Y′` with `p_1^*(f′) = p_2^*(f′)` in `Hom_{S″}(X″, Y″)`,
we want an `f : X → Y` with `f′ = f ×_S id_{S′}`. By IX.1.6 applied on `S′`, `f′` corresponds to an open subset
`Γ′ ⊂ Z′ = X′ ×_{S′} Y′` with `Γ′ → X′` radicial and surjective. The equaliser hypothesis says the two pullbacks
of `Γ′` to `Z″ = Z′ ×_{Z} Z′ = Z ×_S S″` (where `Z = X ×_S Y`) agree — i.e. `Γ′` is **saturated** for the
equivalence relation defined by `Z′ → Z`.

Now `Z′ → Z` is the base change of `g : S′ → S` to `Z`, hence universally submersive (base change preserves
universally submersive, IX.2.1). By IX.2.3, the saturated open subsets of `Z′` correspond bijectively to open
subsets of `Z`. So `Γ′ = π^{-1}(Γ)` for a unique open subset `Γ ⊂ Z`, where `π : Z′ → Z`.

It remains to check that `Γ → X` is radicial and surjective (so that, by IX.1.6 again, `Γ` is the graph of an
`S`-morphism `f : X → Y`). Radiciality and surjectivity descend along the surjective map `X′ → X` (this is part of
file 41 VIII.3.1: surjectivity and radiciality descend along universally submersive base change). Hence `Γ` is the
graph of some `f : X → Y`, and `Γ′` is its pullback, so `f′` is the pullback of `f`. ∎

> **Slogan.** *Descent of `S`-morphisms with étale target is descent of saturated open subsets along universally
> submersive base change.*

### IX.3.3 — Universally submersive = descent morphism for étale preschemes

<!-- source: IX.3.3 -->

**Corollary IX.3.3.** Let `g : S′ → S` be universally submersive. Then `g` is a **morphism of descent** for the
fibred category of étale preschemes over `Sch`.

*Proof.* Specialising IX.3.2 to `X, Y` both étale over `S`, we get the descent equaliser for
`Hom_{Sch}((X, Y))` whenever the target is étale. Since the fibred category of étale preschemes is closed under base
change (IX.1.3) and the descent equaliser for morphisms is the defining property of a descent morphism (file 38
VI.12.1), `g` is a descent morphism. ∎

> **Caveat.** "Descent morphism" is *strictly weaker* than "effective descent morphism." The corollary asserts that
> descent data on étale `S′`-preschemes are *uniquely determined* by `X′` plus the cocycle — but does **not** assert
> that every such descent datum *comes from* an étale `X / S`. The five theorems of §IX.4 supply the additional
> hypotheses under which effectivity holds. Grothendieck remarks (`IX.3.3` body, file `09-descente-…`, page 233):

> > I do not know, however, whether it is necessarily a morphism of **effective** descent for the fibred category in
> > question, even under the additional hypotheses that `S` be noetherian and `g` of finite type, and even
> > restricting to étale coverings.

> Sixty years later this is still open in full generality (cf. Stacks Project tag 0244 for the modern packaging).

### IX.3.4 — Geometrically connected fibres ⇒ fully faithful descent

<!-- source: IX.3.4 -->

**Corollary IX.3.4.** Let `g : S′ → S` be **universally submersive** with **geometrically connected fibres**, i.e.
for every `s ∈ S` and every extension `K / κ(s)`, the fibre `g⁻¹(s) ⊗_{κ(s)} K` is connected. Then:

1. If `S` is connected, then `S′` is connected.
2. The functor `g^*` from étale `S`-preschemes to étale `S′`-preschemes is **fully faithful**.

*This result says:* under geometric connectedness of fibres, the descent functor `g^*` is *fully faithful* — i.e.
descent data are *automatic* whenever they exist, and `g^*` is an equivalence onto its essential image.

*Proof.* (1) An open-and-closed subset `U ⊂ S′` is saturated for the equivalence relation `Z(g) = S′ ×_S S′ → S′`
because the fibres of `g` are connected and `U` is open-and-closed: each fibre lies entirely in `U` or entirely in
the complement. Since `g` is universally submersive, IX.2.3 implies `U = g⁻¹(V)` for some `V ⊂ S` open. The same
argument applied to the complement gives `V` closed. So `V` is open-and-closed; if `S` is connected, `V = ∅` or
`V = S`, hence `U = ∅` or `U = S′`, so `S′` is connected.

(2) Let `X, Y` be étale over `S`, and let `u′ : X′ → Y′` be an `S′`-morphism. By IX.3.3 we need to verify that the
two pullbacks `u_1″, u_2″ : X″ ⇉ Y″` of `u′` agree on `S″ = S′ ×_S S′`. The subscheme of `S″` on which `u_1″` and
`u_2″` agree is the inverse image of the diagonal of `Y″` over `S″`, an open subprescheme of `S″` whose fibres are
**closed in the fibres of `S″ → S`** (the fibres of an étale morphism are sums of separable extensions, hence
separated). So this open subscheme is the inverse image of an open of `S`. Since it contains the diagonal
`S′ ↪ S″`, it contains the (connected) fibre of `S′ → S` over every point of `S`, hence (by the connected-fibres
hypothesis) it contains all of `S″`. Hence `u_1″ = u_2″` everywhere. ∎

> **Slogan.** *Geometrically connected fibres of `g` force the descent equaliser to be automatic; `g^*` is then an
> isomorphism onto its image.*

> **Connection to file 47.** In file 47 we re-read this corollary as the statement that `π₁(S′) → π₁(S)` is
> *surjective* (modulo a base-point matching argument). The π₁ language makes the result transparent: a fully
> faithful pullback functor on étale categories means an *epi* on fundamental groups (file 32 V.6.9).

## §IX.4 — Effectivity criteria

<!-- source: IX.4 -->

The five effectivity criteria. Each follows the same architectural template:

1. State the hypothesis on `g : S′ → S`.
2. Reduce, by IX.4.3 + IX.4.6, to the case where `S` is the spectrum of a complete noetherian local ring.
3. Reduce further to the special fibre using IX.1.8 / IX.1.10 (file 44).
4. Verify effectivity for the residue-field case directly.

The sorites IX.4.2–IX.4.6 are the bookkeeping that makes the reductions work; the substance is in IX.4.1, IX.4.7,
IX.4.9, IX.4.10, IX.4.12.

### IX.4.1 — Faithfully flat quasi-compact: the strongest general criterion

<!-- source: IX.4.1 -->

**Proposition IX.4.1.** Let `g : S′ → S` be **faithfully flat and quasi-compact**. Then `g` is a morphism of
**effective descent** for the fibred category of preschemes **étale, separated, and of finite type** over other
preschemes.

*This result says:* fpqc descent works for the property "étale separated finite-type": every descent datum on such
an `X′ / S′` comes from a *unique* `X / S` étale, separated, and of finite type.

*Proof.* By IX.3.3 (which uses only that fpqc `g` is universally submersive by IX.2.2 (b)), `g` is a descent morphism
for the fibred category of étale preschemes. We need to show that every descent datum on an étale, separated,
finite-type `X′ / S′` is effective.

The descent of "étale separated finite-type" as a property of morphisms follows from IX.1.1 + IX.2.4: étaleness
descends from `X′ / S′` to `X / S` via the non-noetherian definition, separatedness descends by IX.2.4, and
finite type descends by file 41 VIII.3.3.

It remains to descend the *scheme* `X` itself. Here we invoke the file 42–43 machinery:

- `X′` is **quasi-affine** over `S′`. This is a consequence of file 42 VIII.6.2 (quasi-finite separated of finite
  type over noetherian = quasi-affine after reduction) combined with file 42 VIII.6.6 (the noetherian-reduction
  sorites for finite-presentation morphisms over an arbitrary base). The hypothesis "étale of finite type" implies
  "quasi-finite of finite type," and after IX.4.6's reduction to a noetherian local base the conclusion holds.
- *Effective descent of quasi-affine `S′`-preschemes* with descent datum is file 43 VIII.7.9.

Combining the two: `X′` is a quasi-affine `S′`-prescheme with descent datum, hence by VIII.7.9 descends to a
quasi-affine `S`-prescheme `X`, which is étale separated finite-type over `S` because the property descends. ∎

> **Slogan.** *Faithfully flat quasi-compact descent of étale separated finite-type schemes is quasi-affine descent
> plus property descent.*

### IX.4.2 — Reduction along refined covers

<!-- source: IX.4.2 -->

**Corollary IX.4.2.** Let `g : S′ → S` be universally submersive, let `X′` be an étale, separated, finite-type
`S′`-prescheme with descent datum relative to `g`, and let `S_1 → S` be **faithfully flat and quasi-compact**. Form
`S_1′ = S′ ×_S S_1` and `X_1′ = X′ ×_{S′} S_1′`. Then the descent datum on `X′` is effective iff the corresponding
descent datum on `X_1′` (relative to `g_1 : S_1′ → S_1`) is effective.

*Proof sketch.* This is one of the standard sorites of descent theory in categories (Giraud,
[`giraud-descent`](appendix-black-boxes.md#giraud-descent)). The descent-data category is preserved under refinement
of covers; if `S_1 → S` is itself an effective descent morphism (which fpqc `S_1 → S` is by IX.4.1), and `S′ → S`
is at least a descent morphism, then effectivity passes through the refinement. ∎

### IX.4.3 — Local-on-base reduction

<!-- source: IX.4.3 -->

**Corollary IX.4.3.** Let `g : S′ → S` be universally submersive, let `X′ → S′` be étale with descent datum
relative to `g`, and let `\{S_i\}` be a Zariski open cover of `S`. Then the descent datum on `X′` is effective iff,
for every `i`, the descent datum on `X_i′ = X′ ×_{S′} (S′ ×_S S_i)` (relative to `g_i : S′ ×_S S_i → S_i`) is
effective.

*Proof sketch.* Effectivity is Zariski-local on the base (Giraud). The proof packages the Zariski cover as an fpqc
refinement of `S` and applies IX.4.2 in reverse. ∎

### IX.4.4 — Local effectivity around a single point

<!-- source: IX.4.4 -->

**Proposition IX.4.4.** Let `g : S′ → S` be of **finite presentation** and **universally submersive**, let `X′ → S′`
be étale of finite presentation with descent datum, and let `a ∈ S`. There exists an open neighbourhood `U ∋ a` such
that the descent datum on `X_U′ = X′ ×_S U` (relative to `g_U : S′ ×_S U → U`) is effective iff the descent datum
on `X_a′ = X′ ×_S Spec(𝒪_a)` (relative to `g_a : S′ ×_S Spec(𝒪_a) → Spec(𝒪_a)`) is effective.

*Proof sketch.* Necessity is trivial. For sufficiency, assume the descent datum on `X_a′` is effective with descended
scheme `X_a` étale of finite type over `Spec(𝒪_a)`. The standard "passage to a limit of rings" technique
([`ega-iv-limit-of-rings`](appendix-black-boxes.md#ega-iv-limit-of-rings)) extends an étale prescheme over the
filtered colimit `Spec(𝒪_a) = colim_{f ∉ 𝔭_a} Spec(A_f)` to an étale prescheme over some `Spec(A_f) = U`. After
shrinking `U` if necessary, the isomorphism `X_a′ ≃ X_a ×_{Spec(𝒪_a)} S_a′` extends to an isomorphism
`X_U′ ≃ X_U ×_U S_U′`, and after a further shrink it is compatible with the descent data. ∎

### IX.4.5 — Local-on-points reduction

<!-- source: IX.4.5 -->

**Corollary IX.4.5.** Under the conditions of IX.4.4, the descent datum on `X′` is effective iff, for every `a ∈ S`,
the corresponding descent datum on `X_a′` (relative to the morphism `S′ ×_S Spec(𝒪_a) → Spec(𝒪_a)`) is effective.
When `S` is locally noetherian and `X′` is separated over `S′`, one may replace `𝒪_a` by its **completion** in the
preceding criterion.

*Proof sketch.* The first assertion combines IX.4.4 with IX.4.3. The second uses IX.4.2 with `S_1 = Spec(\hat{𝒪_a})
→ Spec(𝒪_a) = S`, which is faithfully flat by [`completion-flat`](appendix-black-boxes.md#completion-flat). ∎

### IX.4.6 — Reduction to a complete local base with algebraically closed residue field

<!-- source: IX.4.6 -->

**Corollary IX.4.6.** Under the conditions of IX.4.4 with `X′ → S′` separated and `S` locally noetherian, the descent
datum on `X′` is effective iff, for every `S`-scheme `S_1` that is the spectrum of a **complete local ring with
algebraically closed residue field**, the descent datum on `X_1′ = X′ ×_S S_1` is effective.

*Proof sketch.* Combine IX.4.5 with IX.4.2 to reduce first to `S_1 = Spec(\hat{𝒪_a})` and then enlarge the residue
field of `𝒪_a` to its algebraic closure (a faithfully flat base change between complete local rings; cf. EGA 0_IV
§19.8). ∎

### IX.4.7 — Finite surjective: effective descent for separated étale finite-type

<!-- source: IX.4.7 -->

**Theorem IX.4.7.** Let `g : S′ → S` be a **finite**, **surjective**, **finite-presentation** morphism (the
finite-presentation hypothesis follows from the other two when `S` is locally noetherian; in fact it suffices that
`g` be **integral** by EGA IV §8). Then `g` is a morphism of **effective descent** for the fibred category of
preschemes étale, separated, and of finite type over other preschemes.

*This result says:* finite surjective descent is effective for the "étale separated finite-type" fibred category.
The full proof — via noetherian induction on `dim S` — is one of the structural arguments of Exposé IX and we
reproduce it in detail.

*Proof.* As in IX.4.1, `g` is a descent morphism for étale preschemes (IX.3.3 plus the fact that finite surjective
implies universally submersive, IX.2.2 (a)). We must show that every descent datum on étale separated finite-type
`X′ / S′` is effective.

**Step 1: Reduce to `S` noetherian.** By IX.4.3, effectivity is local on `S`. Cover `S` by affine opens; each is the
spectrum of a ring. By IX.4.2 and EGA-style passage to noetherian sub-rings
([`ega-iv-constructibility-via-finite-presentation`](appendix-black-boxes.md#ega-iv-constructibility-via-finite-presentation)),
we reduce to the case where `S = Spec(A)` is the spectrum of a **noetherian** ring.

**Step 2: Reduce to `S` the spectrum of a complete local noetherian ring.** By IX.4.5, it suffices to verify
effectivity at each `a ∈ S` after passing to `Spec(\hat{𝒪_a})`. So we may assume `S = Spec(A)` with `A` a
**complete** noetherian local ring; set `n = dim S = dim A`.

**Step 3: Noetherian induction on `n = dim S`.** The base case `n = -∞` (i.e. `S = ∅`) is vacuous. The base case
`n = 0` (i.e. `A = k` a field) holds by **Step 5** below applied to `T = ∅`.

Assume `n ≥ 1` and the theorem holds for all complete noetherian local rings of strictly smaller dimension. Set
`T = S - \{s\}` where `s` is the closed point of `S`. Then `T` is the complement of a closed point in a noetherian
local scheme; the structural ring `\bigotimes_{s ∈ T} 𝒪_{S, s}` has lower dimension. Set `T′ = S′ ×_S T` and
`X_T′ = X′ ×_{S′} T′`. Then `T′ → T` is finite surjective (inherited from `g`), and `X_T′ → T′` is étale separated
finite-type, with the restricted descent datum.

**Step 4: Decompose `X′ = X_1′ ⨿ X_2′`.** Since `S = Spec(A)` with `A` complete local, `S′` is a finite disjoint
union of spectra of complete local rings (the closed-fibre components of `g`). Each connected component of `S′`
maps to `S` finitely. Decompose `X′` according to which closed points of `S′` it lies over:

```text
X_1′  :=  inverse image in X′ of closed points of S′,    (a finite étale scheme over S′)
X_2′  :=  inverse image in X′ of T′.                       (étale over T′)
```

Then `X′ = X_1′ ⨿ X_2′` *as a scheme over `S′`*, because closed points of `S′` are isolated in `S′` (each is the
closed point of a connected component) and the étale `X′` over `S′` decomposes accordingly.

The descent datum on `X′` decomposes correspondingly: the cocycle on `X″ = q_1⁻¹(X_1′) ⨿ q_1⁻¹(X_2′)` matches the
cocycle on `X′`. (Verification: the morphism `q_i : X″ ⇉ X′` factors `q_i⁻¹(X_1′) ⨿ q_i⁻¹(X_2′)` consistently for
`i = 1, 2`, by the universal property of `X_2′` as the inverse image of `T′`.)

**Step 5: Apply the inductive hypothesis to `X_2′` and the residue-field case to `X_1′`.**

(a) *Descent of `X_2′`.* `X_2′ → T′ → T` is finite surjective of strictly lower dimension. By the inductive
hypothesis, the descent datum on `X_2′` (relative to `T′ → T`) is effective; let `X_2 / T` be the descended scheme.
By the local-effectivity criterion IX.4.4, we get an open neighbourhood `U ⊃ T` of the open subset
`T = S - \{s\}` such that the descent datum on `X_2′ ×_{T′} (T′ ∩ S_U′)` is effective. Since `S - U` is closed in
`S` and contained in `\{s\}`, `U = S` or `U = T`. Either way, `X_2 / T` extends to an étale separated finite-type
scheme over `S` (by Zariski gluing if `U = T`).

(b) *Descent of `X_1′`.* `X_1′ → S′` is **finite étale** (since "étale + closed in a separated finite-type scheme"
forces finiteness over the residue-field component, by a Krull-dimension argument). Apply IX.1.8 (file 44): the
finite étale `X_1′` is determined by its base change to `S_0′ = S′ ×_S Spec(k)`, where `k = κ(s)`. The descent
datum on `X_1′` translates to a descent datum on `X_{1,0}′ / S_0′` along the morphism `g_0 : S_0′ → S_0 = Spec(k)`.
Since `S_0` is a field, `g_0` is faithfully flat quasi-compact (everything over a field is flat); by IX.4.1, the
descent datum on `X_{1,0}′` is effective. Lifting back via IX.1.8 gives an effective descent for `X_1′ / S′`.

Combining (a) and (b): the descent datum on `X′ = X_1′ ⨿ X_2′` is effective.

This completes the induction. ∎

> **Inline aside (technical observation).** The proof of IX.4.7 is **elementary** — it does not use the EGA III §5
> existence theorem ([`grothendieck-existence`](appendix-black-boxes.md#grothendieck-existence)). The induction
> base (`X_1′` finite étale) reduces to IX.4.1 (fpqc descent), which in turn uses only the file 42–43
> quasi-affine-descent machinery. The proof of IX.4.12 below will need the existence theorem (specifically IX.1.10's
> fully-faithful direction); this is the technical distinction Grothendieck flags in the original SGA text.

### IX.4.8 — Universally submersive + quasi-finite + finite type, locally noetherian

<!-- source: IX.4.8 -->

**Corollary IX.4.8.** The conclusion of IX.4.7 holds when `g : S′ → S` is **universally submersive**, **of finite
type**, and **quasi-finite**, with `S` locally noetherian.

*Proof.* By IX.4.6, we may assume `S = Spec(A)` with `A` a complete noetherian local ring. By IX.2.5 (file 44),
there exists a finite surjective `S_1 → S` and an `S`-morphism `S_1 → S′`. (Specifically: `S_1` is the sum of the
spectra of the local rings `𝒪_{S′, s′}` over closed points of the fibre `S′_s`; IX.2.5 says that universally
submersive + quasi-finite + finite-type forces this `S_1 → S′` to be surjective.)

Since `S_1 → S` is finite surjective, IX.4.7 says it is an effective descent morphism. By the descent-theory
sorites of Giraud ([`giraud-descent`](appendix-black-boxes.md#giraud-descent)), `g : S′ → S` is also a strict
effective descent morphism for the fibred category in question (the composite `S_1 → S′ → S` is universally
submersive, and `S_1 → S` is strict effective). ∎

### IX.4.9 — Universally open + finite type + surjective, locally noetherian

<!-- source: IX.4.9 -->

**Corollary IX.4.9.** Let `g : S′ → S` be **of finite type**, **surjective**, and **universally open**, with `S`
locally noetherian. Then `g` is a morphism of **effective descent** for étale separated finite-type preschemes.

*Proof.* By IX.4.6, reduce to `S = Spec(A)` with `A` a complete noetherian local ring. We further reduce to the case
where `A` is **integral**: replace `A` by `\prod A / 𝔭_i` over the minimal primes `𝔭_i`, observe that effectivity
distributes over the product, and verify that the hypotheses on `g` are preserved (universal openness, finite type,
surjectivity all distribute).

With `A` integral complete noetherian local, the **integral-dominant-subscheme** result
([`ega-iv-integral-dominant`](appendix-black-boxes.md#ega-iv-integral-dominant)) provides an integral closed
subscheme `S_1 ⊂ S′`, of finite type and dominant over `S`, passing through some point of `S′_s`. Since `A` is
complete, dominant + finite type + complete-local = **finite**, so `S_1 → S` is finite.

Surjectivity of `S_1 → S`: dominance + complete-local + integral target = surjective (because the image is a closed
subset of `S` containing the generic point of `S`, hence all of `S` since `S` is irreducible).

So `S_1 → S` is finite surjective. By IX.4.7 it is an effective descent morphism for the étale-separated-finite-type
fibred category. The composite `S_1 → S′ → S` is also universally submersive (composite of two universally
submersive morphisms is universally submersive). By Giraud's sorites again, `g : S′ → S` is an effective descent
morphism. ∎

### IX.4.10 — Topological invariance of the étale site

<!-- source: IX.4.10 -->

**Theorem IX.4.10.** Let `g : S′ → S` be **finite**, **radicial**, **surjective**, and of **finite presentation**
(the last condition is automatic when `S` is locally noetherian; in fact it suffices that `g` be **integral**,
**radicial**, and **surjective**, by EGA IV §8). Then the **inverse image functor** `X ↦ X ×_S S′` induces an
**equivalence** from the category of preschemes **étale over `S`** to the category of preschemes **étale over `S′`**.

*This result says:* **the étale site is invariant under universal homeomorphisms.** Étale topology cannot
distinguish `S` from `S′` when `S′ → S` is a universal homeomorphism (= finite + radicial + surjective).

*Proof.* The diagonal `S′ → S′ ×_S S′` is a surjective immersion (file 11 I.5.1 + IX.1.4); hence by IX.1.7 (file
44) the functor `X ↦ X ×_{S′} (S′ ×_S S′)` is an *equivalence* from étale `S′`-preschemes to étale `(S′ ×_S
S′)`-preschemes. Iterating, the same holds for the diagonal `S′ → S′ ×_S S′ ×_S S′`.

It follows from Giraud's descent-theory sorites ([`giraud-descent`](appendix-black-boxes.md#giraud-descent)) that
**every** `X′` étale over `S′` is endowed with **one and only one** descent datum relative to `g : S′ → S`. (The
descent datum is the cocycle in the equivalence relation; since the cocycle category over `S′ ×_S S′` is
*equivalent* to the category over `S′`, every étale `X′` has a unique cocycle.)

By IX.3.3, the inverse image functor `g^*` from étale `S`-preschemes to étale `S′`-preschemes is **fully faithful**.
It remains to verify **essential surjectivity**: every étale `X′ / S′` is isomorphic to the inverse image of some
étale `X / S`.

The question is local on `S` *and on `X′`* (since étaleness is a local property and base change preserves it). So
we may assume `S`, `S′`, and `X′` all **affine**. Then `X′` is separated and of finite type over `S′`, and IX.4.7
applies: the descent datum on `X′` is effective, giving an étale `X / S` with `X ×_S S′ ≃ X′`. ∎

> **Slogan.** *Étale topology cannot see Frobenius, nilpotents, or any other universal-homeomorphism phenomenon.*

> **Black-box unpacking.** The black-box row
> [`univ-homeo-equiv`](appendix-black-boxes.md#univ-homeo-equiv) — cited in files 06 and 12 since the rewrite of
> Exposé I — is exactly IX.4.10. The appendix now points back here.

### IX.4.11 — Faithfully flat quasi-compact + radicial: same conclusion

<!-- source: IX.4.11 -->

**Corollary IX.4.11.** The conclusion of IX.4.10 holds if "finite radicial surjective" is replaced by **"faithfully
flat, quasi-compact, and radicial."**

*Proof.* The proof is identical to IX.4.10, with IX.4.1 used in place of IX.4.7 to drive the effective descent step
(IX.4.1's quasi-affine-descent argument works equally well for fpqc + radicial bases). ∎

### IX.4.12 — Proper surjective: effective for finite étale coverings

<!-- source: IX.4.12 -->

**Theorem IX.4.12.** Let `g : S′ → S` be **proper**, **surjective**, of **finite presentation** (the last condition
follows from the others if `S` is locally noetherian). Then `g` is a morphism of **effective descent** for the
fibred category of **étale coverings** (= finite étale morphisms).

*This result says:* proper surjective `g` is effective for finite étale, even though it need not be effective for
the larger fibred category of étale-separated-finite-type schemes.

*Proof.* By IX.3.3 (using IX.2.2 (a): proper surjective is universally submersive), `g` is a descent morphism for
the fibred category of étale coverings. We must show effective descent.

By IX.4.3, reduce to `S` noetherian. By IX.4.6, reduce to `S` the spectrum of a complete noetherian local ring `A`,
introduce `S″ = S′ ×_S S′` and `S‴ = S′ ×_S S′ ×_S S′` as usual. Let `k` be the residue field of `A`,
`S_0 = Spec(k)`, and `S_0′ = S′ ×_S S_0` the geometric special fibre of `g`. Set `S_0″`, `S_0‴` analogously.

By IX.1.10 (file 44), the morphisms `S_0 → S`, `S_0′ → S′`, etc. induce **equivalences** from the category of
étale coverings of the target to the category of étale coverings of the source, *provided* we use only the
**fully-faithful direction** of IX.1.10 (which uses only the Theorem on Formal Functions, not the EGA III §5
existence theorem). For the essential-surjective direction we *do* use EGA III §5, but only on the **target
side**, which can be circumvented as follows: the equivalence on étale coverings *only requires* the fully-faithful
direction for the proof of IX.4.12 to work, because we are reducing to the descent question at the level of *descent
data*, which is preserved by fully faithful functors.

By the descent-theory sorites (Giraud), `g : S′ → S` is a strict descent morphism for the fibred category of étale
coverings iff `g_0 : S_0′ → S_0` is so. But `g_0` is a proper surjective morphism over a *field*; so `g_0` is
faithfully flat quasi-compact (everything over a field is flat), and IX.4.1 applies. Hence `g_0` is an effective
descent morphism for étale separated finite-type schemes, and a fortiori for étale coverings. ∎

> **Caveat (load-bearing).** The proof uses IX.1.10 (file 44) — but only the **fully-faithful direction**, which
> requires the Theorem on Formal Functions (EGA III §4.3) and not the existence theorem (EGA III §5). The original
> SGA 1 IX text records this carefully; the technical point is what lets IX.4.12 *and* IX.4.7 fit in the same
> chapter despite the latter being "elementary" and the former leaning on the proper-coherent machinery.

> **Slogan.** *Proper surjective descent of finite étale coverings reduces to fpqc descent over the residue field
> via the Theorem on Formal Functions.*

## Closing slogan and pointer to file 46

The five effectivity criteria of §IX.4 each give effective descent for a different combination of "how rigid is the
target" (étale separated finite-type vs. finite étale) and "how strong is the base morphism" (faithfully flat
quasi-compact, finite surjective, universally open of finite type, finite radicial surjective, or proper surjective).
The most striking is **IX.4.10**: a finite radicial surjective base change induces an **equivalence** of étale
categories, the **topological invariance of the étale site**.

> **Closing slogan.** *Descent of étale morphisms holds unconditionally; descent of étale schemes is effective in
> five canonical cases; topological invariance is the corner where descent becomes equivalence.*

File 46 turns the descent equivalence into a **calculation** of `π₁(S, a)`: the descent data on a fibred category of
finite étale coverings is the same as a *galoisian-type group presentation* of `π₁(S, a)` in terms of `π_{s′}` for
`s′` in connected components of `S′`. This is the algebraic analogue of Seifert–van Kampen, and the bridge to file
47's fundamental exact sequence.
