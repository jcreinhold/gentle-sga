# Cohomology in low degrees, torsors, and the tangent sheaf (gentle prep for Exposé III)

## What this file is about

A familiar question in geometry asks how much local information determines a global object. Pick a covering of a space
by small patches. On each patch the answer to some question is easy. On the overlaps, the easy answers may disagree. The
disagreements form a kind of bookkeeping problem, and there is a standard apparatus for tracking when the local answers
fit together into a global one and, if they do not, how badly they fail.

This file sets that apparatus up in the small. Three groups of numbers attached to a covering measure, in turn, the
global sections, the principal-bundle-like objects sitting over the space, and the obstruction to gluing locally defined
structures into a single global structure. The later files in this batch use the third group to count the ways a smooth
shape over a thickened point can be extended one infinitesimal step further.

Files 19–22 walk Exposé III. Sections III.1–III.4 reuse machinery already in place: completions of local rings (file
04), formally smooth as a property of homomorphisms (defined inside file 19), infinitesimal neighborhoods (file 03).
Sections III.5–III.7 do not. They pivot to **sheaf cohomology in low degrees**, the classification of **torsors** by
$H^{1}$, and the appearance of $H^{2}$ as a **gluing obstruction** for lifting smooth schemes. They also use the
**tangent sheaf** $\mathfrak{g}_{X/S}$, dual to the Kähler differentials $\Omega^{1}_{X/S}$ of file 03.

This file is the working survey. We do not redevelop sheaf cohomology from scratch; we set up just enough that the
cocycle calculations in files 21–22 land cleanly. A reader who already knows Liu Chapter 5 or Hartshorne Chapter III may
skim. A reader who has only the file-03 picture of sheaves should read carefully — this file does most of the conceptual
work, and files 21–22 then just apply it.

The slogan that runs through:

> **$H^{0}$ measures sections. $H^{1}$ measures torsors. $H^{2}$ measures the obstruction to gluing local solutions into
> a global one.** Each step up adds one cocycle dimension; each step says something concrete you can compute on an open
> cover.

## Recap: what file 03 already gives us

A **sheaf** of abelian groups on a topological space $X$ is a presheaf — a functor $F : Open(X)^{op} \to Ab$ — that
satisfies gluing: compatible local data assemble uniquely into global data. File 03 gives the full definition; here we
need only the gluing axiom in the form

```text
0 → F(X) → ∏_i F(U_i) ⇉ ∏_{i,j} F(U_i ∩ U_j),
```

an **equalizer** in `Ab`: a global section is exactly a tuple $(s_{i})$ of local sections, one per open in a cover
$\mathfrak{U} = (U_{i})$, that agree on every overlap.

We will work with sheaves of $\mathcal{O}_{X}$-modules (almost always **quasi-coherent**, often **coherent**). The
structure-sheaf $\mathcal{O}_{X}$ itself is a sheaf of rings; a quasi-coherent sheaf is what you get by sheafifying a
module — locally $\tilde{M}$ for some $\mathcal{O}_{X}(U)$-module $M$. Coherent quasi-coherent on a noetherian scheme
means `finitely generated as a module locally`, with finitely generated relations.

File 03 also gives the **diagonal** $\Delta_{X/Y} : X \hookrightarrow X \times_{Y} X$ and its ideal sheaf, and the
universal target of $Y$-derivations $\Omega^{1}_{X/Y}$. These re-enter at the end of this file when we define the
tangent sheaf.

## $H^{0}$, $H^{1}$, $H^{2}$ via Čech

### What cohomology is, in one paragraph

A short orientation before any formula. The setting is always a left-exact functor on sheaves — typically global
sections $F \mapsto F(X)$ — that fails to be right-exact. **Cohomology measures exactly that failure.** Given a short
exact sequence of sheaves $0 \to F' \to F \to F'' \to 0$, applying global sections produces a sequence

$$
0 \to F'(X) \to F(X) \to F''(X)
$$

that may not extend to a $0 \to \cdots \to 0$ at the right. The cohomology groups $H^{1}, H^{2}, \cdots$ fill the gap
into a long exact sequence. Concretely:

- $H^{0}(X, F) = F(X)$ is the global sections, the data the sheaf already gives you;
- $H^{1}(X, F)$ measures the obstruction to gluing local sections to a global one — given a `F''`-section globally and
  $F'$-lifts on each piece of a cover, an $H^{1}$-class records whether the lifts agree on overlaps;
- $H^{2}(X, F)$ measures the obstruction to gluing the gluing data — given gluings on overlaps, an $H^{2}$-class records
  whether they cohere on triple overlaps.

Higher $H^{q}$ extend the pattern: $H^{q}$ is the obstruction to gluing the data at depth $q - 1$. Every formula in this
file unpacks one of these slogans. **Čech cohomology** is one concrete recipe for computing the groups; it works
whenever the cover is sufficiently fine. We use it as a calculator.

The cleanest way to compute sheaf cohomology in low degrees is therefore **Čech cohomology** on an open cover. We define
it concretely; every formula in file 21 will be a Čech formula in disguise.

### The Čech complex

Fix a sheaf $F$ of abelian groups on $X$ and an open cover $\mathfrak{U} = (U_{i})_{i \in I}$ with a choice of total
order on $I$. The **Čech complex** $\check{C}^{\bullet}(\mathfrak{U}, F)$ is the cochain complex with

```text
Č^p(𝔘, F) = ∏_{i₀ < i₁ < ... < i_p} F(U_{i₀ i₁ ... i_p}),
```

where $U_{i_{0} i_{1} ... i_{p}} := U_{i_{0}} \cap U_{i_{1}} \cap ... \cap U_{i_{p}}$. A $p$-cochain is a tuple of
sections, one per $(p+1)$-fold ordered intersection. The differential $d : \check{C}^{p} \to \check{C}^{p+1}$ is the
alternating restriction:

```text
(dc)_{i₀ ... i_{p+1}} = Σ_{r=0}^{p+1} (−1)^r c_{i₀ ... î_r ... i_{p+1}}|_{U_{i₀ ... i_{p+1}}},
```

where the hat means "delete this index" and the restriction is to the smaller intersection that includes the new index.

**Čech cohomology of the cover:**

```text
Ȟ^p(𝔘, F) := H^p(Č^•(𝔘, F)) = ker(d_p) / im(d_{p−1}).
```

This is a cover-dependent computation. The **global** Čech cohomology $\check{H}^{p}(X, F)$ is the colimit over
refinements of $\mathfrak{U}$. On the schemes we care about — separated, with affine open covers whose intersections are
again affine — every cohomology group we will name is computable directly from a single affine cover; the colimit is a
technicality we do not need.

### $H^{0}$ is the gluing equalizer

In degree `0`, $\check{C}^{0}(\mathfrak{U}, F) = \prod_{i} F(U_{i})$ and
$\check{C}^{1}(\mathfrak{U}, F) = \prod_{i<j} F(U_{ij})$. The differential sends $(s_{i})$ to the family
$(s_{j}|_{U_{ij}} - s_{i}|_{U_{ij}})$. So $\ker(d) \subset \prod_{i} F(U_{i})$ is exactly the set of compatible local
sections — the equalizer of the two restriction maps in the sheaf axiom.

Combining with the axiom itself:

$$
\check{H}^{0}(\mathfrak{U}, F) = F(X).
$$

For any cover, $H^{0}$ is just global sections. Cohomology becomes non-trivial in degree $\geq 1$.

### $H^{1}$ and Mayer-Vietoris

In degree `1`, a `1`-cochain is a family $(c_{ij})_{i<j}$ with $c_{ij} \in F(U_{ij})$. It is a **`1`-cocycle** if its
differential in $\check{C}^{2}$ vanishes, i.e. for every triple $i < j < k$,

```text
c_{jk}|_{U_{ijk}} − c_{ik}|_{U_{ijk}} + c_{ij}|_{U_{ijk}} = 0
```

(the **cocycle condition** on triple overlaps). It is a **`1`-coboundary** if there exists $(s_{i})_{i}$ with
$s_{i} \in F(U_{i})$ and $c_{ij} = s_{j}|_{U_{ij}} - s_{i}|_{U_{ij}}$. Then

```text
Ȟ¹(𝔘, F) = {1-cocycles} / {1-coboundaries}.
```

When $X = U \cup V$ is a two-element cover, the Čech complex collapses to the **Mayer-Vietoris sequence**

```text
0 → F(X) → F(U) ⊕ F(V) → F(U ∩ V) → Ȟ¹(𝔘, F) → 0.
```

$\check{H}^{1}$ is exactly the failure of the restriction map $F(U) \oplus F(V) \to F(U \cap V)$ to be surjective — the
failure of being able to realize an arbitrary section on the overlap as a difference of sections from the two halves.

### $H^{2}$ and triple-overlap obstructions

In degree `2`, a `2`-cochain is a family $(c_{ijk})_{i<j<k}$ with $c_{ijk} \in F(U_{ijk})$. The cocycle condition is on
`4`-fold overlaps:

```text
c_{jkl} − c_{ikl} + c_{ijl} − c_{ijk} = 0   on U_{ijkl}.
```

A `2`-coboundary is $c_{ijk} = b_{jk} - b_{ik} + b_{ij}$ for some `1`-cochain $(b_{ij})$. We will not need the full
machinery of $\check{H}^{2}$. We will need the special case where local data are given on each pair $U_{ij}$ (an
isomorphism $f_{ji}$ between two locally isomorphic schemes), and the failure of the cocycle relation
$f_{kj} f_{ji} = f_{ki}$ produces a `2`-cocycle measuring **transitivity failure on triple overlaps**. This is exactly
the shape of the obstruction in §III.6.3 (file 21).

> _The slogan_: a `1`-cocycle is data on pairs that **almost glues** to a global object; a `2`-cocycle is data on
> triples that **almost cancels** out of a transitivity check. Both become trivial cohomology classes precisely when the
> gluing or cancellation actually goes through.

## Vanishing on affines (Serre)

The reason cohomology of quasi-coherent sheaves on schemes is **computable** is one foundational vanishing.

**Serre's theorem.** _For any affine scheme $X = \operatorname{Spec} A$ and any quasi-coherent $\mathcal{O}_{X}$-module
$\mathcal{F}$,_

```text
H^i(X, 𝓕) = 0   for all i ≥ 1.
```

We treat this as a black box (`serre-affine-vanishing` row of the appendix; the original is Serre, _Faisceaux
algébriques cohérents_ III.3, also EGA III §1.3.1). The intuition: an affine has "enough global sections" to glue any
local quasi-coherent data; there is no room for higher obstruction.

This vanishing is the engine. Given any noetherian separated scheme $X$ covered by affines $(U_{i})$ with all finite
intersections $U_{i_{0} ... i_{p}}$ again affine — which holds automatically on a separated scheme — the cohomology of
any quasi-coherent sheaf is computable from a single Čech complex. We make this precise next.

## Leray's acyclic-cover theorem

Sheaf cohomology has a derived-functor definition ($H^{q}(X, \mathcal{F}) := R^{q} \Gamma(X, -)(\mathcal{F})$) which we
take as authoritative but treat in the background. Čech cohomology of a particular cover is concrete and computable. The
bridge:

**Leray's theorem.** *Let $F$ be a sheaf of abelian groups on $X$, and let $\mathfrak{U} = (U_{i})$ be an open cover
such that every finite nonempty intersection $U_{i*0 ... i_{p}}$is$F$-acyclic, meaning
$H^{q}(U_{i*0 ... i_{p}}, F) = 0$for all$q \geq 1$. Then the natural map*

```text
Ȟ^p(𝔘, F) ⟶ H^p(X, F)
```

_is an isomorphism for every $p$._

(Black box; appendix row `leray-acyclic-cover`; standard sources Godement II.5, EGA 0_III §12.4.)

For us: combine with Serre's vanishing. On a noetherian separated scheme $X$ with an affine open cover
$\mathfrak{U} = (U_{i})$ (whose finite intersections are then again affine, by separation), every quasi-coherent sheaf
$\mathcal{F}$ is $\mathcal{F}$-acyclic on each $U_{i_{0} ... i_{p}}$. Leray then says

```text
Ȟ^p(𝔘, 𝓕) = H^p(X, 𝓕)  for every p.
```

Every cocycle calculation in file 21 takes place inside one such Čech complex on one such affine cover. We do not need
anything deeper.

## Principal homogeneous sheaves and $H^{1}$

Now the geometric meaning of $H^{1}$. Every cocycle calculation in §III.5 of file 21 is a 1-cocycle calculation, and the
reason is that the natural carrier of "extensions of a given morphism along a square-zero thickening" is a **torsor
under a sheaf of groups**.

### Definition

Let $\mathcal{G}$ be a sheaf of (commutative) groups on $X$. A **formally principal homogeneous sheaf** under
$\mathcal{G}$, also called a **$\mathcal{G}$-torsor in formation**, is a sheaf $\mathcal{P}$ of sets together with a
sheaf-of-sets action

$$
\mathcal{P} \times \mathcal{G} \longrightarrow \mathcal{P}
$$

such that the natural map $\mathcal{G} \times \mathcal{P} \to \mathcal{P} \times \mathcal{P}$ sending
$(g, p) \mapsto (p \cdot g, p)$ is an **isomorphism** of sheaves of sets. Concretely: on each open $U$, either
$\mathcal{P}(U)$ is empty or it is a torsor under $\mathcal{G}(U)$ in the usual sense — a set on which $\mathcal{G}(U)$
acts simply transitively.

We say $\mathcal{P}$ is a **principal homogeneous sheaf**, or simply a **torsor**, under $\mathcal{G}$ if in addition
every stalk $\mathcal{P}_{x}$ is nonempty. Equivalently: there is an open cover $(U_{i})$ on which
$\mathcal{P}|_{U_{i}}$ admits a section, i.e. is **trivial** in the sense that one can choose a
$\mathcal{G}|_{U_{i}}$-equivariant isomorphism $\mathcal{P}|_{U_{i}} \simeq \mathcal{G}|_{U_{i}}$ (with $\mathcal{G}$
acting on itself by right translation).

The terminology comes from Giraud's _Cohomologie non abélienne_; Grothendieck cites it explicitly in SGA 1 III.5.0. For
our purposes, "torsor under $\mathcal{G}$" and "principal homogeneous sheaf under $\mathcal{G}$" are interchangeable.

### From a torsor to a 1-cocycle

Let $\mathcal{P}$ be a torsor under $\mathcal{G}$, trivial on a cover $(U_{i})$. Pick a section
$p_{i} \in \mathcal{P}(U_{i})$ for each $i$. On every overlap $U_{ij}$ both $p_{i}$ and $p_{j}$ are sections of the same
torsor $\mathcal{P}|_{U_{ij}}$, which by simple transitivity is just $\mathcal{G}|_{U_{ij}}$ once a section is chosen.
So there is a unique $g_{ij} \in \mathcal{G}(U_{ij})$ with

$$
p_{j}|_{U_{ij}} = p_{i}|_{U_{ij}} \cdot g_{ij}.
$$

On a triple overlap $U_{ijk}$ we apply this twice and once:

```text
p_k = p_j · g_{jk} = (p_i · g_{ij}) · g_{jk} = p_i · (g_{ij} · g_{jk}),
```

so $p_{k} = p_{i} \cdot g_{ik}$ gives **$g_{ik} = g_{ij} \cdot g_{jk}$** on $U_{ijk}$. Writing the group additively (we
are working with sheaves of abelian groups), this is the cocycle condition

```text
g_{jk} − g_{ik} + g_{ij} = 0   on U_{ijk}.
```

So the $(g_{ij})$ form a Čech 1-cocycle for $\mathcal{G}$ on $\mathfrak{U}$.

### From a 1-cocycle to a torsor

Conversely: given a 1-cocycle $(g_{ij})$ for $\mathcal{G}$ on a cover $(U_{i})$, glue copies of $\mathcal{G}|_{U_{i}}$
along the isomorphisms "translation by $g_{ij}$" on each overlap. The cocycle condition is exactly the consistency
required to make the gluing well-defined on triple overlaps. The result is a sheaf $\mathcal{P}$ with a
$\mathcal{G}$-action, trivial on each $U_{i}$, hence a torsor.

### Isomorphic torsors and cohomologous cocycles

If two torsors $\mathcal{P}, \mathcal{P}'$ under $\mathcal{G}$ are isomorphic over an open cover $(U_{i})$ via maps that
may differ from the chosen trivializations, the resulting cocycles $(g_{ij})$ and $(g'_{ij})$ differ by a coboundary
$g'_{ij} = g_{ij} + (h_{j} - h_{i})$ for some $(h_{i})$ with $h_{i} \in \mathcal{G}(U_{i})$. The verification is
mechanical; the content is that **isomorphism classes of trivializing data** correspond to **cohomology classes**.

### The classification: `{torsors under 𝒢} / iso ⟷ Ȟ¹(X, 𝒢)`

Combining all of the above:

> **Theorem (Giraud).** _The set of isomorphism classes of torsors under $\mathcal{G}$ is in natural bijection with
> $\check{H}^{1}(X, \mathcal{G})$. The trivial class — $\mathcal{G}$ acting on itself — corresponds to torsors that
> globally admit a section._

(For abelian $\mathcal{G}$ this is in any standard cohomology textbook; the non-abelian generalization is Giraud's book.
We treat both as the black-box row `giraud-torsor`. The classifying claim is what Grothendieck appeals to in SGA 1
III.5.0–III.5.4.)

This is the geometric meaning of $H^{1}$: it is the **set of twisted forms** of $\mathcal{G}$ itself — sheaves locally
isomorphic to $\mathcal{G}$ but globally distinct, classified by how the local trivializations disagree on overlaps.

## $H^{2}$ as a gluing obstruction

The cohomology group $H^{2}(X, \mathcal{G})$ plays a different role. It is not the classification of objects; it is the
**obstruction to gluing locally given objects into a global one**. We now spell out the shape of this obstruction so the
reader recognizes it when it appears in §III.6.

### The local-data setup

Suppose we have a problem of the following form. On each pair $U_{ij}$ of an open cover $(U_{i})$, we are given an
object — say, two locally isomorphic schemes $X^{i}$ and $X^{j}$, restricted to $U_{ij}$ — together with an
**isomorphism**

$$
f_{ji} : X^{i}|_{U_{ij}} \longrightarrow X^{j}|_{U_{ij}}.
$$

We want to find a global object $X$ whose restriction to each $U_{i}$ is $X^{i}$, with the $f_{ji}$ as the gluing
isomorphisms. The necessary condition is the **cocycle condition** on triple overlaps:

```text
f_{kj} ∘ f_{ji} = f_{ki}   on U_{ijk}.
```

This is a triple-overlap consistency. If it holds, gluing succeeds — this is the standard sheaf gluing argument promoted
from sections to objects with isomorphisms.

### The 2-cocycle

In general the $f_{ji}$ are not unique: each is determined up to composition with an automorphism of the local object,
and the local object's automorphism sheaf — call it $\mathcal{G}$ — is non-trivial. So the cocycle relation may **fail**
by an automorphism on each triple overlap:

```text
f_{ijk} := (f_{ki})⁻¹ ∘ f_{kj} ∘ f_{ji} ∈ 𝒢(U_{ijk}).
```

A short calculation (Grothendieck's "silly calculation," SGA 1 III.6.3) shows that the family $(f_{ijk})$ is a 2-cocycle
for $\mathcal{G}$ on the cover. It is a **coboundary** — i.e. its class in $H^{2}(X, \mathcal{G})$ is zero — exactly
when one can adjust the $f_{ji}$ by sections $g_{ij} \in \mathcal{G}(U_{ij})$ so that the corrected $f_{ji} g_{ij}$
satisfy the cocycle relation. That is, **the obstruction class in $H^{2}(X, \mathcal{G})$ vanishes if and only if the
local data glue**.

### What vanishing buys

If $[f_{ijk}] = 0$ in $H^{2}(X, \mathcal{G})$, then a global object $X$ exists. The set of such global objects — modulo
isomorphism inducing the identity on every $U_{i}$ — is then a torsor under $H^{1}(X, \mathcal{G})$, and hence (by the
previous section) a principal homogeneous space under $H^{1}(X, \mathcal{G})$.

In file 21 this is exactly the statement of Theorem III.6.3: for the lifting of a smooth scheme $X_{n}$ to $X_{n+1}$,
the obstruction lives in $H^{2}(X_{0}, \mathcal{G})$ with
$\mathcal{G} = \mathfrak{g}_{X_{0}/S_{0}} \otimes gr^{n+1}_{\mathcal{I}}(\mathcal{O}_{S})$, and if it vanishes the set
of lifts is a principal homogeneous space under $H^{1}(X_{0}, \mathcal{G})$.

> _Why this works in practice._ On the schemes of interest — $X_{0}$ separated, affine cover with affine intersections —
> Leray reduces every $H^{1}$ and $H^{2}$ to a Čech computation, every Čech computation to a finite calculation in the
> global sections of $\mathcal{G}$ on the various overlaps. The cohomological obstruction is not an abstract invariant;
> it is a 2-cocycle one can write down, at least in principle.

## The tangent sheaf

The remaining ingredient that files 21–22 use is the **tangent sheaf** $\mathfrak{g}_{X/S}$. This is just the dual of
the Kähler differential sheaf $\Omega^{1}_{X/S}$ from file 03, packaged the right way.

### Recap from file 03: $\operatorname{Hom}_{B}(\Omega^{1}_{B/A}, M) = \operatorname{Der}_{A}(B, M)$

For a ring map $A \to B$ and any $B$-module $M$, file 03 (the "What $\Omega^{1}$ represents abstractly" subsection)
proved:

> *An $A$-linear derivation $\delta : B \to M$ factors uniquely through the universal derivation
> $d : B \to \Omega^{1}_{B/A}$as$\delta = \varphi \circ d$for a unique$B$-module map
> $\varphi : \Omega^{1}_{B/A} \to M$.*

In symbols, $\operatorname{Hom}_{B}(\Omega^{1}_{B/A}, M) \simeq \operatorname{Der}_{A}(B, M)$ naturally in $M$. This is
the universal property of $\Omega^{1}$: it is the universal target of $A$-linear derivations of $B$.

### The tangent sheaf $\mathfrak{g}_{X/S}$

For a morphism $X \to S$ of schemes and a quasi-coherent $\mathcal{O}_{X}$-module $\mathcal{M}$, the **sheaf of
$S$-derivations of $\mathcal{O}_{X}$ into $\mathcal{M}$** is the sheaf

```text
𝒟er_S(𝒪_X, ℳ) : U ⟼ Der_{𝒪_S(?)}(𝒪_X(U), ℳ(U))
```

(with the right base-ring on $S$ chosen via the structure map; the construction is standard and globalizes the affine
case identification above). The universal property of the relative differentials sheaf $\Omega^{1}_{X/S}$ (constructed
in file 03\) gives a canonical isomorphism

```text
𝒟er_S(𝒪_X, ℳ) ≃ ℋ𝓂_{𝒪_X}(Ω¹_{X/S}, ℳ).
```

In particular, taking $\mathcal{M} = \mathcal{O}_{X}$:

> **Definition.** _The **tangent sheaf** of $X$ over $S$ is the dual of the relative cotangent sheaf:_
>
> ```text
> 𝔤_{X/S} := ℋ𝓂_{𝒪_X}(Ω¹_{X/S}, 𝒪_X) = 𝒟er_S(𝒪_X, 𝒪_X).
> ```

It is a quasi-coherent sheaf on $X$, the algebraic analogue of the classical tangent bundle. Its sections over an open
$U$ are the $S$-derivations $\mathcal{O}_{X}(U) \to \mathcal{O}_{X}(U)$.

### Dual to $\Omega^{1}$ for smooth morphisms

When $X \to S$ is **smooth** of relative dimension $n$ (file 14), file 15 proved that $\Omega^{1}_{X/S}$ is locally free
of rank $n$. Then $\mathfrak{g}_{X/S}$ is **also locally free of rank $n$**, dual to $\Omega^{1}_{X/S}$ in the sense of
locally free sheaves: pairing with $\Omega^{1}_{X/S}$ gives the rank-1 trivial line bundle. Conversely, for a smooth
morphism $\Omega^{1}_{X/S}$ and $\mathfrak{g}_{X/S}$ exchange roles under duality, and either one can play the part of
"tangent data" depending on context.

The cohomology groups that appear in files 21–22 are uniformly of the form
$H^{q}(X_{0}, \mathfrak{g}_{X_{0}/S_{0}} \otimes \mathcal{M})$ for various auxiliary tensoring with quasi-coherent
$\mathcal{M}$. The reader should think of $\mathfrak{g}_{X_{0}/S_{0}}$ as **the local degrees of freedom for
infinitesimal moves of $X_{0}$ over $S_{0}$** — exactly what the deformation-theoretic obstruction is measuring.

## What this prepares

We now have:

- **Čech cohomology** in low degrees on a separated noetherian scheme with an affine cover. By Serre's vanishing and
  Leray's theorem, this computes the derived-functor cohomology of any quasi-coherent sheaf.
- **$H^{1}$ classifies torsors** (= principal homogeneous sheaves) under any sheaf of abelian groups. A torsor is "an
  object locally trivializable to the group itself."
- **$H^{2}$ measures gluing obstructions**: when local objects come with isomorphisms on overlaps that fail to compose
  correctly on triple overlaps by an automorphism, the class in $H^{2}$ of the resulting 2-cocycle of automorphisms is
  the obstruction to gluing globally.
- **The tangent sheaf** $\mathfrak{g}_{X/S} = \mathcal{Hm}_{\mathcal{O}_{X}}(\Omega^{1}_{X/S}, \mathcal{O}_{X})$ is the
  dual of relative differentials. For smooth $X / S$ it is locally free of rank equal to the relative dimension.

These are the four ingredients file 21 stitches together. To preview:

- **§III.5** uses the H¹ classification: the sheaf $\mathcal{P}(g_{0})$ of extensions of a given morphism
  $g_{0} : Y_{0} \to X$ along a square-zero thickening $Y_{0} \hookrightarrow Y$ is a torsor under
  $\mathcal{G} = \mathcal{Hm}_{\mathcal{O}_{Y_{0}}}(g^{*}_{0} \Omega^{1}_{X/S}, \mathcal{J})$. Its class in
  $H^{1}(Y_{0}, \mathcal{G})$ is the obstruction to extending $g_{0}$ globally.
- **§III.6** uses the H² obstruction story. To lift a smooth $X_{n} / S_{n}$ to a smooth $X_{n+1} / S_{n+1}$: locally,
  lifts exist (file 20, III.4.1); the local lifts come with isomorphisms on overlaps determined up to automorphisms in
  $\mathcal{G} = \mathfrak{g}_{X_{0}/S_{0}} \otimes gr^{n+1}_{\mathcal{I}}(\mathcal{O}_{S})$; the resulting 2-cocycle's
  class in $H^{2}(X_{0}, \mathcal{G})$ is the obstruction to gluing them into a global lift.
- **§III.7** combines the obstruction theory with vanishing arguments. For a smooth proper **curve** over $k$, both
  $H^{2}(X_{0}, \mathfrak{g}_{X_{0}/k})$ and $H^{2}(X_{0}, \mathcal{O}_{X_{0}})$ vanish for dimension reasons; the curve
  lifts to any complete local ring with residue field $k$.

## What to remember

- Sheaf cohomology in low degrees on a separated noetherian scheme is computable as **Čech cohomology** on any affine
  open cover.
- $H^{0}(X, \mathcal{F}) = \Gamma(X, \mathcal{F})$ is global sections (the gluing equalizer).
- $H^{1}(X, \mathcal{G})$ classifies **torsors** under a sheaf of (abelian) groups $\mathcal{G}$: principal homogeneous
  sheaves, locally isomorphic to $\mathcal{G}$ itself but possibly globally non-trivial.
- $H^{2}(X, \mathcal{G})$ is the **obstruction class** when local objects with isomorphisms on overlaps fail to satisfy
  the triple-overlap cocycle. Vanishing of the class means the obstruction can be killed by adjusting the isomorphisms —
  the local objects glue.
- The **tangent sheaf** $\mathfrak{g}_{X/S} = \mathcal{Hm}_{\mathcal{O}_{X}}(\Omega^{1}_{X/S}, \mathcal{O}_{X})$ is the
  universal carrier of $S$-derivations of $\mathcal{O}_{X}$. For smooth $X / S$ it is locally free of rank equal to the
  relative dimension.
- Files 21–22 will write down explicit $H^{1}$ and $H^{2}$ cohomology classes; the calculations are concrete Čech
  bookkeeping on affine covers, made legitimate by Serre's vanishing and Leray's theorem.
