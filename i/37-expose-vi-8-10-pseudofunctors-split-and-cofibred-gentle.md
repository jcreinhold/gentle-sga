# Exposé VI §§8–10 (gentle): pseudofunctors, split categories, and the dual story

## What this file is about

A cleavage on a fibred category packages its pull-back rule into an assignment: each base map gets an explicit inverse
image, and composed maps get an isomorphism between the composed inverse images. Read in the other direction, the same
data is a rule that hands a category to each base object and a comparison map between categories to each base map,
satisfying a coherence law. This second view is older and lighter — it speaks the language of functors, with one
controlled relaxation. Pinning down the dictionary between the two views, and showing it really is a dictionary, is the
substantive content here.

Tighten the comparison maps to identities and the relaxation goes away. The category-valued rule becomes an honest
strict functor of the base. Categories arising this way are split, and the case is clean but rare in geometry — most
natural pull-backs only agree up to canonical isomorphism, not on the nose. Reverse the direction of pull-back instead
and one gets push-forward — the dual story of co-fibred categories. When both directions exist and are adjoint, the
structure is bi-fibred, and the prototypical example is the pair of inverse-image and direct-image functors on
quasi-coherent sheaves over a scheme.

## Opening: cleavages reconstructed from pseudofunctors

File 36 §VI.7 turned a fibred category with a chosen cleavage into a coherent system of inverse-image functors
$(f^{*}, c_{f, g})$ satisfying the pentagon. §VI.8 reverses the construction: given such data — a **pseudofunctor**
$\varphi : \mathcal{E}^{\circ} \to Cat$ in the sense of
[file 34 Module C](34-sites-sheaves-and-pseudofunctors-gentle.md#module-c-pseudofunctors-cat-and-the-coherence-pentagon)
— we recover a cloven category over $\mathcal{E}$. The two operations are mutually inverse, in the (somewhat technical)
sense that they extend to an _equivalence of 2-categories_ between cloven $\mathcal{E}$-categories and normalised
pseudofunctors $\mathcal{E}^{\circ} \to Cat$.

§VI.9 then isolates the special case where the coherence isomorphisms $c_{f, g}$ are identities: a **split category**.
These are the cloven categories arising from honest functors $\mathcal{E}^{\circ} \to Cat$ (no 2-cells), which is the
simplest case but rare in geometry. Some fibred categories admit a unique split form (when fibres are rigid, VI.9
closing remark); most do not, because strictification fails.

§VI.10 dualises: replace "inverse image" by "direct image" and get **co-fibred**, **bi-fibred** (when both) categories.
The geometric instance is $(f^{*}, f_{*})$ adjoint pairs for quasi-coherent sheaves (file 17), which gives a bi-fibred
category over $(Sch / S_{0})$.

The arc from §VI.6 to §VI.10:

```text
fibred  ⟷  cloven (with coherence)  ⟷  pseudofunctor  ⟷  split  ⟸  bi-fibred
                 §VI.7                       §VI.8         §VI.9       §VI.10
```

§VI.10 is independent of §VI.8–9 (one can dualise any of the preceding without touching pseudofunctorial reformulation),
and we treat it last because the adjoint-pair perspective of bi-fibred categories is the cleanest geometric upshot of
the framework.

## §VI.8 Cloven category from a pseudofunctor

<!-- source: VI.8 -->

*This section says: every normalised pseudofunctor $\varphi : \mathcal{E}^{\circ} \to Cat$ defines a cloven category
$\mathcal{F}*\varphi$over$\mathcal{E}$whose fibres are canonically isomorphic to the values$\varphi(S)$. The
construction is inverse to the one of §VI.7. The two together establish a bijection (extending to a 2-equivalence)
between normalised cloven categories over $\mathcal{E}$and normalised pseudofunctors$\mathcal{E}^{\circ} \to Cat$.*

> **In quasi-coherent modules.** The pseudofunctor side of the dictionary is the one Hartshorne or Vakil writes when
> they say "pullback along $f$": the assignment $S \mapsto QCoh(S)$, $f \mapsto f^{*}$, equipped with the canonical iso
> $g^{*} f^{*} \simeq (fg)^{*}$ of quasi-coherent pullback. The pentagon identity is the routine compatibility that
> $h^{*} g^{*} f^{*} \simeq (fgh)^{*}$ agrees no matter which two factors one associates first; in QCoh it is true on
> the nose for the pullback formula $f^{*} M = f^{-1}M \otimes_{f^{-1}\mathcal{O}_{S}} \mathcal{O}_{T}$. The cloven
> category recovered from this pseudofunctor is the QCoh fibred category of §VI.7's running example.

### The construction

Fix a normalised pseudofunctor $\varphi : \mathcal{E}^{\circ} \to Cat$ with data:

- a category $\varphi(S)$ for each $S \in Ob \mathcal{E}$;
- a functor $f^{*} : \varphi(S) \to \varphi(T)$ for each $f : T \to S$, with $(id_{S})^{*} = id_{\varphi(S)}$ strictly;
- a natural isomorphism $c_{f, g} : g^{*} f^{*} \Longrightarrow (fg)^{*} : \varphi(R) \to \varphi(U)$ for each
  composable $U --g--> T --f--> R$, satisfying the pentagon identity B) of
  [§VI.7.4](36-expose-vi-6-7-fibred-categories-and-cleavages-gentle.md#vi74--coherence-identities-a-and-b) and the unit
  identities A′) (normalisation).

Define the _associated cloven category_ $\mathcal{F} = \mathcal{F}_{\varphi}$ as follows.

**Objects** of $\mathcal{F}$:

```text
Ob(ℱ)  =  ⨆_{S ∈ Ob ℰ} Ob(ϕ(S))
```

— pairs $(S, \xi)$ with $S \in Ob \mathcal{E}$ and $\xi \in Ob \varphi(S)$. Write $\bar{\xi} = (S, \xi)$ (so $S$ is
determined by $\bar{\xi}$).

**Morphisms** of $\mathcal{F}$ from $\bar{\eta} = (T, \eta)$ to $\bar{\xi} = (S, \xi)$ over a fixed $f : T \to S$:

```text
h_f(η̄, ξ̄)  =  Hom_{ϕ(T)}(η, f^*(ξ)).
```

**All morphisms** from $\bar{\eta}$ to $\bar{\xi}$ (varying the base map $f$):

```text
h(η̄, ξ̄)  =  ⨆_{f : T → S} h_f(η̄, ξ̄).
```

(The disjoint union is necessary: two arrows of $\mathcal{E}$ from $T$ to $S$ may be different but give the same
$f^{*}$.)

**Composition.** For composable $(\bar{\eta}, \bar{\xi})$ and$(\bar{\zeta}, \bar{\eta})$ over $f : T \to S$ and
$g : U \to T$, the
composition$h_{f}(\bar{\eta}, \bar{\xi}) \times h_{g}(\bar{\zeta}, \bar{\eta}) \to h_{fg}(\bar{\zeta}, \bar{\xi})$ is

```text
(u, v)  ↦  c_{f, g}(ξ)  ·  g^*(u)  ·  v,
```

i.e., the composite

```text
ζ  --v-->  g^*(η)  --g^*(u)-->  g^* f^*(ξ)  --c_{f, g}(ξ)-->  (fg)^*(ξ).
```

Note that $c_{f, g}(\xi)$ is the coherence isomorphism evaluated at$\xi$.

**Identity.** For $\bar{\xi} = (S, \xi)$, the identity element
of$\operatorname{Hom}_{\varphi(S)}(\xi, \xi) = h_{id_{S}}(\bar{\xi}, \bar{\xi})$ (using normalisation
$(id_{S})^{*} = id_{\varphi(S)}$) is the identity morphism of $\bar{\xi}$ in$\mathcal{F}$.

**Projection** $p : \mathcal{F} \to \mathcal{E}$ sends$\bar{\xi} = (S, \xi) \mapsto S$ and a morphism in
$h_{f}(\bar{\eta}, \bar{\xi})$ to $f$.

### Verification

The verification has six steps, all routine; we reproduce the two crucial ones (associativity of composition,
cartesianness of the canonical morphisms) and refer to Vistoli §3.1.3 for the remaining four.

**Step 1: Associativity.** For composable $V --h--> U --g--> T --f--> S$,
objects$\xi \in \varphi(S), \eta \in \varphi(T), \zeta \in \varphi(U), \tau \in \varphi(V)$, and morphisms

```text
u ∈ h_f(η̄, ξ̄)  =  Hom_{ϕ(T)}(η, f^*(ξ)),
v ∈ h_g(ζ̄, η̄)  =  Hom_{ϕ(U)}(ζ, g^*(η)),
w ∈ h_h(τ̄, ζ̄)  =  Hom_{ϕ(V)}(τ, h^*(ζ)),
```

we have $(u \circ v) \circ w = u \circ (v \circ w)$ in$\operatorname{Hom}_{\varphi(V)}(\tau, (fgh)^{*}(\xi))$. Both
sides are obtained by composing along the upper / lower contour of the diagram

```text
τ --w--> h^*(ζ) --h^*(v)--> h^*g^*(η) --h^*g^*(u)--> h^*g^*f^*(ξ) --h^*(c_{f, g}(ξ))--> h^*(fg)^*(ξ)
                                  \                       |  c_{g, h}(f^*(ξ))             |  c_{fg, h}(ξ)
                                   v ∘ w                  ↓                               ↓
                                                      (gh)^* (η) --(gh)^*(u)--> (gh)^* f^*(ξ) --c_{f, gh}(ξ)--> (fgh)^*(ξ).
```

The middle square commutes by naturality of $c_{g, h}$; the right square is exactly the pentagon B) of file 36 §VI.7.4.
So both contours agree. ∎

**Step 2: Cartesian transport morphisms.** For each $f : T \to S$ and each$\bar{\xi} = (S, \xi) \in Ob \mathcal{F}$, set
$\bar{\eta} = (T, f^{*}(\xi))$ and let

$$
\alpha_{f}(\bar{\xi})  \in  h_{f}(\bar{\eta}, \bar{\xi})
$$

be the element corresponding to $id_{f^{*}(\xi)} \in \operatorname{Hom}_{\varphi(T)}(f^{*}(\xi), f^{*}(\xi))$. We
claim$\alpha_{f}(\bar{\xi})$ is a cartesian morphism over $f$. For any $\bar{\eta}' = (T, \eta')$ and any$f$-morphism
$u' : \bar{\eta}' \to \bar{\xi}$ in $\mathcal{F}$
(so$u' \in h_{f}(\bar{\eta}', \bar{\xi}) = \operatorname{Hom}_{\varphi(T)}(\eta', f^{{}_{\xi}})$), the unique
$T$-morphism $\bar{u} : \bar{\eta}' \to \bar{\eta}$ with$\alpha_{f}(\bar{\xi}) \circ \bar{u} = u'$ is exactly $u'$
itself, viewed in $\operatorname{Hom}_{\varphi(T)}(\eta', f^{{}_{\xi}}) = h_{id_{T}}(\bar{\eta}', \bar{\eta})$. (Use
normalisation:$c_{f, id_{T}}(\bar{\xi}) = id$ by A′).) ∎

The other steps verify:

1. The projection $p : \mathcal{F} \to \mathcal{E}$ is a functor; the
   bijection$h_{f}(\bar{\eta}, \bar{\xi}) \cong \operatorname{Hom}_{f}(\bar{\eta}, \bar{\xi})$ is the identity.
1. The fibres $\mathcal{F}_{S}$ are canonically isomorphic to$\varphi(S)$ via $(S, \xi) \mapsto \xi$.
1. The chosen $\alpha_{f}(\bar{\xi})$'s define a normalised cleavage of$\mathcal{F} \to \mathcal{E}$.
1. The coherence isomorphisms $c_{f, g}$ associated with this cleavage agree, under the iso of step 4, with the
   original$c_{f, g}$ of $\varphi$.

### Grothendieck's axioms A′ and B

The pentagon B) of file 36 §VI.7.4 (= "the diagram of $c$'s commutes") and the unit conditions A′) of normalisation are
together what one needs to _define_ a pseudofunctor in the strict sense. SGA VI states them in the form

```text
A′)  c_{f, id_T}  =  id_{f^*}    and    c_{id_S, f}  =  id_{f^*},
B)   c_{f, gh}  ∘  (h^* * c_{g, h})    =    c_{fg, h}  ∘  (c_{f, g} * h^*).
```

Mac Lane's coherence theorem ([`mac-lane-coherence`](appendix-black-boxes.md#mac-lane-coherence)) guarantees that A′) +
B) imply _every_ coherence diagram commutes (e.g. the four-fold associator for composable quadruples gives, a priori,
two parallel pasting compositions of five $c$'s — they automatically agree). We use this freely without further comment.

### The bijection (cloven categories ↔ normalised pseudofunctors)

The construction of §VI.7 (cloven category → pseudofunctor) and the construction of §VI.8 (pseudofunctor → cloven
category) are mutually inverse, in the sense that:

- Starting from a normalised cloven $\mathcal{F} \to \mathcal{E}$, applying §VI.7 gives a normalised
  pseudofunctor$\varphi_{\mathcal{F}}$, then applying §VI.8 gives a normalised cloven
  $\mathcal{F}_{\varphi_{\mathcal{F}}} \to \mathcal{E}$ canonically isomorphic to the original $\mathcal{F}$ as a cloven
  category.
- Starting from a normalised pseudofunctor $\varphi$, applying §VI.8 then §VI.7 gives a normalised
  pseudofunctor$\varphi_{\mathcal{F}*\varphi}$ isomorphic to $\varphi$ as a pseudofunctor.

The precise statement is that the two assignments extend to quasi-inverse 2-functors between the 2-category
$Cleav(\mathcal{E})$ of normalised cloven$\mathcal{E}$-categories (with appropriately-defined 1-cells and 2-cells) and
the 2-category $PsFun(\mathcal{E}^{\circ}, Cat)$ of normalised pseudofunctors. We name this for context and refer to
[`vistoli-fga-explained`](appendix-black-boxes.md#vistoli-fga-explained) §3.1.3–§3.1.4 for the precise statement and its
verification.

The slogan: **a fibred category with a chosen cleavage _is_ the same data as a normalised pseudofunctor
$\mathcal{E}^{\circ} \to Cat$**. The fibre-and-pull-back perspective and the value-and-coherence perspective are
interconvertible. SGA VI uses both, and so will files 38 and (in the future) Exposé VIII.

## §VI.9 Split categories

<!-- source: VI.9 -->

_This section says: a cloven category whose coherence isomorphisms $c_{f, g}$ are _identities_ (rather than just
isomorphisms) is called **split**. Equivalently, the cleavage arises from an honest
functor$\varphi \: \mathcal{E}^{\circ} \to Cat$ (no 2-cells). Some fibred categories admit a splitting, some do not; an
obstruction class lives in $H^{2}(E, G)$ when the relevant data come from a group extension. Fibred categories with
rigid fibres (no non-trivial automorphisms) always admit a unique splitting._

### Definition

A cleavage of an $\mathcal{E}$-category $\mathcal{F}$ is a **splitting** if every coherence isomorphism$c_{f, g}$ is the
identity:

```text
(fg)^*  =  g^* f^*    (strict equality of functors),
c_{f, g}  =  id_{(fg)^*}.
```

Equivalently, in transport-morphism terms (file 36 §VI.7.1): the set $K \subset Fl(\mathcal{F})$ of transport morphisms
is closed under composition.

A category $\mathcal{F} \to \mathcal{E}$ with a chosen splitting is a **split$\mathcal{E}$-category**.

The category of split $\mathcal{E}$-categories is equivalent to$\operatorname{Hom}(\mathcal{E}^{\circ}, Cat)$ — honest
functors, with no pseudo-prefix. Every split category is a fortiori cloven (and a fortiori prefibred, and is
automatically fibred since the identity 2-cell is an isomorphism).

### Existence of a splitting

A fibred $\mathcal{F}$ admits a splitting iff its coherence data can be chosen identically. This may fail.

**Failure example: group extensions.** Take $\mathcal{E}$ and$\mathcal{F}$ to be one-object groupoids defined by groups
$E$ and $F$, and$p : F \to E$ a surjective group homomorphism (so $\mathcal{F}$ is fibred over $\mathcal{E}$, file 36
§VI.6.1). Let$G = \ker p$. The set of cleavages of $\mathcal{F}$ over $\mathcal{E}$ is in bijection with the set of
_set-theoretic sections_$s : E \to F$ with $p \circ s = id_{E}$ — i.e., systems of representatives for $F / G$. A
cleavage is a splitting iff$s$ is a _group homomorphism_. So splittings exist iff the group extension

$$
1 \to G \to F \to E \to 1
$$

splits as an exact sequence of groups. When $G$ is abelian, the obstruction lives in$H^{2}(E, G)$ (group cohomology,
with $E$ acting on $G$ by inner automorphisms). For non-trivial extensions this$H^{2}$ class is non-zero, and the
splitting fails.

**Success: rigid fibres.** Suppose $\mathcal{F}$ is fibred over$\mathcal{E}$ and each fibre $\mathcal{F}_{S}$ is
**rigid** (every object of $\mathcal{F}_{S}$ has only the identity automorphism). Then$\mathcal{F}$ admits a _unique_
splitting.

_Reason_: by VI.6.2, replacing $\mathcal{F}$ by an$\mathcal{E}$-equivalent category does not change the splitting
question, and one can replace $\mathcal{F}_{S}$ by the equivalent rigid-and-reduced category (where two isomorphic
objects are equal). In a rigid-and-reduced category, every isomorphism between functors $H \to \mathcal{F}_{S}$ is the
identity, so the inverse-image functors$f^{*}$ are determined uniquely (no 2-cells to pin down). ∎

### Strictification

Even when no splitting exists, every pseudofunctor is _equivalent_ to a strict 2-functor, after replacing the values
with equivalent categories. Precisely: every pseudofunctor $\varphi : \mathcal{E}^{\circ} \to Cat$ is equivalent (in the
2-category of pseudofunctors) to a strict 2-functor$\tilde{\varphi} : \mathcal{E}^{\circ} \to Cat$. Equivalently, every
fibred category is $\mathcal{E}$-equivalent to a split category.

We name this as the appendix slug [`strictification`](appendix-black-boxes.md#strictification). The result is the
categorical-coherence half of Mac Lane's coherence story; for a modern treatment see Power, _A general coherence
result_, or Riehl, _Categorical Homotopy Theory_ §10.

### Why splittings still matter when strictification exists

The strictification is constructive but _enlarges_ the source data. For the QCoh pseudofunctor (file 34 Module C example
3), the strictification replaces $QCoh(S)$ by a different (but equivalent) category — typically, a category of "global
modules with a chosen pull-back compatibility for every base morphism". Geometrically, this loses the simplicity of
"quasi-coherent sheaf on$S$". Working with the un-strictified pseudofunctor and tracking the coherence isomorphisms
$c_{f, g}$ is therefore preferable in practice; the splitting-versus-cleavage choice is philosophical, not just
technical.

This is one reason SGA VI develops _both_ the abstract fibred formalism (no choice required) _and_ the
cloven/pseudofunctorial form (choice exposed): the abstract form is canonical, the cloven form is computable, and the
relation between them is a 2-equivalence.

## §VI.10 Co-fibred and bi-fibred categories

<!-- source: VI.10 -->

_This section says: dualise everything. Replace "inverse image" by "direct image" and "cartesian morphism" by
**co-cartesian morphism**. An $\mathcal{E}$-category is **co-fibred** if every base morphism admits direct images and
they compose well. **Bi-fibred** = both fibred and co-fibred; in this case $(f^{*}, f_{*})$ is an adjoint pair on each
fibre._

### Definitions

Let $\mathcal{F}$ be an$\mathcal{E}$-category with projection$p$. A morphism $\alpha : \eta \to \xi$ in $\mathcal{F}$
over$f : T \to S$ is **co-cartesian** if for every $\xi' \in Ob \mathcal{F}_{S}$ the post-composition map

```text
α^*  :  Hom_S(ξ, ξ')  ⟶  Hom_f(η, ξ'),    u ↦ u ∘ α,
```

is bijective. Equivalently: $\alpha$ is cartesian for$\mathcal{F}^{\circ} \to \mathcal{E}^{\circ}$ (the
opposite-category formulation). The dual notion, **direct image** of $\eta$ along $f$, is any$(\xi, \alpha)$ with
$\alpha$ co-cartesian over $f$. We write$f_{*}(\eta)$ for the direct image (when it exists), to distinguish from the
inverse image $f^{*}$.

$\mathcal{F}$ is **co-prefibred** over$\mathcal{E}$ if every $f : T \to S$ admits direct images for every
$\eta \in Ob \mathcal{F}_{T}$.$\mathcal{F}$ is **co-fibred** if it is co-prefibred and composites of co-cartesian
morphisms are co-cartesian. $\mathcal{F}$ is **bi-fibred** if it is both fibred and co-fibred.

### The adjoint-pair perspective

When both $f^{*}$ and$f_{*}$ exist (i.e., $\mathcal{F}$ is prefibred and co-prefibred), the universal properties give
canonical isomorphisms

```text
Hom_S(f_*(η), ξ)  ≅  Hom_f(η, ξ)  ≅  Hom_T(η, f^*(ξ)),
```

natural in $(\eta, \xi) \in \mathcal{F}^{\circ}_{T} \times \mathcal{F}_{S}$. Reading the outer two:`f__` is **left
adjoint** to `f^_`.

```text
f_*  :  ℱ_T  ⇄  ℱ_S  :  f^*,    f_* ⊣ f^*.
```

This is the central geometric instance: the pair $(f^{*}, f_{*})$ of inverse and direct images for quasi-coherent
sheaves on schemes (file 17) are an adjoint pair, and`(QCoh(–), pull-back, push- forward)` is a bi-fibred category over
$(Sch / S_{0})$.

### Composability of the coherence isomorphisms

For composable $g : U \to T$ and$f : T \to S$, the cleavage provides

```text
c_{f, g}  :  g^* f^*  ⟹  (fg)^*    (file 36 §VI.7),
c^{f, g}  :  (fg)_*  ⟹  f_* g_*    (the dual in the co-fibred case).
```

If $(f^{*} \dashv f_{*})$ and`(g^_ ⊣ g__)` are read as adjoint pairs, then $(g^{*} f^{*}) \dashv (f_{*} g_{*})$ as
composite adjoint pairs (left adjoints compose with right adjoints in opposite order). Composing with
`((fg)^_ ⊣ (fg)__)`, we see that$c_{f, g}$ and $c^{f, g}$ are _adjoint_ natural transformations. Hence one is an
isomorphism iff the other is, and:

### VI.10.1 — Bi-fibred ⟺ prefibred + co-prefibred + (one of) the c's invertible

<!-- source: VI.10.1 -->

_This result says: a prefibred and co-prefibred $\mathcal{E}$-category is fibred iff it is co-fibred. Equivalently: the
existence of all inverse and direct images automatically forces both Fib II's (the fibred and the co-fibred), via the
adjoint relation`f__ ⊣ f^_`._

**Proposition.** Suppose $\mathcal{F}$ is prefibred and co-prefibred over$\mathcal{E}$. Then $\mathcal{F}$ is fibred iff
it is co-fibred.

**Proof.** Use the adjointness of $c_{f, g}$ and$c^{f, g}$ described above. Fib II is the assertion that every
$c_{f, g}$ is an iso (file 36 §VI.7.2); the dual Fib II is that every $c^{f, g}$ is an iso. Adjoints share
invertibility, so the two conditions are equivalent. ∎

This is the structural cleanest statement of bi-fibredness: it is automatic given prefibredness + co-prefibredness + the
existence of the adjoint pair. In particular, _every_ situation where we have _both_ well-defined inverse and direct
images of some kind gives a bi-fibred category.

## Worked example: direct image in $Ar(Sch / S_{0})$

Continue the running example. Take $\mathcal{E} = (Sch / S_{0})$ and$\mathcal{F} = Ar(\mathcal{E})$, the arrow category
(file 35, file 36 worked examples). We saw that $\mathcal{F}$ is fibred over $\mathcal{E}$ via the **target**
projection.

**Direct image: composition of arrows.** For $f : Y' \to Y$ in$\mathcal{E}$ and $(X \to Y') \in Ob \mathcal{F}_{Y'}$ (a
$Y'$-scheme), the direct image$f_{*}(X \to Y')$ is

```text
f_*(X → Y')  =  (X --(f ∘ –)--> Y),
```

— composing the structure morphism $X \to Y'$ with$f : Y' \to Y$ gives a $Y$-scheme. The co-cartesian morphism

```text
(X → Y')  --(id_X, f)-->  (X → Y)
```

is the square with vertical maps $id_{X}$ and$f$.

**Verification of co-cartesianness.** For any $(X' \to Y) \in Ob \mathcal{F}_{Y}$ and any$f$-morphism
$(u, f) : (X \to Y') \to (X' \to Y)$ (a square), there is a unique $Y$-morphism$(u, id_{Y}) : (X \to Y) \to (X' \to Y)$
— namely $u$ itself — such that the composite $(u, id_{Y}) \circ (id_{X}, f) = (u, f)$. ∎

**Bi-fibredness.** $Ar(\mathcal{E})$ is **bi-fibred** over$\mathcal{E}$: it is fibred (file 36 worked example) and
co-fibred (just verified). The adjoint pair $f_{*} \dashv f^{*}$ on each fibre is

```text
(Sch / Y')  ⇄  (Sch / Y),
```

with $f_{*}(X \to Y') = (X \to Y' \to Y)$ (composition) and$f^{*}(X \to Y) = (X \times_{Y} Y' \to Y')$ (base change).
The classical "base change is right adjoint to composition" statement for slice categories becomes a special case of
VI.10.1.

**Cohomological side.** The geometric specialisation we will care about in Exposé VIII: when
$\mathcal{E} = (Sch / S_{0})$ and$\mathcal{F}_{S} = QCoh(S)$, the inverse image $f^{*}$ is module pull-back and the
direct image `f*_` is push-forward. The adjunction$f^{{}_{\dashv}} f_{*}$ (now for *quasi-coherent sheaves*, with
$f^{*}$ left adjoint, the opposite direction from the arrow-category example) is the classical adjunction of file 03
§3.4. This gives `QCoh` as a bi-fibred category over$(Sch / S_{0})$ — the central example whose descent statements live
in Exposé VIII.

## Continuing on

File 38 closes Exposé VI with the example library (§VI.11) and the **descent isomorphism** (§VI.12.1). The descent
isomorphism is the categorical identity that makes the entire framework pay off:

> A global $\mathcal{E}$-functor $F : \mathcal{F} \to \mathcal{C}$ on a cloven$\mathcal{E}$-category$\mathcal{F}$ is
> determined by its fibre-wise restrictions $F_{S} = F|_{\mathcal{F}_{S}}$ together with coherence data
> $(\phi_{f})_{f \in Fl(\mathcal{E})}$ satisfying a normalisation and a cocycle identity.

Specialising to $\mathcal{F}_{S} = QCoh(S)$ and$\mathcal{C} =$ Set / Mod gives "global quasi-coherent sheaf assignment =
local data + gluing" — a baby version of fpqc descent. The _strong_ form of this statement, _for an effective fpqc
cover_, is the central theorem of Exposé VIII; we name it but defer its proof.

The §VI.10 example ($Ar(\mathcal{E})$ as a bi-fibred category) and the QCoh pseudofunctor (file 34 Module C) are the two
instances we reuse in file 38.
