# Expose XIII §2 (gentle) — normal-crossings divisors, tame ramification, and the tame fundamental group of an open curve

<!-- source: XIII.2 -->

## What this file is about

Cut a few points out of a smooth surface. The picture in higher dimensions: two coordinate planes meeting at a right
angle, with the missing locus running along the meeting line. The shape that remains has more loops than it started with
— a new one around every cut. Algebraically, the cut lets covers spread out badly near the missing piece, in two
flavours, one controlled and the other not. Restricting to the controlled flavour carves out the part of the fundamental
group that behaves cleanly across families.

The technical name for the controlled flavour is tame. Linear data on the complement that is tame along the cut has
pushforwards that survive base change in any family. The headline payoff is an explicit description of the tame
fundamental group of a punctured smooth curve, lifted from the previous chapter's answer through a familiar mechanism.

File 61 gave the cohomological-properness language. File 62 applies it to the geometric setting that motivates the whole
exposé: an open `U = X − Y` of a proper smooth `S`-scheme `X`, with `Y = Supp D` a *normal-crossings divisor* relative
to `S`. The main theorem (XIII.2.4) says that for a sheaf `F` on `U` that is *tamely ramified* along `D`, both `i_* F`
and the *tame* `R¹_tame i_* F` commute with every base change in `S`. The headline corollary (XIII.2.12) gives an
explicit presentation of the tame fundamental group of a punctured proper smooth curve over a separably closed field, by
lifting the characteristic-zero answer (file 60 XII.5.2 — Riemann existence) into characteristic `p` via the Witt-vector
/ EGA III §7.4 mechanism the transcendental method of file 50 made familiar.

The file is structured as follows: §XIII.2.0 sets up tame ramification over a DVR, in the general (non-separable-
residue) form Mme Raynaud's notes give; §XIII.2.1 defines NC divisors, tame sheaves on `U`, the tame `H¹`, and the tame
fundamental group; §XIII.2.2–XIII.2.3 record the class of "good" coefficients; §XIII.2.4 is the main theorem, with its
three-part proof; §§XIII.2.5–XIII.2.11 collect the specialisation corollaries; §XIII.2.12 is the curve calculation;
§XIII.2.13 records Raynaud's 2003 remark on Abhyankar's conjecture.

______________________________________________________________________

## §XIII.2.0 — Tame ramification over a discrete valuation ring

<!-- source: XIII.2.0 -->

*This section says:* for `R` a DVR with field of fractions `K` and residual characteristic `p`, an étale `K`-algebra
`L = ∏ L_i` is *tamely ramified over `R`* if the inertia group of the Galois closure `L'_i / K` at `R` has order prime
to `p`. The class is stable under subalgebra, tensor product, and base change to a separable-residue extension of `R`.
This is the input that makes the Galois category `C_t` of XIII.2.1.3 well-defined.

### XIII.2.0 — Definition; structure of the inertia group.

<!-- source: XIII.2.0 -->

Let `R` be a DVR with field of fractions `K` and residual characteristic `p ≥ 0`. Let `L` be an étale `K`-algebra,
written as a finite product of fields `L = ∏_{i ∈ I} L_i`, with each `L_i` an étale `K`-extension. Let `L'_i` denote the
Galois closure of `L_i` in some fixed algebraic closure of `L_i`.

**Definition.** *`L` is **tamely ramified over `R`** if for every `i ∈ I` the inertia group `I_i ⊆ Gal(L'_i / K)` of the
valuation extending that of `R` has order prime to `p`.*

**Structural lemma.** In any case (whether or not `L` is tame), the inertia group `I_i` is an extension of a cyclic
group of order prime to `p` by a (possibly trivial) `p`-group `P_i`.

*Proof in the general case (no separable-residue hypothesis).* In the separable-residue case this is Serre's *Local
Fields* IV §1–§2 prop. 7 cor. 4 ([`serre-local-fields-iv-7`](appendix-black-boxes.md#serre-local-fields-iv-7)). In the
general case we reproduce the higher-ramification-filtration argument Mme Raynaud's notes give.

Set `G = Gal(L'_i / K)`, write `A_L` for the integral closure of `R` in `L'_i`, and let `π` be a uniformiser of `A_L`.
Define `H^i ⊆ G_0` (the inertia subgroup) for `i ≥ 1` by

```text
H^i = { s ∈ G_0 : s π / π ∈ U^i },
```

where `U^i = 1 + 𝔪^i_{A_L}` is the higher units filtration. Then:

(i) `G_0 / H^1` is naturally a subgroup of `κ(A_L)^×` modulo a finite quotient; since `κ(A_L)^×` has no element of order
`p`, `G_0 / H^1` has order prime to `p`;

(ii) for `i ≥ 1`, `H^i / H^{i+1}` is naturally a subgroup of the additive group `κ(A_L)^+`, and hence is a `p`-group;

(iii) the filtration `G_0 ⊃ H^1 ⊃ H^2 ⊃ …` is eventually trivial (it stabilises in finite many steps because `A_L` is
noetherian).

The conjunction of (i), (ii), (iii) shows that `H^1` is a `p`-group and `G_0 / H^1` is cyclic of order prime to `p`,
which is the announced statement.

Slogan: **the wild inertia is exactly `H^1`, a (pro-)`p`-group; what is left, `G_0 / H^1`, is the tame inertia, cyclic
of order prime to `p`.**

### XIII.2.0.1 — Strictly-local characterisation.

<!-- source: XIII.2.0.1 -->

*This says:* if `R` is strictly local (= henselian with separably-closed residue field), tame ramification is detected
by the factor-degrees alone.

Let `R` be a strictly local DVR with residual characteristic `p`. An étale `K`-algebra `L = ∏ L_i` is tame over `R`
*iff* `[L_i : K]` is prime to `p` for every `i`. Moreover, in this case each `L_i` is cyclic over `K`.

*Proof.* When `R` is strictly local, `I_i = Gal(L'_i / K)` is the full Galois group, so by XIII.2.0 it is
`cyclic-prime-to-p ⋊ p-group`. If `L` is tame, `I_i` has order prime to `p`, hence equals the cyclic-prime-to-`p`
factor, and `[L_i : K] = |I_i|` is prime to `p`; the `L_i` are then cyclic. Conversely, if `[L_i : K]` is prime to `p`,
then `I_i` cannot have a non-trivial normal `p`-subgroup (such would lie in `H^1`, of order a positive power of `p`,
contradicting prime-to-`p` cardinality). Hence `I_i` is cyclic of order prime to `p`, so `L_i` is tame.

### XIII.2.0.2 — Base change to a separable-residue DVR extension.

<!-- source: XIII.2.0.2 -->

Let `R → R'` be a morphism of DVRs such that the image of a uniformiser `π` of `R` is a uniformiser `π'` of `R'`, and
the residue extension `κ(R') / κ(R)` is separable. Let `L` be an étale `K`-algebra and put `L' = L ⊗_K K'`. Then `L` is
tame over `R` *iff* `L'` is tame over `R'`.

*Proof.* Reduce to `R` strictly local (XIII.2.0.1) and to `L` a single field. Let `L̄ = L ⊗_K K̄`, where `K̄` is the
fraction field of a strict henselisation `R̄ → R̄'` is again separable-residue. Decompose `L̄ = ∏ L̄_i` and
`L̄' = L̄ ⊗_K K̄' = ∏ L̄'_j`. Use the inertia computation of XIII.2.0 in `Gal(L' / K)` and `Gal(L̄' / K̄')`, exploiting
the tower formula `inertia(L'/K) = inertia(L̄'/K̄)` (because `κ(R')/κ(R)` is separable, residue extensions factor
compatibly: [`ega-iv-4-3-2-5`](appendix-black-boxes.md#ega-iv-4-3-2-5)). The wild inertia `P_j` of `L̄'/K̄'` factors
through the wild inertia `P_i` of `L'/K`, and conversely; hence `L'` is tame iff `L` is tame.

Slogan: **tame ramification is invariant under separable-residue base change of the DVR.**

### XIII.2.0.3 — Closure properties of the tame class.

<!-- source: XIII.2.0.3 -->

The class of tame étale `K`-algebras over `R` is closed under:

- subalgebra: if `L` is tame and `M ⊆ L` is an étale `K`-subalgebra, then `M` is tame;
- tensor product: if `L, M` are both tame, then `L ⊗_K M` is tame;
- base change: if `L` is tame and `R → R'` is a DVR map (with separable-residue extension or with the more general
    *tame* extension `R → R'`), then `L ⊗_K K'` is tame;
- *tame descent*: if `R → R'` is a tame DVR map and `L ⊗_K K'` is tame over `R'`, then `L` is tame over `R`.

All four follow from the inertia-structure description of XIII.2.0 by reduction to the strictly-local case via
XIII.2.0.1.

______________________________________________________________________

## §XIII.2.1 — NC divisors, tame sheaves, and the tame fundamental group

<!-- source: XIII.2.1 -->

We now fix an `S`-scheme `X` carrying a divisor `D ≥ 0`, set `Y = Supp D` and `U = X − Y`, and let `i : U → X` be the
canonical open immersion. The constructions below are functorial in `S` and étale-local on `X`.

### XIII.2.1.0 — Normal-crossings divisors relative to `S`.

<!-- source: XIII.2.1.0 -->

The divisor `D` is **strictly with normal crossings relative to `S`** if there is a finite family `(f_i)_{i ∈ I}` of
elements of `Γ(X, 𝒪_X)` such that `D = ∑_{i ∈ I} div(f_i)` and the following holds:

(NC) *For every point `x` of `Supp D`, `X` is smooth over `S` at `x`, and, with `I(x) = { i ∈ I : f_i(x) = 0 }`, the
subscheme `V((f_i)_{i ∈ I(x)})` is smooth over `S` of codimension `#I(x)` in `X`.*

The divisor `D` is **with normal crossings relative to `S`** (or simply "an NC divisor") if it is *étale-locally* on `X`
strictly with normal crossings. (SGA 5 II 4.2.)

The étale-local condition is the right one: it makes the framework étale-local on `X`, and it lets every NC datum be
checked at a single geometric point.

#### Consequences of XIII.2.1.0.

Let `D` be an NC divisor relative to `S` and `Y = Supp D`. For every geometric point `s̄` of `S` and every *maximal
point* `y` of `Y_{s̄}` (a generic point of an irreducible component of `Y_{s̄}`), the local ring `𝒪_{X_{s̄}, y}` is a
*discrete valuation ring*. (At `y`, only one of the `f_i`, say `f_{i_0}`, vanishes; `f_{i_0}` is a uniformiser; `X` is
smooth over `S` at `y`; codimension 1.) Tame ramification along `D` will be checked at these DVRs.

### XIII.2.1.1 — Tamely ramified sheaves of sets / groups along `D` relative to `S`.

<!-- source: XIII.2.1.1 -->

Let `F` be a sheaf of sets on `U`. One says that `F` is **tamely ramified on `X` along `D` relative to `S`** if for
every geometric point `s̄` of `S` and every maximal point `y` of `Y_{s̄}`, the restriction of `F` to the fraction field
`K` of `𝒪_{X_{s̄}, y}` is representable by `Spec(L)` for an étale `K`-algebra `L` that is tamely ramified over the DVR
`𝒪_{X_{s̄}, y}` (XIII.2.0).

When `D` is fixed and unambiguous, we omit mention of it and say "tamely ramified on `X` relative to `S`" or simply
"tame."

*This says:* tameness of an étale sheaf `F` on `U` is *purely a local condition* at maximal points of the geometric
fibres of `Y`. At each such point, the stalk of `F` is an étale `K`-algebra over a DVR; we require it to be tame in the
sense of XIII.2.0.

### XIII.2.1.2 — Tame `H¹` and tame `R¹`.

<!-- source: XIII.2.1.2 -->

Let `F` be a *sheaf of groups* on `U`, tame on `X` relative to `S`. The set

```text
H¹_tame(U, F) := { classes of F-torsors P that are tame on X relative to S } ⊆ H¹(U, F).
```

For a commutative diagram of `S`-schemes

```text
U  -i→  X
 \      |
  g     f
   \    |
       T
```

with `i` as in XIII.2.1, the subsheaf

```text
R¹_tame g_* F  ⊆  R¹ g_* F
```

is the sheaf on `T` associated with the presheaf `T' ↦ H¹_tame(U', F)`, where `T'` ranges over étale schemes over `T`
and `U' = U ×_T T'`. (The presheaf-to-sheaf step is the sheafification of XIII.0.3 applied to the gerbe of tame
torsors.)

For `g` coherent and `t̄` a geometric point of `T`, with `T̄ = T_{(t̄)}` and `Ū = U ×_T T̄`,

```text
(R¹_tame g_* F)_{t̄}  ≃  H¹_tame(Ū, F̄).
```

(SGA 1 XIII §2.1.2.1; cf. the stalk description of `R^1 g_*` in file 61 §XIII.B.2.)

Slogan: **`R¹_tame g_* F` is the "tame piece" of `R^1 g_* F` — the subsheaf classifying only those `F`-torsors that
extend tamely across `D`.**

### XIII.2.1.3 — The Galois category `C_t` and the tame fundamental group.

<!-- source: XIII.2.1.3 -->

Let `U` be connected and let `a` be a geometric point of `U`. Let

```text
C_t = C_t((U, X)/S)
```

be the category of finite étale coverings `U' → U` that are tamely ramified on `X` relative to `S` (XIII.2.1.1 applied
to the sheaf of sets `U' / U`). Define the functor

```text
Γ_t : C_t → Set,  Γ_t(U') = { geometric points of U' above a }.
```

By XIII.2.0 (and especially XIII.2.0.3), the pair `(C_t, Γ_t)` satisfies axioms `(G_1)`–`(G_6)` of V.4 (file 32):

- `(G_1)` `C_t` has a final object (`U` itself) and finite fibre products (intersections of tame étale covers are tame,
    via XIII.2.0.3);
- `(G_2)` finite sums and quotients by finite group actions exist (Galois closure of a tame cover is tame);
- `(G_3)` `Γ_t` is left-exact;
- `(G_4)` `Γ_t` commutes with finite sums;
- `(G_5)` `Γ_t` is right-exact for quotients;
- `(G_6)` `Γ_t` is conservative (cf. file 32 V.4).

Consequently `Γ_t` is **pro-representable**: there is a pro-object `Ũ → U` in `C_t`, called the **tame universal
covering** of `(U, X)/S` pointed at `a`, and a profinite group

```text
π_1^tame((U, X)/S, a)  =  Aut(Ũ → U)^{op}
```

— the **tame fundamental group**. (Notation `π_1^tame(U, a)` or just `π_1^tame(U)` when `X` and `S` are clear from
context.) Since `C_t ⊆` the category of all finite étale coverings of `U`, `π_1^tame(U, a)` is canonically a *quotient*
of `π_1(U, a)` (V.6.9 of file 33).

Slogan: **the tame fundamental group is the étale fundamental group restricted to coverings whose ramification at the
boundary is prime to the residual characteristic.**

### XIII.2.1.4 — Functoriality of tame torsors.

<!-- source: XIII.2.1.4 -->

Let `F` be a sheaf of groups on `U`. Let `P` be a right `F`-torsor and `Q` a left `F`-torsor, both tame on `X` relative
to `S`. Then the *contracted product* `P ∧^F Q` is also tame on `X` relative to `S`.

*Proof.* The question reduces to: if `R` is a DVR with field of fractions `K`, `F` is a finite étale `K`-group, and
`P, Q` are tame `F`-torsors over `R`, then `P ∧^F Q` is tame over `R`. Now `T := P ∧^F Q` is a quotient of `P ×_K Q`,
and (if `L, M, N` represent `T, P, Q` as `K`-algebras) `L` is a `K`-subalgebra of `M ⊗_K N`. Both `M` and `N` are tame
by hypothesis; `M ⊗_K N` is tame by XIII.2.0.3 (closure under tensor product); and `L ⊆ M ⊗_K N` is tame by closure
under subalgebra (XIII.2.0.3 again).

Consequence: if `F` is a sheaf of groups on `U` such that there *exists* a tame `F`-torsor `P` on `X` relative to `S`,
then `F` itself is tame. Indeed, the opposite torsor `P°` is tame (it has the same underlying sheaf of sets as `P`), the
inner twist `^P F = Aut(P°)` is tame by the contracted-product computation, and `F ≃ P° ∧^{^P F} P`, so `F` is tame by
another contracted-product application.

### XIII.2.1.5 — Functoriality across maps `(U_2, X_2)/S_2 → (U_1, X_1)/S_1`.

<!-- source: XIII.2.1.5 -->

A commutative diagram

```text
(U_2, X_2)/S_2  →  (U_1, X_1)/S_1
```

(NC divisors `D_i` on `X_i` over `S_i`, opens `U_i = X_i − Y_i`) with horizontal map sending tame data on the left to
tame data on the right (e.g. a smooth base change of `S`) induces a functor `C_t((U_1, X_1)/S_1) → C_t((U_2, X_2)/S_2)`
by pullback, and hence a homomorphism

```text
π_1^tame((U_2, X_2)/S_2)  →  π_1^tame((U_1, X_1)/S_1).
```

### XIII.2.1.6 — Inertia generation.

<!-- source: XIII.2.1.6 -->

For each irreducible component `Y_j` of `Y = Supp D` of relative codimension `1`, there is an *inertia subgroup*
`I_{Y_j} ⊆ π_1^tame((U, X)/S, a)` (well-defined up to conjugacy), cyclic of order prime to the residual characteristic
at the generic point of `Y_j`. The inertia subgroups generate `Ker(π_1^tame(U) → π_1(X))` *topologically* (i.e. as a
closed subgroup) when `X` is connected. (This is the abstract analogue of file 50 X.2.6's surface-with-punctures inertia
generators.)

______________________________________________________________________

## §XIII.2.2–XIII.2.3 — The class `c` of "good" coefficients

<!-- source: XIII.2.2 -->

We isolate the class of coefficients to which XIII.2.4 will apply. The notation `c` is internal to this exposé.

### XIII.2.2 — Definition of `c`.

<!-- source: XIII.2.2 -->

The class `c` of *good coefficients* on `S` consists of:

(c.1) ind-finite constant étale sheaves of sets, groups, or abelian groups on `S`;

(c.2) closed under restriction to constructible étale subsheaves and under finite étale base change of `S`;

(c.3) (when the residual characteristics of `S` matter) ind-finite sheaves of *groups* on `S` whose orders are prime to
the residual characteristics of `S`.

The fibre at a geometric point `s̄` of `S` is an ind-finite group of order prime to `char κ(s̄)` in case (c.3).

### XIII.2.2.1 — Closure of `c` under subobject / quotient / extension.

<!-- source: XIII.2.2.1 -->

The class `c` is closed under taking subobjects, quotients, and short exact sequences.

### XIII.2.2.2 — Closure under twisting.

<!-- source: XIII.2.2.2 -->

If `F ∈ c` and `P` is an `F`-torsor in `c`, the inner twist `^P F` is in `c`.

### XIII.2.3 — Three stability properties used downstream.

<!-- source: XIII.2.3 -->

The class `c` satisfies:

(a) stability under étale base change of `S`;

(b) stability under tensor product `F ⊗ F'` of coefficients of orders prime to the same set of residual characteristics
(case c.3); equivalently, the orders set is closed under multiplication;

(c) stability under filtered direct limits among coefficients in `c`.

These are the operative properties for XIII.2.4 (b) below.

______________________________________________________________________

## §XIII.2.4 — Main theorem: tame `R¹` along an NC divisor commutes with base change

<!-- source: XIII.2.4 -->

We come to the headline statement of Exposé XIII, the only one whose proof requires the full machine of files 61–64 and
SGA 4 / SGA 5.

### XIII.2.4 — Theorem.

<!-- source: XIII.2.4 -->

Let `f : X → S` be a morphism, let `D` be a divisor on `X` with normal crossings relative to `S` (XIII.2.1.0), and put
`Y = Supp D`, `U = X − Y`, `i : U → X` the canonical immersion. Let `F` be a sheaf of sets, respectively of groups, on
`U`, satisfying one of the following:

**(a)** `F` is locally for the étale topology on `X` and on `S` the inverse image of a sheaf of sets, resp. a
constructible sheaf of groups, on `S`.

**(b)** `F` is locally constant constructible on `U` and tamely ramified on `X` relative to `S`.

Then:

(1) `(F, i)` is cohomologically proper relative to `S` in dimension `≤ 0`; respectively, for every `h : S' → S`, if
`i' : U' → X'` is the inverse image of `i` on `S'`, `F' = F|_{U'}`, and `k = h_{(X)}`, the canonical morphism

```text
Ψ : k^* (R¹_tame i_* F)  →  R¹_tame i'_* F'
```

is an isomorphism. *If `F` is moreover a sheaf of groups of order prime to the residual characteristics of `S`*
(XIII.2.3 (b)), tamely ramified on `X` relative to `S`, then `(F, i)` is cohomologically proper relative to `S` in
dimension `≤ 1`.

(2) If `F` is a constructible sheaf of sets, respectively of groups, then `i_* F`, respectively `R¹_tame i_* F`, is
constructible.

*Slogan.* **`(i_* F, R¹_tame i_* F)` for tame `F` along an NC divisor *is* a cohomologically-proper coefficient pair —
even though `i` is not proper. The non-properness of `i` is exactly the failure of properness that XII's NC hypothesis
controls.**

#### Proof skeleton (faithful to SGA 1 XIII §2.4).

For every `S`-scheme `S'`, consider the cartesian-square diagram

```text
U'  →  U
|       |
i'      i
|       |
X'  →  X
|       |
S'  →  S.
```

The question is local on `X` for the étale topology (XIII.1.5 c, file 61), so we may suppose `D` is *strict* NC relative
to `S`. Restricting `X` to a neighbourhood of `Y` if necessary, we may also suppose `X` is smooth over `S` everywhere.

We split the proof into three blocks: §XIII.2.4.1 (sheaf-of-sets case a), §XIII.2.4.2 (sheaf-of-groups case a),
§XIII.2.4.3 (tame case b). Constructibility (2) follows from each case + B.5 + Stein-factorisation arguments.

### XIII.2.4.1 — Sheaf-of-sets case (a) via SGA 4 XVI 3.2.

<!-- source: XIII.2.4.1 -->

*Setting.* `F = g^* G` is pulled back from a sheaf of sets `G` on `S` along `g = f i : U → S`.

*Argument.* It then follows from [`sga-4-xvi-base-change-smooth`](appendix-black-boxes.md#sga-4-xvi-base-change-smooth)
(SGA 4 XVI 3.2) that the canonical morphism `g^* G → i_* i^* g^* G = i_* F` commutes with every base change `S' → S` in
the appropriate adjunction. Specialised to the cartesian-square diagram above, this gives the base-change comparison
`h^* i_* F → i'_* F'` as an isomorphism for every `h : S' → S`. By XIII.1.2, `(F, i)` is cohomologically proper relative
to `S` in dimension `≤ 0`. Constructibility of `i_* F` for constructible `F` is then automatic from the weak criterion
XIII.1.13.

### XIII.2.4.2 — Sheaf-of-groups case (a) via non-abelian `R^1`.

<!-- source: XIII.2.4.2 -->

*Setting.* `F = g^* G` for a constructible sheaf of groups `G` on `S`.

*Argument.* By Giraud non-abelian cohomology
([`giraud-cohomologie-non-abelienne`](appendix-black-boxes.md#giraud-cohomologie-non-abelienne)), the stack
`Tors(F) = g^* Tors(G)` is the pullback of the constructible stack `Tors(G)` from `S`. We may therefore quote SGA 4 XVI
3.2 again, applied to the stack `Tors(G)` rather than the sheaf `G`: every twist and every base change of `Tors(G)`
commutes with `g^*`, so the comparison functor on stacks `h^* i_* (g^* Tors(G)) → i'_* h'^* (g^* Tors(G))` is an
equivalence. Passing to sheaves of maximal subgerbes (XIII.0.3) identifies this with `h^* R^1 i_* F → R^1 i'_* F'`. The
`H^0` case (cohomological properness in dim `≤ 0`) follows from XIII.2.4.1 applied to the underlying sheaf of sets.

For the *tame* `R¹_tame i_* F`: by Giraud + the inertia description XIII.2.0, an `F`-torsor `P` on `U` is tame *iff* the
underlying `Tors(F)`-object lies in the subgerbe of tame torsors. This subgerbe is the inverse image from `S` of the
subgerbe of `Tors(G)` whose torsors have tame inertia along `D`; both gerbes are constructible by hypothesis on `G`.
Apply XIII.2.4.1 to the *tame subgerbe* of `Tors(F)` and pass to sheaves of maximal subgerbes:
`h^* R¹_tame i_* F → R¹_tame i'_* F'` is an iso.

### XIII.2.4.3 — Tame case (b) via the local Kummer model.

<!-- source: XIII.2.4.3 -->

*Setting.* `F` is locally constant constructible on `U` and tame on `X` relative to `S`.

*Reduction.* The question is local on `X` for the étale topology (XIII.1.5 c). By the NC hypothesis (XIII.2.1.0), we may
suppose `X = Spec(A)` is the strict henselisation of a regular local scheme at a point of `Y`, with
`D = ∑_{i ≤ r} div(f_i)` part of a regular system of parameters and `f` smooth at the chosen point. (After étale
localisation, every NC datum is of this form.)

In this strict-local model, *the local Kummer cover*

```text
X' = X[T_1, …, T_r] / (T_1^{n_1} − f_1, …, T_r^{n_r} − f_r)
```

— for any `r`-tuple `(n_i)` of integers prime to the residual characteristic `p` of `X` — is a connected tame étale
cover of `U` and extends to a finite étale cover of `X'` (XIII.5.1 of file 64). Since `F|_U` is locally constant
constructible and tame, the **absolute Abhyankar lemma** (XIII.5.2 of file 64) says: after passing to a suitable Kummer
base change `X' → X` (with `n_i` chosen as a common multiple of the orders `n_j` of the inertia subgroups), the
pulled-back sheaf `F|_{U'}` extends *uniquely* to a locally-constant-constructible sheaf `F̃` on all of `X'`. (This uses
[`sga-2-xiv-1-11`](appendix-black-boxes.md#sga-2-xiv-1-11) to extend across codim `≥ 2` after the codim-1 case.)

The cover `X' → X` is *proper* (a finite morphism of strict-local schemes is proper); by XIII.1.4 the pair
`(F̃, X' → X)` is cohomologically proper in dim `≤ 1`. Descending along the Kummer cover (which is faithfully flat in
the appropriate sense, since the `n_i` are prime to `p`) recovers the desired cohomological properness of
`(F, i : U → X)` in dim `≤ 0` (resp. dim `≤ 1` if `F` is a group of order prime to `p`).

The base-change statement `Ψ : k^* R¹_tame i_* F → R¹_tame i'_* F'` follows by the same Kummer-cover argument applied to
the base change `S' → S`: the local Kummer model is *itself stable* under base change (XIII.5.4 of file 64), and descent
commutes with the base change.

*Slogan for (b).* **Tame étale sheaves along an NC divisor become unramified after a controlled Kummer base change,
where proper-base-change applies; descent gives the desired statement for the original `U → X → S`.**

#### Constructibility (2).

For constructible `F`, the constructibility of `i_* F` (sheaf-of-sets case) and `R¹_tame i_* F` (sheaf-of-groups case)
follows from XIII.1.15 and XIII.1.17, applied to each of (a) and (b). In case (a) the result is immediate from the
pullback hypothesis; in case (b) it follows from the proper-base-change for the Kummer model.

This completes the proof of XIII.2.4.

______________________________________________________________________

## §XIII.2.5–XIII.2.11 — Specialisation corollaries

The next seven numbered statements unpack XIII.2.4 into more readily quotable forms. Their proofs are short applications
of XIII.2.4 plus the standing bridge.

### XIII.2.5 — Stack-level form of XIII.2.4.

<!-- source: XIII.2.5 -->

*This says:* the stack-level versions of `i_*` (without "tame") and `i_*^tame` (with "tame") behave well under base
change. Specifically, with `f, D, Y, U, i` as in XIII.2.1, `Φ` a stack on `U`, and surjective étale morphisms `S_1 → S`,
`X_2 → X ×_S S_1`, a stack `Ψ` on `S_1`, and an isomorphism `Φ|_{U_2} ≃ Ψ|_{U_2}`:

(1) for every `h : S' → S` with `k = h_{(X)}`, the canonical functor `φ : k^* i_* Φ → i'_* Φ'` is fully faithful;

(2) if `Ψ` is constructible, `ψ : k^* i_*^tame Φ → i'_*^tame Φ'` is an equivalence;

(3) if `Ψ` is constructible (resp. 1-constructible and `S` locally noetherian), `i_* Φ` is constructible (resp.
`i_*^tame Φ` is 1-constructible).

*Proof.* For (1): full faithfulness is checked at geometric points of `X'` by XIII.1.5 b. At a geometric point `x̄'`,
the comparison functor becomes `Φ(Ū) → Φ'(Ū')`. For sections `a, b ∈ Φ(Ū)`, the local 0-acyclicity of `Ū → S̄` (XIII.5.7
of file 64) gives `H^0(Ū, SΦ̄) ≃ H^0(S̄, SΨ̄)`, so `a, b` come from `Ψ`; the sheaf `F = SheafHom(a, b)` descends, and by
XIII.2.4.1 `H^0(Ū, F) → H^0(Ū', F')` is an iso. For (2): full faithfulness as in (1) plus essential surjectivity using
XIII.2.4 (1) on `H^0(Ū, SΦ̄)`. For (3): apply XIII.6.3 (a forward-reference to the constructibility-of-stacks calculus,
omitted here).

### XIII.2.6 — Characteristic-zero corollary.

<!-- source: XIII.2.6 -->

Same notation as XIII.2.4. If `S` has characteristic zero at every point `s` with `Y_s ≠ ∅`, then for every
constructible sheaf of groups `𝓕` on `U` (no tameness needed), `i_* 𝓕` is constructible and `(𝓕, i)` is cohomologically
proper in dim `≤ 1`. In particular, `(R^1 i_* 𝓕)_{s̄}` is computed by `H¹(Ū, 𝓕̄)`.

*Proof.* Tameness is automatic in characteristic zero (every étale algebra is tame); XIII.2.4 (b) applies.

### XIII.2.7 — Cohomologically-proper composite `qi`.

<!-- source: XIII.2.7 -->

Same notation as XIII.2.4, with additionally an `S`-scheme `T`, a proper morphism `p : X → T`, both `X` and `T` of
finite presentation over `S`. Put `q = pi`. If `𝓕` is a constructible sheaf on `U` satisfying XIII.2.4 (a) or (b), then
`(𝓕, q)` is cohomologically proper relative to `S` in dim `≤ 0` (resp. dim `≤ 1` for sheaves of groups of order prime to
the residual characteristics); the canonical morphism

```text
Θ : m^* (R¹_tame q_* 𝓕)  →  R¹_tame q'_* 𝓕'
```

is an iso (with `m = h_{(T)}`); and `q_* 𝓕`, `R¹_tame q_* 𝓕` are constructible.

*Proof.* `q = pi` with `p` proper, so use XIII.1.6 (composition) + XIII.2.4 (for `i`) + XIII.1.4 (for `p`). Cf. SGA 4
XIV 1.1.

### XIII.2.8 — Specialisation of `R¹_tame` for a proper-and-`i` composite.

<!-- source: XIII.2.8 -->

Suppose `f : X → S` is *proper of finite presentation*, `D` is NC relative to `S`, `U = X − Y`, `i : U → X`. Let `ℒ` be
a set of primes; suppose `g = fi : U → S` is locally 0-acyclic (resp. locally 1-aspherical for `ℒ`). If `𝓕` is a locally
constant constructible sheaf of sets (resp. of `ℒ`-groups) on `U` that is tame on `X` relative to `S`, then:

- `f_* 𝓕` (resp. `R¹_tame f_* 𝓕`) is locally constant constructible;
- `(𝓕, f)` is cohomologically proper relative to `S` in dim `≤ 0`; respectively, the formation of `R¹_tame f_* 𝓕`
    commutes with every base change `S' → S`;
- in the non-respective case, for every specialisation `s̄_1 → s̄_2` of geometric points of `S`, the specialisation
    morphism `(R¹_tame f_* 𝓕)_{s̄_2} → (R¹_tame f_* 𝓕)_{s̄_1}` is *injective*.

*Proof.* XIII.2.6 + XIII.1.14 (the tame version of which is proved analogously, by passing to maximal subgerbes).

### XIII.2.9 — Characteristic-zero limit specialisation.

<!-- source: XIII.2.9 -->

Same notation, `f` proper of finite presentation. If `𝓕` is a constructible sheaf of groups on `U`, locally constant
constructible, then for every `K → K'` extension of separably-closed field extensions of `κ(s̄)`, the specialisation
morphism

```text
(R¹ f_* 𝓕)_K  →  (R¹ f_* 𝓕)_{K'}
```

is an iso. (Cf. SGA 4 XV 1.5; the upshot is that `R¹ f_* 𝓕` is *constant* on geometric strict henselisations of
characteristic zero.)

### XIII.2.10 — Cohomologically-proper homotopy-exact-sequence input.

<!-- source: XIII.2.10 -->

If `f : X → S` is locally 0-acyclic, 0-acyclic, and proper of finite presentation, with `D` NC relative to `S`, and the
coefficient class `c` of XIII.2.2 is in play, then for every connected étale cover `S' → S` and every Galois cover `E`
of `X' = X ×_S S'` whose group is an `ℒ`-group, `(E, f')` is cohomologically proper relative to `S'` in dim `≤ 0` and
`f'_* E` is constructible. *This is the input quoted by XIII.4.1.*

### XIII.2.11 — Cospecialisation.

<!-- source: XIII.2.11 -->

Same hypotheses as XIII.2.8 (so `f` proper of finite presentation and `g` locally `1`-aspherical for `ℒ`). For every
specialisation `s̄_1 → s̄_2`, the cospecialisation morphism

```text
π_1^tame((U, X)/S, s̄_2)  →  π_1^tame((U, X)/S, s̄_1)
```

is *surjective*; the analogous statement for the pro-`ℒ` quotient is *bijective*. (Translation of XIII.2.8 into
fundamental groups via the equivalence of `H^1`-categories and groupoid arguments; cf. file 33 V.6.9.)

______________________________________________________________________

## §XIII.2.12 — The tame fundamental group of an open curve

<!-- source: XIII.2.12 -->

This is the headline corollary: the tame fundamental group of a punctured proper smooth curve over a separably closed
field is given by an explicit pro-`p'` surface-with-punctures presentation.

### XIII.2.12 — Theorem.

<!-- source: XIII.2.12 -->

Let `X` be a connected proper smooth curve of genus `g` over a separably closed field `k` of characteristic `p ≥ 0`. Let
`U = X − {a_1, …, a_n}` be the complement of `n` distinct closed points. Then:

(i) `π_1^tame(U)` is *generated topologically* by `2g + n` elements `x_i, y_i` (`1 ≤ i ≤ g`), `σ_j` (`1 ≤ j ≤ n`), where
`σ_j` is a generator of an inertia subgroup corresponding to `a_j`, and these elements satisfy the *surface-
with-punctures relation*

```text
(*)   ∏_{1 ≤ i ≤ g} [x_i, y_i]  ·  ∏_{1 ≤ j ≤ n} σ_j  =  1.
```

(ii) *Universality of the relation in the pro-`p'` quotient.* Writing `p' = {primes ℓ ≠ p}`, the pro-`p'` group
`π_1^{p'}(U)` is the pro-`p'` group on the generators `x_i, y_i, σ_j` subject to the single relation `(*)`.
Equivalently: for every finite group `G` of order prime to `p`, generated by elements `x̄_i, ȳ_i, σ̄_j` satisfying
`(*)`, there exists a finite étale Galois cover of `U` of group `G` with monodromy `x_i ↦ x̄_i`, `y_i ↦ ȳ_i`,
`σ_j ↦ σ̄_j`.

*Slogan.* **`π_1^tame(U)` in characteristic `p` is the pro-`p'` completion of the topological surface-with-punctures
group; in particular, the prime-to-`p` part of the tame fundamental group is *independent of `p`*.**

### Proof of XIII.2.12.

<!-- source: XIII.2.12 -->

Three pieces of machinery from Exposé X are about to be invoked together. Briefly:

- *Recall (file 49, X.2.3–X.2.4).* The **specialisation morphism** `sp : π_1(X̄_{y_1}) → π_1(X̄_{y_0})` is the
    homomorphism of geometric-fibre fundamental groups induced by moving the base point along a specialisation in the
    base from a generic `y_1` to a closed `y_0`, defined up to inner automorphism.
- *Recall (file 49, X.2.3).* **Upper-semicontinuity** of fibre `π_1` along a proper separable family: `sp` is
    surjective, so the fundamental group of a closed fibre is a quotient of the fundamental group of a generic fibre —
    fibre `π_1` can only shrink as the base point specialises.
- *Recall (file 50, X.2.6).* The **transcendental method** lifts a positive-characteristic situation to characteristic
    `0` along a Witt-vector deformation of the base (file 22, III.7.4), computes the relevant fundamental group
    analytically there via GAGA + Riemann existence (Exposé XII), and pushes the resulting bound back down by
    upper-semicontinuity.

The proof has two stages: characteristic zero, then characteristic `p`.

#### Stage 1: characteristic zero (`p = 0`).

Reduce `k` to an algebraically closed extension of a `ℚ`-subfield `k'` of finite transcendence degree, with the data
`(X', a'_1, …, a'_n)` defined over `k'`. Embed `k' ↪ ℂ`. Set `Ũ = U' ×_{k'} ℂ`. Choose an algebraically closed `k''`
admitting maps `k → k''` and `ℂ → k''` over `k'`.

For `g' : U' → k'` the structural map and `𝓕'` a finite constant sheaf of groups on `U''`, XIII.2.9 (now applied
characteristic-zero) gives that the specialisation maps `(R¹ g'_* 𝓕')_ℂ → (R¹ g'_* 𝓕')_{k''} ← (R¹ g'_* 𝓕')_k` are isos.
In terms of fundamental groups, this gives an isomorphism (up to inner automorphism) `π_1(U) → π_1(Ũ)` that *transforms
inertia at `a_j` to inertia at `a_j`*.

So we may assume `k = ℂ`. By the Riemann existence theorem (file 60 §XII.5.2), `π_1(U) = π_1^ét(U) ≃ π̂_1^top(U^an)`,
the profinite completion of the topological fundamental group of `U^an`. The topological side
`π_1^top(Σ_g − {a_1, …, a_n})` is the **surface-with-punctures group**: it is freely generated by `2g + n` elements
`x_i, y_i, σ_j` with the single relation `(*)`, where `σ_j` is the homotopy class of a small loop around `a_j`. (This
calculation is the substance of file 50 X.2.6's transcendental method.) Taking the profinite completion concludes Stage
1\.

#### Stage 2: characteristic `p > 0`.

Choose a complete DVR `A` with residue field `k` and field of fractions `K` of characteristic zero, and a connected
proper smooth `S = Spec A`-scheme `X_1` with `X_1 ×_S Spec k ≃ X`
([`ega-iii-7-4-spec`](appendix-black-boxes.md#ega-iii-7-4-spec) and the deformation discussion of file 50). The points
`a_j` lift to disjoint sections `s_j : S → X_1`; let `Y_{1j} = s_j(S)` (reduced closed subscheme), `Y_1 = ⋃_j Y_{1j}`,
`U_1 = X_1 − Y_1`, `g_1 : U_1 → S` the structural morphism. Let `K̄` be an algebraic closure of `K` and
`Ū = U_1 ×_S Spec K̄`.

For a finite constant group `C`, XIII.2.8 applied to the proper `f : X_1 → S` and the inclusion `i : U_1 → X_1` (noting
that `D = ∑ Y_{1j}` is NC over `S` by construction — each `Y_{1j}` is a horizontal section) gives:

- if `|C|` is arbitrary, `(R¹ g_{1*} C_{U_1})_k → (R¹ g_{1*} C_{U_1})_{K̄}` is *injective*;
- if `|C|` is prime to `p`, the same morphism is *bijective*.

In terms of fundamental groups (and inertia generation, XIII.1.10 + XIII.1.11 + XIII.2.1.6):

```text
π_1(Ū)  ↠  π_1^tame(U)        (surjective specialisation)
π_1^{p'}(Ū)  ≃  π_1^{p'}(U).  (bijective on pro-p' quotient)
```

Stage 1 has identified `π_1(Ū)` with the surface-with-punctures pro-finite group. The bijective pro-`p'` specialisation
imports the *pro-`p'` part of `(*)`* into `π_1^{p'}(U)`; the surjective full specialisation imports the generators
`x_i, y_i, σ_j` and the relation `(*)` (as elements satisfied modulo `p`-torsion in the wild quotient that we discard by
passing to the tame `π_1^tame`).

Finally, by XIII.1.11, the image of a generator of `π_1(D_j)` (the local fundamental group of a small disc around the
generic point `b_j = Y_{1j}(K̄)`) is a generator of the inertia subgroup at `a_j`; this matches the inertia
identification in the topological picture of Stage 1.

This completes the proof.

Slogan again: **the surface-with-punctures presentation of `π_1^top(Σ_g − {a_j})` lifts to characteristic `p` *exactly*
in the pro-`p'` tame quotient.**

______________________________________________________________________

## §XIII.2.13 — Remark (Raynaud 2003) on Abhyankar's conjecture

<!-- source: XIII.2.13 -->

Let `k` be an algebraically closed field of characteristic `p > 0`, `X` a connected proper smooth `k`-curve of genus
`g`, `U` an *affine* open of `X` — the complement of `r ≥ 1` rational points. There are three nested fundamental groups:

```text
π_1(U)  ↠  π_1^tame(U)  ↠  π_1^{p'}(U).
```

`π_1(U)` classifies *all* finite étale covers; `π_1^tame(U)` classifies tame covers (XIII.2.1.3); and `π_1^{p'}(U)` is
the prime-to-`p` quotient.

#### Size of `π_1(U)`: Artin–Schreier on the affine line.

Let `U = 𝔸^1_k = Spec(k[T])`. Then `Hom_{cont}(π_1(U), ℤ/pℤ) ≃ k[T] / wp(k[T])` (file 56 §XI.6.9), where
`wp : a ↦ a^p − a` is the Artin–Schreier operator. Let `E ⊆ k[T]` be the subspace of polynomials `∑ a_i T^i` with
`a_i = 0` whenever `p | i`. The composite `E → k[T] → k[T] / wp(k[T])` is *bijective*. So the coefficients `a_i` with
`gcd(i, p) = 1` are "parametrising coordinates" for cyclic-`p` covers of `𝔸^1`.

Consequences:

(i) `π_1(𝔸^1)` is *not* topologically of finite type;

(ii) for `k → k'` an extension of algebraically closed fields, the natural map `π_1(𝔸^1_{k'}) → π_1(𝔸^1_k)` is
*surjective but not bijective* — unlike the proper case (where it is an iso by XIII.4.7.4 of file 63). The same
phenomena hold for `π_1(V)` for every connected affine `k`-scheme `V` of finite type and dimension `≥ 1`.

#### Abhyankar's conjecture.

For a finite group `G`, write `G^{(p')}` for the maximal prime-to-`p` quotient. For `G` to be a topological quotient of
`π_1(U)`, it is *necessary* that `G^{(p')}` be a topological quotient of `π_1^{p'}(U)` (the obstruction known explicitly
by XIII.2.12). Abhyankar ([`abhyankar-1957-coverings`](appendix-black-boxes.md#abhyankar-1957-coverings)) conjectured
this necessary condition is also *sufficient*.

The conjecture was proved by Raynaud for `𝔸^1` and by Harbater in general
([`raynaud-harbater-abhyankar`](appendix-black-boxes.md#raynaud-harbater-abhyankar)). For `𝔸^1` it reads:

> *A finite group `G` is the Galois group of a connected étale cover of `𝔸^1_k` `⟺` `G^{(p')} = 1`* (equivalently: `G`
> is generated by its Sylow `p`-subgroups).

So every finite simple group whose order is a multiple of `p` is a Galois group over `𝔸^1` in characteristic `p`.

Slogan for XIII.2.13: **in characteristic `p`, the wild part of `π_1` is enormous (not finitely generated) and is
constrained by the Abhyankar conjecture, whose statement uses the tame part XIII.2.12 as a precise constraint.**

______________________________________________________________________

## Closing pointer

File 63 (gentle §§XIII.3 + XIII.4) extracts the general mechanism behind XIII.2.4: generic local acyclicity gives
cohomological properness over a non-empty open of an irreducible base (XIII.3.1–XIII.3.5), and this is exactly the input
that produces the *étale homotopy exact sequence* (XIII.4.1) and the *Künneth formula for `π_1^{p'}`* (XIII.4.6). File
64 (gentle §XIII.5) then provides the relative Abhyankar variants that file 62 has used.
