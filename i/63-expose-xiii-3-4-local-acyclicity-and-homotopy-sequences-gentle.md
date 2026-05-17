# Expose XIII §§3–4 (gentle) — generic local acyclicity, homotopy exact sequences, and the Künneth formula for `π₁^{p'}`

<!-- source: XIII.3 -->

## What this file is about

Push a sheaf forward along a map and ask: does the value at a base point equal what one sees at the fibre above that
point? The previous file isolated a clean special case. The general case is harder and cannot be settled everywhere
— over special points the comparison can fail. The realistic hypothesis is generic. Restrict to a non-empty open
piece of the base, and over that piece the comparison works for every reasonable coefficient.

This generic statement is the engine behind two structural theorems for the algebraic fundamental group. The first
assembles the fundamental groups of fibre, total space, and base into a three-term sequence — the same kind
topologists write for fibre bundles. The second is a product formula for the part coprime to the characteristic. Both
run on inputs imported from later Grothendieck seminars as black boxes.

File 62 isolated tame ramification along an NC divisor as the operative case of cohomological properness. File 63
extracts the *general* mechanism: **generic local acyclicity** (§XIII.3) gives cohomological properness over a non-empty
open of an irreducible base, and this is exactly the input that produces the **étale homotopy exact sequence**
(§XIII.4.1) and the **Künneth formula** `π_1^{p'}(X ×_k Y) ≃ π_1^{p'}(X) × π_1^{p'}(Y)` (§XIII.4.6) for `k` separably
closed and `p` its characteristic.

Throughout this file we quote the SGA 4 / SGA 5 bridge of file 61 §XIII.B. Proofs are sketched in the gentle voice; the
SGA 4 inputs (locally aspherical morphisms, smooth base change, the radicial-base-change reduction VIII 1.1) are named
explicitly at each use.

______________________________________________________________________

## §XIII.3 — Generic local acyclicity

<!-- source: XIII.3 -->

The slogan for §XIII.3 is the **generic** in "generically local acyclic": for `f : X → Y` of finite presentation over an
irreducible base `S` with generic point `s`, one can find a non-empty open `S' ⊆ S` over which `(F, f)` is
cohomologically proper *and* `f_* F` is constructible — for every reasonable étale sheaf `F`. The point is that *some*
hypothesis on the base is needed (cohomological properness fails over the generic point of a general base), but a
generic one suffices.

### XIII.3.1 — Theorem (generic cohomological properness for sheaves of sets).

<!-- source: XIII.3.1 -->

Let `S` be an irreducible scheme with generic point `s`, `X, Y` two `S`-schemes of finite presentation, and `f : X → Y`
an `S`-morphism. For every `S`-scheme `S' → S` write `Y', X', etc.` for the pullbacks. Then:

(1.a) *Generic dim `≤ 0` properness, sheaves of sets.* One can find a non-empty open `S' ⊆ S` such that for every
*finite constant sheaf of sets* `F'` on `X'`, `f'_* F'` is constructible and `(F', f')` is cohomologically proper
relative to `S'` in dim `≤ 0`.

(1.b) *Generic dim `≤ 0` properness, fixed constructible coefficient.* Let `F` be a constructible sheaf of sets on `X`.
One can find a non-empty open `S' ⊆ S`, depending on `F`, such that `f'_* F'` is constructible and `(F', f')` is
cohomologically proper relative to `S'` in dim `≤ 0`.

*Proof.* The standard reduction is by Noetherian induction on `Y` and dévissage on `F`. The two key SGA-4 inputs are:

- [`sga-4-xv-loc-acyclic`](appendix-black-boxes.md#sga-4-xv-loc-acyclic) (SGA 4 XV 1.3, 4.1) — passage to the limit
    along the generic fibre lets us assume `S` is the spectrum of a noetherian local ring with `s` the closed point;
- [`sga-4-xvi-base-change-smooth`](appendix-black-boxes.md#sga-4-xvi-base-change-smooth) (SGA 4 XVI 3.2) — smooth base
    change for sheaves pulled back from the base.

The argument is: spread the constructibility of `F` (B.5) into a stratification of `X` that is geometrically rigid over
`S'`; on each stratum, `F` becomes a finite constant sheaf, and the standard cohomologically-proper-of-finite-
constant-coefficients reduction (B.4 applied to the projection from a relative compactification) gives the result after
shrinking `S` enough.

Slogan: **constructibility + finite-presentation + irreducibility gives cohomological properness on a non-empty open of
the base.**

### XIII.3.1.1 — Generic dim `≤ 1` properness for `ℒ`-group coefficients.

<!-- source: XIII.3.1.1 -->

Under the hypotheses of XIII.3.1, fix a set of primes `ℒ`. There exists a non-empty open `S' ⊆ S` such that for every
*finite constant sheaf of `ℒ`-groups* `F'` on `X'`, `(F', f')` is cohomologically proper relative to `S'` in dim `≤ 1`,
and both `f'_* F'` and `R^1 f'_* F'` are constructible.

*Proof.* The sheaf-of-sets case is XIII.3.1; the additional `R^1` clause comes from XIII.1.14 (the cohomologically-
proper-in-dim-`≤ 1` ⇒ constructible-specialisation criterion). The constructibility of `R^1` for finite `ℒ`-group
coefficients uses the relative étale cohomology calculation
[`sga-4-constructible-sheaves`](appendix-black-boxes.md#sga-4-constructible-sheaves) (SGA 4 IX 2.3).

### XIII.3.1.2 — Soritic: passage to a subscheme of `Y`.

<!-- source: XIII.3.1.2 -->

If XIII.3.1 (or XIII.3.1.1) holds for `(f : X → Y, F)`, the analogous statement holds for `(f|_{X'} : X' → Y', F|_{X'})`
for every constructible subset `Y'` of `Y`. (Cf. SGA 4 IX 2.7.4.)

### XIII.3.1.3 — Soritic: composition.

<!-- source: XIII.3.1.3 -->

If XIII.3.1 holds for `f : X → Y` and `g : Y → Z` separately (with the generic-open shrinking compatible), it holds for
the composite `gf : X → Z`. (Combine XIII.1.6 with the noetherian-induction step.)

### XIII.3.2 — Field base case: full cohomological properness in dim `≤ 0`.

<!-- source: XIII.3.2 -->

Let `k` be a field of characteristic `p ≥ 0`, `p'` the set of primes `≠ p`, and `f : X → Spec(k)` a coherent morphism.
Then:

(1) For *every* sheaf of sets `F` on `X`, `(F, f)` is cohomologically proper relative to `Spec(k)` in dim `≤ 0`.

(2) Suppose moreover one of the following:

(2.a) `f` is of finite type and the finite-type schemes of dimension `≤ dim X` over an algebraic closure of `k` are
*strongly desingularizable*
([`sga-5-i-strongly-desingularizable`](appendix-black-boxes.md#sga-5-i-strongly-desingularizable)).

(2.b) The finite-type schemes over an algebraic closure of `k` are strongly desingularizable.

Then for every finite constant sheaf of `p'`-groups `F` on `X`, `(F, f)` is cohomologically proper relative to `Spec(k)`
in dim `≤ 1`, and `R^1 f_* F` is constructible.

*Proof of (1).* When the base is a field, every base change `Spec(k') → Spec(k)` is flat (vacuously over the point), so
the base-change comparison map `Φ^0 : k' \otimes_k f_* F → f'_* (h^* F)` is the usual `H^0`-base-change for sheaves of
sets — automatic over a field.

*Proof of (2).* The strongly-desingularizable hypothesis gives a resolution `X̃ → X` to which we apply XIII.3.1.1 in its
global form (the base `Spec(k)` is a single point, so the "generic open" is the whole base). The proper-smooth case is
then handled by B.4 applied to the projection from the resolution.

### XIII.3.3 — Strongly-desingularizable ⇒ universal local 1-asphericity.

<!-- source: XIII.3.3 -->

Let `k` be a field of characteristic `p ≥ 0`, `p'` the set of primes `≠ p`, and `f : X → Spec(k)` coherent. Under
hypothesis (2.a) or (2.b) of XIII.3.2, `f` is **universally locally `1`-aspherical for `p'`**: for every base change
`X ×_k T → T` and every torsion `p'`-group constant sheaf `F`, the map `F → R f_* f^* F` is an iso through degree `1`
over every strict localisation of `T`.

*Proof.* The hypothesis gives global cohomological-properness in dim `≤ 1` (XIII.3.2 (2)); by XIII.1.6 and the limit
form XIII.1.12, the property propagates to every coherent base change. Local 1-asphericity on the strict henselisation
is then the strict-localisation form of cohomological-properness in dim `≤ 1` (XIII.1.5 e).

### XIII.3.4 — Universally locally 1-aspherical for `p'`.

<!-- source: XIII.3.4 -->

Let `k`, `p'` be as in XIII.3.3, and `f : X → Spec(k)` coherent. Suppose hypothesis (2.a) or (2.b). Then `f` is
universally locally 1-aspherical for `p'`.

This is XIII.3.3 in the more usable formulation: it generalises to "the geometric fibres of `f` are universally locally
1-aspherical for `p'`," used in the Künneth proof XIII.4.6 below.

*Reduction in case (b).* The question is local on `X`; we may suppose `X` is affine. By passage to the limit
[`sga-4-xv-loc-acyclic`](appendix-black-boxes.md#sga-4-xv-loc-acyclic) (SGA 4 XV 1.3), one is reduced to the case `X` is
of finite type over `k`. Then case (b) reduces to case (a).

### XIII.3.5 — Specialisation of `π_1^ℒ` along generic specialisations.

<!-- source: XIII.3.5 -->

Let `S` be an irreducible scheme with generic point `s`, `f : X → S` of finite presentation. Suppose the finite-type
schemes of dimension `≤ dim X_s` over an algebraic closure `k̄` of `κ(s)` are strongly desingularizable. Let `ℒ` be the
set of primes not in the residual characteristics of `S`. Then there exists a non-empty open `S_1 ⊆ S` such that for
every specialisation `s̄_1 → s̄_2` of geometric points of `S_1`, the specialisation morphism

```text
π_1^ℒ(X_{s̄_1})  →  π_1^ℒ(X_{s̄_2})
```

is *bijective*.

*Proof.* By XIII.3.1 + XIII.3.3, after shrinking `S` to a non-empty open we may assume `f` is locally 1-aspherical for
`ℒ` and that `(F, f)` is cohomologically proper in dim `≤ 1` for every finite constant sheaf `F` of `ℒ`-groups on `X`.
Then XIII.1.14 gives bijective cospecialisation of `R^1 f_* F`. Translating cospecialisation of `R^1 f_* F` into
bijectivity of `π_1^ℒ(X_{s̄_1}) → π_1^ℒ(X_{s̄_2})` uses V.6.9 of file 33 and the description of `π_1^ℒ` as the pro-`ℒ`
Galois category of `X_{s̄}`.

Slogan for XIII.3: **after shrinking the base to a non-empty open, cohomological properness in dim `≤ 1` for `ℒ`-group
coefficients holds, and `π_1^ℒ` of the geometric fibre is locally constant on the base.**

______________________________________________________________________

## §XIII.4 — Exact homotopy sequences

<!-- source: XIII.4 -->

We now use the cohomologically-proper machinery of §§XIII.1–3 to produce the **étale homotopy exact sequence**: for a
"good" morphism `f : X → S`, a geometric point `s̄ → S` and a geometric point `a → X_{s̄}`,

```text
π_1^ℒ(X_{s̄}, a)  →  π_1'(X, a)  →  π_1(S, a)  →  1
```

is exact (XIII.4.1, XIII.4.3). The Künneth formula XIII.4.6 follows by combining the homotopy exact sequence with
XIII.3.4.

### XIII.4.0 — The group `π_1'(X, a)` and the candidate sequence.

<!-- source: XIII.4.0 -->

Let `X, S` be connected schemes, `f : X → S` a morphism, `a` a geometric point of `X`. Let `ℒ` be a set of primes. Set

```text
K := Ker( π_1(X, a) → π_1(S, a) )
```

(a closed normal pro-subgroup of `π_1(X, a)`), and let `N ⊆ K` be the *smallest* closed normal pro-subgroup such that
`K / N` is a pro-`ℒ`-group; write `K^ℒ := K / N` (the maximal pro-`ℒ` quotient of `K`). The subgroup `N` is closed
normal not only in `K` but in `π_1(X, a)` (because conjugation by `π_1(X, a)` preserves both `K` and the pro-`ℒ`
property). We define

```text
π_1'(X, a) := π_1(X, a) / N.
```

If `a` is a geometric point of a geometric fibre `X_{s̄}`, the canonical morphisms

```text
π_1(X_{s̄}, a)  →  π_1(X, a)  →  π_1(S, a)
```

induce morphisms

```text
π_1^ℒ(X_{s̄}, a)  -u→  π_1'(X, a)  -v→  π_1(S, a).
```

Visibly `v ∘ u = 0`: the image of `π_1(X_{s̄})` in `π_1(X)` lies in `K`, and `K / N = K^ℒ` injects into `π_1'(X)`, so
`u` factors through the pro-`ℒ` quotient of `K`. After passing further to `π_1(X) / N = π_1'(X)`, the composite
`π_1^ℒ(X_{s̄}) → π_1'(X) → π_1(S)` annihilates `K^ℒ` and hence everything in the image of `u`.

### XIII.4.1 — Theorem: exactness of the right two terms.

<!-- source: XIII.4.1 -->

Let `S` be a connected scheme, `f : X → S` a *locally 0-acyclic* morphism (SGA 4 XV 1.11) that is moreover *0-acyclic* —
for coherent `f`, equivalent to "the geometric fibres of `f` are connected" (SGA 4 XV 1.16). Let `ℒ` be a set of primes.
Suppose that for every étale cover `S' → S` and every étale cover `E → X'` (with `X' = X ×_S S'`) that is a quotient of
a Galois cover with `ℒ`-group, `(E, f')` is cohomologically proper relative to `S'` in dim `≤ 0` and `f'_* E` is
constructible.

Then for every geometric point `s̄` of `S` and every geometric point `a` of `X_{s̄}`, the sequence

```text
π_1^ℒ(X_{s̄}, a)  -u→  π_1'(X, a)  -v→  π_1(S, a)  →  1
```

is *exact*.

*Proof.* We have already noted `v u = 0`. We split exactness into surjectivity of `v` and surjectivity of `u` onto
`K^ℒ = Ker(v)`.

**Surjectivity of `v`.** Equivalent (V.6.9 of file 33) to: for every connected étale cover `S' → S`, `X' = X ×_S S'` is
also connected. Let `C` be any set with `|C| ≥ 2`; since `f` is 0-acyclic, the canonical map
`H^0(S', C_{S'}) → H^0(X', C_{X'})` is bijective; hence the number of connected components of `X'` equals the number of
connected components of `S'`, which is `1`.

**Surjectivity of `u` onto `K^ℒ`.** By definition of `K^ℒ`, this is equivalent to: for every étale cover `S' → S` and
every Galois cover `Q → X' = X ×_S S'` with `ℒ`-group `F`, such that `P = Q ×_{X'} X̃` is connected on the universal
cover `X̃ = S̃ ×_S X`, `Q|_{X_{s̄}}` is *connected*.

By the standard equivalence-of-categories argument we may instead show the contrapositive: if `Q|_{X_{s̄}}` is
*disconnected*, then *after possibly replacing `S'` by an étale cover*, `Q` itself is disconnected. So suppose
`Q|_{X_{s̄}}` is disconnected. Then there is a subgroup `G ⊊ F` and a `(G|_{X_{s̄}})`-torsor `R` on `X_{s̄}` such that
`Q|_{X_{s̄}}` arises from `R` by extension of structure group `G → F`. Let `E := Q / G` (an étale cover of `X'` with
`F / G ≠ 1` as a quotient of its structure group); then `E|_{X_{s̄}}` *has a section*.

By the cohomologically-proper hypothesis applied to `(E, f')`, `f'_* E` is a locally constant constructible sheaf on
`S'`. Replacing `S'` by a further étale cover, we may assume `f'_* E` is *constant*. Cohomological properness in dim
`≤ 0` says `(f'_* E)_{s̄} ≃ H^0(X_{s̄}, E|_{X_{s̄}}) ≠ ∅` (because `E|_{X_{s̄}}` has a section). So
`H^0(S', f'_* E) ≠ ∅`, which gives a section of `E → X'`, which shows `E = Q / G` admits a section, contradiction — so
`Q` was already disconnected after the étale cover. This proves surjectivity of `u`.

Slogan: **the cohomologically-proper-coefficients hypothesis is what produces the homotopy exact sequence; under it,
every disconnection of `Q|_{X_{s̄}}` lifts to a disconnection of `Q|_{X'}`.**

### XIII.4.2 — Coherent corollary.

<!-- source: XIII.4.2 -->

Let `S` be a connected scheme, `f : X → S` a *coherent* morphism that is *locally 0-acyclic* and *0-acyclic*, `ℒ` a set
of primes. Suppose that for every finite constant sheaf of `ℒ`-groups `F` on `X`, `(F, f)` is cohomologically proper
relative to `S` in dim `≤ 0` and `f_* F` is constructible. Then the exact sequence

```text
π_1^ℒ(X_{s̄}, a)  →  π_1'(X, a)  →  π_1(S, a)  →  1
```

of XIII.4.1 holds.

*Proof.* Specialise XIII.4.1 to the coherent + finite-constant-coefficient case. Coherence ensures the geometric- fibre
criterion XIII.1.5 b applies; 0-acyclicity gives the surjectivity of `v`. The remaining cohomologically- proper
hypothesis is the one assumed.

### XIII.4.3 — Exactness of the full four-term sequence.

<!-- source: XIII.4.3 -->

Let `S` be connected, `f : X → S` a 0-acyclic morphism that is *locally 1-aspherical for `ℒ`*, and let `g : S → X` be a
section of `f`. Let `s̄`, `a` be as in XIII.4.0. Suppose for every constant sheaf of `ℒ`-groups `F`, `(F, f)` is
cohomologically proper in dim `≤ 1`, the direct image by `f` of `Tors(F)` is 1-constructible, and for every étale cover
`E → X'` that is a quotient of a Galois `ℒ`-group cover, `f'_* E` is constructible. Then

```text
1  →  π_1^ℒ(X_{s̄}, a)  -u→  π_1'(X, a)  -v→  π_1(S, a)  →  1
```

is exact.

*Proof.* The right exactness is XIII.4.2. The new content is injectivity of `u`. By V.6.8 (file 33), `u` injective is
equivalent to: every principal cover `Z̄ → X_{s̄}` with `ℒ`-group `C` arises (up to connected component) as the
restriction `Z|_{X_{s̄}}` of some étale cover `Z → X`.

Let `z̄ ∈ H^1(X_{s̄}, C_{X_{s̄}})` be the class of `Z̄`. By XIII.1.5 d (the geometric-fibre form),

```text
(R^1 f_* C_X)_{s̄}  ≃  H^1(X_{s̄}, C_{X_{s̄}}).
```

By XIII.1.16, `R^1 f_* C_X` is locally constant constructible on `S`, so it is constant on an étale cover `S' → S`.
Pulling `s̄` through to a geometric point `s̄ → S'`, we find `z ∈ H^0(S', R^1 f_* C_X)` mapping to `z̄`. By the sublemma
XIII.4.3.1 below, there is a further étale cover `S'_1 → S'`, a torsor `P` on `X'_1 = X ×_S S'_1` with group `C`, whose
image in `H^0(S'_1, R^1 f_* C)` is the pullback of `z`. The torsor `P` is representable by an étale cover `Z → X'_1`
such that `Z ×_{X'_1} X_{s̄} ≃ Z̄`; viewed as an étale cover of `X` over the cover `X'_1 → X` of `X`, this gives the
desired étale cover whose `X_{s̄}`-restriction realises `z̄`.

### XIII.4.3.1 — Sublemma (descent of a torsor class from `R^1 f_*`).

<!-- source: XIII.4.3.1 -->

Let `f : X → S` be 0-acyclic and locally 0-acyclic, `g : S → X` a section, `C` a finite constant group with `(C_X, f)`
cohomologically proper in dim `≤ 0` and `f_* Tors(C_X)` constructible. Then for every `z ∈ H^0(S, R^1 f_* C_X)`, there
is an étale cover `S_1 → S` and an element of `H^1(X_1, C_{X_1})` (where `X_1 = X ×_S S_1`) whose image in
`H^0(S_1, R^1 f_* C_{X_1})` is the pullback of `z`.

*Proof.* For `S' → S` étale, set `X' = X ×_S S'`. Let `G` be the presheaf

```text
G(S') = { iso classes (P, ι : g'^* P ≃ C_{S'}) : P a C_{X'}-torsor on X' }.
```

`G` is in fact a sheaf (descent for the torsor + the section-trivialisation), and the forgetful map `G → R^1 f_* C_X` is
surjective. Let `z ∈ H^0(S, R^1 f_* C_X)`, `H ⊆ G` its preimage. It suffices to show `H` is locally constant
constructible. Locally on `S` we may assume `z` is represented by a torsor `P` on `X` with `g^* P ≃ C_S`. The
trivialisations of `g^* P` are a torsor under `Aut_{C_S}(g^* P) ≃ C` (with `C` viewed as a constant sheaf on `S`),
modulo the image of `f_* Aut_{C_X}(P) → C`. Since `f_* Aut_{C_X}(P)` is locally constant constructible by XIII.1.16, the
quotient `H` is so too.

### XIII.4.4 — Examples: when the hypotheses are satisfied.

<!-- source: XIII.4.4 -->

The hypotheses of XIII.4.1 are satisfied in two key examples:

(i) `f` is *proper, flat, of finite presentation, with connected separable geometric fibres*; `ℒ` arbitrary. (Cf. X.1.3
of file 48 for the smooth analogue.)

(ii) `f` is the projection `X → S` of the complement of an NC divisor relative to `S` in a proper smooth scheme `Z → S`
(XIII.2.4 of file 62), `ℒ` arbitrary.

The hypotheses of XIII.4.3 are satisfied in case (i) if additionally `f` is *smooth* and has a section, with `ℒ` =
primes not in the residual characteristics of `S` (B.4 + SGA 4 XVI 5.2).

### XIII.4.5 — Cleaner pro-`ℒ` versions of XIII.4.3.

<!-- source: XIII.4.5 -->

Three refinements of XIII.4.3 in the pro-`ℒ` regime.

#### XIII.4.5.1 — Pro-`ℒ`-quotient version.

If the section `g` of XIII.4.3 is replaced by a section "up to pro-`ℒ` ambiguity," the same conclusion holds for the
sequence of pro-`ℒ` fundamental groups.

#### XIII.4.5.2 — Smooth-proper case.

If `f` is smooth proper with connected fibres and a section, with `ℒ` = primes not in the residual characteristics of
`S`:

```text
1  →  π_1^ℒ(X_{s̄}, a)  →  π_1^ℒ(X, a)  →  π_1^ℒ(S, a)  →  1
```

is exact.

#### XIII.4.5.3 — Pro-`p'` version for `S = Spec(k)` with `k` separably closed.

`S` reduces to a point and `π_1^ℒ(S) = 1`; the sequence collapses to an iso `π_1^ℒ(X_{s̄}) ≃ π_1^ℒ(X)`. Used in the
Künneth proof XIII.4.6 below.

### XIII.4.6 — The Künneth formula for `π_1^{p'}`.

<!-- source: XIII.4.6 -->

Let `k` be a separably closed field of characteristic `p ≥ 0`, `X` and `Y` two connected `k`-schemes, `a` a geometric
point of `X`, `b` a geometric point of `Y`, `c` a geometric point of `X ×_k Y` above `a` and `b`. Suppose:

(a) `X` is of finite type over `k`, and the finite-type schemes of dim `≤ dim X` over an algebraic closure `k̄` of `k`
are strongly desingularizable; OR

(b) `X` is quasi-compact and quasi-separated, and every finite-type scheme over `k̄` is strongly desingularizable.

Let `p'` be the set of primes `≠ p`. Then the morphism

```text
π_1^{p'}(X ×_k Y, c)  →  π_1^{p'}(X, a) × π_1^{p'}(Y, b)
```

induced by the two projections is an *isomorphism*.

*Proof.* We may suppose `k` algebraically closed and `X` reduced
([`sga-4-viii-1-1-reduction`](appendix-black-boxes.md#sga-4-viii-1-1-reduction); SGA 4 VIII 1.1). Let `Z = X ×_k Y`,
`g : X → k` and `f : Z → Y` the canonical morphisms. By XIII.3.5 / XIII.3.4 the morphism `g`, and hence `f`, is
*universally locally 1-aspherical for `p'`*. Since `X` is connected, `f` is 0-acyclic
([`sga-4-xv-loc-acyclic`](appendix-black-boxes.md#sga-4-xv-loc-acyclic); SGA 4 XV 1.16). On the other hand, by XIII.3.2,
for every finite constant `p'`-group `C` the pair `(C_X, g)` is cohomologically proper relative to `k` in dim `≤ 1`; it
follows by XIII.1.5 c that `(C_Z, f)` is cohomologically proper relative to `Y` in dim `≤ 1`, and that `f_* C_Z` and
`R^1 f_* C_Z` are constant sheaves on `Y`. So `f` satisfies all the hypotheses of XIII.4.2.

Thus we have the exact sequence

```text
π_1^{p'}(X_b, c)  →  π_1^{p'}(Z, c)  →  π_1^{p'}(Y, b)  →  1.
```

The composite

```text
π_1^{p'}(X_b, c)  →  π_1^{p'}(Z, c)  →  π_1^{p'}(Y, b)
```

is zero (composition factors through `K`); but moreover the canonical morphism `π_1^{p'}(X_b, c) → π_1^{p'}(X, a)` is an
isomorphism (since `X_b ≃ X` as a fibre of the projection `Z → Y`). So we have a commutative diagram of exact sequences

```text
π_1^{p'}(X, a)  →  π_1^{p'}(Z, c)  →  π_1^{p'}(Y, b)  →  1
   ‖                    ↓                    ‖
π_1^{p'}(X, a)  →  π_1^{p'}(X, a) × π_1^{p'}(Y, b)  →  π_1^{p'}(Y, b)  →  1.
```

The bottom row is split exact (a product). The vertical map in the middle is the natural one to the product. Since both
rows are exact and the outer verticals are isos, the middle vertical is an iso. This is the desired Künneth.

Slogan: **the Künneth formula for `π_1^{p'}` is the composite of (i) "smooth-and-projection-onto-`Y` is locally
aspherical" XIII.3.4 and (ii) "the homotopy exact sequence" XIII.4.2, both rendered cleanly by the SGA 4 / SGA 5
bridge.**

### XIII.4.7 — Variants and refinements.

<!-- source: XIII.4.7 -->

Several technical variants used in the proper-smooth-surface application:

#### XIII.4.7 (main) — Homotopy exact sequence with retrocompact open.

Let `S` be a connected normal scheme, `U ⊆ S` a dense retrocompact open, `f : X → S` proper of finite presentation with
geometrically connected and irreducible fibres at every point of `T := S − U`. Suppose `f` is *separable*, *smooth at
the points of `f^{-1}(U) ∪ g(T)`* (for some section `g : T → X`), `ℒ` = primes not in the residual characteristics of
`S`, and `X` *regular* at every point of `X_t` for `t ∈ T`. Then the homotopy exact sequence of XIII.4.3 holds for
`f : X → S`.

#### XIII.4.7.4 — Proper-smooth-fibration variant.

If additionally the fibres `X_t` for `t ∈ T` are proper smooth and `f` extends to a proper smooth `X̃ → S̃` over a
closure `S̃` of `S`, the exact sequence `1 → π_1^ℒ(X_{s̄}) → π_1^ℒ(X) → π_1^ℒ(S) → 1` holds, *generalising* the standard
smooth-proper case to a singular base.

### XIII.4.8 — Topological finite presentation of `π_1^ℒ(X)` under `π_1(S) = 1`.

<!-- source: XIII.4.8 -->

The hypotheses are those of XIII.4.7.4. Suppose moreover `π_1(S, a) = 1`. Then

```text
π_1^ℒ(X, a)  ≃  π_1^ℒ(X_{s̄}, a)_K,
```

where the subscript `K` denotes coinvariants under the natural action of `K = Ker(π_1(X) → π_1(S))` on the fibre group
(restricted to its `ℒ`-quotient).

In particular: if `π_1^ℒ(X_{s̄}, a)` is topologically of finite presentation and `K` acts through a group of finite
type, then `π_1^ℒ(X, a)` is topologically of finite presentation.

*Proof.* The iso `π_1^ℒ(X, a) ≃ π_1^ℒ(X_{s̄}, a)_K` is XIII.4.7.4 with `π_1(S, a) = 1`. The finite-presentation part:
suppose `π_1^ℒ(X_{s̄}, a) = L(x_1, …, x_n) / ⟨y_1, …, y_p⟩` (a quotient of the free pro-`ℒ` group on `n` generators by
the closed normal subgroup generated by `p` elements); suppose `K` acts through a finite-type group generated by
`k_1, …, k_q`. Let `z_{ij} ∈ L(x_1, …, x_n)` lift `(k_j · x_i) x_i^{-1}`. Then `π_1^ℒ(X_{s̄}, a)_K` is the quotient of
`L(x_1, …, x_n)` by the closed normal subgroup generated by `y_1, …, y_p` and `z_{ij}` (`1 ≤ i ≤ n`, `1 ≤ j ≤ q`), which
is finitely many elements.

#### Murre's application to proper smooth surfaces.

XIII.4.8 + a Murre fibration argument (reduce a connected proper smooth surface `X / k` to a fibration `X → ℙ^1_k` over
an open `U ⊆ ℙ^1_k` via blow-up, then apply XIII.4.7 + XIII.4.8) gives:

**Theorem (Murre, after Raynaud).** *For `X` a proper smooth surface over a separably closed field `k` of characteristic
`p`, `π_1^{p'}(X)` is topologically of finite presentation. More generally, for any connected finite-type `k`-scheme `X`
such that the finite-type schemes over `k̄` of dimension `≤ dim X` are strongly desingularizable, `π_1^{p'}(X)` is
topologically of finite presentation.*

The full Murre / Raynaud argument is in
[`sga-7-fund-group-proper-smooth`](appendix-black-boxes.md#sga-7-fund-group-proper-smooth) (SGA 7).

Slogan for XIII.4.8: **with simply-connected base and strongly-desingularizable fibres, the étale `π_1^{p'}` of the
total space is the coinvariants of the geometric-fibre group under the base monodromy — and is therefore topologically
of finite presentation in standard situations.**

______________________________________________________________________

## Closing pointer

File 64 (gentle §XIII.5) develops the Abhyankar variants quoted in file 62 (§XIII.2.4.3) and file 63 (§XIII.4 via the
XIII.2.4 application): the local Kummer cover XIII.5.1, the absolute Abhyankar lemma XIII.5.2, and the relative variants
XIII.5.3–XIII.5.6. After file 64, the gentle SGA project closes; the forward path is SGA 4 (étale cohomology in full),
SGA 4½ + Deligne (Weil conjectures), and SGA 5 (higher cohomologically-proper machinery + trace formula).
