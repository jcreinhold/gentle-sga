# Exposé VI §§11–12 (gentle): examples and the descent isomorphism

## What this file is about

Local data plus gluing instructions ought to determine global data. A surface is built from charts and overlap rules. A
vector field on a manifold is given chart by chart together with how the local pieces transform across overlaps. The
slogan is reassuring, but the precise statement — when exactly does fibre-wise data plus compatibility produce a single
object above? — has been deferred all through the framework. Examples first. The geometric instances that drove the
abstraction in the previous files: families of maps, sheaves on varying spaces, modules over varying rings, and
finite-cover data over schemes.

Then the slogan becomes a theorem. For a fibred category of any kind, the category of functors out of the whole
structure is canonically the same as the category of fibre-wise data equipped with gluing compatibility and a cocycle
law. This is the descent isomorphism. Every later faithfully-flat descent result — for modules, for sheaves, for
morphisms of schemes — is this single isomorphism specialised to a particular setting. The cost paid is purely formal: a
cocycle condition controls how local data agrees on triple overlaps. The payoff is one statement that covers many.

## Opening: from framework to descent

A global object on a fibred category is determined by local data on each fibre, plus gluing instructions across the
base, plus a cocycle condition on triple overlaps. That is the descent isomorphism, and §VI.12 states it once and for
all. Every later faithfully-flat descent theorem — for modules, sheaves, morphisms of schemes — is this one isomorphism
specialised.

Files 35–37 set up the apparatus. **§VI.11** collects the examples that show the apparatus was worth setting up — seven
sub-examples (a)–(g) ranging from the running arrow category through presheaves / sheaves on variable spaces to the
two-object base. **§VI.12** distils the entire formalism into a single isomorphism (VI.12.1):

> For a normalised cloven $\mathcal{E}$-category $\mathcal{F}$ and any target category $\mathcal{C}$, the category
> $\operatorname{Hom}(\mathcal{F}, \mathcal{C})$ of _functors out of $\mathcal{F}$_ is canonically isomorphic to a
> category $\mathcal{H}(\mathcal{F}, \mathcal{C})$ of _fibre-wise data plus coherence_.

This is the **descent isomorphism**: local data (functors `F_S` on each fibre $\mathcal{F}_{S}$), gluing instructions
(natural transformations $\phi_{f} : F_{T} \circ f^{*} \Longrightarrow F_{S}$), and a cocycle condition.

SGA VI does not specialise the statement to schemes — that is **Exposé VIII**'s job. But the apparatus is already sharp:
every later "faithfully flat descent of modules / quasi-coherent sheaves / morphisms" theorem is a specialisation of
VI.12.1 to a particular cloven $\mathcal{F}$ and a particular target $\mathcal{C}$. We close the file (and the present
pass of the gentle SGA project) with a forward pointer.

## §VI.11 Examples

<!-- source: VI.11 -->

We treat (a)–(g) at varying depth: (a) and (b) get a full walk-through (these are the examples we will reuse); (c)–(g)
get a short paragraph.

### a) Arrow categories $Ar(\mathcal{E}) = \operatorname{Hom}(\Delta^{1}, \mathcal{E})$

The running example of the entire exposé (see file 35, file 36, file 37).

Take $\Delta^{1}$ to be the totally-ordered set `[0, 1]` viewed as a category (two objects `0, 1`; one non-identity
arrow $(0, 1) : 0 \to 1$). The **arrow category** $Ar(\mathcal{E})$ is

$$
Ar(\mathcal{E})  =  \operatorname{Hom}(\Delta^{1}, \mathcal{E}),
$$

with objects = arrows of $\mathcal{E}$ and morphisms = commutative squares. The two object inclusions
$0, 1 : pt \to \Delta^{1}$ give two canonical functors

```text
Ar(ℰ)  --source-->  ℰ,        Ar(ℰ)  --target-->  ℰ.
```

For our running example we use the **target** projection. Then the fibre $Ar(\mathcal{E})_{S} = \mathcal{E}_{/ S}$ is
the slice category of $S$-objects.

**Bi-fibred when fibre products exist.** As we worked out in files 35–37: $Ar(\mathcal{E})$ is co-fibred with
co-splitting (direct image = composition: $f_{*}(\eta : Y \to T) = (Y \to T \to S)$); it is prefibred iff fibre products
exist in $\mathcal{E}$ (inverse image = base change: $f^{*}(\xi : X \to S) = (X \times_{S} T \to T)$); when both hold,
it is bi-fibred (file 37 §VI.10.1). The coherence isomorphism $c_{f, g}$ for the cleavage of file 36 is the
associativity of fibre products.

A morphism in $Ar(\mathcal{E})$ is in bijective correspondence with a commutative square

```text
Y  --u-->  X
↓v          ↓
T  --f-->  S.
```

The morphism is **cartesian** (over $f$) iff the square is a *pullback square* in$\mathcal{E}$. The morphism is
**co-cartesian** (over $v$) iff the upper arrow $u$ is the identity (file 37 worked example).

**Specialisation to schemes.** When $\mathcal{E} = (Sch / S_{0})$, the arrow category$Ar(\mathcal{E}) \to \mathcal{E}$
is bi-fibred (fibre products of $S_{0}$-schemes always exist). This is the foundational fibred category that all later
examples — quasi-coherent sheaves, modules, finite étale covers — embed into or descend from.

### b) Presheaves and sheaves on variable spaces

Let $\mathcal{E} = Top$ (or any category of "spaces" — topological, schemes with the étale site, etc.). For each
$T \in Ob \mathcal{E}$, write $\mathcal{U}(T)$ for its category of opens (with inclusions). For a fixed target category
$\mathcal{C}$, write $\mathcal{P}(T) = \operatorname{Hom}(\mathcal{U}(T)^{\circ}, \mathcal{C})$ for the category
of$\mathcal{C}$-valued presheaves on $T$, and $\mathcal{S}h(T) \subset \mathcal{P}(T)$ for the full subcategory of
sheaves (file 34 Module A).

**Direct image.** A continuous map $f : T \to S$ gives, via$U \mapsto f^{-1}(U)$, a functor
$\mathcal{U}(S) \to \mathcal{U}(T)$, and so a _push-forward_ functor

```text
f_*  :  𝒫(T)  →  𝒫(S),    (f_* P)(U)  =  P(f⁻¹(U)).
```

The push-forward of a sheaf is a sheaf (this is automatic from the definition; left exactness is preserved). So $f_{*}$
also restricts to$\mathcal{S}h(T) \to \mathcal{S}h(S)$.

**Functoriality is strict.** $(g f)_{*} = g_{*} f_{*}$ holds *on the nose* (composition of preimages).
So$S \mapsto \mathcal{P}(S)$ is an honest covariant functor $Top \to Cat$. Equivalently,
$S \mapsto \mathcal{P}(S)^{\circ}$ is a contravariant functor$Top \to Cat$, hence by §VI.9 a *split* category over
`Top`.

**Inverse image is more delicate.** When the target $\mathcal{C}$ admits small filtered colimits, the inverse image
$f^{*} : \mathcal{P}(S) \to \mathcal{P}(T)$ exists (left adjoint to $f_{*}$). For sheaves, however, the inverse image of
a sheaf is *not in general* a sheaf — one has to apply the sheafification functor. So while `𝒮h(–)` is a co-fibred
subcategory of `𝒫(–)`, the inclusion $\mathcal{S}h \hookrightarrow \mathcal{P}$ is **not a fibred subcategory** of the
(fibred) category $\mathcal{P}^{\circ}$ over $Top^{\circ}$. This is the categorical reason why "the inverse image of a
sheaf" notation $f^{*}$ is a slight abuse — it is the *sheafification of the inverse-image presheaf*, not the
inverse-image presheaf itself.

**The general form.** SGA VI also describes the larger fibred category $Cat_{//\mathcal{C}}$ over`Cat` from which
$\mathcal{P}$ is recovered by base change along $Top^{\circ} \to Cat$,$S \mapsto \mathcal{U}(S)$. We name this for
context and refer the interested reader to Vistoli §3.2
([`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained)).

### c) Objects-with-operators over an object-with-operators

Take a group $G$ acting on the left on an object$S$ of $\mathcal{E}$. Encode $G \curvearrowright S$ as a
functor$\lambda : \mathcal{E}' \to \mathcal{E}$ from the one-object groupoid $\mathcal{E}' = BG$ to $\mathcal{E}$,
with$\lambda$ sending the unique object of `BG` to $S$ and each$g \in G$ to $g \cdot \bullet : S \to S$.

Base-changing a fibred $\mathcal{F} \to \mathcal{E}$ along$\lambda$ gives a fibred
$\mathcal{F}' = \mathcal{F} \times_{\mathcal{E}} \mathcal{E}' \to \mathcal{E}'$. By VI.6.9 (file 36), $\mathcal{F}'$
inherits the (pre)fibred structure. A cartesian section$s : \mathcal{E}' \to \mathcal{F}'$ is the same as an
$\mathcal{E}$-functor $\mathcal{E}' \to \mathcal{F}$ over$\lambda$, which in this case is a $G$-equivariant object
$\xi \in \mathcal{F}_{S}$ — an object with operators.

This is the categorical generalisation of file 30's $Y \times E$ formalism: the principal-covering data of file 30
§V.2.6 are sections of an appropriate fibred category over`BG`.

### d) Pairs of quasi-inverse adjoint functors; autodualities

Let $\mathcal{E}$ be the connected rigid groupoid with two objects`a, b` and a single non-identity isomorphism
$f : a \to b$ (with inverse $g = f^{-1}$). A normalised cloven category$\mathcal{F} \to \mathcal{E}$ is the same data
as:

- two categories $\mathcal{F}_{a}, \mathcal{F}_{b}$,
- two functors $F = f^{*} : \mathcal{F}_{b} \to \mathcal{F}_{a}$ and$G = g^{*} : \mathcal{F}_{a} \to \mathcal{F}_{b}$,
- two natural isomorphisms $c_{f, g} : F G \Longrightarrow id_{\mathcal{F}_{a}}$
  and$c_{g, f} : G F \Longrightarrow id_{\mathcal{F}_{b}}$,

with the pentagon B) of file 36 §VI.7.4 (applied to the composables `fgf` and`gfg`) automatically supplying the
adjunction triangle identities. So $(F, G)$ is a quasi-inverse _adjoint equivalence_.

The **autoduality** specialisation: $\mathcal{F}_{b} = \mathcal{F}^{\circ}_{a}$,$G = F^{\circ}$,
$c_{g, f} = c^{\circ}_{f, g}$. An _autoduality_ on a category $\mathcal{C}$ is a
functor$D : \mathcal{C} \to \mathcal{C}^{\circ}$ together with an iso $u : D D^{\circ} \Longrightarrow id_{\mathcal{C}}$
satisfying $D(u(x)) = u(D(x))$ for every$x$. Examples: vector spaces with `D = (–)^*` and $u =$ canonical biduality on
finite-dimensional spaces.

### e) Discrete bases

If $\mathcal{E}$ is a discrete category (only identity arrows), an$\mathcal{E}$-category $\mathcal{F}$ is just an
$Ob \mathcal{E}$-indexed family of categories $(\mathcal{F}_{i})_{i \in Ob \mathcal{E}}$. Every $\mathcal{E}$-category
is automatically fibred (every $\mathcal{E}$-morphism is an identity, hence cartesian). One has

```text
Hom_{ℰ/-}(ℱ, 𝒢)  ≅  ∏_i Hom(ℱ_i, 𝒢_i),
Lim←(ℱ / ℰ)  ≅  ∏_i ℱ_i.
```

A degenerate but useful case: it shows that the framework _reduces to_ the obvious thing when there is no base structure
to deal with.

### f) Two-object base with one non-identity arrow

$\mathcal{E}$ has two objects`S, T` and one non-identity arrow $f : T \to S$. An $\mathcal{E}$-category$\mathcal{F}$ is
determined by:

- two categories $\mathcal{F}_{S}, \mathcal{F}_{T}$,
- a bifunctor $H : \mathcal{F}^{\circ}_{T} \times \mathcal{F}_{S} \to Set$,
  where$H(\eta, \xi) = \operatorname{Hom}_{f}(\eta, \xi)$ in $\mathcal{F}$.

$\mathcal{F}$ is prefibred (= fibred, since the only base composition is trivial) iff`H(η, –)` is representable in $\xi$
for every $\eta$ — i.e., iff$f^{*}$ exists. Dually for co-prefibred.

This is the categorical compactification of "fibred categories over a single arrow are _correspondences_
$\mathcal{F}_{S} \dashrightarrow \mathcal{F}_{T}$" — the simplest non-trivial fibred-category situation.

### g) Constant fibre

Let $\mathcal{F} = \mathcal{C} \times \mathcal{E}$ with projection$pr_{2} : \mathcal{F} \to \mathcal{E}$. Then
$\mathcal{F}$ is both fibred and co-fibred over $\mathcal{E}$, with canonical splittings corresponding to the constant
functor$S \mapsto \mathcal{C}$ (and likewise on $\mathcal{E}^{\circ}$). The fibre $\mathcal{F}_{S} = \mathcal{C}$ for
every$S$. One has

```text
Γ̲(ℱ / ℰ)  ≅  Hom(ℰ, 𝒞),
Lim←(ℱ / ℰ)  ⊆  Hom(ℰ, 𝒞)
```

— the latter being the full subcategory of functors $\mathcal{E} \to \mathcal{C}$ sending every morphism to an
isomorphism (i.e., factoring through the localisation$\mathcal{E} \to \mathcal{E}[\mathcal{E}^{-1}]$).

## §VI.12 Functors on a cloven category and the descent isomorphism

<!-- source: VI.12 -->

We arrive at the categorical heart of descent theory. Throughout, $\mathcal{F} \to \mathcal{E}$ is a normalised cloven
category with cleavage data $(f^{*}, \alpha_{f}, c_{f, g})$ as in file 36 §VI.7. Let
$i_{S} : \mathcal{F}_{S} \to \mathcal{F}$ denote the inclusion of the fibre.

### Concrete reading: covers, gluings, triple overlaps

Before the abstract statement, the picture the abstract statement records.

Pick the running example **quasi-coherent modules**: $\mathcal{E}$ is the category of schemes,
$\mathcal{F} \to \mathcal{E}$ is the fibred category whose fibre over a scheme $S$ is the category of quasi-coherent
$\mathcal{O}_{S}$-modules, and for a morphism $f : T \to S$ the inverse image $f^{*}$ is the usual pullback of
quasi-coherent sheaves.

In this setting, descent data on a cover ${U_{i} \to S}$ of a scheme $S$ is exactly what one's intuition expects.

- **Local pieces.** A quasi-coherent module $M_{i}$ on each $U_{i}$.

- **Gluings on pairwise overlaps.** An isomorphism
  $\phi_{ij} : M_{j} |_{U_{i} \times_{S} U_{j}} \cong M_{i} |_{U_{i} \times_{S} U_{j}}$ for each ordered pair $(i, j)$,
  telling how $M_{i}$ and $M_{j}$ are to be identified on the overlap. The convention here is that $\phi_{ii} = id$ and
  $\phi_{ji} = \phi^{-1}_{ij}$.

- **Cocycle condition on triple overlaps.** On the triple overlap $U_{i} \times_{S} U_{j} \times_{S} U_{k}$,

    ```text
    φ_{ij}  ∘  φ_{jk}  =  φ_{ik}.
    ```

    Going $k \to j \to i$ agrees with going $k \to i$. This is the obstruction to inconsistent gluings: if the cocycle identity
    fails, two different routes through the overlaps give two different identifications, and the local data cannot
    assemble.

The descent isomorphism VI.12.1 says: **giving such a triple $((M_{i}), (\phi_{ij}))$ satisfying the cocycle condition
is the same data as giving a single global quasi-coherent module $M$ on $S$.** The forward direction is restriction:
$M_{i} := M |_{U_{i}}$, and the $\phi_{ij}$ are the canonical identifications. The backward direction is the substance —
gluings that agree on triple overlaps assemble to a unique global module.

The abstract statement below replaces "module" with "functor into a target category $\mathcal{C}$," and replaces
"restriction to $U_{i}$" with "the fibre-wise functor `F_S`," and replaces the pairwise gluings $\phi_{ij}$ with natural
transformations $\phi_{f}$ along base maps. The cocycle condition stays the same shape: it asks that two routes through
the cleavage agree, which is what the diagram in subsection b) below expresses for the natural transformations
$\phi_{f}$. Reading the abstract statement, hold the QCoh picture in mind; the diagram of $\phi_{f}$'s recovers the
triple-overlap identity for $\phi_{ij}$'s under the dictionary

```text
covering map   U_i → S        ⟷    base morphism   f : T → S
restriction    M |_{U_i}       ⟷    inverse image   f^* M
overlap        U_i ×_S U_j     ⟷    composable pair g : U → T,  f : T → S
gluing         φ_{ij}           ⟷    natural transformation     φ_f
cocycle        φ_{ij} ∘ φ_{jk} ⟷    cocycle diagram of φ_f, φ_g, c_{f, g}.
```

This dictionary will resurface in file 40 §VIII.1, where descent specialises to quasi-coherent modules and the global
module is constructed concretely from $((M_{i}), (\phi_{ij}))$. The abstract content of VI.12.1 is what makes that
construction work; here, we keep both readings in mind and prove the abstract version.

### Set-up: the functorial homomorphism $\alpha_{f}$

The cleavage's transport morphisms $\alpha_{f}(\xi) : f^{*}(\xi) \to \xi$ package into a natural transformation

```text
α_f  :  i_T ∘ f^*  ⟹  i_S    :   ℱ_S → ℱ.
```

Naturally in $\xi$, this is the data "the$f$-morphism component of the cleavage". When we apply any functor
$F : \mathcal{F} \to \mathcal{C}$ to $\alpha_{f}$, we get a natural transformation

```text
φ_f  :=  F * α_f    :    F_T ∘ f^*  ⟹  F_S    :   ℱ_S → 𝒞,
```

where $F_{S} := F \circ i_{S} : \mathcal{F}_{S} \to \mathcal{C}$ is the restriction of$F$ to the fibre.

### The data $(F_{S}, \phi_{f})$

So every functor $F : \mathcal{F} \to \mathcal{C}$ produces:

- a family $(F_{S})_{S \in Ob \mathcal{E}}$ of functors$F_{S} : \mathcal{F}_{S} \to \mathcal{C}$;
- a family $(\phi_{f})_{f \in Fl(\mathcal{E})}$ of natural
  transformations$\phi_{f} : F_{T} \circ f^{*} \Longrightarrow F_{S}$.

These satisfy:

- **a) Normalisation.** $\phi_{id_{S}} = id_{F_{S}}$ (using the normalised-cleavage assumption
  that$\alpha_{id_{S}} = id$).

- **b) Cocycle identity.** For composable $g : U \to T$ and$f : T \to S$ in $\mathcal{E}$, the diagram of natural
  transformations of functors $\mathcal{F}_{S} \to \mathcal{C}$

    ```text
    F_U ∘ g^* ∘ f^*    --F_U * c_{f, g}-->    F_U ∘ (fg)^*
         |                                          |
         φ_g * f^*                                  φ_{fg}
         ↓                                          ↓
    F_T ∘ f^*           --φ_f-->                   F_S
    ```

    commutes. This is the consistency between successive pull-backs ($g^{*} f^{*}$ vs$(fg)^{*}$) and the way $F$ assigns
    morphisms to the cleavage transports.

The cocycle identity b) is what makes "compatible families of fibre-wise functors" into something rigid enough to
recover the global functor $F$.

### Morphisms of $(F_{S}, \phi_{f})$

Given two functors $F, G : \mathcal{F} \to \mathcal{C}$ with associated data$(F_{S}, \phi_{f})$ and $(G_{S}, \psi_{f})$,
a natural transformation $u : F \Longrightarrow G$ produces:

- a family $(u_{S})_{S \in Ob \mathcal{E}}$ of natural transformations$u_{S} : F_{S} \Longrightarrow G_{S}$,

satisfying:

- **c) Compatibility with cleavage.** For every $f : T \to S$ in$\mathcal{E}$, the square

    ```text
    F_T ∘ f^*    --φ_f-->    F_S
         |                       |
         u_T * f^*                u_S
         ↓                       ↓
    G_T ∘ f^*    --ψ_f-->    G_S
    ```

    commutes.

### The category $\mathcal{H}(\mathcal{F}, \mathcal{C})$

We package the data into a category $\mathcal{H}(\mathcal{F}, \mathcal{C})$:

- **Objects:** pairs of families $((F_{S})_{S \in Ob \mathcal{E}}, (\phi_{f})_{f \in Fl(\mathcal{E})})$ satisfying a)
  and b).
- **Morphisms:** families $(u_{S})_{S \in Ob \mathcal{E}}$ satisfying c).
- **Composition:** componentwise composition of natural transformations.

The construction $F \mapsto ((F_{S}), (\phi_{f}))$ is a functor

```text
K  :  Hom(ℱ, 𝒞)  ⟶  ℋ(ℱ, 𝒞).
```

### VI.12.1 — The descent isomorphism

<!-- source: VI.12.1 -->

_This result says: the functor $K$ is **an isomorphism of categories**. Every system $((F_{S}), (\phi_{f}))$ satisfying
a) and b) comes from a unique global functor $F : \mathcal{F} \to \mathcal{C}$; every compatible family $(u_{S})$
satisfying c) comes from a unique natural transformation$u : F \Longrightarrow G$. The categorical statement "functors
out of $\mathcal{F}$ are the same as compatible fibre-wise data" is the **descent isomorphism**._

**Proposition.** The functor

```text
K  :  Hom(ℱ, 𝒞)  ⟶  ℋ(ℱ, 𝒞)
```

is an **isomorphism of categories**.

**Proof.** _Functoriality of $K$_ is clear from the construction.

_Fully faithful:_ for $F, G : \mathcal{F} \to \mathcal{C}$, the
map$\operatorname{Hom}(F, G) \to \operatorname{Hom}(K F, K G)$ is trivially injective (a natural transformation is
determined by its components). It is surjective because condition c) in $\mathcal{H}(\mathcal{F}, \mathcal{C})$ exactly
says that the family $(u_{S}(\xi))$, on objects of the fibres, extends to a natural transformation on$\mathcal{F}$:
every $f$-morphism $\alpha : \eta \to \xi$ in$\mathcal{F}$ factors uniquely as $\alpha = \alpha_{f}(\xi) \circ \bar{u}$
for a unique $T$-morphism$\bar{u} : \eta \to f^{*}(\xi)$ (file 35 §VI.5.1), and so the value $u(\alpha)$ is determined
by $u_{T}(\bar{u})$ (functoriality on the fibre$\mathcal{F}_{T}$) and $u_{S}(\xi)$ together with $\psi_{f}$ via
condition c).

_Bijective on objects:_ the surjectivity is the substantive content. Given $((F_{S}), (\phi_{f}))$
in$\mathcal{H}(\mathcal{F}, \mathcal{C})$, define $F : \mathcal{F} \to \mathcal{C}$ by

```text
F(ξ)  =  F_S(ξ)        for ξ ∈ Ob ℱ_S,
F(α_f(ξ) ∘ ū)  =  φ_f(ξ) ∘ F_T(ū)    for ū : η → f^*(ξ) a T-morphism.
```

_Functoriality of $F$_: every morphism $\alpha : \eta \to \xi$ in$\mathcal{F}$ over $f : T \to S$ factors uniquely as
$\alpha_{f}(\xi) \circ \bar{u}$ (file 35 §VI.5.1 again). Composability$F(u v) = F(u) F(v)$ for $u : \eta \to \xi$ over
$f$ and$v : \zeta \to \eta$ over $g$ reduces to the equality

```text
F(u) F(v)  =  φ_f(ξ)  ∘  F_T(u') v'    via the c_{f, g} pasting,
```

which holds by the cocycle identity b) (and by the definition of composition in the cloven-category construction of file
37 §VI.8).

The verification is the diagram

```text
F_U(ζ) ──F_U(v')──> F_U g^*(η) ──F_U g^*(u')──> F_U g^* f^*(ξ) ──F_U(c_{f,g}(ξ))──> F_U(fg)^*(ξ)
   ____________ F(v) ___________/                    | φ_g(f^*(ξ))                       | φ_{fg}(ξ)
                                                       ↓                                   ↓
                                          F_T(η) ──F_T(u')──> F_T f^*(ξ) ──φ_f(ξ)──> F_S(ξ).
```

The left triangle commutes by the definition of $F(v)$; the middle square commutes by naturality of$\phi_{g}$; the right
square commutes by condition b). So the outer perimeter commutes, which is exactly $F(u v) = F(u) F(v)$. ∎

The slogan: **a global functor on a fibred category is the same data as fibre-wise functors plus a cocycle.**

### Refinement: $\mathcal{E}$-functors into a cloven target $\mathcal{G}$

When the target $\mathcal{C}$ is itself a normalised cloven$\mathcal{E}$-category $\mathcal{G}$ — say with cleavage
$(f^{*}_{\mathcal{G}}, \alpha^{\mathcal{G}}_{f}, c^{\mathcal{G}}_{f, g})$ — and we restrict to
**$\mathcal{E}$-functors** $F : \mathcal{F} \to \mathcal{G}$, the descent isomorphism refines to use the cleavage of
$\mathcal{G}$ as well.

For each $f : T \to S$ in$\mathcal{E}$, the $f$-morphism $F(\alpha_{f}(\xi))$ in$\mathcal{G}$ factors uniquely as
$\alpha^{\mathcal{G}}_{f}(F_{S}(\xi)) \circ \phi_{f}(\xi)$ for a unique $T$-morphism

$$
\phi_{f}(\xi)  :  F_{T}(f^{*}_{\mathcal{F}}(\xi))  \longrightarrow  f^{*}_{\mathcal{G}}(F_{S}(\xi)).
$$

Naturally in $\xi$, this is

```text
φ_f  :  F_T ∘ f^*_ℱ  ⟹  f^*_𝒢 ∘ F_S    :   ℱ_S → 𝒢_T.
```

The data $(F_{S}, \phi_{f})$ now satisfies:

- **a′)** $\phi_{id_{S}} = id_{F_{S}}$ (normalisation).

- **b′)** Compatibility with both cleavages: the diagram

    ```text
    F_U ∘ g^*_ℱ ∘ f^*_ℱ        --F_U * c^ℱ_{f, g}-->        F_U ∘ (fg)^*_ℱ
          |                                                       |
          φ_g * f^*_ℱ                                              φ_{fg}
          ↓                                                       ↓
    g^*_𝒢 ∘ F_T ∘ f^*_ℱ
          |
          g^*_𝒢 * φ_f
          ↓
    g^*_𝒢 ∘ f^*_𝒢 ∘ F_S        --c^𝒢_{f, g} * F_S-->        (fg)^*_𝒢 ∘ F_S
    ```

    commutes. The two pasting compositions reach $(fg)^{*}_{\mathcal{G}} \circ F_{S}$ by tracking the$f$-pull-back through $F$ in two ways.

The descent isomorphism extends: $\mathcal{E}$-functors$F : \mathcal{F} \to \mathcal{G}$ correspond bijectively to
systems $((F_{S}), (\phi_{f}))$ satisfying a′) and b′). **Cartesian** $\mathcal{E}$-functors$F$ correspond exactly to
those systems for which every $\phi_{f}$ is an _isomorphism_ (rather than just a natural transformation).

We do not reproduce the (entirely parallel) verification.

### The remark of VI.12

Grothendieck closes the section with a remark we should internalise: _it is usually better to reason directly on fibred
categories without using explicit cleavages_. The cloven description is computable but imposes choices that pollute
intrinsic statements; the abstract fibred description is canonical. The descent isomorphism is therefore best read as a
_structural_ statement about $\operatorname{Hom}_{\mathcal{F}, \mathcal{E}}(\mathcal{F}, \mathcal{C})$, not as a recipe
for "construct$F$ from cleavage data". This is the philosophical point of file 37 §VI.9's "splittings rarely exist": in
geometry, forcing a strict choice obscures the natural picture.

## §VI.13 Bibliography

<!-- source: VI.13 -->

The exposé closes with two references, both to Grothendieck's own works:

- **[VI.1]** Grothendieck, _Sur quelques points d'algèbre homologique_, Tôhoku Math. J. **9** (1957), 119–221. The
  Tôhoku paper is the original source for abelian categories, derived functors, and the categorical infrastructure SGA
  VI draws on for its category-of-categories formalism (file 35 §VI.1).
- **[VI.2]** Grothendieck, _Technique de descente et théorèmes d'existence en géométrie algébrique I_, Séminaire
  Bourbaki 190, December 1959. The Bourbaki seminar that introduced fpqc descent of modules — already cited in our
  appendix as [`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190). The geometric content of VI.2 is what
  Exposé VIII works out in full.

(Exposé VII does not exist in SGA 1 — Grothendieck reserved the number but never wrote the corresponding text.)

## Closing pointer: faithfully flat descent (Exposés VIII and IX)

The descent isomorphism VI.12.1 is the categorical core. Its geometric specialisations live in the next two exposés.

**Exposé VIII** — _Descente fidèlement plate_. The fibred category of _quasi-coherent sheaves_
`QCoh : (Sch / S₀)° → Cat` (file 34 Module C example 3, file 37 §VI.10 worked example) is equipped with the *fpqc
topology* on$(Sch / S_{0})$ (file 34 Module A). For an fpqc cover $T \to S$, the *category* $QCoh(T)$ together with its
inverse-image data along$T \to S$ classifies quasi-coherent sheaves on $S$. Concretely:

> A quasi-coherent sheaf on $S$ is the same data as: a quasi-coherent sheaf on$T$ together with a _descent datum_ — an
> isomorphism between its two pull-backs to $T \times_{S} T$ satisfying the cocycle condition on
> $T \times_{S} T \times_{S} T$.

This is the special case of VI.12.1 in which `ℰ = (` a single arrow$T \to S$ in the fpqc site`)`, `ℱ = QCoh(–)`, and the
cocycle reduces to the cleanly visible "agreement on overlaps". The general fpqc-cover version follows by Čech- type
assembly.

**Exposé IX** — _Descente des morphismes étales_. The same machinery applied to the fibred category of finite étale
coverings (file 33 §V.7) over $(Sch / S_{0})$ gives:

> A finite étale cover of $S$ is the same data as: a finite étale cover of$T$ together with a descent datum on
> $T \times_{S} T$.

This is the precise version of "principal coverings descend along faithfully flat covers" that we cited via
[`bourbaki-sem-190`](appendix-black-boxes.md#bourbaki-sem-190) in file 30 (V.2.6), file 31 (V.3.6), and file 33 (V.7).

The project's central toy examples line up. The principal covering
$\operatorname{Spec} \mathbb{Z}[\sqrt{2}] \to \operatorname{Spec} \mathbb{Z}[1/2]$ (file 30, file 33) is a fpqc cover;
the descent datum for an arbitrary scheme$X / \operatorname{Spec} \mathbb{Z}[1/2]$ along this cover is _exactly_ the
$\mathbb{Z}/2$-Galois data that file 33 V.7 used to construct objects classified by
$\pi_{1}(\operatorname{Spec} \mathbb{Z}[1/2], a)$. The Exposés VIII and IX statements turn the working ad hoc descent of
file 30 into a rigorous theorem.

A future pass of the gentle SGA project will rewrite Exposés VIII and IX. For now, the reader who wants the geometric
content of fpqc descent should open Vistoli's notes Ch. 4 or Poonen, _Rational Points on Varieties_, Ch. 4 — both modern
accounts that work out the descent statements via VI.12.1's machinery.

______________________________________________________________________

This closes Exposé VI in the gentle reading. The framework is in place; the geometric application is one exposé away.

The arc through six exposés:

- **Exposé I** (étale, file 12 closing). Étale = smooth + relative dimension `0`.
- **Exposé II** (smooth, file 16 closing). Smooth = locally étale over a polynomial scheme.
- **Exposé III** (formally smooth, file 22 closing). Formally smooth = lifting + cohomological vanishing.
- **Exposé IV** (flat, file 27 "Continuing on"). Flat = exactness of `M ⊗_A –`; flat morphisms are open; generic
  flatness is the spread-out theorem.
- **Exposé V** (étale fundamental group, file 33 "Closing the project"). The étale fundamental group $\pi_{1}(S, a)$ is
  the Galois group of the universal finite étale cover.
- **Exposé VI** (fibred categories and descent, _this file_). A global functor on a fibred category is determined by its
  fibre-wise restrictions plus a cocycle.

The first five build the étale story to its global Galois statement; the sixth provides the framework that Exposés VIII
and IX (faithfully flat descent of modules and morphisms) then turn into a working geometric tool.
