# Rewritten Exposé X, sections X.2.6–X.2.14 — the transcendental method; topological finite generation; Lefschetz and Tamagawa pointers

<!-- source: X.2 -->

## What this file is about

A curve has a shape. A doughnut has one hole; a pretzel has more. The number of independent loops on a smooth closed
curve is its genus, and over the complex numbers the picture is classical: a curve of genus g looks like a surface
with g holes, and its loops are described by a standard group on twice as many generators bound by a single relation.
Algebraic geometers want the same answer over more exotic ground fields, including those of positive characteristic,
where the topological picture is unavailable.

In characteristic zero the recovery is exact. In positive characteristic only half survives: the generator count is
right, but one relation is no longer enough, and elliptic curves already show this. A finite-generation theorem
extends the curve case to higher-dimensional spaces, and a closing rigidity result of Tamagawa foreshadows the
anabelian philosophy.

File 49 closed §X.2.5 with the drop counterexamples: upper semicontinuity is a real upper bound on fibre `π₁`, and
even for smooth proper families M. Artin's unpublished counterexample shows there is no straightforward "fibre `π₁` as
a flat local system" theorem in characteristic `p`. The natural follow-up is: what *do* we know about `π₁` of a
**proper smooth curve** over an algebraically closed field, and what can we say about `π₁` of a general **proper
connected scheme**?

This file develops three answers.

The first (X.2.6) is the **transcendental method**: for `X₀` a proper smooth connected curve of genus `g` over an
algebraically closed `k`, `π₁(X₀)` has `2g` topological generators bound by a single commutator relation
`(s₁t₁s₁⁻¹t₁⁻¹) ⋯ (s_g t_g s_g⁻¹t_g⁻¹) = 1`. In characteristic 0 the presentation is exact (the profinite completion
of the classical topological surface group); in characteristic `p` only the *2g-generator part* is asserted (X.2.8
shows the relation cannot be the only one in char `p` — elliptic curves are the simplest witness). The argument
combines:
- the algebraic-closure invariance X.1.8 (file 48), reducing `k` first to a finite-transcendence-degree extension of
  `ℚ`, then to a subfield of `ℂ`, then to `ℂ` itself;
- the comparison theorem `π₁^ét(X) ≃ π₁^top(X^an)^{\widehat{}}` (the profinite completion of the topological
  fundamental group) for `X` proper over `ℂ` — Exposé XII (GAGA), invoked as a black box at this stage;
- and, in characteristic `p`, the **Witt-vector lift** of a smooth proper curve to characteristic 0 (file 22, III.7.4),
  together with the upper-semicontinuity X.2.3 (file 49) to descend the topological-genus bound back to `k`.

The second (X.2.9) is the **topological finite generation theorem**: `π₁` of any proper connected scheme over an
algebraically closed field is topologically finitely generated. The proof reduces via Chow's lemma (EGA II 5.6.2) +
normalisation to the *projective normal* case, then proceeds by induction on dimension. The base case (curves) is
X.2.6; the inductive step (X.2.10) is hyperplane section + Bertini's theorem (X.2.11) + Zariski's connectedness
theorem.

The third (X.2.14) is **A. Tamagawa's solvable specialisation theorem** — a *rigidity* statement closing §X.2: for a
proper smooth curve of genus `g ≥ 2` over a complete DVR with finite residue field, if the solvable specialisation
morphism is bijective then the curve is constant. This is an anabelian-style result, recently elaborated in
Tamagawa's *Duke Math. J.* paper (2001). We develop it fully with surrounding modern context.

The X.2.13 Lefschetz hyperplane theorem for `π₁` (forward-reference to SGA 2 X.3.10) is recorded briefly between X.2.12
and X.2.14.

## §X.2.6 — The transcendental method for `π₁` of a proper smooth curve

<!-- source: X.2.6 -->

### Setting up the calculation

<!-- source: X.2.6 -->

Let `X₀` be a **proper smooth connected curve of genus `g`** over an algebraically closed field `k`. We want a
presentation of `π₁(X₀, a₀)` for `a₀` a chosen geometric point. The strategy is **transcendental** — we will reduce
the calculation, via algebraic-closure invariance, to the case `k = ℂ` (the complex numbers), and there we will
compare with the classical topology.

**Step 1 — Reduce to finite transcendence degree over `ℚ` (char 0) or over `𝔽_p` (char `p`).** Every algebraic
geometry over `k$ involves only finitely many "parameters" — the curve `X₀$ is defined by a finite set of polynomial
equations over a finite-type subring `k_0 ⊂ k$. So `X₀$ is obtained by base change from a curve defined over `k_0$,
which is algebraically closed of *finite transcendence degree* over the prime subfield.

By the algebraic-closure invariance X.1.8 (file 48), `π₁(X₀, a₀) = π₁(X₀ ⊗_{k_0} k_0, a₀)$ depends only on the base
change to any algebraically closed subfield. We may therefore replace `k$ by `k_0$ — algebraically closed of finite
transcendence degree over the prime field.

**Step 2 (char 0) — Embed in `ℂ`.** When `\mathrm{char}(k_0) = 0$, `k_0$ embeds in `ℂ$ as an algebraically closed
subfield of finite transcendence degree. Choosing such an embedding, another application of X.1.8 gives `π₁(X₀, a_0)
= π₁(X₀ ⊗_{k_0} ℂ, a_0)$. We have reduced to `k = ℂ$.

**Step 2 (char `p > 0`) — Lift via Witt vectors.** When `\mathrm{char}(k_0) = p > 0$, we cannot directly embed `k_0$
into a characteristic-0 algebraically closed field. Instead, use the **Witt-vector lift** of file 22 (gentle III.7.4):
there is a smooth proper curve `X / \mathrm{Spec}(W(k_0))$ over the Witt-vector ring of `k_0$, with closed fibre
`X₀$ and generic fibre `X_K = X ⊗ K$ smooth proper of dimension 1 over the fraction field `K$ of `W(k_0)$. The genus
of `X_K$ equals the genus of `X₀$ — this is the **invariance of Euler-Poincaré characteristic** under specialisation
in a smooth proper family, recorded as the new appendix row
[`ega-iv-12-2-smoothness`](appendix-black-boxes.md#ega-iv-12-2-smoothness).

Now `X_K$ is a proper smooth connected curve of genus `g$ over the characteristic-0 field `K$. Take an algebraic
closure `K̄$ of `K$; the geometric generic fibre `X_{K̄}$ is again a proper smooth connected curve of genus `g$ over
the algebraically closed `K̄$ of char 0.

Apply Step 2 (char 0) to `X_{K̄}$: we get a presentation of `π₁(X_{K̄})$ from the topology of `X(ℂ)$.

Apply the upper-semicontinuity X.2.3 (file 49): the specialisation morphism `sp : π₁(X_{K̄}) → π₁(X₀)$ is **surjective**.
Hence `π₁(X₀)$ is a *quotient* of `π₁(X_{K̄})$, which we know explicitly. The presentation transfers (modulo the
caveat that we lose injectivity along the specialisation; see X.2.8).

This is the **Witt-vector + specialise** strategy: lift to characteristic 0, compute there transcendentally, descend
back via X.2.3.

### Step 3 — The topology of a complex Riemann surface

<!-- source: X.2.6 -->

Now we are in the case `k = ℂ`. Let `X₀ / ℂ$ be a proper smooth connected curve of genus `g$. By **GAGA** (Exposé XII,
a deferred gentle pass), the associated analytic space `X₀^{an}$ is a **compact Riemann surface of genus `g$**, and
the étale fundamental group of `X₀$ over `ℂ$ is canonically isomorphic to the **profinite completion** of the
topological fundamental group of `X₀^{an}$:

```text
π₁^ét(X₀, a_0) = π_1^{top}(X₀^{an}, a_0)^{\widehat{}}.
```

This is the standard comparison theorem; we record the GAGA pointer as part of the appendix-XII coverage to come, with
the immediate reference being the Cadoret–Murre treatment cited in
[`murre-cadoret-galois-categories`](appendix-black-boxes.md#murre-cadoret-galois-categories).

The classical topology of a compact orientable genus-`g$ surface gives the **surface group presentation**: the
topological fundamental group is generated by `2g$ elements `s_1, t_1, …, s_g, t_g$ subject to the **single relation**

```text
(s_1 t_1 s_1^{-1} t_1^{-1}) ⋯ (s_g t_g s_g^{-1} t_g^{-1}) = 1.
```

The geometric meaning of the generators: each pair `(s_i, t_i)$ is a **meridian–longitude pair** of the `i$-th
"handle" of the genus-`g$ surface. The relation is the **commutator product equals identity** — it says that walking
once around the boundary of a `4g$-gon (the standard CW model of `Σ_g$) returns to the start, which is the topological
content of having a 2-dimensional cell whose boundary is the commutator product.

This is recorded as the new appendix row
[`surface-group-presentation`](appendix-black-boxes.md#surface-group-presentation), with Hatcher *Algebraic Topology*
§1.2 as the standard textbook reference.

Profinite completion of this presentation gives `π_1^{top}(X₀^{an})^{\widehat{}}$ as a **galoisian-type group** on the
same `2g$ generators with the same relation. (Recall: every relator of the topological group is automatically closed
in the profinite topology, so profinite completion does not impose any *new* relations beyond profinitely closing the
existing single relation.)

Combining Steps 1–3, we have proved (modulo the GAGA comparison theorem):

### Theorem X.2.6 — surface presentation of `π₁` of a proper smooth curve

<!-- source: X.2.6 -->

**Theorem X.2.6.** Let `X₀` be a smooth, proper, connected algebraic curve of genus `g` over an algebraically closed
field `k`. Then `π₁(X₀)` admits a system of `2g` **topological generators** `s_1, t_1, …, s_g, t_g$ bound by the
relation

```text
(s_1 t_1 s_1^{-1} t_1^{-1}) ⋯ (s_g t_g s_g^{-1} t_g^{-1}) = 1.
```

When `\mathrm{char}(k) = 0`, `π₁(X₀)$ is the **galoisian-type group freely generated by these `2g$ generators subject
to the above single relation** — i.e. the profinite completion of the topological surface group of genus `g$.

In characteristic `p > 0$, only the *2g-generators* part is asserted; **the single relation is not the only one** —
see X.2.8 below.

*This result says:* the étale fundamental group of a proper smooth curve of genus `g$ over an algebraically closed
field is *topologically* presented by `2g$ generators with the commutator-product-equals-identity relation. In
characteristic 0 this is the complete presentation; in characteristic `p$ there are *additional* relations (or, more
precisely, certain quotients are non-trivial), reflecting wild inseparable phenomena.

*Proof.* Steps 1–3 above. In characteristic 0, the surjection `π_1^{top, \widehat{}} → π_1^{ét}$ is an isomorphism by
the GAGA comparison theorem. In characteristic `p$, the upper-semicontinuity X.2.3 (file 49) gives only a
surjection `π_1^{top, \widehat{}}(\Sigma_g) → π_1^{ét}(X₀)$. The `2g$-generators bound by the commutator-product
relation are therefore **topological generators** of `π_1^{ét}(X₀)$, but the kernel of the surjection may be
non-trivial. □

> **Slogan.** *`π₁$ of a proper smooth curve of genus `g$ over an algebraically closed field is topologically
> `2g$-generated in any characteristic; in characteristic 0 it is the profinite completion of the topological
> surface group; in characteristic `p$ it is a proper quotient of the latter.*

## §X.2.7 — On the absence of purely algebraic proof

<!-- source: X.2.7 -->

### Remark X.2.7 — there is no purely algebraic proof of X.2.6

<!-- source: X.2.7 -->

**Remark X.2.7.** At present (and to the editor's knowledge — that is, the editor of SGA 1, but the situation has not
changed in any essential way since 1961), there is **no purely algebraic proof** of Theorem X.2.6, except in genera 0
and 1.

The fundamental difficulty: it is **not even clear how to *distinguish*** `2g$ elements in `π₁(X₀)$ which one could
then expect to form a system of topological generators. Algebraic constructions tend to produce *single* elements (a
specific étale cover) or *whole groups* (the full profinite completion), not a labelled generating set.

A related but cleaner case is the **rational line punctured at `n$ points**, where the situation is more sympathetic:
the ramification groups at the `n$ punctures provide `n$ elements of the fundamental group to be studied, and one can
show *purely algebraically* that these generate the **tame fundamental group** topologically. This story is the
subject of Exposé XII (and the modern Cadoret–Murre treatment; cited at file 33's [`murre-cadoret-galois-categories`]).
The footnote in the SGA source notes that even in this concrete case, the ramification generators are determined only
up to conjugacy, so a judicious simultaneous choice of representatives is required — and a fully algebraic proof
remains delicate.

The only fact concerning `π₁$ of a curve that one knows how to prove by purely algebraic methods, **apart from**:

(a) the weak finiteness theorem X.2.12 below (Lang–Serre, see [`tamagawa-anabelian-curves`]([appendix](appendix-black-boxes.md#tamagawa-anabelian-curves) for the surrounding anabelian context), and
(b) the determination of the **abelianised** fundamental group `π_1(X_0)^{ab}$ via the Jacobian (file 46, IX.5.8
closing remark — the slogan there is that `π_1(\mathrm{Pic}^0(X_0)) = π_1(X_0)^{ab}$, which captures the abelian part
of `π_1$ in any characteristic),

— is the transcendental presentation X.2.6 itself, which is *not* purely algebraic.

> **Slogan.** *X.2.6 has no purely algebraic proof. Both the existence of a `2g$-generating system and the precise
> form of the relation are transcendental facts at the level of SGA 1. The only purely algebraic facts about `π_1$ of
> a curve at this level are the Lang–Serre finiteness (X.2.12) and the abelian part via the Jacobian (file 46,
> IX.5.8).*

## §X.2.8 — The last assertion of X.2.6 fails in characteristic `p > 0$

<!-- source: X.2.8 -->

### Remark X.2.8 — the relation is not the only one in char `p$

<!-- source: X.2.8 -->

**Remark X.2.8.** The **last assertion** of X.2.6 — that the surface relation is the *only* relation defining the
group — is **no longer valid** in characteristic `p > 0$. This is already visible for **elliptic curves**.

**The elliptic case.** Let `E / k$ be a smooth proper elliptic curve over an algebraically closed `k$ of characteristic
`p > 0$. The geometric topological surface group of genus 1 is `ℤ² = \langle s, t \mid sts^{-1}t^{-1} = 1 \rangle$ —
the **free abelian group on 2 generators**. Profinite completion gives `\hat{ℤ}^2$.

But the actual fundamental group `π_1(E)$ in characteristic `p$:

- The **prime-to-`p$ part** is `\hat{ℤ}^{(p), 2} = \prod_{ℓ ≠ p} ℤ_ℓ^2$ — the prime-to-`p$ profinite completion of the
  free abelian group of rank 2. This matches the X.2.6 prediction.
- The **`p$-part** is `ℤ_p$ for `E$ **ordinary** (i.e., `p \nmid$ the number of `p$-torsion points after lifting) or
  `0$ for `E$ **supersingular** (i.e., `E$ has no `p$-torsion).

So `π_1(E)$ in characteristic `p$ is `\hat{ℤ}^{(p), 2} \times A$, where `A = ℤ_p$ (ordinary) or `A = 0$ (supersingular)
— **neither** of which agrees with `\hat{ℤ}^2 = \prod_{ℓ} ℤ_ℓ^2$. The discrepancy in the `p$-part shows the X.2.6
surface relation alone does *not* present `π_1(E)$ — there are *additional* relations forcing the `p$-part to take its
"correct" value.

**The general curve.** For a smooth proper curve of genus `g ≥ 2$ over `k$ algebraically closed of char `p > 0$, the
situation is even more dramatic: the `p$-part of `π_1$ depends on subtle invariants of the curve (its `p$-rank, its
`p$-adic Hodge structure, …) in ways that have no transcendental analogue.

A separate open question: **is `π_1(X_0)$ topologically *finitely presented*?** That is, does it admit a presentation
with finitely many generators *and finitely many relations*? In characteristic 0 yes (the surface presentation has 1
relation). In characteristic `p$, this is open, and Grothendieck (in the SGA source) flags it as "**quite improbable**"
— the structure of the `p$-part appears to require infinitely many relations to specify.

> **Slogan.** *In characteristic `p > 0$, the surface relation is not the only relation defining `π_1$ of a smooth
> proper curve. The `p$-part of `π_1$ encodes wild inseparable structure that has no transcendental analogue. Whether
> `π_1$ is topologically finitely presented in characteristic `p$ is open — likely false.*

## §X.2.9 — Topological finite generation of `π₁` of a proper scheme

<!-- source: X.2.9 -->

### Theorem X.2.9 — `π₁` of a proper connected scheme is topologically finitely generated

<!-- source: X.2.9 -->

**Theorem X.2.9.** Let `k` be an algebraically closed field, and let `X` be a **proper connected scheme** over `k`.
Then `π₁(X)` is **topologically finitely generated** — that is, there is a finite subset `S ⊂ π_1(X)` such that the
closed subgroup generated by `S$ is all of `π_1(X)$ (equivalently, the closure of `S$ in the profinite topology is the
whole group).

*This result says:* every proper connected scheme over an algebraically closed field has finite topological data on
its étale fundamental group: a finite set of monodromy generators suffices to generate `π_1$ topologically. This
strong finiteness contrasts with the situation for *affine* schemes in characteristic `p$ (the Artin–Schreier
phenomena, X.1.10 in file 48), where `π_1$ can be infinitely generated even topologically.

*Proof.* We proceed by **induction on `n = \dim X$**. The assertion is trivial for `n ≤ 0$ (`X = \mathrm{Spec}$ of a
finite field extension is `π_1 = e$, since `k$ is algebraically closed).

Suppose `n > 0` and the theorem is proved for proper connected schemes of dimension `< n$.

**Step 1: reduction to `X$ projective and normal.** By **Chow's lemma** ([`chow-lemma`](appendix-black-boxes.md#chow-lemma),
EGA II §5.6.2), there exists a **projective** `k$-scheme `X′$ and a surjective morphism `X′ → X$. We may assume `X′$
is reduced (replacing `X′$ by `X′_{red}$ does not change `π_1$, since the reduction map is a finite radicial surjective
morphism — a universal homeomorphism — and étale coverings descend along universal homeomorphisms by IX.4.10 in file
45). After passing to the normalisation `X′′ → X′$ (file 12, I.10), we may further assume `X′′ → X$ is a surjective
morphism with `X′′` **projective and normal**.

By descent theory (file 45, IX.5.2), the topological finite generation of `π_1(X)$ reduces to the topological finite
generation of `π_1$ of each connected component of `X′′$. Each connected component of `X′′$ is again projective and
normal, and surjects onto `X$ — so we have reduced to the case where `X$ itself is **projective and normal**.

**Step 2: dimension induction.** Suppose now `X$ is projective normal connected of dimension `n$ over the algebraically
closed `k$.

- If `n = 1$: apply X.2.6. `π_1(X)$ has `2g$ topological generators, where `g$ is the genus of the smooth proper
  normalisation of `X$ (one can check that finitely many additional generators suffice to account for any non-smooth
  singular points via pinching, file 46 IX.5.4). The conclusion: `π_1(X)$ is topologically finitely generated.
- If `n ≥ 2$: consider a projective immersion `g : X → ℙ^r_k$ and a hyperplane section `Y = X \cdot H = X \times_{ℙ^r}
  H$, endowed with the **reduced induced structure**, chosen so that `Y ≠ X$ (i.e., `H$ does not contain `X$ entirely).
  Then `\dim Y < n$. By the induction hypothesis, `π_1(Y)$ is topologically finitely generated.

  It now suffices to prove that the morphism `π_1(Y) → π_1(X)$ is **surjective**. If yes, then topological generators
  of `π_1(Y)$ map to topological generators of `π_1(X)$, finishing the induction. The surjectivity statement is the
  content of X.2.10 below, which we now prove.

> **Slogan.** *`π₁$ of a proper connected scheme over an algebraically closed field is topologically finitely generated.
> The proof: Chow's lemma reduces to projective normal; induction on dimension reduces to curves; X.2.6 finishes
> the base case.*

### Lemma X.2.10 — surjectivity from hyperplane section to ambient

<!-- source: X.2.10 -->

**Lemma X.2.10.** Let `X` be a prescheme proper over an algebraically closed field `k`, and let `g : X → ℙ^r_k` be a
morphism. Suppose `X` is irreducible and normal, and `\dim g(X) ≥ 2`. Let `H` be a **hyperplane** of `ℙ^r_k`, and let
`Y = X \times_{ℙ^r} H` be the corresponding hyperplane section (with its reduced induced structure). Then:

(i) `Y$ is **connected**, and
(ii) the homomorphism `π_1(Y) → π_1(X)$ is **surjective**.

*This result says:* under the dimension condition `\dim g(X) ≥ 2$, the étale fundamental group of a hyperplane section
`Y \subset X$ surjects onto the étale fundamental group of `X$. Topologically: monodromy in `X$ is detected by monodromy
in any sufficiently large hyperplane section. This is the algebraic analogue of "every loop in `X$ can be deformed to
lie in `Y$", which is the topological hyperplane-section theorem (Lefschetz hyperplane theorem for `π_1$ in dim ≥ 2).

(ii) is the engine of the X.2.9 induction; (i) is the technical step that says hyperplane sections of irreducible
normal `X$ remain connected — the connectedness is essential because we want to compare `π_1$ groups of *connected*
schemes.

These assertions follow from the next corollary X.2.11, which proves a stronger fact: connected étale covers of `X$
restrict to connected étale covers of `Y$.

### Corollary X.2.11 — connected étale covers stay connected on hyperplane sections

<!-- source: X.2.11 -->

**Corollary X.2.11.** Under the preceding conditions, let `X′ → X$ be a **connected** étale covering of `X$, and let
`Y′ = X′ \times_X Y = X′ \times_{ℙ^r} H$ be the induced covering on `Y$. Then `Y′$ is **connected**.

*This result says:* base-changing a connected étale cover of `X$ along a hyperplane section keeps it connected. This is
the key technical step that makes the X.2.10 surjectivity work: a non-trivial étale cover of `X$ remains non-trivial
when restricted to `Y$, so `Y$ "sees" all of `X$'s étale monodromy.

*Proof.* Since `X$ is normal, the étale covering `X′ → X$ has `X′$ normal as well (étale + normal base ⇒ normal upper
side, file 12, I.10.3). Connected + normal ⇒ **irreducible**: `X′$ is irreducible. The image of `X′$ in `ℙ^r_k$
contains the image of `X$, so has dimension `≥ 2$.

Apply **Bertini's theorem** (Zariski's lemma; new appendix row
[`bertini-jouanolou`](appendix-black-boxes.md#bertini-jouanolou)): if `H_1$ is the **generic hyperplane** in `ℙ^r_k$
(defined over a large extension `K / k$), then `X′ \times_{ℙ^r} H_1$ is **universally irreducible** as a scheme over
`K$ — that is, irreducible after every further base change. In particular it is universally connected over `K$.

Apply **Zariski's connectedness theorem** (new appendix row
[`zariski-connectedness`](appendix-black-boxes.md#zariski-connectedness), EGA III §4.3): for *every* hyperplane `H$,
defined over any extension of `k$, the fibre product `X′ \times_{ℙ^r} H$ is **geometrically connected**. This is the
specialisation step: Bertini gives the conclusion for the *generic* hyperplane, and Zariski's connectedness theorem
spreads it to *every* hyperplane via a flatness argument (the family `X′ \times \mathbb{H}$ over the dual projective
space `\mathbb{H}$ is proper with connected generic fibre, hence has connected fibres in a dense open of
`\mathbb{H}$; the closed set on which connectedness fails is closed in a flat family of proper schemes, etc.).

Hence `Y′ = X′ \times_{ℙ^r} H$ is connected for the specific hyperplane `H$ that we chose. This proves X.2.11. □

**Proof of X.2.10.** Surjectivity of `π_1(Y) → π_1(X)$ follows from X.2.11: a non-trivial connected étale cover of `X$
gives a non-trivial connected étale cover of `Y$ (by X.2.11), so any element of `π_1(X)$ that maps to the identity in
`π_1(Y)$ must be already trivial — i.e., the kernel of `π_1(Y) → π_1(X)$ is *injective on the level of étale covers*,
which is the X.2.10 statement of surjectivity (file 33, V.6.9). Connectedness of `Y$ itself is also X.2.11 applied to
the trivial cover. □

> **Slogan.** *Connectedness of étale covers is preserved under hyperplane section in the irreducible normal projective
> case, by Bertini + Zariski's connectedness. This is the topological-finite-generation engine: monodromy from
> hyperplane sections suffices to generate `π_1$ of the ambient scheme.*

## §X.2.12 — The Lang–Serre finiteness corollary

<!-- source: X.2.12 -->

### Corollary X.2.12 — finiteness of principal `G`-coverings

<!-- source: X.2.12 -->

**Corollary X.2.12 (Lang–Serre).** Under the conditions of X.2.9 — `k$ algebraically closed, `X$ proper connected over
`k$ — for every **finite group `G$**, the set of isomorphism classes of **principal coverings of `X$ with group `G$**
is **finite**.

*This result says:* for a proper connected scheme `X$ over algebraically closed `k$ and a fixed finite group `G$, only
finitely many isomorphism classes of `G$-Galois étale covers of `X$ exist. Topologically: there are only finitely many
homomorphisms `π_1(X) → G$ up to conjugation.

*Proof.* By X.2.9, `π_1(X)$ is topologically finitely generated. Standard profinite-group theory: a topologically
finitely generated profinite group has only **finitely many continuous homomorphisms** to any fixed finite group `G$.
(The proof: continuous homomorphisms `π → G$ factor through the open subgroups `\ker(π → G)$ of finite index; an
open subgroup of finite index is determined by its image of a finite generating set of `π$; only finitely many subsets
of `G$ of bounded cardinality, so only finitely many possible images.) Up to conjugation, this gives finitely many
isomorphism classes of `G$-Galois étale covers. □

This is the **Lang–Serre theorem** ([`tamagawa-anabelian-curves`](appendix-black-boxes.md#tamagawa-anabelian-curves)
the modern survey; original: Lang–Serre, "Sur les revêtements non ramifiés des variétés algébriques," *Amer. J. Math.*
**79** (1957)). It is one of the foundational results of the algebraic-geometric theory of `π_1$, and was the initial
motivation for the abstract theory developed in Exposé V.

> **Slogan.** *For `X$ proper connected over an algebraically closed field, only finitely many `G$-Galois étale covers
> exist for each finite group `G$. This is a purely algebraic finiteness result, available by the topological
> finite-generation theorem X.2.9 and standard profinite-group arguments.*

## §X.2.13 — The Lefschetz hyperplane theorem for `π_1$

<!-- source: X.2.13 -->

### Remark X.2.13 — Lefschetz for higher-dimensional ambient

<!-- source: X.2.13 -->

**Remark X.2.13.** Under the conditions of X.2.10, when `\dim g(X) ≥ 3$, the surjectivity of `π_1(Y) → π_1(X)$
upgrades to an **isomorphism**, at least when `g$ is an **immersion** (i.e., `X \subset ℙ^r_k$ is a closed subscheme,
not merely the source of a morphism) and `X$ is **regular**.

This is the **Lefschetz hyperplane theorem for `π_1$**: for a regular projective `X / k$ of dimension `≥ 3$ and a
smooth hyperplane section `Y \subset X$, the inclusion `Y ↪ X$ induces an isomorphism `π_1(Y) → π_1(X)$.

The proof is **not** at the level of Exposé X — it requires the SGA 2 machinery of **local cohomology** and **Lefschetz
pencils**. We record the result as the forward-reference

```text
SGA 2, Exposé X, Theorem 3.10.
```

and the new appendix row [`sga2-lefschetz-pi1`](appendix-black-boxes.md#sga2-lefschetz-pi1).

In the **classical complex case**, this is the Lefschetz hyperplane theorem for `π_1$ via Morse theory (the standard
reference is **Milnor, *Morse Theory*** §VII for the homology version; **Hartshorne *Algebraic Geometry* III.5** for
the cohomological version in algebraic geometry).

There are also analogous statements for **homology groups** and **higher homotopy groups** in the classical case,
which "sooner or later must be incorporated into abstract algebraic geometry," as the SGA source notes. The étale
homotopy theory of **Artin–Mazur** (Springer LNM 100, 1969) provides a partial framework for higher étale homotopy
groups; we do not pursue it here.

Even for **Hodge cohomology** `H^p(X, Ω^q)$, the Lefschetz theorems are subtle in characteristic `p$ and "it is hardly
likely that for the latter the Lefschetz theorems remain valid as stated in characteristic `p > 0$" (SGA source). The
modern resolution uses crystalline / `p$-adic cohomology, which is again beyond Exposé X.

> **Slogan.** *In dimension `≥ 3$, the X.2.10 surjection upgrades to a Lefschetz isomorphism `π_1(Y) → π_1(X)$ for a
> smooth hyperplane section of a regular projective `X$. The proof is in SGA 2, X.3.10; in dimension 2 only the
> surjectivity holds, as X.2.10 shows.*

## §X.2.14 — A. Tamagawa's solvable specialisation theorem

<!-- source: X.2.14 -->

### Setting: a curve over `k[[T]]$

<!-- source: X.2.14 -->

**Remark X.2.14 (M. Raynaud).** Let `R$ be a complete discrete valuation ring with algebraically closed residue field
`k$ of characteristic `p > 0$ and fraction field `K$. Let `Y / R$ be a **proper smooth connected curve of genus `g$**.

By X.2.4 (file 49), there is a surjective specialisation morphism

```text
sp : π_1(Y_{K̄}) → π_1(Y_k),
```

defined up to inner automorphism. We have already observed (file 49, X.2.5; degenerate elliptic curve cases) that if
`K$ has characteristic 0, `sp$ is **not** an isomorphism as soon as `g ≥ 1$. Suppose now that `K$ has **equal
characteristic** `p$ (i.e. char `K = p$ as well), so that `R \cong k[[T]]$ is a power-series ring over `k$.

**The question.** In equal characteristic `p > 0$, the fundamental group is **not determined by the genus `g$** — as
already seen for elliptic curves, which may be **ordinary** (`p$-rank 1) or **supersingular** (`p$-rank 0), giving
distinct `π_1$. Can we rigidify by passing to *some* canonical quotient?

The right answer is to pass to the **solvable** quotient of the specialisation.

### Definitions: `G^{res}$, the solvable specialisation morphism

<!-- source: X.2.14 -->

**Definition.** For a profinite group `G$, write `G^{res}$ for the **inverse limit of the finite solvable topological
quotients** of `G$ — equivalently, the maximal pro-solvable quotient. The "`res$" superscript stands for "résoluble"
(solvable).

The specialisation morphism `sp : π_1(Y_{K̄}) → π_1(Y_k)$ induces, by passage to the solvable quotient, a
**solvable specialisation morphism**

```text
sp^{res} : π_1(Y_{K̄})^{res} → π_1(Y_k)^{res}.
```

This is again surjective (since `sp$ is), so `sp^{res}$ is a surjection of pro-solvable profinite groups.

### Theorem X.2.14 (A. Tamagawa) — solvable rigidity of equal-`p$ curves

<!-- source: X.2.14 -->

**Theorem X.2.14 (A. Tamagawa).** Suppose `g ≥ 2$, the special fibre `Y_k$ is **definable over a finite field** (i.e.,
`Y_k$ is the base change of a curve over some `𝔽_q ⊂ k$), and the solvable specialisation morphism `sp^{res} :
π_1(Y_{K̄})^{res} → π_1(Y_k)^{res}$ is **bijective**. Then the curve `Y$ is **constant over `R$**.

*This result says:* under the equal-characteristic hypothesis (so that `R = k[[T]]$ and `\mathrm{Gal}(K̄/K)$ is
solvable), if the solvable étale fundamental group of the generic geometric fibre equals the solvable étale
fundamental group of the closed fibre (without dropping), then the curve `Y$ has no genuine generic-fibre variation —
it equals the constant family `Y_k \times_k R$ generically.

The **rigidity** interpretation: solvable potential good reduction (of every solvable cover of `Y_K$) forces the curve
to be constant. The original published source: **A. Tamagawa, "Resolution of nonsingularities of families of curves,"
*Duke Math. J.* **106** (2001), 121–144**. Recorded as the new appendix row
[`tamagawa-anabelian-curves`](appendix-black-boxes.md#tamagawa-anabelian-curves).

### What the theorem says — three paragraphs of gentle context

<!-- source: X.2.14 -->

**Paragraph 1 — concrete translation.** The condition `sp^{res}$ bijective means: every **finite solvable Galois
étale covering `X_K → Y_K$** of the generic fibre `Y_K$, after possibly replacing `R$ by its normalisation in a
finite extension of `K$, extends to a **finite étale covering of `Y$**. Equivalently: every finite solvable Galois
étale cover of the generic fibre has **potentially good reduction** — the cover's branch locus on `Y$ disappears after
some finite base change `R → R′$.

Translated this way, Tamagawa's theorem is a **rigidity** statement: **solvable potential good reduction of every
solvable cover of the generic fibre forces the curve to be constant.** The hypothesis "solvable" is essential — for
non-solvable covers, the analogous statement fails (there are families of curves with non-trivial monodromy on the
non-solvable part of `π_1$).

**Paragraph 2 — context.** In **mixed characteristic** (`R$ a complete DVR with `\mathrm{char}(K) = 0$,
`\mathrm{char}(k) = p$), the analogous statement is **false** in general: the specialisation drops (file 49, X.2.5
degenerate elliptic curves), even on the solvable quotient.

The **equal-characteristic** `p$ case is special because the Galois group `\mathrm{Gal}(K̄/K)$ is **solvable**. To see
this: `R = k[[T]]$ has fraction field `K = k((T))$, and `\mathrm{Gal}(K̄/K)$ is the absolute Galois group of a local
field of equal characteristic `p$. By the classical theory of local fields (Serre, *Local Fields* IV §1, recorded as
[`serre-local-fields-tameness`](appendix-black-boxes.md#serre-local-fields-tameness)), this Galois group is
**solvable** — a successive extension of the inertia subgroup `G_i$ (which is the absolute Galois group of the
algebraic closure of `k$ in `K̄$, trivial since `k$ is algebraically closed) by the **tame quotient** (cyclic of order
prime to `p$) and the **wild inertia** (pro-`p$, hence solvable in profinite-`p$-group sense).

So the solvable quotient `π_1(Y_{K̄})^{res}$ is exactly what is naturally controlled by the Galois action of
`\mathrm{Gal}(K̄/K)$; that is the natural place to look for rigidity in the equal-`p$ case.

**Paragraph 3 — modern references.** The result was unpublished when the SGA source was written (1961), and is
attributed to A. Tamagawa via a personal communication. It is now part of a larger story in **anabelian geometry**, the
study of "what fundamental-group data is enough to reconstruct a geometric object." The surrounding context is
surveyed in:

- **Nakamura, Tamagawa, Mochizuki**, "The Grothendieck Conjecture on Fundamental Groups of Algebraic Curves,"
  *Sugaku Expositions* **14** (2001), 31–53. The accessible survey of the Grothendieck conjecture and Tamagawa's
  contribution.
- **Szamuely, *Galois Groups and Fundamental Groups*** (Cambridge Studies in Adv. Math. **117**, CUP 2009), §6.7
  develops the precise statement and proof in the equal-`p$ case.
- **Cadoret, *Galois Categories*** §10–11 covers the prime-to-`p$ continuity story (file 51's X.3.8) which is
  Tamagawa's **prime-to-`p$ analogue** of the solvable theorem.

The **broader anabelian framework** — that hyperbolic curves over number fields and `p$-adic local fields are
determined up to isomorphism by their étale fundamental groups (plus outer Galois actions) — is **Grothendieck's
anabelian conjecture**, partially proved by Tamagawa and Mochizuki for various cases. The X.2.14 statement is one of
the earliest results in this direction.

> **Slogan.** *In the equal-characteristic `p$ case, the solvable étale fundamental group rigidifies smooth proper
> curves of genus `g ≥ 2$ over a complete DVR with finite residue field: if the solvable specialisation morphism is
> bijective, the curve is constant. This is a rigidity result in the anabelian style — a refinement of upper
> semicontinuity X.2.3 (file 49) into an isomorphism *if* the solvable parts already coincide.*

### Why "solvable" is the right quotient

<!-- source: X.2.14 -->

#### Aside (solvable quotients in anabelian geometry).

*Skip if anabelian geometry is not part of your current concern; the X.2.14 statement stands on its own.*

The deep reason "solvable" is the right quotient: in characteristic `p$, the **non-solvable** part of `π_1$ of a curve
varies wildly under specialisation (it includes the wild Artin–Schreier-type covers that file 48 X.1.10 displayed),
and there is no clean rigidity theorem for it. The **solvable** quotient is the part of `π_1$ that is "tame enough" to
admit anabelian reconstruction — informally, the part where Galois descent is well-behaved.

The choice "solvable" also matches the structural fact that `\mathrm{Gal}(K̄/K)$ for `K = k((T))$ is itself solvable.
So the natural action of the absolute Galois group on `π_1(Y_K̄)^{res}$ factors through a solvable group; Tamagawa's
theorem says this factorisation rigidifies the curve.

**Modern refinements** (Mochizuki and others, post-2001) extend the rigidity to **larger quotients** — e.g., the
**tame** quotient, the **`p$-tempered** quotient, the **`p$-adic Teichmüller** quotient. The full Grothendieck
anabelian conjecture asks for rigidity at the level of the *whole* `π_1$, with appropriate hypotheses; partial answers
are now known for hyperbolic curves over various base fields.

The X.2.14 result is the **gateway** to this entire framework; modern anabelian geometry is the long-form sequel.

______________________________________________________________________

## Closing pointer to file 51

This file gave the **transcendental method** for `π₁$ of a proper smooth curve (X.2.6) — the surface presentation
with `2g$ generators and one commutator relation, exact in characteristic 0 and an upper bound in characteristic `p$.
It gave the **topological finite generation theorem** (X.2.9) — `π_1$ of a proper connected scheme over an algebraically
closed field is topologically finitely generated, with Bertini + Zariski's connectedness as the engine of the
hyperplane-section induction. It gave the **Lang–Serre finiteness corollary** (X.2.12) — only finitely many
isomorphism classes of `G$-Galois étale covers for each finite `G$. It recorded the **Lefschetz forward-reference**
(X.2.13) to SGA 2 X.3.10. And it developed **A. Tamagawa's solvable specialisation theorem** (X.2.14) — a rigidity
statement closing §X.2 in the anabelian style.

File 51 closes Exposé X with the **continuity theorem** (X.3.8): for `f$ proper *smooth* with geometrically connected
fibres, the specialisation morphism is an isomorphism on prime-to-`p$ quotients of `π_1$. The proof requires two new
black boxes: **Zariski–Nagata purity of the branch locus** (stated as a general black box, proved inline in the dim-2
case via depth-`≥ 2` + freeness on a regular dim-2 local ring), and **Abhyankar's lemma** (proved in full along the
SGA lines). The continuity theorem gives — in characteristic 0 — a clean isomorphism `sp : π_1(X̄_{y_1})
\xrightarrow{\sim} π_1(X̄_{y_0})$, and — in characteristic `p$ — the prime-to-`p$ analogue. The closing corollary
(X.3.10) is the curve case: `π_1(X_0)^{(p)} = Γ^{(p)}$, where `Γ$ is the universal pro-(prime-to-`p$) surface group on
`2g$ generators with the commutator relation.
