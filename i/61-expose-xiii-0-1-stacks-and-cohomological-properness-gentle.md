# Expose XIII §§0–1 (gentle) — stacks, étale cohomology bridge, cohomological properness

<!-- source: XIII -->

## What this file is about

What happens when a family of geometric objects is allowed to leak out to infinity, or when the data carried over the
family is allowed to vary continuously instead of in a fixed discrete way? Earlier files handled the simpler case: a
compact family with discrete data, where the answer at one slice transported cleanly to nearby slices. With the
restrictions removed, that rigidity breaks. Values at neighbouring slices no longer have to agree, and the comparison
between them becomes the object of study.

The families and data for which the comparison still works are the subject of the next three files. Setting up the
language costs machinery from two later Grothendieck seminars, imported as a controlled list of borrowed facts. After
the borrowing, the vocabulary develops in plain voice and the applications follow.

Files 57–60 closed the gentle pass through Exposé XII with the Riemann existence theorem and the $\pi_{1}$ comparison.
Exposé XIII picks up where the SGA-1-internal story leaves off. It generalises the Stein-factorisation and homotopy-
exact-sequence results of Exposés IX and X to *sheaves of (possibly non-commutative) groups* in the *étale topology* on
schemes. Its main theorems are: cohomological properness of the tame $R^{1}$ along a normal-crossings divisor
(XIII.2.4); the explicit calculation of the tame fundamental group of an open curve (XIII.2.12); the homotopy exact
sequence and a Künneth formula for the prime-to-$p$ fundamental group (XIII.4.1, XIII.4.6); and the relative Abhyankar
lemma (XIII.5.2).

Exposé XIII is the only exposé in SGA 1 that genuinely depends on **SGA 4** (the étale topology, étale cohomology of
sheaves of sets / groups / abelian groups, base-change theorems) and on **SGA 5 II** (cohomologically proper morphisms,
locally aspherical morphisms). The gentle SGA series does not cover SGA 4 or SGA 5. This file therefore opens with a
standing bridge, §XIII.B, that quotes the SGA 4 / SGA 5 results we will need as black boxes — each gets an entry in the
appendix — and then proceeds through the SGA-1-internal mathematics of §XIII.0 (stacks reminder) and §XIII.1
(cohomological-properness language) in the gentle voice.

A reader who already knows the étale topology should still skim §XIII.B for our notation and for the exact statements we
will quote downstream.

______________________________________________________________________

## §XIII.B — A standing bridge to SGA 4 and SGA 5

<!-- source: XIII -->

This bridge collects, in the gentle voice, the facts about the étale topology and étale cohomology that Exposé XIII
needs. Nothing here is proved; everything is quoted from SGA 4 (with one Giraud reference) or SGA 5 II, with appendix
entries. Downstream we will *cite the bridge*, not paraphrase it again.

The étale topology is finer than the Zariski one. Where a Zariski neighbourhood of a point is an open subset containing
it, an étale neighbourhood is any unramified cover — the algebraic analogue of an open piece of a finite Riemann surface
lying above the point. Sheaves on this finer topology, and the cohomology those sheaves carry, are the right setting for
fundamental-group theory and for the comparison results Exposé XIII proves; building the setting properly is the work of
SGA 4. The eight items below extract just the parts of SGA 4 and SGA 5 II that Exposé XIII actually uses: the étale site
and its sheaves (B.1); the pushforward of an étale sheaf along a map of schemes and the higher derived versions that
record cohomology along the fibres (B.2); the comparison map between cohomology and base-changed cohomology, whose
failure or success is the protagonist of cohomological properness (B.3); the proper base-change theorem, which says that
comparison succeeds when the map is proper (B.4); the class of *constructible* sheaves, which stays closed under the
operations we need (B.5); locally acyclic morphisms, which generalise "every fibre is a point" to higher dimensions
(B.6); the radicial-base-change reduction VIII 1.1, the standing reduction trick that lets us pass freely between a
scheme and its reduction (B.7); and strong desingularization, the input that makes our base-change machine apply to
general schemes (B.8). The last subsection (B.9) opens the parallel theory of stacks and gerbes, which the
non-commutative coefficients of XIII.1 require.

#### B.1. The étale site $X_{et}$ and étale sheaves.

For a scheme $X$ the **étale site** $X_{et}$ is the category of étale $X$-schemes, equipped with the étale topology
(coverings are surjective families of étale morphisms). An **étale sheaf** on $X$ is a presheaf of sets on $X_{et}$ that
satisfies the sheaf condition for étale coverings. The same definition produces étale sheaves of groups, of abelian
groups, of rings; sheafification, restriction along an étale morphism, and pullback / pushforward along an arbitrary
morphism of schemes work as in any reasonable topos. Source: [`sga-4-etale-site`](appendix-black-boxes.md).

Notation: we write $X^{\sim}_{et}$ for the topos of étale sheaves on $X$ when we need to refer to the topos itself, and
use $X_{et}$ for the site. A **geometric point** $\bar{s} \to X$ is a morphism from the spectrum of a separably closed
field; the strict henselisation of the local ring at the image is the **strict localisation** $X_{(\bar{s})}$. For an
étale sheaf $F$, the **geometric stalk** $F_{\bar{s}}$ is the value of $F$ on $X_{(\bar{s})}$.

#### B.2. Pushforward and the higher direct images.

For $f : X \to Y$ a morphism of schemes and $F$ an étale sheaf of abelian groups on $X$, the pushforward $f_{*} F$ is
again an étale sheaf on $Y$, and the right-derived functors $R^{q} f_{*} F$ are again étale sheaves. The stalk
$(R^{q} f_{*} F)_{\bar{y}}$ at a geometric point $\bar{y} \to Y$ is $H^{q}(X \times_{Y} Y_{(\bar{y})}, F)$, where the
strict henselisation $Y_{(\bar{y})}$ is the small geometric neighbourhood of `ȳ`. For a sheaf of (possibly
non-commutative) groups $F$ on $X$, $f_{*} F$ and $R^{1} f_{*} F$ make sense (the latter as a *sheaf of pointed sets /
classifying gerbe data*) and have the same stalk description. Sources:
[`sga-4-direct-image-and-rqf`](appendix-black-boxes.md); [`giraud-cohomologie-non-abelienne`](appendix-black-boxes.md)
for the non-abelian $R^{1}$.

#### B.3. The base-change comparison map.

A cartesian square

```text
X'  --h'→  X
|          |
f'         f
|          |
Y'  --h→   Y
```

produces, for every étale sheaf $F$ on $X$ and every $q \geq 0$, a canonical natural transformation

```text
Φ^q : h^* R^q f_* F  →  R^q f'_* (h'^* F).
```

This is the **base-change comparison map**. It is built from the unit and counit of the adjunctions $(h^{*}, h_{*})$ and
$(f^{*}, f_{*})$. Source: [`sga-4-direct-image-and-rqf`](appendix-black-boxes.md).

We will write $F' = h'^{*} F$ once the cartesian square is fixed, so
$\Phi^{q} : h^{*} R^{q} f_{*} F \to R^{q} f'_{*} F'$.

#### B.4. Proper base change.

If $f$ is **proper** and $F$ is torsion, then $\Phi^{q}$ is an isomorphism for every $q \geq 0$ and every cartesian
square as in B.3. The finite-coefficients case (the only one we need below) follows the same pattern: for a
constructible étale sheaf $F$ of torsion abelian groups, or of finite groups, on $X$, with $f$ proper, $\Phi^{q}$ is an
iso. Source: [`sga-4-proper-base-change`](appendix-black-boxes.md).

We use the proper-base-change theorem mainly in the form: a proper morphism is cohomologically proper in every dimension
for torsion / ind-finite coefficients (XIII.1.4 below).

#### B.5. Constructible sheaves.

An étale sheaf $F$ of sets / groups on $X$ is **constructible** if there exists a finite stratification of $X$ by
locally closed constructible subsets such that the restriction of $F$ to each stratum is locally constant with finite
fibres. The class of constructible sheaves is closed under $f_{*}$ and $R^{1} f_{*}$ in the regimes we use. Source:
[`sga-4-constructible-sheaves`](appendix-black-boxes.md).

#### B.6. Locally $n$-acyclic and $n$-acyclic morphisms.

A morphism $f : X \to S$ is **locally 0-acyclic** if, for every strict geometric localisation $S_{(\bar{s})}$ of $S$ and
every torsion abelian sheaf $F$ on $X$, the canonical map $F \to R f_{*} f^{*} F$ is an iso in degree 0 over
$S_{(\bar{s})}$. It is **locally $n$-acyclic** if the analogous statement holds up to degree $n$. The morphism is
**0-acyclic** (resp. $n$-acyclic) if the same is true after replacing $S_{(\bar{s})}$ by $S$ itself.

For coherent $f$, 0-acyclic ⇔ geometrically connected fibres. A smooth morphism is locally $n$-acyclic for every
$n < (relative dimension)$. Sources: [`sga-4-xv-loc-acyclic`](appendix-black-boxes.md);
[`sga-4-xvi-base-change-smooth`](appendix-black-boxes.md).

We use locally `0`-acyclic and locally `1`-aspherical *for a set of primes $\mathcal{L}$* throughout XIII.4: the
qualifier "for $\mathcal{L}$" means "with finite constant coefficients whose order is in $\mathcal{L}$."

#### B.7. Strongly desingularizable schemes.

A scheme $X$ of finite type over a field $k$ is **strongly desingularizable in dimension ≤ $d$** if every reduced closed
subscheme of $X$ of dimension $\leq d$ admits a strong resolution of singularities, in the sense of SGA 5 I 3.1.5.
Hironaka resolution gives this in characteristic zero for every $d$; in characteristic $p > 0$ it is an open hypothesis.
Source: [`sga-5-i-strongly-desingularizable`](appendix-black-boxes.md).

This is the operative hypothesis for XIII.3.3, XIII.3.4, and XIII.4.6.

#### B.8. Cohomologically proper morphisms.

The phrase **$(F, f)$ is cohomologically proper relative to $S$ in dimension $\leq n$** is defined in §XIII.1 below. We
flag here that the general framework is SGA 5 II: it gives the sorites we will gentle-walk through in §XIII.1.5–
XIII.1.17. Source: [`sga-5-ii-cohomologically-proper`](appendix-black-boxes.md).

Slogan for the bridge: **everything in Exposé XIII downstream of B.1–B.8 is proved gently from material in earlier
gentle files plus a fixed quote from SGA 4 / SGA 5 II.**

______________________________________________________________________

## §XIII.0 — Reminders on the theory of stacks

<!-- source: XIII.0 -->

The "stack" framework is what Exposé XIII uses to package the non-abelian $R^{1} f_{*}$ cleanly. We need only the étale-
site case, and we will not develop the framework from scratch. This section states the operating definitions and the two
structural results (the sheaf of maximal subgerbes, the constructible / ind-$\mathcal{L}$-finite refinements) that
XIII.1 and XIII.2 quote.

*This section says:* a stack $F$ on $X_{et}$ is a fibred category over $X_{et}$ that satisfies effective descent for the
étale topology; a **gerbe** is a stack whose fibre categories are non-empty connected groupoids; the basic example is
the stack of torsors under a sheaf of groups; the sheaf of maximal subgerbes of a stack $F$ is a sheafification of the
presheaf "isomorphism classes of objects of $F_{X}'$."

#### XIII.0.1. — Stacks on $X_{et}$.

<!-- source: XIII.0 -->

A **stack** on $X$ is a fibred category $F \to X_{et}$ such that:

(i) for every étale $X' \to X$ and every pair `x, y` of objects of the fibre $F_{X'}$, the presheaf
$SheafHom_{X'}(x, y)$ on $X'_{et}$ is a sheaf; and

(ii) for every surjective étale morphism $X'' \to X'$, every object $x'' \in F_{X''}$ equipped with a descent datum
relative to $X'' \to X'$ is the inverse image of an object of $F_{X'}$.

The category of **cartesian sections** of $F$ over $X'$ is denoted $F(X')$. The framework extends from $X_{et}$ to
$Sch_{X}$ with the étale topology by formal sheafification; we keep the notation $F(X')$ for the resulting cartesian
sections on the larger site.

#### XIII.0.2. — Gerbes.

<!-- source: XIII.0 -->

A **gerbe** is a stack $F$ on $X_{et}$ such that:

(a) for every étale $X' \to X$ and every pair $x, y \in F_{X'}$, every morphism $x \to y$ is an isomorphism (the fibres
are groupoids);

(b) for every $X' \to X$ étale, any two objects $x, y \in F_{X'}$ are locally isomorphic on $X'_{et}$ (the fibres are
locally connected);

(c) the étale sites $X' \to X$ for which $F_{X'}$ is non-empty form a covering refinement of $X_{et}$ (the fibres are
locally non-empty).

*Example.* For a sheaf of groups $G$ on $X_{et}$, the stack $Tors(G)$ of $G$-torsors on $X_{et}$ is a gerbe; it has a
cartesian section, namely the trivial torsor.

*Converse.* A gerbe $F$ with a cartesian section $x \in F_{X}$ is canonically equivalent to
$Tors(\operatorname{Aut}(x))$, where $\operatorname{Aut}(x) = SheafAut_{X}(x)$ is the sheaf of automorphisms of $x$.

#### XIII.0.3. — The sheaf of maximal subgerbes.

<!-- source: XIII.0 -->

Let $F$ be a stack on $X_{et}$. There is an evident notion of subgerbe of $F$ (a substack that is a gerbe). For each
cartesian section $x$ of $F$ over $X'$ there exists a unique **maximal subgerbe** $G_{x} \subseteq F|_{X'}$ such that
$x$ factors through $G_{x}$; this $G_{x}$ is itself a trivial gerbe (it has the section $x$). One calls $G_{x}$ the
**subgerbe generated by $x$**.

Let `SF` be the presheaf on $X_{et}$ defined by

```text
SF(X') = { maximal subgerbes of F|_{X'} }.
```

It is a sheaf, the **sheaf of maximal subgerbes** of $F$. The presheaf $O$ defined by

```text
O(X') = { iso. classes of objects of F_{X'} }
```

maps to `SF` by $x \mapsto G_{x}$. *This says:* `SF` is the sheafification of $O$. (SGA 5 III 2.1.4 in the conventions
of the source.)

*Why we care.* When $F = Tors(G)$ is the stack of $G$-torsors for a sheaf of groups $G$ on $X$, the sheaf of maximal
subgerbes of $f_{*} F$ is canonically $R^{1} f_{*} G$. So `SF` is the abstract counterpart of the non-abelian first
derived image; it is what makes $R^{1} f_{*}$ make sense for sheaves of (non-commutative) groups.

#### XIII.0.4. — Constructible, ind-$\mathcal{L}$-finite, 1-constructible.

<!-- source: XIII.0 -->

Let $\mathcal{L}$ be a set of prime numbers. A stack $F$ on $X_{et}$ is:

- **constructible** if, for every étale $X' \to X$ and every $x \in F_{X'}$, the sheaf of automorphisms
  $SheafAut_{X'}(x)$ is constructible (SGA 5 VII 2.2.1);
- **ind-$\mathcal{L}$-finite** if each $SheafAut_{X'}(x)$ is ind-$\mathcal{L}$-finite (an inductive limit of finite
  constant sheaves of $\mathcal{L}$-groups);
- **1-constructible** if $F$ is constructible and its sheaf of maximal subgerbes `SF` is constructible.

These are the regularity hypotheses on coefficient stacks that XIII.1 sorites use.

Slogan for §XIII.0: **a stack is the étale-site analogue of a fibre system of categories, a gerbe is the analogue of a
fibre system of pointed connected groupoids, and the sheaf of maximal subgerbes is the abstract $R^{1} f_{*}$ for
non-commutative coefficients.**

______________________________________________________________________

## §XIII.1 — Cohomological properness

<!-- source: XIII.1 -->

*This section says:* a coefficient $(F, f)$ is **cohomologically proper relative to $S$ in dimension $\leq n$** if the
base-change comparison map $\Phi^{q}$ (B.3) is an iso for $q \leq n$ and for every base change $S' \to S$. Proper
morphisms are the "free" examples. The class of cohomologically proper coefficients is stable under composition, étale
base change, and other moves: the sorites of XIII.1.5–XIII.1.7. The geometric-fibre criterion XIII.1.5 b reduces
cohomological properness to a check on strict henselisations. Specialisation morphisms (XIII.1.8–XIII.1.14) make sense
because $R^{q} f_{*}$ is constant in a small étale neighbourhood; the input XIII.1.14 is what produces the homotopy
exact sequence in §XIII.3 + §XIII.4.

The numbering in this section follows SGA 1 XIII §1 exactly: XIII.1.0 fixes the cartesian-square diagram, XIII.1.1 is
the definition for a stack $F$, XIII.1.2 specialises to sheaves of sets, XIII.1.3 to sheaves of groups, XIII.1.3.1 gives
the equivalent torsor-level conditions, XIII.1.4 records the proper-morphism example, XIII.1.5–XIII.1.7 collect the
sorites, XIII.1.8–XIII.1.11 introduce specialisation, XIII.1.12 is passage to the limit, XIII.1.13–XIII.1.14 are the
cohomologically-proper specialisation statements used in XIII.3, and XIII.1.15–XIII.1.17 are the constructibility
results for non-abelian $R^{1}$ used in XIII.2.

### XIII.1.0 — The standing cartesian-square diagram.

<!-- source: XIII.1.0 -->

Let $S$ be a scheme and $f : X \to Y$ a morphism of $S$-schemes. For every $S$-scheme $S'$ we consider the diagram of
cartesian squares

```text
X'  -h-→  X
|          |
f'         f
|          |
Y'  -g-→  Y
|          |
S'  -→    S.
```

(SGA 1 XIII §1.0.1.) If $Y_{1} \to Y$ is étale we put $X_{1} = X \times_{Y} Y_{1}$, $Y_{1}' = Y' \times_{Y} Y_{1}$, and
use the analogous cartesian square (XIII.1.0.2). The maps `h, g` are pullbacks of the base change $S' \to S$. Throughout
§XIII.1 we keep this notation.

### XIII.1.1 — Definition (stack version).

<!-- source: XIII.1.1 -->

Let $F$ be a stack on $X$. One says that **$(F, f)$ is cohomologically proper relative to $S$ in dimension $\leq n$** —
written $n \in {-1, 0, 1}$ — if for every $S$-scheme $S'$ the canonical functor

```text
g^* f_* F  →  f'_* (h^* F)
```

is:

- **faithful** when $n = -1$,
- **fully faithful** when $n = 0$,
- **an equivalence of categories** when $n = 1$.

(The map is built by the universal property of inverse image of stacks.) When $S = Y$ we drop "relative to $S$" and say
simply "cohomologically proper."

*Why three numbers.* The dimensions $-1, 0, 1$ correspond, after specialising to a sheaf of sets / sheaf of groups, to
the base-change comparison map $\Phi^{q}$ for $q = -1, 0, 1$ — i.e. to injectivity of $f_{*} F$, bijectivity of
$f_{*} F$, and bijectivity of both $f_{*} F$ and $R^{1} f_{*} F$ (XIII.1.2, XIII.1.3, XIII.1.3.1 below). We use only
$n = 0$ and $n = 1$ in applications.

### XIII.1.2 — Specialisation to sheaves of sets.

<!-- source: XIII.1.2 -->

Let $F$ be a sheaf of sets on $X$. The **stack in discrete categories** associated with $F$ is the stack $\Phi$ whose
fibre at every étale $X_{1} \to X$ is the discrete category with object set $F(X_{1})$. One says that **$(F, f)$ is
cohomologically proper relative to $S$ in dimension $\leq -1$** (resp. $\leq 0$) if $(\Phi, f)$ is cohomologically
proper relative to $S$ in dimension $\leq 0$ (resp. $\leq 1$).

After passage to associated discrete-category stacks, the comparison map of XIII.1.1 becomes the canonical morphism

```text
g^* f_* F  →  f'_* h^* F
```

of sheaves of sets on $Y'$. Faithfulness for discrete-category stacks is injectivity; full faithfulness is bijectivity.
So:

*$(F, f)$ cohomologically proper in dim $\leq -1$ iff* $g^{*} f_{*} F \to f'_{*} h^{*} F$ is *injective* for every base
change; *$(F, f)$ cohomologically proper in dim $\leq 0$ iff it is bijective.*

### XIII.1.3 — Specialisation to sheaves of groups.

<!-- source: XIII.1.3 -->

Let $F$ be a sheaf of groups on $X$. Let $\Phi = Tors(F)$ be the stack of $F$-torsors on $X$ (XIII.0.2 example). One
says that $(F, f)$ is **cohomologically proper relative to $S$ in dimension $\leq n$** if $(\Phi, f)$ is so. The next
subproposition unpacks this into testable conditions on torsors.

### XIII.1.3.1 — Testable form for sheaves of groups.

<!-- source: XIII.1.3.1 -->

Use the notation of XIII.1.0.1 and XIII.1.0.2. Let $F$ be a sheaf of groups on $X$, and let $F', F_{1}, F_{1}'$, etc.,
be the inverse images. The following are equivalent:

(i) $(F, f)$ is cohomologically proper relative to $S$ in dim $\leq n$ for $n \in {-1, 0, 1}$.

(ii) For every $S' \to S$, every étale $Y_{1} \to Y$, and every `F_1`-torsor $P$ on `X_1`, let ${}^{P} F_{1}$ denote the
inner twist of `F_1` by $P$. Then:

- $n = -1$: the canonical morphism

    ```text
    a_0 : g_1^* (f_{1*} (^P F_1)) → f_{1*}' (^{P'} F_1')
    ```

    is *injective*;

- $n = 0$: $a_{0}$ is *bijective*; and the canonical morphism

    ```text
    a_1 : g^* (R^1 f_* F) → R^1 f'_* F'
    ```

    is *injective*;

- $n = 1$: both $a_{0}$ and $a_{1}$ are *bijective*.

(ii bis) The analogous condition with arbitrary torsors $R$ under ${}^{P} F_{1}$ in place of ${}^{P} F_{1}$ itself.

*This says:* cohomological properness in dim $\leq 0$ is "every twist ${}^{P} F_{1}$ survives base change at the
$H^{0}$-level" (plus the iff with $a_{1}$ injective); cohomological properness in dim $\leq 1$ is "every twist survives
at the $H^{0}$-level *and* the non-abelian $H^{1}$ survives." The condition on ${}^{P} F_{1}$ rather than `F_1` alone is
essential: without inner twisting, the abelian case is recovered, but the non-abelian story collapses.

*Proof sketch (faithful to the source).* The torsor stack $Tors(F)$ has, for two objects `x, y` of class `P, Q`, the
internal hom $SheafHom_{F}(P, Q) \simeq Q \wedge^{F} P^{\circ}$, where $P^{\circ}$ is the opposite torsor (SGA 5 II
4.1.2.3). So the sheaf of maps $x \to y$ is computed by the inner twist $Q \wedge^{F} P^{\circ}$. The comparison functor
$g^{*} f_{*} Tors(F) \to f'_{*} Tors(F')$:

- is *faithful* iff for every `P, Q`, the map on sheaves of homs
  $H^{0}(Y_{1}', g^{*}_{1} f_{1*}(Q \wedge^{F_{1}} P^{\circ})) \to H^{0}(Y_{1}', f_{1*}' (Q' \wedge^{F_{1}'} P'^{\circ}))$
  is injective; this is the $a_{0}$ statement for the twisted group ${}^{P} F_{1}$;

- is *fully faithful* iff that map is bijective for every `P, Q`; and, by the maximal-subgerbe argument (XIII.0.3), iff
  in addition the map $a_{1}$ (which is the corresponding map on sheaves of maximal subgerbes) is *injective*;

- is *an equivalence* iff $a_{0}$ and $a_{1}$ are bijective for every $P$ (taking $Q = P$ recovers the iso classes;
  varying $Q$ over a covering recovers descent on the torsor side).

The descent step uses that $Tors(F)$ is a stack and the fully-faithful base case has already been established. This is
the proof in SGA 1 XIII §1.3.1 reproduced cleanly.

Slogan for XIII.1.3.1: **$(F, f)$ cohomologically proper in dim $\leq 1$ means: every twist of $F$ survives base change
at $H^{0}$, and the non-abelian $H^{1}(X, F)$ survives base change.**

### XIII.1.4 — Proper morphisms are cohomologically proper.

<!-- source: XIII.1.4 -->

Let $f : X \to Y$ be a proper morphism. Then for every ind-finite stack $F$ on $X$ (XIII.0.4), the pair $(F, f)$ is
cohomologically proper relative to $Y$ in dimension $\leq 1$.

In particular: for every sheaf of sets, resp. sheaf of groups, resp. sheaf of ind-finite groups, $F$ on $X$, the pair
$(F, f)$ is cohomologically proper in dim $\leq 0$, resp. $\leq 0$, resp. $\leq 1$.

*Proof.* This is proper base change (B.4), quoted from [`sga-4-proper-base-change`](appendix-black-boxes.md) and SGA 5
VII 2.2.2: for a proper $f$ and ind-finite torsion coefficient stack $F$, the comparison functor
$g^{*} f_{*} F \to f'_{*} h^{*} F$ is an equivalence under every base change. The three specialisations follow by
XIII.1.2, XIII.1.3, XIII.0.4.

Slogan: **the "free" cohomologically proper morphisms are the proper ones, in every dimension $\leq 1$; the work in
XIII.2 is to find *non-proper* $f$ for which the same is true for *good* coefficient classes (tame torsors along an NC
divisor).**

### XIII.1.5 — Sorites: a vs ab; coherent geometric-fibre criterion; étale-local; non-stability under base change.

<!-- source: XIII.1.5 -->

(a) Let $F$ be a sheaf of groups on $X$ with $(F, f)$ cohomologically proper relative to $S$ in dim $\leq n$. The
*forgetful-to-sheaf-of-sets* version is also cohomologically proper relative to $S$ in the same dimension. **The
converse is false in general**: a counterexample lives over a strictly local DVR, where the closed fibre is empty and
the non-abelian twist ${}^{P} F$ has trivial $H^{0}(X_{s}, {}^{P} F|_{X_{s}})$ while $H^{0}(X, F)$ is non-trivial.

(b) **Geometric-fibre criterion.** Suppose $f$ is coherent (quasi-compact and quasi-separated). Let $F$ be a stack on
$X$. For every geometric point `ȳ` of $Y'$, write `Ȳ`, `Ȳ'` for the strict localisations of $Y$, $Y'$ at `ȳ`, and put
$\bar{X} = X \times_{Y} \bar{Y}$, $\bar{X}' = X' \times_{Y'} \bar{Y}'$. Then $(F, f)$ is cohomologically proper relative
to $S$ in dim $\leq n$ *iff* for every $S' \to S$ and every geometric point `ȳ` of $Y'$, the canonical functor

$$
\bar{F}(\bar{X})  \to  \bar{F}'(\bar{X}')
$$

is faithful (resp. fully faithful, resp. an equivalence). *This is the operative working form of XIII.1.1.* It reduces
cohomological properness to a strict-henselisation check.

The proof is the fibre-by-fibre criterion for inverse image of stacks (SGA 5 III 2.1.5.9) combined with the calculation
of geometric fibres of $f_{*} F$ for coherent $f$ (SGA 5 VII 2.1.5).

(c) Cohomological properness in any of the three dimensions is **local on $Y$ for the étale topology**: if
$Y = \bigcup Y_{\alpha}$ is an étale cover and $(F|_{X \times_{Y} Y_{\alpha}}, f|_{X \times_{Y} Y_{\alpha}})$ is
cohomologically proper for every $\alpha$, then $(F, f)$ is. This is immediate from XIII.1.0.2.

(d) **Base change of $(F, f)$.** If $(F, f)$ is cohomologically proper relative to $S$ in dim $\leq 1$, the same is true
of the base change `(F', f')` along any $S' \to S$. **But** in dim $\leq -1$ or $\leq 0$, cohomological properness need
not be preserved under base change. An explicit counterexample (SGA 1 XIII §1.5 c): take $S' = \operatorname{Spec}(R)$ a
strictly local DVR, $f' : E_{S'} \to S'$ an affine space over $S'$, and a sheaf $F'$ on $E_{S'}$ that is constant
outside a closed point above the generic point and has fibre of cardinality 2 at that point. After pulling back to a
larger base $S = S'[Z]$, extend to a sheaf supported on $Z \neq 0$; the base change at $Z = 0$ loses cohomological
properness. The point is that cohomological properness in low dimensions is a *fibrewise* condition and is sensitive to
whether the support of $F$ meets the closed fibre.

(e) **Pointwise fibre form.** Let $F$ be a stack on $X$ with $(F, f)$ cohomologically proper relative to $Y$ in dim
$\leq n$. Then for every geometric point `ȳ` of $Y$, the canonical functor

$$
(f_{*} F)_{\bar{y}}  \to  F(X_{\bar{y}})
$$

is faithful (resp. fully faithful, resp. an equivalence). This is the $S = Y$ case of (b), spelled out at a single
geometric point.

Slogan for XIII.1.5: **cohomological properness in dim $\leq 1$ is a stable property; in dim $\leq 0$ it is fibrewise
and fragile.**

### XIII.1.6 — Composition (and reverse composition).

<!-- source: XIII.1.6 -->

Let $f : X \to Y$ and $g : Y \to Z$ be $S$-morphisms, and let $\Phi$ be a stack on $X$.

(1) If $(\Phi, f)$ and $(f_{*} \Phi, g)$ are both cohomologically proper relative to $S$ in dim $\leq n$, then so is
$(\Phi, gf)$.

(2) Conversely: assume $(\Phi, gf)$ is cohomologically proper relative to $S$ in dim $\leq n'$ and $(\Phi, f)$ is
cohomologically proper relative to $S$ in dim $\leq n'-1$. Then $(f_{*} \Phi, g)$ is cohomologically proper relative to
$S$ in dim $\leq n'$. (Read $n' \in {-1, 0, 1}$; the "in dim $\leq -1$" hypothesis on $(\Phi, f)$ is empty when
$n' = -1$.)

*Proof.* Standard "two-out-of-three" for the comparison of associated stack-pushforwards. Spell out the cartesian
diagram (SGA 1 XIII §1.6.1) and observe that the comparison map for the composite `gf` is the composite
$m^{*}(g_{*} f_{*} \Phi) \to g'_{*}(k^{*} f_{*} \Phi) \to g'_{*} f'_{*} (h^{*} \Phi)$; (1) says both factors are
faithful / fully faithful / equivalence, hence so is the composite; (2) reverses one factor. The fully-faithful and
equivalence parts of (2) use that fully-faithfulness of a composite plus faithfulness of the right factor implies
fully-faithfulness of the left factor, etc.

### XIII.1.7 — Behaviour under étale base change of $S$.

<!-- source: XIII.1.7 -->

Cohomological properness in dimension $\leq n$ for the pair $(F, f : X \to Y)$ relative to $S$ is preserved under étale
base change of $S$. (Special case of XIII.1.5 c.)

The next four numbers XIII.1.8–XIII.1.11 set up the specialisation map.

### XIII.1.8 — Specialisation: cospecialisation morphism.

<!-- source: XIII.1.8 -->

Let $\bar{s}_{1} \to \bar{s}_{2}$ be a specialisation of geometric points of $S$ (i.e. a morphism between strict
localisations, $S_{(\bar{s}_{1})} \to S_{(\bar{s}_{2})}$). For every stack $F$ on $X$ we obtain a **cospecialisation
morphism**

```text
(f_* F)_{s̄_2}  →  (f_* F)_{s̄_1}
```

by applying the geometric-fibre description (B.2 + XIII.1.5 e) to the pair $\bar{s}_{1} \to \bar{s}_{2}$. This is
functorial in the specialisation and in the stack $F$.

### XIII.1.9 — Specialisation of $R^{q}$: sheafification statement.

<!-- source: XIII.1.9 -->

For $F$ an étale sheaf and $q \geq 0$, the cospecialisation map
$(R^{q} f_{*} F)_{\bar{s}_{2}} \to (R^{q} f_{*} F)_{\bar{s}_{1}}$ is the specialisation of the sheaf $R^{q} f_{*} F$ at
the morphism $\bar{s}_{1} \to \bar{s}_{2}$. By B.2, the stalk is $H^{q}$ over the strict localisation; cospecialisation
is the restriction map $H^{q}(X_{(\bar{s}_{2})}, F) \to H^{q}(X_{(\bar{s}_{1})}, F)$ along the inclusion
$X_{(\bar{s}_{1})} \subset X_{(\bar{s}_{2})}$.

### XIII.1.10 — Specialisation at a closed point.

<!-- source: XIII.1.10 -->

For $S = \operatorname{Spec}(A)$ a strictly local henselian ring with closed geometric point $\bar{s}$ and generic point
$\bar{\eta}$, the cospecialisation morphism

```text
(f_* F)_{s̄}  →  (f_* F)_{η̄}
```

is in particular an instance of the canonical morphism

$$
\pi : \pi_{1}(X_{\bar{\eta}}) \to \pi^{tame}_{1}(X_{s})
$$

(in terms of fundamental groups, when $F = \pi$-equivariant data and $X$ is a curve; this is the form we will use in
XIII.2.12). For arbitrary $F$, the cospecialisation is computed by the étale stalk map.

### XIII.1.11 — Generic-to-closed inertia.

<!-- source: XIII.1.11 -->

In the specialisation morphism $\pi$ of XIII.1.10 for a relative curve $X_{1} \to S$ with a horizontal section $Y_{1j}$,
the image of a generator of the local fundamental group $\pi_{1}(D_{j})$ at a small disc around the generic point of
$Y_{1j}$ is a generator of an inertia group of $X_{s} - {a_{j}}$ at the closed point $a_{j}$. (We will quote this fact
in XIII.2.12.)

### XIII.1.12 — Passage to the limit.

<!-- source: XIII.1.12 -->

Cohomological properness in any of the three dimensions commutes with filtered direct limits in $Y$ when $f$ is
coherent. (SGA 4 IX 2.7.4 + XIII.1.5 b; see [`sga-4-constructible-sheaves`](appendix-black-boxes.md).) The same applies
to the sheaf-of-groups case via XIII.1.3.1.

### XIII.1.13 — Weak cohomological properness criterion.

<!-- source: XIII.1.13 -->

Let $f : X \to S$ be coherent and let $F$ be a sheaf of sets on $X$. Suppose that:

(i) for every strict localisation $S_{(\bar{s})}$ of $S$, $F$ restricted to $X \times_{S} S_{(\bar{s})}$ is locally
constant constructible; and

(ii) the formation of $f_{*} F$ commutes with passage to a strict localisation: for every $\bar{s}$, the canonical map
$(f_{*} F)_{\bar{s}} \to H^{0}(X \times_{S} S_{(\bar{s})}, F)$ is bijective.

Then $(F, f)$ is cohomologically proper relative to $S$ in dim $\leq 0$.

This is the "weak" criterion: when $F$ is constructible on the strict localisations and $f_{*}$ is the
strict-localisation $H^{0}$, base change is automatic. It is the form used in XIII.2.4.1.

### XIII.1.14 — Cohomologically proper ⇒ constructible specialisation.

<!-- source: XIII.1.14 -->

Let $(F, f)$ be cohomologically proper relative to $S$ in dim $\leq 1$, with $F$ a sheaf of constructible groups and $f$
coherent. Then for every specialisation $\bar{s}_{1} \to \bar{s}_{2}$ of geometric points of $S$, the cospecialisation
morphism

```text
(R^1 f_* F)_{s̄_2}  →  (R^1 f_* F)_{s̄_1}
```

is *bijective*.

*Proof.* By XIII.1.5 b applied at the strict localisation $S_{(\bar{s}_{2})} \to S_{(\bar{s}_{1})}$, the comparison
functor $f_{*} Tors(F)|_{S_{(\bar{s}_{2})}} \to f_{*}' Tors(F)|_{S_{(\bar{s}_{1})}}$ is an equivalence. Passing to
sheaves of maximal subgerbes (XIII.0.3) identifies this with
$(R^{1} f_{*} F)_{\bar{s}_{2}} \to (R^{1} f_{*} F)_{\bar{s}_{1}}$.

This is the input to XIII.3.5 — the cospecialisation of $\pi^{\mathcal{L}}_{1}(X_{\bar{s}})$ along specialisations of
geometric points in $S$ is bijective whenever $(F, f)$ is cohomologically proper in dim $\leq 1$ for all finite
$\mathcal{L}$-group coefficients.

### XIII.1.15 — Cohomologically proper ⇒ constructible $f_{*}$.

<!-- source: XIII.1.15 -->

Under the hypotheses of XIII.1.13 (or XIII.1.4 for proper $f$), $f_{*} F$ is itself constructible. The argument is the
fibre-by-fibre criterion + B.5.

### XIII.1.16 — Local constance of $f_{*} F$ on cohomologically-proper components.

<!-- source: XIII.1.16 -->

If `(E, f')` is cohomologically proper relative to $S'$ in dim $\leq 0$ and $f'_{*} E$ is constructible, then after
étale base change $S' \to S$ we may assume $f'_{*} E$ is *constant* on the relevant cohomologically-proper component.
(This is the input we will quote in XIII.4.1 for the surjectivity of the homotopy-exact-sequence map $u$.)

### XIII.1.17 — Maximal-subgerbe constructibility.

<!-- source: XIII.1.17 -->

If $(F, f)$ is cohomologically proper in dim $\leq 1$ and $F$ is a 1-constructible stack (XIII.0.4), then
$R^{1} f_{*} F$ is a constructible sheaf of sets. This is the non-abelian analogue of "constructible coefficients have
constructible $R^{1} f_{*}$" and is the input to XIII.2.4 part 2.

Slogan for §XIII.1: **cohomological properness is the language; the sorites pin its scope; the specialisation /
constructibility statements XIII.1.13–XIII.1.17 are the inputs to the geometric applications of §XIII.2 and §XIII.4.**

______________________________________________________________________

## Closing pointer

File 62 (gentle §XIII.2) applies the language built here to the geometric setting that motivates the whole exposé: an
open $U = X - Y$ of a proper smooth $S$-scheme $X$ with $Y = Supp D$ a normal-crossings divisor relative to $S$. The
*main theorem* XIII.2.4 says that for a sheaf $F$ on $U$ that is *tamely ramified* along $D$, both $i_{*} F$ and the
*tame* $R^{1}_{tame} i_{*} F$ commute with base change in $S$. The headline corollary XIII.2.12 — the tame fundamental
group of a punctured proper smooth curve over a separably closed field — uses XIII.1.14 + the file-60 Riemann existence
theorem + a Witt-vector lifting (file 50) to identify $\pi^{tame}_{1}(U)$ with the pro-$p'$ surface-with-punctures
group.
