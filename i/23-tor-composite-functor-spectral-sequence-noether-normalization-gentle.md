# Tor, the spectral sequence for composite functors, and Noether's normalization (gentle prep for Exposé IV)

## What this file is about

The next batch of files cites three pieces of algebra it does not stop to prove. The first is a sequence of gadgets
attached to a pair of modules that detects how badly tensoring fails to preserve exact sequences. The second is a
bookkeeping device that organises two operations applied in succession into a grid of groups, with a five-term
consequence used once. The third is a classical fact, due to Emmy Noether, saying every finitely generated algebra over
a field is finite over a polynomial subring.

This file makes the three pieces honest. A reader who already knows them can skip. Everyone else should read the
relevant section before opening the file that uses it. The point is to keep the next batch self-contained without
redoing each tool from scratch.

The gentle rewrite of Exposé IV (files 24–27) cites three pieces of conceptual machinery that have not appeared in the
project before. The first is the **Tor functor** `Tor^A_i(M, N)`, the left-derived functor of the tensor product. Tor is
the natural home for the algebraic content of flatness: `M` is `A`-flat exactly when `Tor^A₁(M, N)` vanishes for every
`A`-module `N`. The second is the **spectral sequence for composite functors** in its low-degree five-term form. SGA 1
IV.5.2 — Serre's lemma on extending flatness across a base change — uses it once. The third is **Noether's normalization
lemma**: every finite-type integral algebra over a field is finite over a polynomial subring. SGA 1 IV.6.7 — the
generic-freeness lemma that powers generic flatness — uses it once.

A reader who already knows these can skip this file. A reader for whom any of the three is new should read the
corresponding section before opening file 26 (the local flatness criterion; uses the spectral sequence in IV.5.2's
proof) or file 27 (constructibility, openness, generic flatness; uses Noether normalization in IV.6.7's proof). The
reductions and ideas in this prep file are textbook-standard. We lean on the appendix (`tor-derived-functor`,
`spectral-sequence-composite-functors`, `noether-normalization`) for the full constructions, and use this file to record
what the rewrite needs and why.

## The Tor functor

`Tor` is the left-derived functor of `⊗`. The shape of the construction is the same as for any derived functor: take a
projective (or merely flat) resolution of one argument, apply the functor, and read off the homology.

### Definition via free resolution

Let `A` be a commutative ring with `1`, and let `M` be an `A`-module. A **free resolution** of `M` is an exact sequence

```text
… → L₂ → L₁ → L₀ → M → 0
```

with each `L_i` a free `A`-module. Free resolutions exist for every `M` — choose generators, take a free module on them,
take generators of the kernel, repeat. (Over a noetherian ring with `M` finite, the `L_i` can also be chosen finite, but
we do not need that.) Drop `M` from the sequence to get a chain complex `L_•`, and tensor with another `A`-module `N`:

```text
… → L₂ ⊗_A N → L₁ ⊗_A N → L₀ ⊗_A N → 0.
```

The result is no longer exact in general; the failure measures how much `M` and `N` "interact" through tensoring.

**Definition.** Set

```text
Tor^A_i(M, N) := H_i(L_• ⊗_A N).
```

By construction `Tor^A₀(M, N) = M ⊗_A N`. The higher `Tor^A_i` are abelian-group invariants of the pair `(M, N)`. The
reader who wants the full account should open Cartan-Eilenberg, _Homological Algebra_ (chapter VI) or Weibel,
_Introduction to Homological Algebra_ (chapter 3). We record what the rewrite uses.

### Independence of the resolution

A standard chain-homotopy argument (the comparison theorem for projective resolutions) shows that any two free
resolutions of `M` give chain-homotopic complexes after tensoring with `N`, hence isomorphic homology. So
`Tor^A_i(M, N)` depends only on `M`, `N`, `A`, and `i`. Source: appendix row `tor-derived-functor`.

### The long exact sequence

A short exact sequence in either argument produces a long exact sequence in `Tor`. Spelled out: a short exact sequence
`0 → N' → N → N'' → 0` of `A`-modules gives a natural long exact sequence

```text
… → Tor^A₂(M, N'') → Tor^A₁(M, N') → Tor^A₁(M, N) →
    Tor^A₁(M, N'') → M ⊗_A N' → M ⊗_A N → M ⊗_A N'' → 0.
```

By symmetry (next subsection), the same holds in the first argument. This is the workhorse in every Tor calculation.

### Symmetry

There is a canonical isomorphism

```text
Tor^A_i(M, N) ≅ Tor^A_i(N, M)
```

for every `i ≥ 0`. The proof routes through a flat resolution of either argument and is recorded in any
homological-algebra text. The consequence we use: to compute `Tor^A_i(M, N)`, resolve whichever of `M` or `N` is more
convenient.

### Vanishing characterization of flatness

This is the bridge between the abstract derived-functor machinery and Exposé IV. The statement collected from the
literature:

> **`M` is `A`-flat** ⟺ **`Tor^A₁(M, N) = 0` for every `A`-module `N`** ⟺ **`Tor^A_i(M, N) = 0` for every `A`-module `N`
> and every `i ≥ 1`**.

Why the equivalence holds. If `M` is flat, then `M ⊗_A −` is exact, so for any short exact `0 → N' → N → N'' → 0` the
sequence `0 → M ⊗ N' → M ⊗ N → M ⊗ N'' → 0` is exact, so the connecting map `Tor^A₁(M, N'') → M ⊗_A N'` is zero, and
therefore `Tor^A₁(M, N'') = 0` for every `N''`. Iterating with projective resolutions gives `Tor^A_i = 0` for `i ≥ 1`.
Conversely, if `Tor^A₁(M, N) = 0` for every `N`, then for any short exact `0 → N' → N → N''→ 0` the connecting map is
zero, so `0 → M ⊗ N' → M ⊗ N → M ⊗ N'' → 0` is exact, so `M ⊗_A −` is exact, so `M` is flat.

This is exactly how flatness will enter every proof in §§1–2 of the exposé (file 24): we will argue with `Tor^A₁(M, N)`
and read the answer as "flat" or "not flat" depending on whether the Tor vanishes.

### Reduction to `N = A/I`

A second standard fact: `M` is flat iff `Tor^A₁(M, A/I) = 0` for every ideal `I` of `A`, and it suffices to consider `I`
of finite type. The reduction uses the long exact sequence and the fact that `Tor` commutes with directed colimits.
Spelled out: every finitely generated `A`-module admits a composition series with quotients `A/I_j`; vanishing of `Tor`
on each `A/I_j` propagates up the series; vanishing on every finitely generated `N` then propagates to all `N` because
`Tor` commutes with directed colimits.

This reduction is exactly what SGA 1 IV.1 (lines 30–58 of the source) uses without naming. The gentle rewrite in file 24
will lean on it freely.

Exposé IV uses Tor in §IV.2, where the vanishing of `Tor₁` characterises flatness, and in §IV.5, where higher Tor groups
detect when a module fails to be free.

## The spectral sequence for composite functors

Grothendieck's spectral sequence relates the derived functors of `G ∘ F` to the composition of the derived functors of
`G` and `F` separately, when the bookkeeping aligns. SGA 1 IV.5.2 uses exactly one of its consequences — the five-term
exact sequence in low degrees — and we record only what is needed.

### Statement

Let `𝓐, 𝓑, 𝓒` be abelian categories with enough projectives, and let

```text
F : 𝓐 → 𝓑,    G : 𝓑 → 𝓒
```

be additive right-exact functors. Suppose `F` carries projective objects of `𝓐` to `G`-acyclic objects of `𝓑` (i.e.,
objects on which the left-derived functors of `G` vanish in positive degrees). Then there is a spectral sequence

```text
E²_{p, q} = (L_p G)((L_q F)(M))  ⇒  L_{p+q}(G ∘ F)(M)
```

for every object `M` of `𝓐`. Source: appendix row `spectral-sequence-composite-functors`. Cartan-Eilenberg XV.5 (or
Weibel §5.8) gives the construction.

There is a parallel statement for left-exact functors with right- derived functors and injective resolutions. SGA 1
IV.5.2 uses the homological / left-derived form above.

### The five-term exact sequence

The convergence of the spectral sequence in low degrees produces the so-called **five-term exact sequence**

```text
0 ← L₀(G ∘ F)(M) ← L₀G(L₀ F(M)) ← L₁G(L₀ F(M)) ←
    L₁(G ∘ F)(M) ← L₀G(L₁ F(M)).
```

(In cohomological / right-derived notation this is the dual sequence going from `H⁰` to `H²`; we use the homological
direction throughout because Tor is left-derived.) The right-hand-side vanishings produced by feeding flat / acyclic
objects into the sequence are exactly what IV.5.2 will exploit.

For the rewrite in file 26 we need only the part

```text
L₁G(L₀ F(M)) ← L₁(G ∘ F)(M) ← L₀G(L₁ F(M))
```

— that is, the connecting map and the next term. We will identify `L₁` with `Tor₁` for the relevant tensor functors and
read the conclusion off.

### Verification of hypotheses for `F = − ⊗_A B`, `G = − ⊗_B N`

This is the application IV.5.2 makes. Fix `A → B` a ring homomorphism, `M` an `A`-module, `N` a `B`-module. Take

```text
F : A-Mod → B-Mod,    F(M) := M ⊗_A B,
G : B-Mod → Ab,       G(P) := P ⊗_B N.
```

`F` is right exact (tensor product is right exact). `G` is right exact. The composition `G ∘ F` sends `M` to
`(M ⊗_A B) ⊗_B N`, which by associativity of tensor product is `M ⊗_A N` viewed as an abelian group via the structure
`A → B` provides — i.e., the same as restricting `N` to an `A`-module.

The hypothesis "`F` carries projectives to `G`-acyclics" reads: if `M` is a free `A`-module, then `F(M) = M ⊗_A B` is a
free `B`-module, hence `G`-acyclic in the sense that `L_i G(F(M)) = Tor^B_i(F(M), N) = 0` for `i ≥ 1`. This holds — free
`B`-modules are `Tor^B`-acyclic (their Tor with any module is zero in positive degree).

So the spectral sequence applies. Identifying derived functors with `Tor`, the five-term sequence reads

```text
Tor^B₁(M ⊗_A B, N) ← Tor^A₁(M, N) ← Tor^A₁(M, B) ⊗_A N
```

(the relevant central segment, ignoring the surrounding terms), which is exactly the exact sequence SGA 1 IV.5.2 invokes
directly.

The whole point of recording this here is that the rewrite of IV.5.2 in file 26 can quote the five-term sequence by
name, gesture at this prep file, and proceed to the conclusion without unpacking the spectral sequence again.

Exposé IV calls on the spectral sequence in §IV.5 (the local flatness criterion) and in §IV.6 (generic flatness over a
noetherian base).

## Noether's normalization lemma

A finite-type algebra over a field looks complicated until one realizes it is, after a change of variables, a finite
extension of a polynomial ring. That observation is Noether's normalization lemma. SGA 1 IV.6.7 — the generic-freeness
lemma — uses it as the inductive base.

### Statement

Let `K` be a field, and let `B` be a finitely generated `K`-algebra. Then there exist algebraically independent elements
`t₁, …, t_n ∈ B` such that `B` is finite (i.e., finitely generated as a module) over the polynomial subring
`K[t₁, …, t_n]`. The integer `n` equals the **Krull dimension of `B`**, which when `B` is integral is also the
transcendence degree of `Frac(B)` over `K`.

Source: appendix row `noether-normalization`. The classical proof is in Atiyah-Macdonald, _Introduction to Commutative
Algebra_ §5.1 or Bourbaki AC V §3.1. The statement extends to the case `K` an infinite field with `B` integral, where
the `t_i` can be chosen as generic linear combinations of a fixed set of generators of `B`.

### Geometric reading

`B` corresponds to an affine `K`-scheme `Spec B`. The conclusion says there is a finite morphism

```text
Spec B → Spec K[t₁, …, t_n] = 𝔸^n_K
```

where the `t_i` are coordinates on the polynomial subring. So _every affine variety of dimension `n` over a field admits
a finite map to `𝔸^n`_. The map is not unique — different choices of generators and different change-of-variables steps
produce different maps — but its existence is robust.

For a non-trivial example: the affine plane curve `B = K[x, y]/(y² − x³)` is integral of dimension `1`. Noether
normalization picks out a coordinate `t` on a polynomial subring `K[t]` such that `B` is finite over `K[t]`. The choice
`t := x` gives `B = K[t][y]/(y² − t³)`, a degree-`2` finite extension; the map `(x, y) ↦ x` realizes the cusp `y² = x³`
as a degree-`2` cover of the line.

### Sketch of proof

Order the generators `b₁, …, b_m` of `B`. If they are algebraically independent, we are done with `t_i := b_i` and
`n = m`. Otherwise there is a non-trivial polynomial relation `f(b₁, …, b_m) = 0` over `K`. The trick: substitute
`b'_i := b_i − b_m^{r_i}` for `i < m`, with the integers `r_i` chosen so that one variable in the substituted relation
has strictly higher degree than the others. The substituted relation becomes monic in `b_m` over `K[b'₁, …, b'_{m-1}]`,
exhibiting `b_m` as integral over the latter ring. Recurse: now `B` is generated by `b'₁, …, b'_{m-1}` over the integral
closure of `K[b'₁, …, b'_{m-1}]` in `B`, and we apply the inductive hypothesis to those `m - 1` generators.

The substitution trick is the heart of the proof; see Atiyah- Macdonald §5.1 for the carefully bookkept argument.

### Where IV.6.7 uses it

IV.6.7 (file 27) reads: for `A` noetherian integral, `B` a finite-type `A`-algebra, `M` a finite-type `B`-module, there
exists a non-zero `f ∈ A` such that `M_f` is free over `A_f`. The proof is by induction on the dimension of the support
of `M ⊗_A K` over `B ⊗_A K` (where `K = Frac(A)`). At the start of each induction step, one needs to know that `B ⊗_A K`
is finite over a polynomial ring `K[t₁, …, t_n]` — i.e., that **Noether's normalization applies to `B ⊗_A K`**. That is
the one and only place the lemma enters.

The recursion then exhibits the generic part of `M` as a finite free extension over `K[t₁, …, t_n]`, which descends to a
finite free extension over `A_f[t₁, …, t_n]` for some `f ∈ A`. The induction step reduces the dimension by one. The base
case (dimension `−1`, where `M ⊗_A K = 0`) is handled by clearing denominators: some `f ∈ A` annihilates `M`, giving
`M_f = 0`, which is trivially free.

Exposé IV uses Noether normalisation in §IV.6 to reduce questions about finitely-generated algebras to the case of
polynomial algebras, where flatness and openness are visible.

## What this prepares

Three forward references for the gentle reader:

- **File 24 (= IV.1, IV.2)** uses Tor's vanishing characterization of flatness pervasively. The reduction to `N = A/I`
    of finite type appears in the source's own proof of the flatness definition (lines 30–58 of
    `04-morphismes-plats.md`); we lay the algebra here so the rewrite can quote it.
- **File 26 (= IV.5)** uses the spectral sequence for composite functors exactly once, in the proof of IV.5.2 (Serre's
    lemma on extending flatness through `A → B`). The rewrite there cites the five-term exact sequence from this file by
    name.
- **File 27 (= IV.6)** uses Noether's normalization exactly once, in the proof of IV.6.7 (the generic-freeness lemma).
    The rewrite there cites the geometric reading and the inductive argument from this file.

A reader who has finished file 22 can read this prep file in a single pass and move to file 24. A reader rushing to the
geometric payoff (constructibility and generic flatness in file 27) can defer file 23's spectral-sequence section until
needed.
