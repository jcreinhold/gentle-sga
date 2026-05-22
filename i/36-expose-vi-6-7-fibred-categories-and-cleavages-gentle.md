# Exposé VI §§6–7 (gentle): fibred categories and cleavages

## What this file is about

A pull-back rule is supposed to do two things. It is supposed to exist — every map between base points should drag
fibres above one to fibres above the other. And it is supposed to compose well — dragging along a path of two steps
should give the same answer as dragging along the steps in turn. Spelling out each demand carefully separates them, and
the two demands turn out to be independent. The first can hold without the second. The first alone is enough to define
inverse images; the second is what makes them honest functors of the base.

Naming these two demands as axioms turns "category over a base" into a real structure. The weaker one alone gives a
prefibred category; both together give a fibred category. Once a fibred category has been singled out, one can ask for
something more: an explicit choice of inverse image for every base map, rather than just the assurance that one exists.
That choice is a cleavage. Cleavages make the framework concrete enough to compute with, but the choice is never
canonical. The looseness it introduces — a coherence isomorphism mediating composed pull-backs — is exactly the two-cell
that bridges abstract fibrations to the explicit functor-valued machinery the next file develops.

## Opening: from cartesian arrows to fibred structure

§5 (file 35) introduced the _property_ of being a cartesian morphism — the universal-property formulation of "pull-back
along $f$". §6 turns the property into _structure_:

- **Fib I.** Every morphism $f : T \to S$ of the base admits inverse images. (Equivalently: the inverse-image functor
  $f^{*} : \mathcal{F}_{S} \to \mathcal{F}_{T}$ exists.) An $\mathcal{E}$-category satisfying Fib I is **prefibred**.
- **Fib II.** Composites of cartesian morphisms are cartesian. A prefibred category satisfying Fib II is **fibred**.

The two axioms are independent. Fib I gives us the inverse-image functors; Fib II ensures they compose well — that
$(g f)^{*} \cong f^{*} g^{*}$ as functors $\mathcal{F}_{R} \to \mathcal{F}_{T}$ for composable $T \to S \to R$. Without
Fib II we still have inverse-image functors but no coherent way to identify "pull-back along the composite" with
"successive pull-backs". The pentagon coherence of file 34 Module C is exactly the 2-cell incarnation of "Fib II".

§7 then adds **structure-as-data**: a **cleavage** is an _explicit choice_ of inverse-image functor for every
$f \in Fl(\mathcal{E})$, together with the chosen cartesian morphisms $\alpha_{f}(\xi) : f^{*}(\xi) \to \xi$. Every
prefibred category admits a cleavage (axiom of choice on objects); the cleavage is _not_ canonical. Once a cleavage is
chosen, we can write down a natural transformation $c_{f, g} : g^{*} f^{*} \Longrightarrow (fg)^{*}$ — the **coherence
isomorphism** — and ask whether it is invertible. _VI.7.2_: cloven $\mathcal{F}$ is fibred iff every $c_{f, g}$ is
invertible. This is the bridge between "abstract fibred" (a property of $\mathcal{F} \to \mathcal{E}$) and "concrete
cleaved" (an explicit pseudofunctor $\mathcal{E}^{\circ} \to Cat$).

We follow the source's order: §6 first (axioms and the properties they grant), §7 second (cleavages and coherence). The
worked example — the cleaved arrow category of file 35 — runs throughout.

## §VI.6 Fibred categories

<!-- source: VI.6 -->

### VI.6.1 — Definition: prefibred, fibred, fibred in groupoids

<!-- source: VI.6.1 -->

_This result says: an $\mathcal{E}$-category $\mathcal{F} \to \mathcal{E}$ is **prefibred** when every base morphism
admits inverse images (Fib I), and **fibred** when additionally composites of cartesian morphisms are cartesian (Fib
II). It is **fibred in groupoids** when every morphism of $\mathcal{F}$ is cartesian — equivalently, when $\mathcal{F}$
is fibred and every fibre $\mathcal{F}_{S}$ is a groupoid._

**Definition.** Let $\mathcal{F}$ be an $\mathcal{E}$-category, with projection $p : \mathcal{F} \to \mathcal{E}$.

- $\mathcal{F}$ is **prefibred over $\mathcal{E}$** if it satisfies:

    - **Fib I.** For every morphism $f : T \to S$ in $\mathcal{E}$, the inverse-image functor
      $f^{*} : \mathcal{F}_{S} \to \mathcal{F}_{T}$ exists (i.e., for every $\xi \in Ob \mathcal{F}_{S}$, there is a
      cartesian $f$-morphism $f^{*}(\xi) \to \xi$).

- $\mathcal{F}$ is **fibred over $\mathcal{E}$** (the projection $p$ is **fibrant**) if it satisfies Fib I and:

    - **Fib II.** The composite of two cartesian morphisms is cartesian.

- $\mathcal{F}$ is **fibred in groupoids over $\mathcal{E}$** if every morphism of $\mathcal{F}$ is cartesian.
  Equivalently: $\mathcal{F}$ is fibred and each fibre $\mathcal{F}_{S}$ is a groupoid.

**Subcategory variants.** A subcategory $\mathcal{G} \subseteq \mathcal{F}$ is a **(pre)fibred subcategory** if it is
itself (pre)fibred over $\mathcal{E}$ and the inclusion $\mathcal{G} \hookrightarrow \mathcal{F}$ is a cartesian
functor. For _full_ subcategories, this reduces to: for every $f : T \to S$ and every $\xi \in Ob \mathcal{G}_{S}$, the
inverse image $f^{*}_{\mathcal{F}}(\xi)$ is $T$-isomorphic to an object of $\mathcal{G}_{T}$. (The full-subcategory case
is what most geometric examples will satisfy.)

**The cartesian sub-fibred-category.** Given a fibred $\mathcal{F}$, let $\tilde{\mathcal{F}} \subseteq \mathcal{F}$ be
the subcategory with the same objects but with only _cartesian_ morphisms (so $\tilde{\mathcal{F}}_{S} =$ the **groupoid
of fibre isomorphisms** of $\mathcal{F}_{S}$, since $S$-morphisms that are also cartesian are exactly the
$S$-isomorphisms; cf. file 35 §VI.5.1's "stability" property). Then $\tilde{\mathcal{F}}$ is a fibred subcategory of
$\mathcal{F}$, and
$\operatorname{Hom}_{\mathcal{E}/-}(\mathcal{E}, \tilde{\mathcal{F}}) \to Lim\leftarrow(\mathcal{F} / \mathcal{E})$ is
faithful (but in general not full).

**Example: extensions of groups.** Take $\mathcal{E}$ and $\mathcal{F}$ to be one-object groupoids defined by groups $E$
and $F$, and the projection $p : F \to E$ to be a group homomorphism. Then $\mathcal{F}$ is fibred over $\mathcal{E}$
iff $p$ is _surjective_, in which case $p$ exhibits $F$ as an extension of $E$ by $G = \ker p$. Fibres are all
isomorphic to `BG` (the one-object groupoid of $G$), and inverse-image functors are inner automorphisms by lifts.

### VI.6.2 — Fibredness invariant under $\mathcal{E}$-equivalence

<!-- source: VI.6.2 -->

_This result says: if $F : \mathcal{F} \to \mathcal{G}$ is an $\mathcal{E}$-equivalence (file 35 §VI.4.3), then
$\mathcal{F}$ is (pre)fibred iff $\mathcal{G}$ is._

**Proposition.** Let $F : \mathcal{F} \to \mathcal{G}$ be an $\mathcal{E}$-equivalence. Then $\mathcal{F}$ is fibred
(resp. prefibred) over $\mathcal{E}$ iff $\mathcal{G}$ is.

**Proof.** By VI.5.3 (1) (file 35), a morphism $\alpha$ of $\mathcal{F}$ is cartesian iff $F(\alpha)$ is cartesian in
$\mathcal{G}$. Since $F$ is an $\mathcal{E}$-equivalence, every object of $\mathcal{G}$ is in the essential image of
$F$, and inverse-image data on either side transports across the equivalence. Fib I and Fib II therefore correspond term
by term. ∎

### VI.6.3 — Cartesianness in products is componentwise

<!-- source: VI.6.3 -->

*This result says: a morphism $(\alpha_{1}, \alpha_{2})$ of $\mathcal{F}_{1} \times*\mathcal{E} \mathcal{F}*2$is
cartesian iff each$\alpha_{i}$ is cartesian.*

**Proposition.** Let $\mathcal{F}_{1}, \mathcal{F}_{2}$ be $\mathcal{E}$-categories and let
$\alpha = (\alpha_{1}, \alpha_{2})$ be a morphism in
$\mathcal{F} = \mathcal{F}_{1} \times_{\mathcal{E}} \mathcal{F}_{2}$ over $f : T \to S$. Then $\alpha$ is cartesian iff
each $\alpha_{i}$ is cartesian.

**Proof sketch.** The hom-set commutative square

```text
Hom_T(η', η)                       →  Hom_f(η', ξ)
   ∥                                       ∥
Hom_T(η'₁, η₁) × Hom_T(η'₂, η₂)  →  Hom_f(η'₁, ξ₁) × Hom_f(η'₂, ξ₂)
```

has bijective vertical arrows by the universal property of fibre products; the bottom arrow is bijective iff each
component is. That gives the equivalence "top arrow bijective ⟺ bottom arrow bijective", which is "α cartesian ⟺ each
α_i cartesian" after fixing $\eta' = (\eta'_{1}, \eta'_{2})$ appropriately. ∎

### VI.6.4 — Cartesian functors into a product

<!-- source: VI.6.4 -->

*This result says: a functor $F : \mathcal{G} \to \mathcal{F}_{1} \times*\mathcal{E} \mathcal{F}*2$is cartesian iff each
component$F_{i} = pr_{i} \circ F : \mathcal{G} \to \mathcal{F}_{i}$is. Equivalently,$\operatorname{Hom}_{cart}$ factors
through products.*

**Corollary.** Let $\mathcal{F} = \mathcal{F}_{1} \times_{\mathcal{E}} \mathcal{F}_{2}$, let $\mathcal{G}$ be an
$\mathcal{E}$-category, and let $F = (F_{1}, F_{2})$ be an $\mathcal{E}$-functor $\mathcal{G} \to \mathcal{F}$. Then $F$
is cartesian iff $F_{1}$ and $F_{2}$ are cartesian. This gives an isomorphism of categories

```text
Hom_{cart}(𝒢,  ℱ₁ ×_ℰ ℱ₂)  ≅  Hom_{cart}(𝒢, ℱ₁)  ×  Hom_{cart}(𝒢, ℱ₂),
```

and in particular, taking $\mathcal{G} = \mathcal{E}$,

```text
Lim←((ℱ₁ ×_ℰ ℱ₂) / ℰ)  ≅  Lim←(ℱ₁ / ℰ)  ×  Lim←(ℱ₂ / ℰ).
```

**Proof.** Apply VI.6.3 morphism-by-morphism. ∎

### VI.6.5 — Products of (pre)fibred are (pre)fibred

<!-- source: VI.6.5 -->

_This result says: the fibre product over $\mathcal{E}$ of (pre)fibred categories is (pre)fibred. Same statement extends
to arbitrary families._

**Corollary.** Let $\mathcal{F}_{1}, \mathcal{F}_{2}$ be (pre)fibred over $\mathcal{E}$. Then
$\mathcal{F}_{1} \times_{\mathcal{E}} \mathcal{F}_{2}$ is (pre)fibred over $\mathcal{E}$.

**Proof.** Fib I: an inverse image of $(\xi_{1}, \xi_{2})$ is $(f^{*}_{1} \xi_{1}, f^{*}_{2} \xi_{2})$, with the product
cartesian morphism (VI.6.3). Fib II: composites of cartesian morphisms in the product are componentwise composites, each
cartesian (Fib II in each $\mathcal{F}_{i}$), so the product composite is cartesian (VI.6.3 again). ∎

### VI.6.6 — Cartesianness preserved under base change

<!-- source: VI.6.6 -->

*This result says: a morphism $\alpha'$ in $\mathcal{F}' = \mathcal{F} \times*\mathcal{E} \mathcal{E}'$is cartesian iff
its image$\alpha$in$\mathcal{F}$ is cartesian.*

**Proposition.** Let $\mathcal{F}$ be an $\mathcal{E}$-category, $\lambda : \mathcal{E}' \to \mathcal{E}$, and
$\mathcal{F}' = \mathcal{F} \times_{\mathcal{E}} \mathcal{E}'$ viewed as $\mathcal{E}'$-category. A morphism $\alpha'$
of $\mathcal{F}'$ is cartesian (over its image in $\mathcal{E}'$) iff $pr_{1}(\alpha')$ is cartesian (over its image in
$\mathcal{E}$).

**Proof.** Direct verification on the universal property, identifying fibres
$(\mathcal{F}')_{S'} = \mathcal{F}_{\lambda(S')}$. ∎

### VI.6.7 — Base change of a cartesian functor is cartesian

<!-- source: VI.6.7 -->

*This result says: if $F : \mathcal{F} \to \mathcal{G}$ is cartesian, so is
$F' := F \times*\mathcal{E} \mathcal{E}' : \mathcal{F}' \to \mathcal{G}'$. So base change restricts to a functor on
cartesian-functor categories: `Hom_{cart}(ℱ, 𝒢) → Hom_{cart}(ℱ', 𝒢')`.*

**Corollary.** For every cartesian $\mathcal{E}$-functor $F : \mathcal{F} \to \mathcal{G}$ and every
$\lambda : \mathcal{E}' \to \mathcal{E}$, the pulled-back functor
$F' = F \times_{\mathcal{E}} \mathcal{E}' : \mathcal{F}' \to \mathcal{G}'$ is a cartesian $\mathcal{E}'$-functor.
Consequently, base change refines to a functor

```text
Hom_{cart}(ℱ, 𝒢)  ⟶  Hom_{cart}(ℱ', 𝒢')
```

natural in $\mathcal{E}', \mathcal{F}, \mathcal{G}$.

**Proof.** Cartesianness on $\mathcal{F}' \to \mathcal{G}'$ corresponds to cartesianness on
$\mathcal{F} \to \mathcal{G}$ by VI.6.6 applied to source and target. ∎

### VI.6.8 — Lim← as cartesian sections

<!-- source: VI.6.8 -->

*This result says: cartesian sections $s : \mathcal{E}' \to \mathcal{F}'$ over $\mathcal{E}'$ of
$\mathcal{F}' = \mathcal{F} \times*\mathcal{E} \mathcal{E}'$are the same as$\mathcal{E}$-functors
$\mathcal{E}' \to \mathcal{F}$that send arbitrary morphisms to cartesian morphisms. Equivalently (when$\mathcal{F}$is
fibred):$Ob Lim\leftarrow(\mathcal{F}' / \mathcal{E}') \cong \operatorname{Hom}_{\mathcal{E}/-}(\mathcal{E}', \tilde{\mathcal{F}})$for$\tilde{\mathcal{F}}$
the cartesian sub-fibred-category.*

**Corollary.** $Lim\leftarrow(\mathcal{F}' / \mathcal{E}')$ is naturally isomorphic to the full subcategory of
$\operatorname{Hom}_{\mathcal{E}/-}(\mathcal{E}', \mathcal{F})$ whose objects are the $\mathcal{E}$-functors
$\mathcal{E}' \to \mathcal{F}$ sending arbitrary morphisms to cartesian morphisms. When $\mathcal{F}$ is fibred, with
cartesian sub-fibred-category $\tilde{\mathcal{F}} \subset \mathcal{F}$,

```text
Ob Lim←(ℱ' / ℰ')  ≅  Hom_{ℰ/-}(ℰ', ℱ̃).
```

This is the technical version of "a cartesian section assigns fibre-wise objects with cartesian transition data". The
$\mathcal{E}' \to \tilde{\mathcal{F}}$ formulation will recur in file 38 §VI.12 as "a section is the same as a coherent
compatible family".

### VI.6.9 — Base change of (pre)fibred is (pre)fibred

<!-- source: VI.6.9 -->

_This result says: pulling a (pre)fibred category $\mathcal{F} \to \mathcal{E}$ back along
$\lambda : \mathcal{E}' \to \mathcal{E}$ gives a (pre)fibred category $\mathcal{F}' \to \mathcal{E}'$._

**Corollary.** If $\mathcal{F}$ is (pre)fibred over $\mathcal{E}$, then
$\mathcal{F}' = \mathcal{F} \times_{\mathcal{E}} \mathcal{E}'$ is (pre)fibred over $\mathcal{E}'$.

**Proof.** Fib I and Fib II both transport across the identification of fibres
$(\mathcal{F}')_{S'} \cong \mathcal{F}_{\lambda(S')}$ (file 35 §VI.4) and the cartesianness statement VI.6.6. ∎

### VI.6.10 — Faithful / fully faithful / equivalence on fibres

<!-- source: VI.6.10 -->

_This result says: for a cartesian $\mathcal{E}$-functor $F : \mathcal{F} \to \mathcal{G}$ between prefibred categories,
$F$ is faithful (resp. fully faithful, resp. an $\mathcal{E}$-equivalence) iff each fibre functor
$F_{S} : \mathcal{F}_{S} \to \mathcal{G}_{S}$ is._

**Proposition.** Let $F : \mathcal{F} \to \mathcal{G}$ be a cartesian $\mathcal{E}$-functor of prefibred
$\mathcal{E}$-categories. Then $F$ is faithful (resp. fully faithful, resp. an $\mathcal{E}$-equivalence) iff every
fibre functor $F_{S} : \mathcal{F}_{S} \to \mathcal{G}_{S}$ is.

**Proof.** Fix $f : T \to S$ and morphisms $u, v : \eta \to \xi$ in $\mathcal{F}$ over $f$. Choose cartesian morphisms
$\alpha^{\mathcal{F}}_{f}(\xi) : f^{*}_{\mathcal{F}}(\xi) \to \xi$ and
$\alpha^{\mathcal{G}}_{f}(F \xi) : f^{*}_{\mathcal{G}}(F \xi) \to F(\xi)$. Cartesianness of $F$ gives an isomorphism
$F(f^{*}_{\mathcal{F}}(\xi)) \cong f^{*}_{\mathcal{G}}(F \xi)$ over $T$. Hence $\operatorname{Hom}_{f}(\eta, \xi)$ in
$\mathcal{F}$ is in bijection with $\operatorname{Hom}_{T}(\eta, f^{*}_{\mathcal{F}}(\xi))$ via the universal property;
same on the$\mathcal{G}$side. The action of$F$on$\operatorname{Hom}_{f}$reduces to the action on$\operatorname{Hom}_{T}$
via these bijections. So fibre-wise faithful (resp. fully faithful) implies global. The equivalence statement follows by
combining with VI.4.2 (file 35 §VI.4.2 (3)). ∎

### VI.6.11 — Fib II equivalent to a stronger universal property

<!-- source: VI.6.11 -->

_This result says: a prefibred $\mathcal{F}$ is fibred iff its cartesian morphisms enjoy a stronger universal property
than the definition demands. The stronger property is that for cartesian $\alpha : \eta \to \xi$ over $f$ and *any*
further morphism $g : U \to T$, precomposition
$\operatorname{Hom}_{g}(\zeta, \eta) \to \operatorname{Hom}_{fg}(\zeta, \xi)$ is bijective._

**Proposition.** A prefibred $\mathcal{E}$-category $\mathcal{F}$ is fibred iff it satisfies:

- **Fib II′.** For every cartesian morphism $\alpha : \eta \to \xi$ in $\mathcal{F}$ over $f : T \to S$, every morphism
  $g : U \to T$ in $\mathcal{E}$, and every $\zeta \in Ob \mathcal{F}_{U}$, the precomposition map

    ```text
    α_*  :  Hom_g(ζ, η)  ⟶  Hom_{fg}(ζ, ξ),    u ↦ α ∘ u,
    ```

    is bijective.

The original Fib II (composites of cartesian morphisms are cartesian) is the special case $g = id_{T}$. So Fib II′ is a
priori stronger; the proposition says it is in fact equivalent to Fib II for prefibred $\mathcal{F}$.

**Proof.** Fib II′ ⟹ Fib II: take $g = id_{T}$ in Fib II′ to get the bijection
$\operatorname{Hom}_{T}(\zeta, \eta) \cong \operatorname{Hom}_{f}(\zeta, \xi)$, which is exactly $\alpha$ cartesian
(file 35 §VI.5.1). Fib II ⟹ Fib II′: pick a cartesian $g$-morphism $\beta : \zeta' \to \eta$ above$g$;
then$\alpha \circ \beta$is cartesian (by Fib II) over`fg`, so cartesianness of$\alpha \circ \beta$ gives the universal
property in question. ∎

### VI.6.12 — When is a morphism an isomorphism?

<!-- source: VI.6.12 -->

_This result says: an isomorphism $\alpha$ in $\mathcal{F}$ projects to an isomorphism $p(\alpha)$ in $\mathcal{E}$ and
is automatically cartesian. The converse holds when $\mathcal{F}$ is fibred: $\alpha$ is an isomorphism iff $p(\alpha)$
is an isomorphism and $\alpha$ is cartesian._

**Corollary.** Let $\mathcal{F}$ be an $\mathcal{E}$-category and $\alpha : \eta \to \xi$ a morphism. If $\alpha$ is an
isomorphism, then $p(\alpha)$ is an isomorphism and $\alpha$ is cartesian. Conversely, if $\mathcal{F}$ is fibred and
$p(\alpha)$ is an isomorphism and $\alpha$ is cartesian, then $\alpha$ is an isomorphism.

**Proof.** "Only if": every isomorphism enjoys precomposition bijectivity unrestrictedly, hence cartesianness. "If"
(when $\mathcal{F}$ fibred): use Fib II′ (VI.6.11) plus the fact that $\alpha$ is cartesian and $p(\alpha)$ is iso to
read off, for every $\zeta \in Ob \mathcal{F}$, that
$\operatorname{Hom}(\zeta, \eta) \to \operatorname{Hom}(\zeta, \xi)$ is bijective. By Yoneda $\alpha$ is iso. ∎

### VI.6.13 — Two-of-three for cartesian morphisms (in fibred ℱ)

<!-- source: VI.6.13 -->

_This result says: in a fibred category, given composable morphisms $\alpha : \eta \to \xi$ (cartesian) and
$\beta : \zeta \to \eta$, the composite $\alpha \beta$ is cartesian iff $\beta$ is. So "cartesian" satisfies a
two-of-three property along with the cartesianness of $\alpha$._

**Corollary.** Let $\mathcal{F}$ be fibred over $\mathcal{E}$. For composable morphisms $\beta : \zeta \to \eta$ and
$\alpha : \eta \to \xi$ in $\mathcal{F}$, with $\alpha$ cartesian: $\alpha \beta$ is cartesian iff $\beta$ is cartesian.

**Proof.** Use Fib II′ (VI.6.11): cartesianness of $\alpha$ gives, for every $g : U \to T$ and every
$\zeta' \in \mathcal{F}_{U}$, the bijection
$\operatorname{Hom}_{g}(\zeta', \eta) \to \operatorname{Hom}_{fg}(\zeta', \xi)$; the further claim that the map sends
`β ∘ –` bijectively onto `(α β) ∘ –` is mechanical. ∎

## §VI.7 Cloven categories

<!-- source: VI.7 -->

We arrive at the structural choice that turns "abstract fibred" into "concrete pseudofunctorial data". Throughout,
$\mathcal{F}$ is an $\mathcal{E}$-category.

### VI.7.1 — Definition: cleavage, normalised cleavage, cloven category

<!-- source: VI.7.1 -->

*This result says: a **cleavage** of $\mathcal{F}$ is a function $f \mapsto f^{*}$ choosing, for every
$f \in Fl(\mathcal{E})$, an inverse-image functor $f^{*} : \mathcal{F}_{S} \to \mathcal{F}_{T}$. The cleavage is
**normalised** if $(id_{S})^{*} = id_{\mathcal{F}_{S}}$for every$S$. A **cloven category** is an $\mathcal{E}$-category
with a chosen cleavage. Cleavages exist iff $\mathcal{F}$is prefibred. Equivalently, a cleavage is a
subset$K \subset Fl(\mathcal{F})$of **transport morphisms**, one over each$(f, \xi)$, all cartesian.*

**Definition.** Let $\mathcal{F}$ be an $\mathcal{E}$-category.

- A **cleavage** of $\mathcal{F}$ is the data of, for every $f \in Fl(\mathcal{E})$, an inverse-image functor
  $f^{*} := f^{*}_{\mathcal{F}} : \mathcal{F}_{p(target(f))} \to \mathcal{F}_{p(source(f))}$, together with a chosen
  cartesian morphism $\alpha_{f}(\xi) : f^{*}(\xi) \to \xi$ for every $\xi \in Ob \mathcal{F}_{target(f)}$.
- A cleavage is **normalised** if for every $S \in Ob \mathcal{E}$, $(id_{S})^{*} = id_{\mathcal{F}_{S}}$ and
  $\alpha_{id_{S}}(\xi) = id_{\xi}$.
- A **cloven category** (resp. **normalised cloven category**) is an $\mathcal{E}$-category with a (resp. normalised)
  cleavage.

**Existence.** $\mathcal{F}$ admits a cleavage iff $\mathcal{F}$ is prefibred. (Fib I says inverse-image functors exist;
the cleavage _names_ one for every $f$. Existence of names uses choice on objects.) Any prefibred $\mathcal{F}$ admits a
_normalised_ cleavage (replace $(id_{S})^{*}$ by$id_{\mathcal{F}_{S}}$and adjust$\alpha_{id_{S}}$).

**Equivalent presentation: transport morphisms.** The set of cleavages of $\mathcal{F}$ is in bijection with the set of
subsets $K \subset Fl(\mathcal{F})$ satisfying:

1. Every $\alpha \in K$ is a cartesian morphism.
1. For every $f : T \to S$ in $\mathcal{E}$ and every $\xi \in Ob \mathcal{F}_{S}$, there is _exactly one_ $f$-morphism
   in $K$ with target $\xi$.

The cleavage is normalised iff $K$ additionally satisfies:

1. Every identity morphism of $\mathcal{F}$ is in $K$.

The morphisms in $K$ are called the **transport morphisms** of the cleavage.

> **In quasi-coherent modules.** A cleavage of the QCoh fibred category is a choice of pullback functor
> $f^{*} : QCoh(S) \to QCoh(T)$ for every morphism $f : T \to S$ of schemes, plus the canonical transport
> $\alpha_{f}(M) : f^{*}(M) \to M$ for every quasi-coherent module $M$ on $S$. The standard sheaf-theoretic pullback
> gives a normalised cleavage: $(id_{S})^{*} = id$ on quasi-coherent sheaves over $S$. This is the cleavage Hartshorne
> or Vakil uses implicitly every time they write $f^{*}$.

### From cleavage to coherence: defining $c_{f, g}$

Given a cloven $\mathcal{F}$ and composable $g : U \to T$, $f : T \to S$ in $\mathcal{E}$, and
$\xi \in Ob \mathcal{F}_{S}$, the universal property of the cartesian morphism
$\alpha_{fg}(\xi) : (fg)^{*}(\xi) \to \xi$ (which is over `fg`) gives a unique $U$-morphism

```text
c_{f, g}(ξ)  :  g^* f^*(ξ)  ⟶  (fg)^*(ξ)
```

making the diagram

```text
g^* f^*(ξ)  --α_g(f^*(ξ))-->  f^*(ξ)
   |                              |
   c_{f, g}(ξ)                    α_f(ξ)
   ↓                              ↓
(fg)^*(ξ)  --α_{fg}(ξ)-->         ξ
```

commute. Naturally in $\xi$, this is a 2-cell of `Cat`:

```text
c_{f, g}  :  g^* f^*  ⟹  (fg)^*    :   ℱ_S ⟶ ℱ_U.
```

(Note the contravariant order: $c_{f, g}$ goes from $g^{*} f^{*}$, the "inner pull-back along$g$, then outer along$f$",
to$(fg)^{*}$, the "pull-back along the composite". This matches the convention of file 34 Module C.)

The 2-cell $c_{f, g}$ need not be invertible; that is what the next proposition addresses.

### VI.7.2 — Cloven $\mathcal{F}$ is fibred ⟺ every $c_{f, g}$ is invertible

<!-- source: VI.7.2 -->

_This result says: a cloven $\mathcal{E}$-category is fibred iff every coherence 2-cell $c_{f, g}$ is a natural
isomorphism. So "fibred" is the precise abstract condition that the cleavage's pseudofunctorial data is
pseudofunctorial-with-isomorphism, not merely with-natural-transformation._

**Proposition.** A cloven $\mathcal{E}$-category $\mathcal{F}$ is fibred iff for every composable pair $(f, g)$ of
arrows of $\mathcal{E}$, the coherence 2-cell $c_{f, g} : g^{*} f^{*} \Longrightarrow (fg)^{*}$ is a natural
isomorphism.

**Proof.** "⟹": Fib II says the composite $\alpha_{f}(\xi) \circ \alpha_{g}(f^{*}(\xi))$ is cartesian over`fg`. By the
universal property of the chosen cartesian morphism $\alpha_{fg}(\xi)$, the unique $U$-morphism $c_{f, g}(\xi)$ from
$g^{*} f^{*}(\xi)$ to$(fg)^{{}_{\xi}}$ filling the diagram is an isomorphism. (Two cartesian morphisms over the same
`fg` with the same target are unique up to unique $U$-isomorphism.) "⟸": Conversely, if every$c_{f, g}$ is invertible,
then the composite $\alpha_{f}(\xi) \circ \alpha_{g}(f^{{}_{\xi}})$ is, up to invertible 2-cell, the chosen cartesian
$\alpha_{fg}$, hence cartesian. ∎

### VI.7.3 — In fibred cloven $\mathcal{F}$, $f^{*}$ is an equivalence for $f$ iso

<!-- source: VI.7.3 -->

_This result says: in a fibred cloven category, when $f : T \to S$ is an isomorphism in $\mathcal{E}$, the inverse-image
functor $f^{*} : \mathcal{F}_{S} \to \mathcal{F}_{T}$ is an equivalence of categories (with quasi-inverse $(f^{-1})^{*}$
up to canonical iso)._

**Corollary.** Let $\mathcal{F}$ be a fibred cloven $\mathcal{E}$-category. For every isomorphism $f : T \to S$ in
$\mathcal{E}$, the functor $f^{*} : \mathcal{F}_{S} \to \mathcal{F}_{T}$ is an equivalence of categories.

**Proof.** Take $g = f^{-1}$ in
VI.7.2:$c_{f, f^{-1}} : (f^{-1})^{*} f^{*} \Longrightarrow (id_{S})^{*} = id_{\mathcal{F}_{S}}$ is a natural isomorphism
(using normalisation). Symmetrically `c_{f⁻¹, f} : f^_ (f⁻¹)^_ ⟹ id_{ℱ_T}` is a natural isomorphism. So $(f^{-1})^{*}$
is a quasi-inverse to$f^{*}$. ∎

### VI.7.4 — Coherence identities A) and B)

<!-- source: VI.7.4 -->

*This result says: the coherence 2-cells $c_{f, g}$of any cloven category satisfy two identities. **A)** Two unit
identities (absorbed into the normalisation when the cleavage is
normalised):$c_{f, id_{T}}(\xi) = \alpha_{id_{T}}(f^{*}(\xi))$ and$c_{id_{S}, f}(\xi) = f^{*}(\alpha_{id_{S}}(\xi))$.
**B)** A pentagon: for composable $h : V \to U \to T \to S$ and $\xi \in \mathcal{F}_{S}$,*

```text
c_{f, gh}  ∘  (h^* * c_{g, h})    =    c_{fg, h}  ∘  (c_{f, g} * h^*),
```

_i.e., the two natural transformations $h^{*} g^{*} f^{*} \Longrightarrow (fgh)^{*}$ agree. This is **the** pentagon
coherence of file 34 Module C._

**Proposition.** Let $\mathcal{F}$ be a cloven $\mathcal{E}$-category. Then for every composable triple $h : V \to U$,
$g : U \to T$, $f : T \to S$ in $\mathcal{E}$, and every $\xi \in Ob \mathcal{F}_{S}$:

- **A) Unit identities.**

    ```text
    c_{f, id_T}(ξ)  =  α_{id_T}(f^*(ξ)),
    c_{id_S, f}(ξ)  =  f^*(α_{id_S}(ξ)).
    ```

    In a normalised cleavage these become $c_{f, id_{T}} = id_{f^{*}}$ and$c_{id_{S}, f} = id_{f^{*}}$ — call this **A′)**.

- **B) Pentagon.** The diagram of natural transformations of functors $\mathcal{F}_{S} \to \mathcal{F}_{V}$

    ```text
    h^* g^* f^*       --c_{g, h} * f^*-->   (gh)^* f^*
         |                                       |
         h^* * c_{f, g}                          c_{f, gh}
         ↓                                       ↓
    h^* (fg)^*        --c_{fg, h}-->        (fgh)^*
    ```

    commutes. Equivalently:

    ```text
    c_{f, gh}  ∘  (h^* * c_{g, h})  =  c_{fg, h}  ∘  (c_{f, g} * h^*).
    ```

In the **fibred case** (where every $c_{f, g}$ is invertible by VI.7.2), the pentagon expresses the slogan that "any two
parallel pasting compositions of coherence isomorphisms agree" — this is the
\[`mac-lane-coherence`\](appendix-black-boxes.md#mac-lane-coherence) input to file 34 Module C. Without invertibility,
the pentagon is still an equality, but the theorem-statement is about pasting natural transformations, not isomorphisms.

**Proof of B).** Both sides are `(fgh)`-morphisms`h^_ g^_ f^_(ξ) → (fgh)^_(ξ)`. By the universal property of
$\alpha_{fgh}(\xi) : (fgh)^{*}(\xi) \to \xi$, two such morphisms are equal iff they have the same composite with
$\alpha_{fgh}(\xi)$. Form the cube whose top face is the diagram in the proposition (with$(fgh)^{*}(\xi)$ added at the
bottom-right corner) and whose four side faces are obtained by attaching $\alpha$-morphisms to each vertex; the side
faces commute by naturality and by the definition of the various $c_{\cdot, \cdot}$'s. Hence the bottom face commutes,
which is exactly the equality sought. ∎

### Summary: cloven category as pseudofunctorial data

Specialise to a **normalised** cloven $\mathcal{E}$-category. The data extracts as:

1. A function $S \mapsto \mathcal{F}_{S} : Ob \mathcal{E} \to Cat$ (the fibres).
1. A function $f \mapsto f^{*} : Fl(\mathcal{E}) \to Mor(Cat)$ (the inverse-image functors), with
   $(id_{S})^{*} = id_{\mathcal{F}_{S}}$.
1. A family of natural transformations `c_{f, g} : g^_ f^_ ⟹ (fg)^*`, satisfying A′) and B).

This is exactly the data of a **pseudofunctor** $\mathcal{E}^{\circ} \to Cat$ in the sense of file 34 Module C, except
for the (mild) reformulation of contravariance. File 37 §VI.8 gives the _converse_ construction: from any pseudofunctor,
build a cloven category. The two operations are mutually inverse (up to a 2-categorical equivalence we will name but not
prove).

## Worked example: cleavage of the arrow category

Continue the worked example of file 35. Take $\mathcal{E} = (Sch / S_{0})$ and$\mathcal{F} = Ar(\mathcal{E})$, the arrow
category.

**A canonical cleavage.** For each $f : Y' \to Y$ in$\mathcal{E}$ and each $(X \to Y) \in Ob \mathcal{F}_{Y}$, define

```text
f^*(X → Y)  :=  (X ×_Y Y'  →  Y'),
α_f(X → Y)  :=   the cartesian square X ×_Y Y' → X over f.
```

This requires a _choice_ of fibre product $X \times_{Y} Y'$ for every`(X, Y, Y', f)`; the choice depends on a choice of
representing object for each fibre-product universal property. Once made, we have a cleavage.

**Normalisation.** When $f = id_{Y}$, the chosen fibre product$X \times*Y Y$ is canonically isomorphic to $X$, but not
equal to it. We normalise by stipulating $(id_{Y})^{*} = id_{\mathcal{F}_{Y}}$ and
adjusting$\alpha_{id_{Y}}(X \to Y) = id_{X}$.

**Coherence isomorphisms.** For composable $g : Y'' \to Y'$ and$f : Y' \to Y$ in $\mathcal{E}$, the coherence
`c_{f, g}(X → Y) : g^_ f^_(X → Y) → (fg)^*(X → Y)` is the canonical isomorphism

```text
(X ×_Y Y') ×_{Y'} Y''  ≅  X ×_Y Y''.
```

This is the **associativity of fibre products**. It is invertible (both sides represent the same universal property of
"object with three compatible morphisms to `X, Y, Y''`, then$Y$"). So by VI.7.2, $Ar(\mathcal{E})$ is fibred — Fib II
holds.

**Pentagon check.** For composable $h : Y''' \to Y''$,$g$,$f$, both pasting compositions of $c$'s yield natural
isomorphisms $((X \times*Y Y') \times_{Y'} Y'') \times_{Y''} Y''' \cong X \times_{Y} Y'''$. Both are the unique iso
witnessing the four-fold universal property; by uniqueness, they agree. The pentagon B) holds.

**The split-vs-cloven question.** Is $Ar(\mathcal{E})$ a *split* category (file 37 §VI.9)? That is, can the cleavage be
chosen so that`(fg)^_ = g^_ f^*` on the nose, with $c_{f, g} = id$? Equivalently: can we choose fibre products
coherently so that $(X \times*Y Y') \times_{Y'} Y'' = X \times_{Y} Y''$ literally, for *all*`(X, Y, Y', Y'')`?

The answer is **no** — there is no global functorial choice of "fibre product" in $(Sch / S_{0})$ that strictly
satisfies associativity. (The category of fibre products is equivalent to, but not isomorphic to, a strict-associative
version. The strictification theorem [`strictification`](appendix-black-boxes.md#strictification) of file 37 §VI.9 says
we *can* make$Ar(\mathcal{E})$ equivalent to a split category, but the equivalence is not the identity.)

This is the example whose strictification failure motivates fibred-category theory: one _cannot_ pretend the
inverse-image functors compose strictly; one _must_ track the coherence isomorphisms $c_{f, g}$.

## Continuing on

File 37 takes the next step: from a normalised cloven category we extract a pseudofunctor $\mathcal{E}^{\circ} \to Cat$
(the natural-transformation data of §VI.7.4). The reverse construction — from a
pseudofunctor$\varphi : \mathcal{E}^{\circ} \to Cat$, build a cloven category over $\mathcal{E}$ — is **§VI.8**, the
central reconstruction theorem of the exposé. The two operations together establish a bijection between cloven
categories over $\mathcal{E}$ and normalised pseudofunctors$\mathcal{E}^{\circ} \to Cat$.

§VI.9 then isolates the _split_ case (where $c_{f, g} = id$ on the nose), and §VI.10 dualises to **co-cartesian**
morphisms, **direct images**$f**$, and **bi-fibred** categories — the setting in which adjoint pairs $(f^{*}, f**)$
live.

After file 37, file 38 closes Exposé VI with the example library (§VI.11) and the **descent isomorphism** (§VI.12.1):
the categorical identity that says "a global functor on a fibred category is determined by fibre-wise data plus a
cocycle." The geometric specialisation (faithfully flat descent of modules and schemes) lives in Exposés VIII–IX; we
close with a forward pointer.
