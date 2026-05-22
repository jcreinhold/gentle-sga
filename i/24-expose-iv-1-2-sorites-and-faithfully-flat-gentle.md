# Exposé IV, sections 1–2: sorites on flat modules, faithfully flat modules (gentle)

## What this file is about

Imagine an algebraic family of shapes parametrised by a base. As the parameter moves, the shape over each value changes.
The cleanest families are the ones with no surprises: nothing jumps up in dimension at a special value, nothing
collapses, nothing disappears. The technical word for this kind of well-behaved variation, used as a black box in almost
every file so far, is flatness.

This file opens the box. The first section collects the closure properties: flatness is preserved under composition,
under base change, and under combinations of these. The second section sharpens flatness into a stronger condition
called faithful flatness, which corresponds to the geometric notion of a covering map that reaches every point of the
base. This is the algebraic backbone of descent, treated much later in the seminar.

Files 04, 05, 11, 12, and 14–22 have used flatness as a black box. Whenever the étale or smooth theory needed "flat is
preserved under base change," "the flat locus is open," or "flat plus finite over a local ring is free," we cited the
appendix rows `flatness-sorites`, `local-flatness-criterion`, `completion-flat`, or `completion-test-for-flatness` and
moved on. This is the file that opens those boxes.

The view from inside is plain. **Flatness is exactness of the functor $M \otimes_{A} -$.** Everything else in this
exposé follows from that one definition by careful bookkeeping with `Tor` (file 23). The sorites of §IV.1 — composition,
base change, transitive combination, behavior under localization — are the closure properties one would guess from the
definition, and they are proven by chasing the relevant Tor terms through long exact sequences. The single non-routine
fact in §IV.1 is **IV.1.1**, the "as good as split" lemma: a short exact sequence with a flat quotient stays exact under
any tensor product, and $M$ and $M'$ are flat together.

Section §IV.2 introduces the strengthening of flatness most relevant to descent: **faithful flatness**. A faithfully
flat $A$-module $M$ is one for which $M \otimes_{A} -$ _reflects_ exactness, not just preserves it — the tensor product
detects whether a sequence of $A$-modules was already exact. Geometrically: if $M = B$ is a faithfully flat $A$-algebra,
then $\operatorname{Spec} B \to \operatorname{Spec} A$ is **surjective** (IV.2.3), and conversely flatness plus
surjectivity implies faithful flatness (IV.2.6). The right mnemonic: faithful flatness is the algebraic content of
"covering map" in the geometric sense that every prime of the base is hit.

The slogan that runs through:

> **Flat = $M \otimes_{A} -$ is exact. Faithfully flat = $M \otimes_{A} -$ is exact and reflects exactness, equivalently
> $M \otimes N = 0 \Longrightarrow N = 0$, equivalently $\operatorname{Spec}(B) \to \operatorname{Spec}(A)$ is
> surjective in the algebra case.** Flatness underwrites the closure properties used everywhere in EGA; faithful
> flatness is the descent hypothesis Grothendieck's school built around.

Throughout this file we write $Tor^{A}_{i}(M, N)$ for the left-derived functor of $M \otimes_{A} -$. The reader should
consult [file 23](23-tor-composite-functor-spectral-sequence-noether-normalization-gentle.md) for the definition, the
long exact sequence, the symmetry, and the vanishing characterization of flatness.

A long-form sequel to this exposé exists in EGA IV §§11–12, where the systematic study of fiber dimension, cohomological
dimension, and depth for $X \to Y$ of finite type with coherent $F$ flat over $Y$ is carried out. We do not reproduce
it; the appendix row `ega-fibers-systematic` records the pointer. The Bourbaki _Algèbre Commutative_ I (Modules plats)
presentation of these sorites covers the case of a non-commutative base ring; we work in the commutative setting
throughout, and refer to the appendix row `bourbaki-flat-modules` for the alternative.

## IV.1 Sorites on flat modules

<!-- source: IV.1 -->

### Setup: the definition

An $A$-module $M$ is **flat**, or $A$-flat, if the functor

```text
T_M : N ↦ M ⊗_A N
```

— which is in any case right exact — is **exact**, i.e. carries monomorphisms to monomorphisms. Equivalently (file 23):

> $M$ is flat ⟺ $Tor^{A}_{1}(M, N) = 0$ for every $A$-module $N$ ⟺ $Tor^{A}_{i}(M, N) = 0$ for every $N$ and every
> $i \geq 1$.

Two reductions are useful and we will use them often.

- Since `Tor` commutes with directed colimits, it is enough to verify these vanishings for $N$ of finite type.
- A finitely generated $N$ admits a composition series whose successive quotients are monogenic, i.e. of the form $A/I$
  for an ideal $I$. So it is enough to verify $Tor^{A}_{1}(M, A/I) = 0$ for ideals $I$ of finite type.

For $N = A/I$, the long exact sequence applied to $0 \to I \to A \to A/I \to 0$ reads

```text
0 = Tor^A₁(M, A) → Tor^A₁(M, A/I) → I ⊗_A M → A ⊗_A M → A/I ⊗ M → 0,
```

so $Tor^{A}_{1}(M, A/I) = 0$ if and only if the natural map

```text
I ⊗_A M → IM
```

is **injective**. Combined with the always-surjective map of the same shape, this says

> $M$ is flat ⟺ $I \otimes_{A} M \to IM$ is an isomorphism for every ideal $I$ (and it suffices to consider $I$ of
> finite type).

This is a working criterion in concrete situations: to verify flatness, check that tensoring with $M$ does not introduce
relations among elements of an ideal that were independent in $A$.

### Closure properties

The closure properties below all follow from the exactness characterization. We list them and indicate the proof.

- **Direct sums and direct factors.** If $(M_{\alpha})$ is a family of flat $A$-modules, then $\oplus M_{\alpha}$ is
  flat (tensor product commutes with direct sums; direct sums of exact functors are exact). A direct factor of a flat
  module is flat (a retract of an exact functor is exact).
- **Free, projective ⟹ flat.** $A$ is $A$-flat (the identity functor is exact). So a free $A$-module is flat. A
  projective $A$-module is a direct factor of a free one, hence flat.
- **Tensor product.** If $M_{1}, M_{2}$ are $A$-flat, then $M_{1} \otimes_{A} M_{2}$ is $A$-flat: tensoring with
  $M_{1} \otimes_{A} M_{2}$ is the composition of tensoring with $M_{2}$ and then with $M_{1}$, both exact.
- **Base change.** If $M$ is $A$-flat and $A \to B$ is any ring map, then $M \otimes_{A} B$ is $B$-flat: for any
  $B$-module $N$, $(M \otimes_{A} B) \otimes_{B} N = M \otimes_{A} N$ (associativity), and the right side is exact in
  $N$ because $M \otimes_{A} -$ is exact and the underlying $A$-module functor is exact.
- **Transitive composition.** If $M$ is $B$-flat and $B$ is $A$-flat, then $M$ is $A$-flat: tensoring with $M$ over $A$
  is the composition of tensoring with $B$ over $A$ (exact) and then with $M$ over $B$ (exact).
- **Localization is flat.** For $S \subset A$ a multiplicative set, $S^{-1}A$ is $A$-flat because
  $S^{-1}A \otimes_{A} N = S^{-1}N$ is an exact functor in $N$ (the universal property of localization preserves
  exactness). Consequently, if $M$ is $A$-flat then $S^{-1}M = S^{-1}A \otimes_{A} M$ is $S^{-1}A$-flat by base change,
  and (more strongly) is $A$-flat by transitive composition.

The reader who wants the subobject-bookkeeping consequences — that for an exact functor $T$ and submodules
$N', N'' \subset N$, $T(N' \cap N'') = T(N') \cap T(N'')$ and $T(N' + N'') = T(N') + T(N'')$ — can extract them from the
same exactness of $M \otimes_{A} -$. We will not need them in displayed form.

### Proposition: short exact sequence with flat quotient

<!-- source: IV.1.1 -->

_This proposition says: in a short exact sequence whose right-hand term is flat, the sequence behaves under tensor
product as if it were split — it remains exact after tensoring with anything, and the middle term is flat exactly when
the left term is._

**Proposition IV.1.1.** _Let_

$$
0 \to M' \to M \to M'' \to 0
$$

_be an exact sequence of $A$-modules with `M''` flat. Then:_

1. _The sequence remains exact after tensoring with any $A$-module $N$._
1. _$M$ is flat if and only if $M'$ is flat._

**Proof.** (1) Apply $- \otimes_{A} N$ to the short exact sequence. The long exact sequence in `Tor` reads

```text
… → Tor^A₁(M'', N) → M' ⊗_A N → M ⊗_A N → M'' ⊗_A N → 0.
```

Since `M''` is flat, $Tor^{A}_{1}(M'', N) = 0$ (file 23, vanishing characterization), so the displayed three-term
sequence on the right is exact and the connecting map vanishes. So
$0 \to M' \otimes N \to M \otimes N \to M'' \otimes N \to 0$ is exact.

(2) Apply $- \otimes_{A} N$ to the same sequence and look further left in the long exact sequence:

```text
Tor^A₂(M'', N) → Tor^A₁(M', N) → Tor^A₁(M, N) → Tor^A₁(M'', N).
```

By flatness of `M''`, the outer two terms vanish. So $Tor^{A}_{1}(M', N) \cong Tor^{A}_{1}(M, N)$ for every $N$. The
vanishing characterization gives $M'$ flat ⟺ $M$ flat. ∎

The slogan in the source is:

> "From the point of view of behavior under tensor products, flat modules are 'as good' as free or projective modules;
> the exact sequence of IV.1.1 is 'as good' as if it split."

### Proposition: flatness is local on the second ring

<!-- source: IV.1.2 -->

_This proposition says: when an $A$-module structure is built on top of a $B$-module by way of a ring map $A \to B$, the
flatness question is local on $B$ — it can be checked at the maximal ideals of $B$. The first half of the proposition
records the trivial direction (localization is flat), and the second half is the substantive local-to-global._

**Proposition IV.1.2.** _Let $A \to B$ be a ring homomorphism, let $M$ be a $B$-module, and let $T$ be a multiplicative
set in $B$._

1. _If $M$ is $A$-flat, then $T^{-1}M$ is $A$-flat (and hence $S^{-1}A$-flat for every multiplicative set $S$ of $A$
   mapping into $T$)._
1. *Conversely, if $M*\mathfrak{n}$is flat over$A*\mathfrak{n}$for every maximal ideal$\mathfrak{n}$of$B$(equivalently
   over$A*\mathfrak{m}$where$\mathfrak{m}$is the inverse image of$\mathfrak{n}$in$A$), then $M$is$A$-flat.*

**Proof.** Both halves use the functorial isomorphism

```text
T⁻¹M ⊗_A N = T⁻¹(M ⊗_A N),
```

natural in the $A$-module $N$. (Both sides identify with $T^{-1}B \otimes_{B} M \otimes_{B} N_{(B)}$ where
$N_{(B)} = N \otimes_{A} B$, by associativity of tensor product and the universal property of localization.)

(1) If $M \otimes_{A} N$ is exact in $N$, then composing with the exact functor $T^{-1}(-)$ gives that
$T^{-1}M \otimes_{A} N$ is exact in $N$.

(2) An equality of $B$-modules (or of $A$-modules underlying $B$-modules) holds iff it holds after localizing at every
maximal ideal of $B$. So a sequence $0 \to P' \to P \to P'' \to 0$ of $A$-modules tensored with $M$ is exact iff the
localizations at every maximal $\mathfrak{n}$ are exact, iff (by the displayed isomorphism)
$(P' \otimes_{A} M)_{\mathfrak{n}} \to (P \otimes_{A} M)_{\mathfrak{n}} \to (P'' \otimes_{A} M)_{\mathfrak{n}}$ is
exact, iff (by part (1) applied to $M_{\mathfrak{n}}$ over $A$, equivalently over $A_{\mathfrak{m}}$) the original
sequence tensored with $M_{\mathfrak{n}}$ over $A_{\mathfrak{m}}$ is exact — which holds by hypothesis. So
$M \otimes_{A} -$ is exact, i.e. $M$ is $A$-flat. ∎

This is the practical local criterion for flatness. To check flatness of a $B$-module over $A$, it suffices to check
flatness of each $B_{\mathfrak{n}}$-module $M_{\mathfrak{n}}$ over the corresponding local ring $A_{\mathfrak{m}}$.
Combined with [file 23](23-tor-composite-functor-spectral-sequence-noether-normalization-gentle.md)'s Tor
characterization, this reduces flatness of $M / A$ to a local Tor computation.

### Proposition: flat over integral, flat over Dedekind

<!-- source: IV.1.3 -->

_This proposition says: over an integral ring, flat modules are torsion-free, and over a principal ideal domain (e.g. a
Dedekind ring like $\mathbb{Z}$ or the integers of a number field), torsion-free is the whole story._

**Proposition IV.1.3.** _Let $A$ be a ring._

1. _Let $M$ be a flat $A$-module. If $x \in A$ is not a zero- divisor in $A$, then $x$ is not a zero-divisor in $M$. In
   particular, if $A$ is integral, $M$ is torsion-free._
1. *Suppose $A$ is integral and $A*\mathfrak{m}$is a principal ideal domain for every maximal
   ideal$\mathfrak{m}$(e.g.$A$Dedekind, or$A$itself a PID). Then an$A$-module $M$ is flat if and only if it is
   torsion-free.*

**Proof.** (1) Multiplication by $x$ on $A$ is injective by hypothesis. Tensoring this injection with $M$ gives an
injection $x \cdot : A \otimes_{A} M = M \to A \otimes_{A} M = M$, which is multiplication by $x$ on $M$. Tensoring
preserves injections because $M$ is flat.

(2) By IV.1.2 (ii), flatness over $A$ may be checked at each maximal ideal of $A$, so we may assume $A$ is a principal
ideal domain. We need to show that for every ideal $I$, the inclusion $I \to A$ tensored with $M$ is injective. Since
$A$ is a PID, $I = (x)$ for some non-zero-divisor $x \in A$. The inclusion $I \to A$ becomes "multiplication by $x$ from
$A$ to $A$," and tensoring gives "multiplication by $x$ from $M$ to $M$," which is injective by torsion-freeness of $M$.
∎

The geometric reading: over $\operatorname{Spec} \mathbb{Z}$, a flat $\mathbb{Z}$-module is the algebraic content of "no
fiber suddenly drops rank as you move to a different prime $p$." Torsion-free $\mathbb{Z}$-modules are exactly those for
which no prime annihilates a non-zero element; over a PID, this single condition certifies flatness.

The arithmetic running examples will use this constantly. For $\mathbb{Z}[t]$ viewed as a $\mathbb{Z}$-module, the
underlying additive group is free (as $\mathbb{Z}$-module): a basis is ${t^{n} : n \geq 0}$. Free implies flat. So
$\operatorname{Spec} \mathbb{Z}[t] \to \operatorname{Spec} \mathbb{Z}$ is flat; the flat-ness of this map is the
substance of "the polynomial scheme over $\mathbb{Z}$ has no arithmetic jumps."

For $\mathbb{Z}[t]/(pt) \to \mathbb{Z}$ with $p \in \mathbb{Z}$ prime, the module $\mathbb{Z}[t]/(pt)$ viewed over
$\mathbb{Z}$ is **not** torsion-free: the element $t$ is annihilated by $p$. So $\mathbb{Z}[t]/(pt)$ is not
$\mathbb{Z}$-flat, by IV.1.3 (i). Geometrically, the fiber of
$\operatorname{Spec} \mathbb{Z}[t]/(pt) \to \operatorname{Spec} \mathbb{Z}$ over `(p)` has an embedded component along
$t = 0$ that is not present at the generic point — the family jumps algebraically.

## IV.2 Faithfully flat modules

<!-- source: IV.2 -->

### Setup: faithful, faithful exact

A functor $F : \mathcal{C} \to \mathcal{D}$ is **faithful** if for every pair of objects $X, Y \in \mathcal{C}$, the
induced map

```text
Hom_𝓒(X, Y) → Hom_𝓓(F(X), F(Y))
```

is **injective**. For an additive functor between additive categories, faithfulness is equivalent to "$F(u) = 0$ implies
$u = 0$," which in particular implies "$F(X) = 0$ implies $X = 0$" (apply to $u = id_{X}$).

A functor $F$ between abelian categories is **faithful and exact** iff for every sequence $M' \to M \to M''$ of
morphisms in $\mathcal{C}$, the transformed sequence $F(M') \to F(M) \to F(M'')$ is exact **if and only if** the
original is exact. Equivalently, $F$ is exact and $F(X) = 0 \Longrightarrow X = 0$.

A useful reformulation. Suppose $(M_{i})$ is a family of non-zero objects of $\mathcal{C}$ such that every non-zero
object of $\mathcal{C}$ has a subobject admitting a quotient isomorphic to some $M_{i}$. Then a functor $F$ is faithful
and exact iff $F$ is exact and $F(M_{i}) \neq 0$ for every $i$. For $\mathcal{C} = A$-Mod, one may take the family
$(A/\mathfrak{m})$ indexed by the maximal ideals $\mathfrak{m}$ of $A$: every non-zero $A$-module admits a non-zero
monogenic submodule isomorphic to $A/I$ for some proper ideal $I$, and Krull's theorem gives a maximal ideal
$\mathfrak{m} \supset I$, hence a quotient $A/\mathfrak{m}$.

### Proposition: equivalent conditions for faithful flatness

<!-- source: IV.2.1 -->

_This proposition says: faithful flatness — flatness plus the property that the tensor functor reflects, not just
preserves, exactness — is equivalent to flatness plus any of three "detection" conditions. The condition most useful in
practice is "tensoring with $M$ does not annihilate any non-zero module," or equivalently
"$M \otimes A/\mathfrak{m} \neq 0$ for every maximal ideal $\mathfrak{m}$."_

**Proposition IV.2.1.** _Let $M$ be an $A$-module. The following are equivalent:_

1. _The functor $M \otimes_{A} -$ is faithful and exact._
1. _$M$ is flat, and $M \otimes_{A} N = 0$ implies $N = 0$._
1. _$M$ is flat, and $M \otimes_{A} A/\mathfrak{m} \neq 0$ for every maximal ideal $\mathfrak{m}$ of $A$._
1. _For every sequence of homomorphisms $N' \to N \to N''$, the sequence tensored with $M$ is exact if and only if the
   original is exact._

**Proof.** The pattern is the same in each direction. (i) ⟺ (ii) by definition of "faithful" + "exact" applied to
$M \otimes_{A} -$ (a functor between $A$-Mod and itself is faithful iff $F(N) = 0 \Longrightarrow N = 0$, given
exactness).

(ii) ⟹ (iii). The $A$-module $A/\mathfrak{m}$ is non-zero, so $M \otimes A/\mathfrak{m} \neq 0$ is the (ii)-condition
applied with $N = A/\mathfrak{m}$.

(iii) ⟹ (ii). Suppose $M \otimes_{A} N = 0$ for some $N \neq 0$. Then $N$ admits a non-zero monogenic submodule, hence a
quotient $A/\mathfrak{m}$ for some maximal $\mathfrak{m}$. Tensoring the surjection $N \to A/\mathfrak{m} \to 0$ with
$M$ ($M$-flat, so right-exact suffices), get $M \otimes N \to M \otimes A/\mathfrak{m} \to 0$. The left side is zero, so
$M \otimes A/\mathfrak{m} = 0$, contradicting (iii).

(i) ⟺ (iv). This is just the categorical equivalent formulation of "$F$ is faithful and exact" in an abelian category,
applied to $F = M \otimes_{A} -$. ∎

The conditions (ii), (iii) of IV.2.1 are usually called **conditions (i bis), (i ter)** in the SGA-IV-EGA tradition,
following Grothendieck's labeling. We use the modernized roman numerals.

We say $M$ is a **faithfully flat** $A$-module when these conditions hold. The familiar consequence: tensoring with $M$
not only preserves but **reflects** monomorphisms, epimorphisms, and isomorphisms.

The same closure properties as in §IV.1 propagate: tensor product of faithfully flat modules is faithfully flat (use
(iii) and tensor of "non-zero on $A/\mathfrak{m}$"); base change $M \otimes_{A} B$ is faithfully flat over $B$ if $M$ is
faithfully flat over $A$; transitive composition along $A \to B \to C$ lifts faithful flatness along the way.

### Corollary: local-to-local case

<!-- source: IV.2.2 -->

_This corollary says: in the most arithmetically common setting — a local map of local rings, with a finite-type module
— the distinction between flat and faithfully flat collapses, and is detected by whether the module is non-zero._

**Corollary IV.2.2.** _Let $A \to B$ be a local homomorphism of local rings, and let $M$ be a finite-type $B$-module.
Then $M$ is faithfully flat over $A$ if and only if $M$ is flat over $A$ and $M \neq 0$._

In particular, when $M = B$ itself is a finite-type $B$-module of the trivial sort: **$B$ is $A$-flat iff $B$ is
$A$-faithfully flat**.

**Proof.** "Only if" is trivial: $M \otimes_{A} A/\mathfrak{m} \neq 0$ (with $\mathfrak{m}$ the maximal ideal of $A$)
certainly forces $M \neq 0$.

"If" uses condition (iii) of IV.2.1. We need $M \otimes_{A} A/\mathfrak{m} \neq 0$. By Nakayama (appendix row
`nakayama`) applied to the finite-type $B$-module $M$ and to the maximal ideal $\mathfrak{n}$ of $B$: since $M \neq 0$,
$M / \mathfrak{n} M \neq 0$. Now $M \otimes_{A} A/\mathfrak{m} = M / \mathfrak{m} M \supset M / \mathfrak{n} M$ (as
quotients of $M$, using that $\mathfrak{m} B \subset \mathfrak{n}$ because $A \to B$ is local). The quotient
$M / \mathfrak{n} M \neq 0$, so $M / \mathfrak{m} M \neq 0$, so $M \otimes_{A} A/\mathfrak{m} \neq 0$. ∎

### Proposition: surjectivity on Spec

<!-- source: IV.2.3 -->

_This proposition says: faithful flatness of $B$ over $A$ implies that the map of spectra
$\operatorname{Spec} B \to \operatorname{Spec} A$ is surjective. Geometrically, faithful flatness is the algebraic
content of "surjective covering"._

**Proposition IV.2.3.** _Let $A \to B$ be a ring homomorphism, and let $M$ be a $B$-module faithfully flat over $A$. For
every prime ideal $\mathfrak{p}$ of $A$, there exists a prime ideal $\mathfrak{q}$ of $B$ inducing it (i.e.,
$\mathfrak{q} \cap A = \mathfrak{p}$)._

**Proof.** Fix $\mathfrak{p}$. Reduce modulo $\mathfrak{p}$: replace $(A, B, M)$ by
$(A/\mathfrak{p}, B/\mathfrak{p}B, M/\mathfrak{p}M)$. Now $A$ is integral, and we want a prime of $B$ inducing the zero
prime of $A$.

Localize at the zero prime `(0)` of $A$ (i.e., invert all non-zero elements): replace $(A, B, M)$ by
$(K, B \otimes_{A} K, M \otimes_{A} K)$ where $K = Frac(A)$. Now $A = K$ is a field. The faithful flatness of $M$ over
$A$ survives base change. By the characterization (iii) of IV.2.1:
$M \otimes_{A} A/\mathfrak{m} = M \otimes_{K} K/(0) = M \neq 0$ (faithful flatness, with $K$ the only field-on-itself
field having maximal ideal `(0)`). So $M \neq 0$, hence $B \neq 0$ (otherwise $M = M \otimes_{B} B = 0$), so $B$ has a
prime ideal $\mathfrak{q}$, which is forced by $A = K$ to induce `(0)`. ∎

In algebra terms: $\operatorname{Spec}(B) \to \operatorname{Spec}(A)$ is **surjective**.

### Corollary: minimal primes lift

<!-- source: IV.2.4 -->

_This corollary says: under flatness plus a support hypothesis, not just any prime of the base lifts — the minimal
primes of the fiber over $\mathfrak{p}$ induce precisely $\mathfrak{p}$._

**Corollary IV.2.4.** *Suppose $M$ is $A$-flat, finite-type over $B$, and $Supp M = \operatorname{Spec}(B)$ (i.e.,
$M*\mathfrak{q} \neq 0$for every prime$\mathfrak{q} \in \operatorname{Spec} B$). Then for every prime
$\mathfrak{p}$of$A$, the prime ideals $\mathfrak{q}$of$B$containing$\mathfrak{p}B$and minimal among such ideals
induce$\mathfrak{p}$.*

**Proof.** Reduce to the case $\mathfrak{p} = 0$, which preserves all hypotheses. Then $A$ is integral. The reduction is
to the following corollary, which we state and prove independently.

### Corollary: minimal primes induce minimal primes

<!-- source: IV.2.5 -->

_This corollary says: when $M$ is flat, finite-type, with full support, every minimal prime of $B$ lies over a minimal
prime of $A$. Geometrically: every irreducible component of $\operatorname{Spec}(B)$ dominates an irreducible component
of $\operatorname{Spec}(A)$._

**Corollary IV.2.5.** _With $M$ as in IV.2.4, every minimal prime $\mathfrak{q}$ of $B$ induces a prime
$\mathfrak{p} = \mathfrak{q} \cap A$ of $A$ that is minimal._

**Proof.** Localize at $\mathfrak{q}$ and $\mathfrak{p}$. The hypotheses are preserved: $A \to B$ becomes a local map of
local rings, $M = M_{\mathfrak{q}}$ is non-zero (full-support hypothesis) and flat over $A_{\mathfrak{p}}$, and
$B = B_{\mathfrak{q}}$ has dimension zero (since $\mathfrak{q}$ was minimal). We must show $A$ has dimension zero, i.e.
that $\mathfrak{p}$ was minimal.

By IV.2.2, $M_{\mathfrak{q}}$ is faithfully flat over $A_{\mathfrak{p}}$. By IV.2.3, every prime of $A_{\mathfrak{p}}$
is induced by a prime of $B_{\mathfrak{q}}$. The only primes of $B_{\mathfrak{q}}$ are subsets of the maximal ideal
(because $\dim B_{\mathfrak{q}} = 0$ means there is just one prime — the maximal one); so the only prime of
$A_{\mathfrak{p}}$ induced from $B_{\mathfrak{q}}$ is the maximal ideal of $A_{\mathfrak{p}}$. So every prime of
$A_{\mathfrak{p}}$ equals its maximal ideal, i.e. $\dim A_{\mathfrak{p}} = 0$. So $\mathfrak{p}$ was minimal. ∎

Geometrically: every irreducible component of $X = \operatorname{Spec} B$ dominates some irreducible component of
$Y = \operatorname{Spec} A$, provided there exists a quasi-coherent sheaf of finite type on $X$, with support all of
$X$, and flat over $Y$.

The remark at the end of the source: in IV.2.4, we did not need $M$ faithfully flat over $A$. But without that
hypothesis, nothing guarantees a prime of $B$ containing $\mathfrak{p} B$ exists. Faithful flatness gives existence
(IV.2.3); IV.2.4 then gives the more refined conclusion that **minimal** primes containing $\mathfrak{p}B$ actually
induce $\mathfrak{p}$.

### Proposition: six equivalent conditions for $B$ faithfully flat over $A$

<!-- source: IV.2.6 -->

_This proposition says: when $M = B$ is a ring map (not just an abstract module), faithful flatness has six equivalent
forms. The most useful for descent are (ii) "flat plus surjective on Spec" and (iv) "injective with flat cokernel"; the
most useful for ideal-theoretic verification is (vi) "tensor product gives isomorphism $I \otimes_{A} B \to IB$ and the
inverse image of `IB` is $I$"._

**Proposition IV.2.6.** _Let $i : A \to B$ be a ring homomorphism. The following are equivalent:_

1. _$B$ is a faithfully flat $A$-module._
1. _$B$ is $A$-flat and $\operatorname{Spec}(B) \to \operatorname{Spec}(A)$ is surjective._
1. _$B$ is $A$-flat and every maximal ideal of $A$ is induced by an ideal of $B$._
1. _$i$ is injective and `Coker i` is a flat $A$-module._
1. _The functor $M \mapsto M_{(B)} = M \otimes*A B$on$A$-modules is exact, and the canonical map $M \to M_{(B)}$is
   injective for every$M$._
1. _For every ideal $I$ of $A$, the canonical map $I \otimes_{A} B \to IB$ is an isomorphism, and the inverse image of
   `IB` in $A$ equals $I$._

**Proof.** (i) ⟹ (ii) is IV.2.3. (ii) ⟹ (iii) is trivial: maximal ideals are special cases of primes.

(iii) ⟹ (i). By the criterion (iii) of IV.2.1, we need $B \otimes_{A} A/\mathfrak{m} \neq 0$ for every maximal
$\mathfrak{m}$ of $A$. By hypothesis there is an ideal $J$ of $B$ with $J \cap A = \mathfrak{m}$. Pick a maximal ideal
$\mathfrak{n} \supset J$; then $\mathfrak{n} \cap A \supset \mathfrak{m}$ is a proper ideal of $A$, so
$\mathfrak{n} \cap A = \mathfrak{m}$. So $\mathfrak{m} B \subset \mathfrak{n}$, hence $B / \mathfrak{m} B \neq 0$ (it
surjects onto $B/\mathfrak{n} \neq 0$). So $B \otimes_{A} A/\mathfrak{m} = B/\mathfrak{m}B \neq 0$.

(iii) ⟹ (iv). Apply IV.1.1 (the "as good as split" lemma) to

```text
0 → A → B → Coker i → 0
```

(once we know $i$ is injective). Injectivity of $i$: suppose $a \in A$ with $i(a) = 0$. Tensor $0 \to (a) \to A$ with
$B$: the left becomes $(a) \otimes_{A} B$, the right becomes $B$, and the map sends $a \otimes 1$ to $i(a) = 0$. By
IV.2.1 (i) (which is "(i) ⟺ (ii)" plus exactness of $B \otimes_{A} -$, which holds by $B$ flat), the map
$(a) \otimes_{A} B \to B$ is injective; so $a \otimes 1 = 0$ in $(a) \otimes_{A} B$. Since $(a) \cong A / Ann(a)$ is a
quotient of $A$, the tensor $(a) \otimes_{A} B = B / Ann(a) B$. Vanishing of $a \otimes 1$ means $1 \in Ann(a) B$,
equivalently $Ann(a) B = B$, so $Ann(a) \supset A$ (no proper ideal of $A$ extends to $B$ in this case by (iii)), so
$a \cdot 1 = 0$, so $a = 0$. Now $i$ is injective, and IV.1.1 (ii) applied to the sequence with flat quotient $B$: $A$
is flat (always); so `Coker i` flat ⟺ $B$ flat. By hypothesis $B$ is flat, so `Coker i` is flat.

(iv) ⟹ (v). Take the second part of (v): for any $M$, apply $- \otimes_{A} M$ to $0 \to A \to B \to Coker i \to 0$. By
IV.1.1 (i) (Coker i flat): the sequence stays exact, so $0 \to M \to M \otimes_{A} B \to M \otimes_{A} (Coker i) \to 0$
is exact. So $M \to M \otimes_{A} B$ is injective. For the first part: $B$ is flat (it embeds in a flat extension with
flat cokernel; equivalently, IV.1.1 (ii) on the same sequence with $M' = A$ flat).

(v) ⟹ (i). Exactness of $M \otimes_{A} B$ says $B$ is flat. The injectivity of $M \to M \otimes_{A} B$ for every $M$:
suppose $B \otimes_{A} N = 0$ for some $N \neq 0$. Then in particular the map $N \to N \otimes_{A} B = 0$ is the zero
map; injectivity forces $N = 0$, contradiction. So $B \otimes_{A} N = 0 \Longrightarrow N = 0$, the condition (ii) of
IV.2.1.

(iv) ⟹ (vi). For any ideal $I$ of $A$, apply $- \otimes_{A} B$ to $0 \to I \to A \to A/I \to 0$: by `Coker i` flat plus
$B$ flat (equivalent in this setting), $0 \to I \otimes_{A} B \to A \otimes_{A} B \to (A/I) \otimes_{A} B \to 0$ is
exact, and the arrows identify with $I \otimes_{A} B \to B \to B/IB \to 0$. So $I \otimes_{A} B \to IB$ is an
isomorphism. For the second part of (vi): take $M = A/I$ in (v). The injection $A/I \to A/I \otimes_{A} B = B/IB$ forces
$i^{-1}(IB) = I$.

(vi) ⟹ (i). The first part of (vi) is the flatness criterion "$I \otimes_{A} B \to IB$ iso for all $I$" we developed at
the start of §IV.1. The second part $i^{-1}(IB) = I$ for every ideal $I$ implies in particular
$i^{-1}(\mathfrak{m} B) = \mathfrak{m}$ for every maximal ideal $\mathfrak{m}$, which contains $\mathfrak{m} B \neq B$,
so $B / \mathfrak{m} B \neq 0$, which is (iii) of IV.2.1.

The cycle is complete. ∎

The pieces of IV.2.6 are individually used everywhere in descent theory.

> **Concrete special case.** For $A \to B = \hat{A}$ the $\mathfrak{m}$-adic completion of a noetherian local ring (file
> 25, IV.3.2): the map is faithfully flat. By IV.2.6 (iv): the natural map $A \to \hat{A}$ is injective and
> $\hat{A} / A$ is $A$-flat. By IV.2.6 (vi): $I \hat{A} \cap A = I$ for every ideal $I$ of $A$ — the **Krull
> intersection** style fact that completion preserves ideal structure. These two facts together are why the gentle SGA
> has been treating `completion-flat` as a universally available black box since file 04.

### Closing remark

The five-page workout above is the substance of "flat = exactness of $M \otimes_{A} -$ and faithfully flat = exactness
plus reflection of exactness." Everything else in Exposé IV is downstream:

- **§3** (file 25) applies IV.2 to completion: `Â` is flat over $A$ (IV.3.1), and faithfully flat exactly when $I$ is in
  the radical (IV.3.2). The proof is one line each, using IV.2.1.
- **§4** (file 25) uses IV.1.1 to lift bases through `gr` and Nakayama (IV.4.1), giving the "free iff $Tor_{1} = 0$"
  criterion.
- **§5** (file 26) uses IV.5.2 (Serre's lemma, via the spectral sequence of file 23) to globalize the Tor criterion
  across a base change $A \to B$, culminating in the local flatness criterion IV.5.6.
- **§6** (file 27) uses IV.2.2 + IV.2.3 in the proof of IV.6.6 (open-image theorem for flat morphisms), and uses Noether
  normalization (file 23) in the proof of IV.6.7 (generic freeness).

Read on into [file 25](25-expose-iv-3-4-completion-and-free-modules-gentle.md) for the completion and free-module
corollaries; into [file 26](26-expose-iv-5-local-flatness-criterion-gentle.md) for the local flatness criterion; and
into [file 27](27-expose-iv-6-constructibility-openness-and-generic-flatness-gentle.md) for the geometric payoff and the
closing of the project.
