# Rewritten Exposé XII, section XII.5 — Riemann existence theorem and `π_1` comparison

<!-- source: XII.5 -->

## What this file is about

Take a complex algebraic variety. Build a finite cover of it by analytic means — wind around it the way one winds a
helix above a circle, layer extra sheets above each point, glue everything together using only the tools of complex
analysis. The construction lives entirely outside algebra. The result is the headline theorem of this file: every such
cover, no matter how it was assembled, secretly comes from a polynomial cover. Algebraic geometry catches all of them.
This is the bridge from topology to algebra. As a consequence, the fundamental group computed by walking loops in the
analytic space matches, after a profinite completion, the fundamental group computed by classifying finite algebraic
covers. The two stories — topological and algebraic — agree.

Files 57, 58, 59 built the analytification functor and the algebraic-analytic dictionary at four levels: at the level of
the structure morphism `φ : X^an → X` and its completion isomorphism (XII.1), at the level of scheme properties
(XII.2.1), at the level of morphism properties (XII.3.1, XII.3.2), and at the level of coherent cohomology (XII.4.2).
For proper `ℂ`-schemes the cohomological side delivers a sharp equivalence `Coh(X) ≃ Coh(X^an)` (XII.4.4) and a
finite-étale equivalence (XII.4.6) on the analytic side.

This file (§XII.5) closes the comparison story by removing the *properness* hypothesis from XII.4.6. The clean statement
(XII.5.1) is the **Riemann existence theorem**: for any `ℂ`-scheme `X` locally of finite type — proper or not — the
analytification functor `X' ↦ X'^an` is an equivalence between finite étale coverings of `X` and finite étale coverings
of `X^an`. The proof routes through three reductions (normal, regular, affine-regular) and then through Hironaka
resolution + the Grauert–Remmert theorem on extending normal finite coverings across divisors.

The most-cited corollary is XII.5.2: the étale fundamental group `π_1^ét(X, φ(x))` is canonically isomorphic to the
*profinite completion* of the topological fundamental group `π_1^top(X^an, x)`. This is the analytic underpinning of the
**transcendental method** of file 50 (X.2.6): the surface-group presentation of `π_1^top(Σ_g)` for a smooth proper curve
of genus `g`, together with a Witt-vector lift to characteristic `0` and base change to `ℂ`, gives the étale fundamental
group of any curve of genus `g` over any algebraically closed field of any characteristic, as the profinite completion
of the topological surface group.

The supporting analytic theory — XII.5.3 (normal cover extension across thin subsets), XII.5.4 (Grauert–Remmert), and
the warning XII.5.5 (the `T^2 − sin(1/z)` counterexample) — is the analytic backbone of the proof of XII.5.1. The
closing remark XII.5.6 of the source records Raynaud's 2003 observation about Higman groups and Toledo's
non-residually-finite construction: the natural map `π_1^top(V^an) → π_1^ét(V)` is generally *not* injective. The
profinite completion in XII.5.2 is therefore load-bearing.

The slogan that emerges by the end of this file: **for `ℂ`-schemes locally of finite type, finite étale coverings and
topological covering theory agree at the level of profinite completions of `π_1`** — and that is exactly what the étale
fundamental group of files 30–33 was designed to detect.

______________________________________________________________________

## §XII.5.0 — Bridge: the Riemann existence theorem in three forms

<!-- source: XII.5.0 -->

The **classical Riemann existence theorem** in complex analysis says: every connected unramified topological covering of
a Riemann surface comes from an algebraic structure on the cover. Explicitly: given a meromorphic function `f` on a
Riemann surface `X` and a degree-`n` algebraic equation `P(z, w) = 0` with `P` polynomial in `w` and meromorphic in `z`,
the multi-valued function `w(z)` cuts out a connected `n`-sheeted covering of the complement-of-branch-locus of `X`, and
this covering carries a unique compatible analytic structure that makes the projection a morphism of Riemann surfaces.

XII.5.1 is Grothendieck's algebraic-scheme-theoretic abstraction of this principle. The bridge from the classical form
to XII.5.1 is, roughly:

- The "Riemann surface" `X` is replaced by an arbitrary `ℂ`-scheme `X` locally of finite type.
- The "connected unramified topological covering" is replaced by the *analytic-space* notion of a finite étale covering.
- The conclusion — that the analytic covering comes from an algebraic one — is unpacked as the equivalence of categories
    XII.5.1.

Three nested forms of the theorem will emerge in this file.

#### Form 1: finite étale categories agree.

The cleanest statement (XII.5.1): the functor `X' ↦ X'^an` is an equivalence

```text
{finite étale coverings of X}  ≃  {finite étale coverings of X^an}.
```

This is the "categorical Riemann existence theorem". XII.4.6 already gave it for *proper* `X`; XII.5.1 removes the
properness hypothesis.

#### Form 2: `π_1^ét(X) = π̂_1^top(X^an)`.

A corollary of Form 1 by general nonsense about Galois categories (file 33): the étale fundamental group
`π_1^ét(X, φ(x))` is isomorphic to the **profinite completion** of the topological fundamental group `π_1^top(X^an, x)`.
This is XII.5.2.

#### Form 3: a covering of the regular open of `X^an` extends.

The analytic-side backbone of the proof (XII.5.3 and XII.5.4): a finite normal covering of a normal analytic space,
étale away from a rare closed analytic subset, extends uniquely to a finite normal covering of the whole space.

We will prove Form 1 (XII.5.1) by induction on the structure of `X`, reducing successively to the normal, regular, and
finally affine-regular case. The affine-regular case uses Hironaka resolution to compactify, then local Kummer
extensions at boundary points to extend the étale covering, then Grauert–Remmert (Form 3) to globalise the extension,
then XII.4.6 to descend the resulting covering to algebra.

______________________________________________________________________

## §XII.5.1 — The Riemann existence theorem

<!-- source: XII.5.1 -->

### Theorem XII.5.1 — Riemann existence theorem

<!-- source: XII.5.1 -->

**Theorem XII.5.1 (Riemann existence theorem).** Let `X` be a `ℂ`-scheme locally of finite type. The functor
`Ψ : X' ↦ X'^an` from finite étale coverings of `X` to finite étale coverings of `X^an` is an equivalence of categories.

*This result says:* every finite étale covering of the analytic space `X^an` comes from a finite étale covering of the
scheme `X`, uniquely up to isomorphism. The analytic and algebraic categories of finite étale coverings agree, without
any properness hypothesis on `X`.

#### Proof structure.

We verify the two clauses: fully faithful (XII.5.1, step 1) and essentially surjective (XII.5.1, step 2). Step 2 is the
substantive case and proceeds by three nested reductions, each handled in its own block.

#### Step 1 — `Ψ` is fully faithful.

<!-- source: XII.5.1 -->

Let `X', X''` be finite étale coverings of `X`. We must show the canonical map

<!-- label: eq:XII.5.* -->

```text
(*)   Hom_X(X', X'')  →  Hom_{X^an}(X'^an, X''^an)
```

is bijective.

We may assume `X'` is *connected* (the general case splits over connected components). To give an `X`-morphism from `X'`
to `X''` is equivalent to giving a connected component `X_i` of `X' ×_X X''` such that the morphism `X_i → X'` induced
by the first projection is an isomorphism. (Indeed, a morphism `X' → X''` is the graph construction: it picks out the
closed subscheme `Z ⊂ X' ×_X X''` that is the graph of the morphism, with first projection an iso. For a *connected*
`X'` and a finite étale `X''`, every such graph is a connected component of `X' ×_X X''`.)

By the same construction on the analytic side, an analytic `X^an`-morphism from `X'^an` to `X''^an` corresponds to a
connected component of `(X' ×_X X'')^an = X'^an ×_{X^an} X''^an` whose first projection is an analytic iso.

By XII.2.6 (file 58), connected components of `X' ×_X X''` correspond bijectively to connected components of
`X'^an ×_{X^an} X''^an`. By XII.3.1 (ix) (file 58), a morphism `X_i → X'` is an iso iff its analytification is.
Combining these two bijections, the set of "algebraic graphs" is in bijection with the set of "analytic graphs", which
proves `(*)` bijective. ∎\_{step 1}

#### Step 2 — `Ψ` is essentially surjective.

<!-- source: XII.5.1 -->

Let `𝓧' → X^an` be a finite étale covering of `X^an`. We must produce an étale covering `X' → X` and an isomorphism
`X'^an ≃ 𝓧'`. In view of Step 1, the question is *local on `X`*, so we may assume `X` is affine.

We proceed by three reductions.

##### (a) Reduction to `X` normal.

<!-- source: XII.5.1 -->

We may suppose `X` reduced. Indeed, suppose the theorem proved for `X_{red}`. The functor

```text
Θ : \{finite étale coverings of X^an\}  →  \{finite étale coverings of X_{red}^an\},
    𝓧'  ↦  𝓧'^{red}
```

is fully faithful (a finite étale covering is determined by its restriction to the reduced subscheme of the base,
because the base extension preserves étaleness and the underlying topological space of a reduced finite étale covering
matches the underlying topological space of the original). Composing with the equivalence on `X_{red}` proves the
equivalence on `X`.

We may further suppose `X` normal. Let `p : X̃ → X` be the normalisation morphism. Then `p` is finite, so by IX.4.7
(file 45, also `bourbaki-sem-190`), `p` is a *morphism of effective descent for the category of étale coverings of `X`*.

Suppose the theorem proved for `X̃`. Define

```text
𝓧̃'  :=  𝓧' ×_{X^an} X̃^an
```

as a finite étale covering of `X̃^an`. By the inductive hypothesis (theorem on `X̃`), there exist an étale covering
`X̃' → X̃` and an iso `X̃'^an ≃ 𝓧̃'`. By Step 1 (full faithfulness, applied to `X̃`), the natural descent datum on `𝓧̃'`
along `X̃^an → X^an` lifts to a descent datum on `X̃'` along `X̃ → X`. By effective descent (IX.4.7), the descent datum
is effective, giving an étale covering `X' → X` with an iso

```text
i : X'^an ×_{X^an} X̃^an  ≃  𝓧̃',
```

whose two pullbacks to `X̃^an ×_{X^an} X̃^an` agree.

By IX.3.2 (file 45, with its analytic-context analogue valid), the analytic morphism `X̃^an → X^an` is a *morphism of
descent for the category of finite étale coverings*. Hence the descent datum `i` extends uniquely to an iso
`X'^an ≃ 𝓧'`.

This reduces the theorem to the case `X` normal. ∎\_{step 2a}

##### (b) Reduction to `X` regular.

<!-- source: XII.5.1 -->

Let `U` be the open subset of regular points of `X`. By Input 2 of file 58 (excellence + openness of the regular locus),
`U` is open and dense in `X`. By XII.2.1 (iv), `U^an` is the open subset of regular points of `X^an`. Since `X` is
normal, `codim_X(X − U) ≥ 2` (this is a standard fact about normal noetherian schemes).

We claim it suffices to extend `𝓧'|_{U^an}` to a finite étale covering on all of `X^an`, then descend the extension.
Suppose `U' → U` is an étale covering with `U'^an ≃ 𝓧'|_{U^an}`. Show: `U'` extends to an étale covering `X' → X` such
that `X'^an ≃ 𝓧'`.

We just need to show `U'` extends to an étale `X' → X` over the whole of `X`. (Once we have this, the analytic
restriction `X'^an|_{U^an} ≃ 𝓧'|_{U^an}` is given; and by the codim-≥-2 + normal hypothesis the canonical maps of
structure sheaves

```text
𝓕  →  i_*^an(𝓕|_{U^an}),     𝓖  →  i_*^an(𝓖|_{U^an}),
```

where `𝓕` is the coherent analytic algebra defining `𝓧'` and `𝓖` is the coherent analytic algebra defining `X'^an`, are
isomorphisms by `serre-prolongement-faisceaux` (file 58 lemma XII.2.5 codim-2 case). Hence `𝓕 ≃ 𝓖`, and so
`𝓧' ≃ X'^an`.)

To show `U'` extends, the question is local on `X`. For every point `y ∈ X^an − U^an`, consider the étale covering

```text
U'_{φ(y)}  :=  U' ×_X Spec(𝒪_{X, φ(y)})
```

of `U_{φ(y)} := U ×_X Spec(𝒪_{X, φ(y)})`. We need to show this extends to an étale covering of `Spec(𝒪_{X, φ(y)})`.

Let `H` be the coherent `𝒪_U`-algebra defining `U'`. The canonical map

```text
α : (i_* H)^an  →  i_*^an(H^an)  =  𝓕
```

defines a stalk map on `Spec(𝒪_{X^an, y})`:

```text
α_y : (i_* H)^an_y  →  𝓕_y,
```

whose restriction to

```text
U_y  :=  U_{φ(y)} ×_{Spec(𝒪_{X, φ(y)})} Spec(𝒪_{X^an, y})
```

is an isomorphism. This is because over the regular open `U`, the local algebraic and analytic algebras agree after
completion (XII.1.1), and the étale-cover algebra `H` is finite-locally-free, hence preserved by passage to completion +
faithful-flatness.

The iso on `U_y` says that `H|_{U_y}` is a trivial finite-flat algebra (= a free module of given rank). This triviality
propagates to `Spec(𝒪_{X, φ(y)})` by Serre's prolongation theorem (`serre-prolongement-faisceaux`), using
`codim_X(X − U) ≥ 2`: the algebra `i_* H` is reflexive (because `H` is free, hence reflexive on `U`), so the stalk
`(i_* H)_{φ(y)}` is the algebra defining the extension of `U'` to `Spec(𝒪_{X, φ(y)})`.

This proves the local extension at every `y ∈ X^an − U^an`, hence by gluing, `U'` extends to an étale `X' → X`. ∎\_{step
2b}

##### (c) Affine regular case.

<!-- source: XII.5.1 -->

Suppose `X` is *affine and regular*. Let

```text
j : X  →  P
```

be a compactification of `X`, where `P` is a *projective* `ℂ`-scheme and `j` is a dominant open immersion. (One
constructs `P` as the projective closure of an affine embedding; the dominance comes from the affine embedding being
open in its closure.)

By **Hironaka resolution of singularities** (`hironaka-resolution`, since we are in characteristic 0), we can find a
regular projective `ℂ`-scheme `R` and a projective morphism

```text
r : R  →  P
```

such that `r` induces an isomorphism `r^{-1}(X) ≃ X` and such that `R − r^{-1}(X)` is a **divisor with normal
crossings** in `R`. Let

```text
k := r^{-1} ∘ j : X  →  R
```

be the canonical immersion of `X` into the regular projective compactification.

We will show: there exists a finite normal covering `𝓡' → R^an` (in the sense of XII.5.0; specifically a normal analytic
finite-cover) that extends the étale covering `X'^an = 𝓧'|_{X^an}` of `X^an = r^{-1}(X)^an`.

By **XII.5.3** (proved below), such an extension `𝓡'` is *unique* up to isomorphism — if it exists, it is determined by
its restriction to the dense open `X^an ⊂ R^an`. So the problem of extending `𝓧'` to `R^an` is **local on `R^an` near
`R^an − X^an`**.

But each point of `R^an − X^an` has, by the normal-crossings structure of the boundary, an open neighbourhood `𝓥`
analytically isomorphic to an open ball in some `ℂⁿ`, with `𝓥 − 𝓥 ∩ X^an` defined by the vanishing of the first `p`
coordinate functions `z_1, …, z_p`, where `0 ≤ p ≤ n`. (When `p = 0`, the boundary is trivial; when `p ≥ 1`, it is a
normal-crossings union of `p` divisors locally.)

The fundamental group of `𝓤 := 𝓥 ∩ X^an = 𝓥 − {z_1 ⋯ z_p = 0}` is the abelianization of `ℤ^p` (more precisely,
`π_1^top(𝓤) ≃ ℤ^p`, with generators given by small loops around each `z_i = 0` hyperplane). Therefore every finite étale
covering of `𝓤` is a quotient of a *Kummer-type* covering

```text
𝓤''  :=  𝓤[T_1, …, T_p] / (T_1^{n_1} − z_1, …, T_p^{n_p} − z_p)
```

(for integers `n_i > 0`) by a subgroup `H ⊂ ℤ/n_1ℤ × ⋯ × ℤ/n_pℤ` of the Galois group of `𝓤''`.

The advantage of the Kummer form: `𝓤''` *extends naturally* to a regular finite analytic covering of `𝓥`:

```text
𝓥''  :=  𝓥[T_1, …, T_p] / (T_1^{n_1} − z_1, …, T_p^{n_p} − z_p).
```

The variety `𝓥''` is regular (the equations `T_i^{n_i} = z_i` cut out a regular hypersurface in a polydisc), and the
group `H` acts on it. The quotient `𝓥'' / H` is then the desired extension of `𝓤'' / H` to `𝓥`.

Globalising over the cover of `R^an − X^an` by such normal-crossings neighbourhoods, we obtain the desired normal finite
analytic covering `𝓡' → R^an`.

Now apply **XII.4.6** (file 59): since `R` is a *proper* (in fact projective) `ℂ`-scheme, the analytification functor is
an equivalence between finite (étale) `R`-schemes and finite (étale) analytic `R^an`-spaces. Hence the finite normal
analytic covering `𝓡'` of `R^an` comes from a finite normal covering `R' → R` of the projective scheme `R`, with
`R'^an ≃ 𝓡'`. By XII.3.1 (iii), since `𝓡'|_{X^an} = 𝓧'` is *étale*, so is its restriction to `X`, i.e. `X' := R' ×_R X`
is finite étale over `X`. And `X'^an ≃ 𝓡'|_{X^an} = 𝓧'`. ∎\_{step 2c}

This proves Theorem XII.5.1. ∎

> **Slogan.** *The functor `X' ↦ X'^an` is an equivalence between finite étale coverings of `X` and finite étale
> coverings of `X^an`, for every `ℂ`-scheme `X` locally of finite type.* No properness hypothesis is needed; the proof
> factors through Hironaka resolution + local Kummer extensions + Grauert–Remmert extension.

#### Aside (why Hironaka and not étale local arguments).

The use of Hironaka resolution (`hironaka-resolution`) in step (c) is essential for the *local* picture of the boundary
`R^an − X^an` as a normal-crossings divisor. Without normal crossings, the local étale-cover classification at boundary
points becomes much more delicate (a general boundary is a stratification of varying-dimensional pieces, each with its
own fundamental group of the link), and the explicit Kummer-extension construction breaks down.

This is one of two essential uses of resolution-of-singularities in SGA 1 XII (the other is XII.5.4 below). Both uses
are *characteristic 0* — Hironaka's theorem is char 0. The characteristic-`p` analogue would require de Jong's
alterations (1996) and a more elaborate analytic-side proof, neither of which is in SGA 1.

______________________________________________________________________

## §XII.5.2 — The `π_1` comparison

<!-- source: XII.5.2 -->

### Corollary XII.5.2 — `π_1^ét(X, φ(x)) ≃ π̂_1^top(X^an, x)`

<!-- source: XII.5.2 -->

**Corollary XII.5.2.** Let `X` be a *connected* `ℂ`-scheme locally of finite type, let `φ : X^an → X` be the canonical
morphism, and let `x ∈ X^an`. Then there is a canonical isomorphism of profinite groups

```text
π_1^ét(X, φ(x))  ≃  π̂_1^top(X^an, x),
```

where the left side is the étale fundamental group of the scheme `X` at the base-point `φ(x)` (defined in file 33 V.7),
and the right side is the **profinite completion** of the topological fundamental group of the analytic space `X^an` at
`x`.

*This result says:* the étale fundamental group is the profinite completion of the topological fundamental group.
Specifically, `π_1^ét(X, φ(x))` is the completion of `π_1^top(X^an, x)` for the topology defined by subgroups of finite
index.

**Proof.** Let `𝓒` be the category of finite étale coverings of `X^an`, and let `F : 𝓒 → Set` be the *fibre functor*

```text
F(𝓧')  :=  \{ \text{points of } 𝓧' \text{ above } x \}.
```

By construction of the profinite fundamental group of a category-and-fibre-functor pair (V.4, file 33), there is a
canonical profinite group `π̂_1^top(X^an, x)` associated with `(𝓒, F)`, such that `(𝓒, F)` is *equivalent to the
category of finite continuous actions of `π̂_1^top(X^an, x)` on finite sets*.

Now: every finite étale covering of `X^an` is a quotient of the **universal covering** of `X^an` (which is itself a
topological space, the universal cover in the classical sense) by a subgroup of finite index. Hence the profinite group
associated with `(𝓒, F)` is exactly the profinite completion of `π_1^top(X^an, x)`:

```text
π̂_1^top(X^an, x)  =  \text{prof. completion of} \pi_1^top(X^an, x)  \text{for the topology of finite-index subgroups}.
```

By XII.5.1, the functor `𝓒 ≃ \{\text{finite étale coverings of} X\}`. The fibre functor of
`\{\text{finite étale coverings of} X\}` is `F' : X' ↦ X'(x̄)` for `x̄ = φ(x)` a geometric point. By V.6.10 (file 33),
the associated profinite group is `π_1^ét(X, φ(x))`.

Combining the two equivalences:

```text
π_1^ét(X, φ(x))  =  \text{profinite completion of}  \pi_1^top(X^an, x).
```

∎

> **Slogan.** *`π_1^ét(X) ≃ π̂_1^top(X^an)` over `ℂ`.* The étale fundamental group is the analytic fundamental group
> profinitely completed.

#### Aside (the analytic side of the transcendental method of file 50).

The corollary XII.5.2 is the analytic side of the **transcendental method** of file 50 (X.2.6). The
transcendental-method-as-applied-in-file-50 reasoning runs as follows:

1. Take a smooth proper curve `X_0` of genus `g` over an algebraically closed field `k` of characteristic `p`.
1. By the Witt-vector lifting theorem (file 22 III.7.4), there exists a smooth proper `W(k)`-curve `X` with closed fibre
    `X_0`. The generic fibre `X_K = X ⊗ K` (`K` the fraction field of `W(k)`) is a smooth proper curve of genus `g`
    over `K`.
1. Base change to `K → ℂ` (any embedding) gives a smooth proper curve `X_ℂ` of genus `g` over `ℂ`.
1. By XII.5.2, `π_1^ét(X_ℂ) ≃ π̂_1^top(X_ℂ^an)`.
1. Topology of compact Riemann surfaces:
    `π_1^top(X_ℂ^an) = π_1^top(Σ_g) = ⟨s_1, …, s_g, t_1, …, t_g | ∏ [s_i,  t_i] = 1⟩` (the surface group).
1. Specialisation X.2.3 (file 49): `π_1^ét(X_ℂ) ↠ π_1^ét(X_0)`, surjective.

Combining (4)–(6): `π_1^ét(X_0)` is a quotient of `π̂_1^top(Σ_g)`, the profinite completion of the surface group. By
continuity X.3.8 (file 51), this surjection is an iso on prime-to-`p` quotients.

This is exactly the X.2.6 statement that `π_1^ét(X_0)^{(p')}` is the prime-to-`p` profinite completion of the surface
group on `2g` generators. XII.5.2 is the analytic input.

______________________________________________________________________

## §XII.5.3 — Normal cover extension across thin subsets

<!-- source: XII.5.3 -->

### Proposition XII.5.3 — normal-finite-cover restriction is fully faithful

<!-- source: XII.5.3 -->

**Proposition XII.5.3.** Let `𝓧` be a normal complex analytic space, and let `𝓨 ⊂ 𝓧` be a closed analytic subset such
that `𝓤 := 𝓧 − 𝓨` is *dense* in `𝓧`. The restriction functor

```text
\{\text{normal finite coverings of} 𝓧\}  →  \{\text{normal finite coverings of} 𝓤\},
              𝓧'  ↦  𝓧'|_𝓤
```

is *fully faithful*.

*This result says:* a normal finite covering of a normal analytic space is recoverable from its restriction to a dense
open complement of a closed analytic subset. This is the uniqueness half of the XII.5.4 Grauert–Remmert extension
theorem.

**Proof.** Let `𝓧', 𝓧''` be normal finite coverings of `𝓧`. We must show

```text
Hom_𝓧(𝓧', 𝓧'')  →  Hom_𝓤(𝓧'|_𝓤, 𝓧''|_𝓤)
```

is bijective. Let `u, v` be `𝓧`-morphisms `𝓧' → 𝓧''` with `u|_𝓤 = v|_𝓤`. We show `u = v`.

**Injectivity.** The two morphisms `u, v` coincide on `𝓤 ×_𝓧 𝓧'`, which is a dense open of `𝓧'`. By
`[XII.4, no. 19, §4, cor. 5]` (an analytic-space fact: two morphisms of normal analytic spaces agreeing on a dense open
agree everywhere — analytic continuation), `u = v` on `𝓧'`.

**Surjectivity.** Let `u : 𝓧'|_𝓤 → 𝓧''|_𝓤` be a `𝓤`-morphism. We show that `u` extends to a morphism `𝓧' → 𝓧''` on all
of `𝓧`.

We may suppose `𝓧'` regular. Indeed, the singular locus of `𝓧'` is a closed analytic subset `𝓢' ⊂ 𝓧'` of codimension
`≥ 1`. There is an open `𝓥 ⊂ 𝓧` with complement `𝓢 ⊂ 𝓧` of codimension `≥ 2` such that
`𝓥' := 𝓧' ×_𝓧 𝓥 = (regular part of 𝓧')|_𝓥` is regular. Let `𝓥'' := 𝓧'' ×_𝓧 𝓥`. If the proposition is proved for the
regular `𝓥'`, the extension of `u|_{𝓥'}` to a morphism `𝓥' → 𝓥''` is given.

Then: with the morphism of `𝒪_𝓥`-algebras

```text
g''_* 𝒪_{𝓥''}  →  g'_* 𝒪_{𝓥'}
```

associated to the extended morphism `𝓥' → 𝓥''`, where `g', g''` are the projections, one deduces a morphism

```text
i_* g''_* 𝒪_{𝓥''}  →  i_* g'_* 𝒪_{𝓥'},
```

where `i : 𝓥 ↪ 𝓧` is the inclusion. Using the iso `i_*' 𝒪_{𝓥'} ≃ 𝒪_{𝓧'}` and `i_*'' 𝒪_{𝓥''} ≃ 𝒪_{𝓧''}`
(`serre-prolongement-faisceaux`, applied to the codim-≥-2 complement), we deduce a morphism of `𝒪_𝓧`-algebras

```text
f''_* 𝒪_{𝓧''}  →  f'_* 𝒪_{𝓧'},
```

hence the desired morphism `𝓧' → 𝓧''` (analytic spectra reverse the arrow).

So suppose `𝓧'` regular. Let `𝓤' := 𝓤 ×_𝓧 𝓧'`. Let `𝓨' := 𝓧' − 𝓤'` (a closed analytic subset of `𝓧'`, viewed as a
reduced analytic subspace). If `𝓨'_1` is the singular closed subset of `𝓨'`, then `dim 𝓨'_1 < dim 𝓨'` (Grauert–Remmert).
By induction on `dim 𝓨'`, we may suppose `𝓨'` is **smooth**.

Since the question is local on `𝓨'` (it suffices to extend `u` to an open neighbourhood of each point of `𝓨'`), we may
by the implicit function theorem suppose `𝓧'` is an open ball in `ℂⁿ` and `𝓨'` is the closed subset defined by the
vanishing of the first `p` coordinate functions `z_1, …, z_p` (`0 ≤ p ≤ n`).

To `u` we associate a section `s` of

```text
p_2 : 𝓧' ×_𝓧 𝓧''  →  𝓧'
```

over `𝓤'`. After restricting `𝓧'` if necessary, we may suppose `(p_2)_*(𝒪_{𝓧' ×_𝓧 𝓧''})` is generated by elements
`x_1, …, x_q ∈ Γ(𝓧', (p_2)_* 𝒪_{𝓧' ×_𝓧 𝓧''})` (finite generation: `𝓧''` is finite over `𝓧`, so `p_2 : 𝓧' ×_𝓧 𝓧'' → 𝓧'`
is finite; the algebra `(p_2)_* 𝒪_{𝓧' ×_𝓧 𝓧''}` is coherent over `𝒪_{𝓧'}` and locally finitely generated).

Let `u_1, …, u_q ∈ Γ(𝓤', 𝒪_{𝓧'})` be the images by `s` of `x_1|_{𝓤'}, …, x_q|_{𝓤'}`. The statement "`s` extends to `𝓧'`"
is equivalent to "each `u_i` extends to a section of `Γ(𝓧', 𝒪_{𝓧'})`".

But `𝓧'' → 𝓧'` is finite, so each `u_i` is *integral* over the holomorphic functions on `𝓧'`. In coordinates, each `u_i`
is a Laurent series in `z_1, …, z_p` with coefficients that are convergent power series in `z_{p+1}, …, z_n`, and
satisfies an integral-dependence relation. Integrality forces the Laurent series to have *no negative powers*: a Laurent
series satisfying a monic polynomial equation over holomorphic functions on a neighbourhood of the origin has only
non-negative terms (Riemann removable singularity in several variables). Hence `u_i` is a convergent power series in
`z_1, …, z_n`, and extends to `𝓧'`.

This proves the extension, hence the surjectivity. ∎

> **Slogan.** *On a normal analytic space, a finite normal cover is recoverable from its restriction to a dense open.*
> The proof routes through (i) reduction to the regular case via `serre-prolongement-faisceaux`, (ii) the implicit
> function theorem to pick coordinates, (iii) integrality and Riemann removable singularity to upgrade Laurent series to
> power series.

______________________________________________________________________

## §XII.5.4 — The Grauert–Remmert theorem

<!-- source: XII.5.4 -->

### Theorem XII.5.4 — Grauert–Remmert: existence of normal extension

<!-- source: XII.5.4 -->

**Theorem XII.5.4 (Grauert–Remmert).** Let `𝓧` be a normal complex analytic space, and let `𝓨 ⊂ 𝓧` be a closed analytic
subset such that `𝓤 := 𝓧 − 𝓨` is *dense* in `𝓧`. Let `𝓤'` be a normal finite covering of `𝓤`. Suppose there exists a
rare closed analytic subset `𝓢 ⊂ 𝓧` such that the restriction of `𝓤'` to `𝓤 − 𝓤 ∩ 𝓢` is *étale*. Then there exists a
normal finite covering `𝓧' → 𝓧` extending `𝓤'`, and `𝓧'` is unique up to isomorphism.

*This result says:* a normal finite covering of an open subset, étale away from a thin subset, extends uniquely to a
normal finite covering of the whole space. The étale-away-from-thin hypothesis is essential (XII.5.5 warning).

**Proof.** *Uniqueness* follows from XII.5.3.

*Existence.* The problem of extending `𝓤'` is local on `𝓧`. We may suppose `𝓤` regular (the singular locus of `𝓤` is a
rare closed analytic subset, and we replace `𝓤` by its regular part) and `𝓤'` étale over `𝓤` (by shrinking `𝓤` further
to the étale locus).

Let `y ∈ 𝓧 − 𝓤`. We show `𝓤'` extends to a neighbourhood of `y`. After restricting `𝓧` to an open neighbourhood of `y`,
by **Hironaka resolution of singularities** (`hironaka-resolution`) we find a regular analytic space `𝓧_1` and a
projective morphism

```text
f : 𝓧_1  →  𝓧
```

inducing by restriction to `𝓤` an iso `𝓤_1 := f^{-1}(𝓤) ≃ 𝓤`, such that `𝓤_1` is the complement in `𝓧_1` of a *divisor
with normal crossings*.

We show `𝓤'` extends to a normal finite covering of `𝓧_1`. Since the question is local on `𝓧_1`, we may suppose `𝓧_1` is
an open ball in some `ℂⁿ` and `𝓧_1 − 𝓤_1` is defined by the vanishing of the first `p` coordinate functions
`z_1, …, z_p`, with `0 ≤ p ≤ n`.

The étale covering `𝓤'` of `𝓤_1` is a quotient of a *Kummer-type* covering

```text
𝓤_2  :=  𝓤_1[T_1, …, T_p] / (T_1^{n_1} − z_1, …, T_p^{n_p} − z_p)
```

by a subgroup `H` of the Galois group `ℤ/n_1ℤ × ⋯ × ℤ/n_pℤ` (the local model of `π_1^top(𝓤_1) = ℤ^p`).

The covering `𝓤_2` extends naturally to the regular finite covering

```text
𝓧_2  :=  𝓧_1[T_1, …, T_p] / (T_1^{n_1} − z_1, …, T_p^{n_p} − z_p)
```

of `𝓧_1` (now over the whole ball, not just the complement of the normal-crossings divisor). The group `H` acts on
`𝓧_2`. Define

```text
𝓧'_1  :=  𝓧_2 / H,
```

a normal finite covering of `𝓧_1` extending `𝓤'`.

Now push forward along `f : 𝓧_1 → 𝓧`. Let `𝓕_1` be the coherent analytic `𝒪_{𝓧_1}`-algebra defining `𝓧'_1`. By the
**Grauert–Remmert finiteness theorem** (`grauert-remmert-coherence`, the analytic analogue of the EGA III
coherence-of-direct-images theorem for proper morphisms), `f_* 𝓕_1` is a coherent analytic `𝒪_𝓧`-algebra. Take the
analytic spectrum:

```text
𝓧'  :=  \text{Spec}_{an}(f_* 𝓕_1).
```

This is a finite covering of `𝓧` (because `f_* 𝓕_1` is coherent) extending `𝓤'` (because `f_* 𝓕_1|_{𝓤} ≃ 𝓤'`-algebra by
construction). It is normal because `𝓧'_1` is regular (a finite cover of a regular space by a regular space is normal).
∎

> **Slogan.** *Grauert–Remmert: a normal-finite-cover defined on `𝓤`, étale on a thin-complement, extends uniquely to a
> normal-finite-cover of `𝓧`.* The proof routes through Hironaka resolution + local Kummer + pushforward of coherent
> analytic algebras (Grauert–Remmert finiteness).

### Remark XII.5.5 — the étale-locus hypothesis is essential

<!-- source: XII.5.5 -->

**Remark XII.5.5.** The hypothesis in XII.5.4 that `𝓤'` is *étale away from a rare closed analytic subset* cannot be
removed.

**Counterexample.** Let `𝓧 := \{ z ∈ ℂ : |z| < 1 \}` be the unit disc, and let `𝓤 := 𝓧 − \{0\}`. Define

```text
𝓤'  :=  𝓤[T] / (T^2 − sin(1/z)),
```

the analytic double cover of `𝓤` branched at the zeros of `sin(1/z)`.

Then `𝓤'` is a normal finite covering of `𝓤`. But `𝓤'` does *not* extend to a finite covering of `𝓧`. Indeed, suppose
`𝓤'` extended to a finite covering `𝓧' → 𝓧`. The locus of points of `𝓧` where `𝓧' → 𝓧` is not étale is a closed analytic
subset of `𝓧`. This locus contains all points `z ∈ 𝓧` with `sin(1/z) = 0`, i.e. all points `z = 1/(nπ)` for
`n ∈ ℤ_{≥ 1}`. But this set has the origin `z = 0` as an accumulation point — a closed analytic subset of `𝓧` cannot
have an accumulation point in its interior. Contradiction.

The pathology here is that `𝓤'` is *not étale away from a rare subset*: the non-étale locus is the zero set of
`sin(1/z)`, which accumulates at the origin and so is not contained in any rare closed analytic subset of `𝓧`.

#### Strengthening for codimension ≥ 2.

When `codim_𝓧(𝓧 − 𝓤) ≥ 2`, the étale-locus hypothesis on `𝓢` can be dropped from XII.5.4. Indeed: suppose `𝓤'` is a
normal finite covering of `𝓤` without the étale hypothesis. By the **Remmert–Stein theorem** (analytic extension of
subvarieties of codimension `≥ 2`), the locus of points where `𝓤' → 𝓤` is not étale is the trace on `𝓤` of a divisor of
`𝓧`. We may then suppose `𝓤` regular (the singular locus of `𝓤` is part of the boundary when `codim ≥ 2`). The locus of
points of `𝓤` where `𝓤' → 𝓤` is not étale is a divisor of `𝓤`, and it follows from Remmert–Stein that it is the trace on
`𝓤` of a divisor of `𝓧`. In this codim-≥-2 case, taking `𝓧' := \text{Spec}_{an}(i_* 𝓐)`, where `𝓐` is the coherent
`𝒪_𝓤`-algebra such that `𝓤' = \text{Spec}_{an}(𝓐)`, gives the desired extension; `i_* 𝓐` is coherent by
`serre-prolongement-faisceaux` (`[XII.11, no. 1, th. 1]`).

> **Slogan.** *Normal-finite-cover extension is automatic across thin subsets (under the étale hypothesis); the
> hypothesis can be dropped when the boundary has codim `≥ 2`.* The `T^2 − sin(1/z)` example pins down the precise
> limit.

______________________________________________________________________

## §XII.5.5 — Raynaud's 2003 remark on non-residually-finite `π_1`

<!-- source: XII.5.6 -->

### Remark XII.5.6 — Higman groups and the failure of `π_1^top → π_1^ét` to be injective

<!-- source: XII.5.6 -->

**Remark XII.5.6 (M. Raynaud, added in 2003).** There exist nontrivial finitely-presented groups `G` having no proper
subgroup of finite index. For example, **G. Higman's group** (`higman-non-residually-finite`; cf. J.-P. Serre, _Arbres
et amalgames_, Astérisque **46**, prop. 6, ch. I §1).

Consequently, if such a group `G` could be realised as the topological fundamental group of a `ℂ`-scheme `V` locally of
finite type — say smooth and projective — then the analytic space `V^an` would *not* be topologically simply connected
(`π_1^top(V^an) = G ≠ 1`), but `V` would be *algebraically simply connected*
(`π_1^ét(V) = π̂_1^top(V^an) = profinite completion of G = 1`, by XII.5.2 and the fact that `G` has trivial profinite
completion). At present *no such `V` is known* — the existence of a smooth proper `ℂ`-variety with Higman fundamental
group is an open problem.

Let us nevertheless mention that **D. Toledo** (`toledo-non-residually-finite-pi1`) constructed smooth projective
`ℂ`-schemes `V` whose topological fundamental group `π_1^top(V^an)` is **not separated** for the topology of subgroups
of finite index — i.e. `π_1^top(V^an)` is not residually finite. The natural map

```text
π_1^top(V^an)  →  π_1^ét(V)
```

(induced by XII.5.2 and the universal property of profinite completion) is therefore *not injective*: it kills the
intersection of all finite-index subgroups of `π_1^top(V^an)`, which is non-trivial when `π_1^top` is not residually
finite.

> **Slogan.** *`π_1^ét(V)` is the *profinite* completion of `π_1^top(V^an)`, not `π_1^top(V^an)` itself.*

#### Aside (the historical context).

The historical context here is striking. In 1960, when SGA 1 was written, it was unclear how much the étale fundamental
group could "see" — whether it could distinguish, for example, surfaces of different geometric behaviour over `ℂ`. The
XII.5.2 result was the first clear statement that the étale `π_1` *recovers* the profinite information of the
topological `π_1`.

Toledo's 1993 result and Raynaud's 2003 remark add the sharp boundary: the étale `π_1` recovers *only* the profinite
information, not the full topological `π_1`. There exist smooth proper `ℂ`-varieties whose topological `π_1` is not
residually finite, and for those the étale `π_1` strictly *under-determines* the topological `π_1`. The Higman
conjecture sharpens this further: there might exist smooth proper `ℂ`-varieties with trivial étale `π_1` and yet
non-trivial topological `π_1`. As of 2026 no such example is known, but the existence remains open.

______________________________________________________________________

## §XII.5.6 — Closing pointers and the gentle SGA closing

<!-- source: XII.5 -->

#### File 50's transcendental method = XII.5.2 + topological surface group.

The **transcendental method** of file 50 (X.2.6) — the calculation of `π_1^ét` for a smooth proper curve of any genus
`g` in any characteristic, by lifting to characteristic 0 via Witt vectors, base-changing to `ℂ`, and applying the
surface-group presentation `π_1^top(Σ_g) = ⟨s_1, …, s_g, t_1, …, t_g | ∏ [s_i, t_i] = 1⟩` — is exactly **XII.5.2 applied
to the analytic-side computation of `π_1^top(Σ_g)`**.

This is the "deep" use of GAGA in SGA 1: not just as a *property* dictionary (file 58) or *cohomological* comparison
(file 59), but as a *transcendental method for computing `π_1^ét`* in characteristic `p`.

#### Forward-pointer to gentle Exposé XIII and SGA 4.

The next gentle pass — files 61–64 — covers **Exposé XIII** (cohomological properness of sheaves of sets and of
non-commutative groups). Exposé XIII is the only exposé in SGA 1 that genuinely depends on **SGA 4** (étale cohomology)
and on **SGA 5 II** (cohomologically proper morphisms in higher dimension). Files 61–64 quote both as a standing bridge
and prove the SGA-1-internal content in the gentle voice: cohomological properness of the tame `R¹` along a
normal-crossings divisor (XIII.2.4); the tame fundamental group of an open curve (XIII.2.12); the étale homotopy exact
sequence and the Künneth formula for `π_1^{p'}` (XIII.4.1, XIII.4.6); and the absolute Abhyankar lemma
(XIII.5.1–XIII.5.2).

SGA 4 itself is the next chapter: the full étale topology, derived functor `H^i_{et}`, the proper-base-change theorem
for étale sheaves (the étale-cohomology analogue of XIII's coherent version), the smooth-base-change theorem, ℓ-adic
cohomology, the Lefschetz trace formula in characteristic `p`. The XII.5.1 + XII.5.2 results of this file are *the
input* SGA 4 takes for granted on the étale-fundamental-group side; everything in SGA 4 beyond is the topological /
cohomological / coefficient-level upgrade.

> **Final slogan for file 60 (and for the gentle Exposé XII).** *Finite étale coverings of a `ℂ`-scheme `X` and of its
> analytification `X^an` are the same, in a precise and effective way; the étale fundamental group is the profinite
> completion of the topological fundamental group.* The Riemann existence theorem (XII.5.1) is the analytic foundation;
> the `π_1` comparison (XII.5.2) is the corollary that powers the transcendental method of file 50; the Grauert–Remmert
> extension theorem (XII.5.4) and Hironaka resolution are the analytic tools that fuel the proof.

______________________________________________________________________

## Closing of file 60 (and of the gentle Exposé XII)

With this file, the gentle SGA pass through **Exposé XII — Algebraic Geometry and Analytic Geometry** is complete (files
57–60):

- **File 57 (§XII.1)** — the analytification functor `X ↦ X^an` and its representing universal property; bijection on
    `ℂ`-points; completion isomorphism `𝒪̂_{X, φ(x)} ≃ 𝒪̂_{X^an, x}`; flatness of `φ`; functoriality (commuting with
    fibre products); the inverse-image functor `F ↦ F^an = φ^* F` on coherent sheaves, exact, faithful, and
    conservative.
- **File 58 (§§XII.2–XII.3)** — the property dictionaries: eight scheme-level properties transfer between `X` and
    `X^an`; eleven morphism-level properties without finite-type assumption; six more under a finite-type hypothesis;
    closure / open / dense / `π_0` agreement; XII.2.5 connectedness lemma for normal analytic spaces.
- **File 59 (§XII.4)** — cohomological GAGA: the comparison map `θ_p : (R^p f_* F)^an → R^p f_*^an(F^an)` is an iso for
    `f` proper and `F` coherent; specialised to absolute cohomology; specialised to coherent-sheaf categories;
    specialised to morphism sets and to finite (étale) coverings of proper schemes.
- **File 60 (§XII.5)** — the Riemann existence theorem `Ψ : X' ↦ X'^an` is an equivalence of finite-étale categories;
    the `π_1` comparison `π_1^ét(X, φ(x)) ≃ π̂_1^top(X^an, x)`; XII.5.3 normal-cover extension; XII.5.4 Grauert–Remmert;
    XII.5.5 obstruction example; XII.5.6 Raynaud 2003 remark on Higman / Toledo.

The **gentle SGA project — as of files 52–60 — now covers Exposés I, II, III, IV, V, VI, VIII, IX, X, XI, XII**. Exposé
**XIII (cohomological properness)** of SGA 1 is files 61–64.
