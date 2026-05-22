# Rewritten Exposé XI, section XI.6 — Kummer and Artin–Schreier theories

<!-- source: XI.6 -->

## What this file is about

Two old constructions turn the previous file's machinery into a working calculator, one for each kind of prime. The
first, going back to Kummer, takes a function on a space that is nowhere zero and builds a cover of the space by
adjoining a fixed integer root of that function — the square root, the cube root, and so on. This works cleanly for
every prime except the one the underlying field knows about as its characteristic. The second construction, due to Artin
and Schreier, fills in exactly that missing prime, using a different and more delicate twist available only in prime
characteristic. Together the two constructions reach every prime.

Feeding each construction into the six-term machinery of the previous file turns it into an explicit calculation. The
Kummer side reads off most of the algebraic fundamental group of a compact algebraic object in terms of its lines — the
group of line bundles on the object, the Picard group. The Artin–Schreier side reads off the missing piece in terms of a
different but still classical invariant. A closing master formula due to Cartier unifies the two pictures into a single
statement: one formula that, fed the right input, recovers either side. Specialised back to abelian varieties, it
recovers the loop count from file 53.

File 55 set up the framework: principal homogeneous bundles in the fpqc sense (XI.4.1), the six-term cohomology exact
sequence (XI.4.5) attached to a short exact sequence of commutative $S$-groups, and the identifications
$H^{1}(S, \mathbb{G}_{m}) = \text{Pic}(S)$ and $H^{1}(S, \mathbb{G}_{a}) = H^{1}(S, \mathcal{O}_{S})$ (XI.5.3) reducing
fpqc $H^{1}$ for GL_n, 𝔾_m, 𝔾_a to classical Zariski cohomology.

This file (gentle Exposé XI §XI.6) feeds two specific exact sequences into that machine:

- The **Kummer exact sequence** $0 \to \mu_{n} \to \mathbb{G}_{m} \to \mathbb{G}_{m} \to 0$ ($n$-th power, $n$ prime to
  characteristic).
- The **Artin–Schreier exact sequence** $0 \to \mathbb{Z}/p\mathbb{Z} \to \mathbb{G}_{a} \to \mathbb{G}_{a} \to 0$ (in
  characteristic $p$, via $wp = id - F$).

The outputs are six-term sequences linking the *finite group* on the left ($\mu_{n}$, $\mathbb{Z}/p\mathbb{Z}$) to the
*continuous group* on the right ($\mathbb{G}_{m}$, $\mathbb{G}_{a}$) and from there to the Picard group /
structure-sheaf cohomology via XI.5.3. The result is a powerful computational tool for $\pi^{ab}_{1}(S)$ of proper
schemes via the Picard scheme.

The culminating remark §XI.6.5 develops the **Cartier-duality master formula**:

```text
H^1(S, G) \cong \text{Hom}_{k\text{-grp}}(D(G), \text{Pic}_{S/k})
```

for $S$ proper over algebraically closed $k$, $G$ a finite commutative $k$-group scheme, and $D(G)$ its Cartier dual.
This formula simultaneously generalises Kummer (specialising to $G = \mu_{n}$ gives
$H^{1}(S, \mu_{n}) = \text{Pic}(S)[n]$) and Artin–Schreier (specialising to $G = \mathbb{Z}/p\mathbb{Z}$ gives
$H^{1}(S, \mathbb{Z}/p\mathbb{Z})$ in terms of $H^{1}(S, \mathcal{O}_{S})^{F}$), and ties back to the **true fundamental
group** of an abelian variety (file 53, §XI.2.5): the abelianisation of $\pi^{N}_{1}(A, 0)$ is
$T\cdot(\text{Pic}_{A/k}) = T\cdot(A^{\vee}) = T\cdot(A)$ (using biduality), exactly the Tate-module computation of
XI.2.4.

The lesson: **Kummer and Artin–Schreier are the two universal computational tools for $\pi^{ab}_{1}$ of proper
schemes**, and the Cartier-duality master formula is the universal statement that unifies them.

______________________________________________________________________

## §XI.6.0 — Bridge: why Kummer and Artin–Schreier

<!-- source: XI.6 -->

Recall the setup. For $S$ a proper scheme over an algebraically closed field $k$, we want to understand the
abelianisation $\pi^{ab}_{1}(S)$. By the universal property of the abelianisation:

```text
H^1(S, ℤ/nℤ) = \text{Hom}_{\text{cont}}(π_1^{ab}(S), ℤ/nℤ).
```

So computing $H^{1}(S, \mathbb{Z}/n\mathbb{Z})$ for all $n$ (in fact for all finite commutative $G$) is equivalent to
computing $\pi^{ab}_{1}(S)$. The Kummer and Artin–Schreier theories give two computational windows on this:

- **Kummer** (any characteristic, $n$ prime to char): $H^{1}(S, \mu_{n})$ is computed via the Picard group
  $\text{Pic}(S)$, with $\mu_{n} \simeq \mathbb{Z}/n\mathbb{Z}$ (canonically once an $n$-th root of unity is chosen).
  So: `H¹(S, ℤ/nℤ) \simeq \text{Pic}(S)[n]` for $n$ prime to char $k$. This is the famous identification.
- **Artin–Schreier** (characteristic $p$): $H^{1}(S, \mathbb{Z}/p\mathbb{Z})$ is computed via
  $H^{1}(S, \mathcal{O}_{S})^{F}$, the Frobenius-invariant subspace of the structure-sheaf cohomology. So:
  $H^{1}(S, \mathbb{Z}/p\mathbb{Z}) \simeq H^{1}(S, \mathcal{O}_{S})^{F}$ for $S$ proper over algebraically closed $k$
  of char $p$.

Together, these compute the *prime-to-$p$ part* and the *$p$-part* (étale) of $\pi^{ab}_{1}(S)$. The Cartier-duality
master formula §XI.6.5 generalises both to arbitrary finite commutative $G$.

______________________________________________________________________

## §XI.6.1 — The Kummer exact sequence

<!-- source: XI.6.1 -->

### Proposition XI.6.1 — μ_n is finite locally free; Kummer exact sequence

<!-- source: XI.6.1 -->

**Proposition XI.6.1.** Let $S$ be a prescheme and $n > 0$ an integer. Let

```text
u_n : 𝔾_{m, S} \to 𝔾_{m, S}
```

be the $n$-th power homomorphism, and let $\mu_{n, S} := \ker(u_{n})$.

(a) `μ_{n, S} \cong \text{Spec } \mathcal{O}_S[t]/(t^n - 1)`. In particular, $\mu_{n, S}$ is **finite locally free** of
rank $n$ over $S$.

(b) $\mu_{n, S}$ is **étale** over $S$ iff $n$ is invertible in every $\mathcal{O}_{S, s}$ for $s \in S$ — equivalently,
the residue characteristics of $S$ are all coprime to $n$.

(c) The sequence of homomorphisms of $S$-groups

```text
0 \to μ_{n, S} \to 𝔾_{m, S} \xrightarrow{u_n} 𝔾_{m, S} \to 0
```

is **exact** in the sense of XI.4 (file 55). This is the **Kummer exact sequence** of rank $n$ over $S$.

*This result says:* $\mu_{n}$ is a finite locally-free group scheme that fits into the universal exact sequence
expressing "raising to the $n$-th power on $\mathbb{G}_{m}$" as a surjection with kernel $\mu_{n}$. The étaleness is
exactly when $n$ is invertible.

**Proof of (a).** Write `𝔾_{m, S} = \text{Spec } \mathcal{O}_S[t, t^{-1}]`. The morphism $u_{n}$ corresponds to the ring
homomorphism $\mathcal{O}_{S}[t, t^{-1}] \to \mathcal{O}_{S}[t, t^{-1}]$ sending $t \mapsto t^{n}$. The **unit section**
of $\mathbb{G}_{m, S}$ corresponds to the augmentation $\mathcal{O}_{S}[t, t^{-1}] \to \mathcal{O}_{S}$, $t \mapsto 1$,
which has kernel $(t - 1)$. Pulling this kernel back along $u_{n}$ gives \`(t^n - 1) \\subset \\mathcal{O}\_S[t,
t^{-1}]$. Hence

```text
\mu_{n, S} = \text{Spec}\, \mathcal{O}_S[t, t^{-1}] / (t^n - 1) \cong \text{Spec}\, \mathcal{O}_S[t] / (t^n - 1),
```

where the last identification is because $t^{n} - 1 = 0$ already determines $t$ to be a unit (with $t^{-1} = t^{n-1}$).
Hence `\mu_{n, S}$ is the spectrum of a free`\\mathcal{O}\_S$-algebra of rank $n$, with basis
$1, t, t^{2}, \ldots, t^{n-1}$. ✓

**Proof of (b).** The reduced fibre over $s \in S$ is
`\kappa(s)[t]/(t^n - 1)$. This algebra is **étale** over`\\kappa(s)`iff`t^n -
1$is **separable** in$\\kappa(s)[t]`— i.e., has no repeated roots in an algebraic closure. The roots of`t^n - 1$ in an
algebraic closure of `\kappa(s)$ are the `n`-th roots of unity; these are distinct iff `n \neq 0` in
`\kappa(s)`, i.e., iff `\text{char}(\kappa(s))` is coprime to `n`. ✓

**Proof of (c).** We must verify that the Kummer sequence is exact in the XI.4 sense (file 55, §XI.4.4): the composite
$\mu_{n} \hookrightarrow \mathbb{G}_{m} \to \mathbb{G}_{m}$ is zero (immediate: $u_{n}$ annihilates the kernel), and the
morphism $u_{n} : \mathbb{G}_{m} \to \mathbb{G}_{m}$ is a **principal$\\mu_n\`-bundle\*\* (XI.4.1, file 55).

By XI.4.2 (file 55), this reduces to checking that
`u_n$ is **faithfully flat quasi-compact**. We check faithful flatness on affines: pull back to an affine`\\text{Spec}(A)
= U \\subset S$, so `𝔾_{m, A} = \text{Spec}(A[t,
t^{-1}])$. We need: `u_n^* : A[t, t^{-1}] \to A[t, t^{-1}]$, sending$t \\mapsto t^{n}$, makes$A[t, t^{-1}]$ a **free**
module of rank $n$ over $A[s, s^{-1}]$ where$s = t^n$. The basis `1, t, t^2, \ldots, t^{n-1}$ does the trick (linear
independence is by degrees modulo \`n$, and span is by Euclidean division of exponents). ✓

> **Slogan.** *The Kummer sequence $0 \to \mu_{n} \to \mathbb{G}_{m} \to \mathbb{G}_{m} \to 0$ is the cleanest non-trivial fpqc exact sequence of
> commutative $S$-groups.*

______________________________________________________________________

## §XI.6.2 — Kummer covering. $\mu_{n}$ versus $\mathbb{Z}/n\mathbb{Z}$

<!-- source: XI.6.2 -->

### Definition XI.6.2 — Kummer covering of rank $n$

<!-- source: XI.6.2 -->

**Definition.** A **Kummer covering of rank $n$ over $S$** is a principal homogeneous bundle (XI.4.1, file 55) over $S$
whose structure group is `\mu_{n, S}$. The set of these is`H^1(S, \\mu_n)\`.

Note: when `\mu_{n, S}$ is étale (i.e.,`n$ is invertible on $S$), the Kummer cover is even an étale principal
covering in the V.2.7 sense (file 30) — Kummer covers are *generalised principal coverings*, étale exactly when
`\mu_n$ is.

### Corollary XI.6.3 — $\mu_{n} \simeq \mathbb{Z}/n\mathbb{Z}$ iff $n$ is invertible + roots of unity

<!-- source: XI.6.3 -->

**Corollary XI.6.3.** Suppose $\mu_{n, S}$ is \acute{e}tale over$S$. Then there is a one-to-one correspondence between:

(a) Group-scheme isomorphisms `(\mathbb{Z}/n\mathbb{Z})_S \xrightarrow{\sim} \mu_{n, S}`;

(b) Sections of $\mathcal{O}^{*}_{S}$ that are of **exact order $n$** on every connected component of $S$.

In particular, `\mu_{n, S} \cong (\mathbb{Z}/n\mathbb{Z})_S` *as $S$-groups* iff
`n$ is invertible in every`\\mathcal{O}\_{S, s}$ AND `S$ admits a section of
`\mathcal{O}_S^*$ of exact order$n$on each component (called a **primitive$n$-th root of unity over`S\`\*\*).

*This result says:* the classical Kummer theory hypothesis (the base field contains primitive $n$-th roots of unity) is
exactly what is needed for
`\mu_n$ to *look like* the constant group`\\mathbb{Z}/n\\mathbb{Z}`. Working directly with`\\mu_n$, we **avoid this
hypothesis**.

**Proof.** A group-scheme morphism `\phi : (\mathbb{Z}/n\mathbb{Z})_S \to \mu_{n, S}$ is determined by`\\phi(1)$,
a section of $\mu_{n, S}$ whose$n`-th power is the identity — i.e., an element of
`\mathcal{O}_S^*$ of order dividing$n$. The morphism`\\phi$ is an **isomorphism** iff `\phi(1)$ has exact order $n$ (so
that the kernel is trivial and the image is all of \`\\mu_n$). ✓

> **Slogan.** *$\mu_{n}$ is the right$n$-th-roots-of-unity group; `ℤ/nℤ$ is a contingent identification.* The gentle SGA
> works with \`μ_n$ directly.

______________________________________________________________________

## §XI.6.3 — The Kummer–Picard six-term sequence (XI.6.4–XI.6.6)

<!-- source: XI.6.4 -->

### Proposition XI.6.4 — six-term Kummer–Picard sequence

<!-- source: XI.6.4 -->

**Proposition XI.6.4.** Let $S$ be a prescheme. Applying the XI.4.5 six-term exact sequence (file 55) to the Kummer
exact sequence (XI.6.1) and using XI.5.3 (file 55) to identify $H^{i}(S, \mathbb{G}_{m}) = \text{Pic}^{?}(S)$, we obtain the canonical
exact sequence:

```text
0 \to H^0(S, \mu_n) \to H^0(S, 𝒪_S^*) \xrightarrow{(\cdot)^n} H^0(S, 𝒪_S^*) \to H^1(S, \mu_n)
   \to \text{Pic}(S) \xrightarrow{(\cdot)^n} \text{Pic}(S),
```

where the $(\cdot)^{n}$ maps are "raising to the $n$-th power" on units and on line bundles. Equivalently, with
$A = H^{0}(S, \mathcal{O}_{S})$, `\text{Pic}(S)_n = \ker(\cdot^n : \text{Pic}(S) \to \text{Pic}(S)) = $ "`n`-torsion in`\\text{Pic}$",
and $A^{*}/(A^{*})^{n} = $ "units modulo$n`-th powers", we get the **short exact sequence**:

```text
0 \to A^* / (A^*)^n \to H^1(S, \mu_n) \to \text{Pic}(S)_n \to 0.
```

*This result says:* a Kummer covering of $S$ is determined, up to its image in
`\text{Pic}(S)_n$, by a unit-mod-`n`-th-power class. The Kummer-Picard sequence is the universal computation of`\\mu_n$-covers.

**Proof.** The XI.4.5 six-term sequence for \`0 → \\mu_n → 𝔾_m → 𝔾_m → 0$ reads:

```text
0 \to H^0(S, \mu_n) \to H^0(S, 𝔾_m) \to H^0(S, 𝔾_m) \to H^1(S, \mu_n) \to H^1(S, 𝔾_m) \to H^1(S, 𝔾_m).
```

Identify $H^{0}(S, \mathbb{G}_{m}) = H^{0}(S, \mathcal{O}^{*}_{S})$ and$H^1(S, 𝔾_m) = \\text{Pic}(S)$ via XI.5.3 (file
55). The maps between copies of $H^{0}$ and$H^1$ are induced by the`n$-th-power homomorphism on `𝔾_m$, which on
$\mathcal{O}^{*}_{S}$ and on$\\text{Pic}(S)$ is "raise to the `n$-th power". Reading the cokernel and kernel structures
gives the displayed short exact sequence. ✓

### Corollary XI.6.5 — case $\operatorname{Pic}(S)_{n} = 0$ (e.g., local or factorial $S$)

<!-- source: XI.6.5 -->

**Corollary XI.6.5.** If `\text{Pic}(S)_n = 0$ — for example, when`S$ is the spectrum of a local ring or of a
factorial (UFD) ring — and `A = H^0(S, 𝒪_S)$, then

```text
H^1(S, \mu_n) \cong A^* / (A^*)^n.
```

*This result says:* in the "no Picard torsion" case, Kummer covers are classified by $n$-th-power units modulo \`n$-th
powers of units. This is the **classical Kummer theory**.

### Corollary XI.6.6 — case $A$ an $n$-th-power-saturated ring (e.g., `S$ proper over`k̄$)

<!-- source: XI.6.6 -->

**Corollary XI.6.6.** Suppose every element of $H^{0}(S, \mathcal{O}_{S})$ is an$n$-th power — for example, when `H^0(S,
𝒪_S) $ is a composite of algebraically closed fields, OR when `S$ is reduced proper over an algebraically closed
field`k$ (so `H^0(S, 𝒪_S) = k$ and `n$-th powers cover`k\`). Then

```text
H^1(S, \mu_n) \cong \text{Pic}(S)_n.
```

*This result says:* in the "saturated rings" case, Kummer covers are classified by the **$n$-torsion in the Picard
group**. This is the form most commonly used in algebraic geometry — the bridge between étale $\pi^{ab}_{1}$ and Picard
schemes.

#### Application: $\pi^{ab}_{1}(S)$ from \`Pic(S)$.

For `S$ proper connected over algebraically closed`k$, `n$ prime to \`\\text{char}(k)$:

```text
\text{Hom}(π_1(S), \mathbb{Z}/n\mathbb{Z}) = H^1(S, \mathbb{Z}/n\mathbb{Z}) = H^1(S, \mu_n) \cong \text{Pic}(S)_n
   = P(k)_n
```

(using `\mu_n \cong \mathbb{Z}/n\mathbb{Z}$ since`k$ is algebraically closed and contains primitive `n$-th roots of
unity), where `P = \text{Pic}_{S/k}$ is the **Picard scheme** of`S/k$ (appendix
[`pic-scheme-fga`](appendix-black-boxes.md#pic-scheme-fga)).

If the connected component $P^{0}$ of$P$ is a **proper** group scheme of dimension `g$ (e.g., when
`S$ is smooth projective), then by general structure theory of group schemes,`P^0$ is an **abelian variety**, and by
XI.2.4 (file 53):

```text
T_\ell(P^0) \cong (\pi_1(P^0))_{\ell} \cong \mathbb{Z}_\ell^{2g} \quad (\text{for } \ell \neq \text{char}(k)).
```

Combined with the Néron–Severi torsion finiteness (a separate input from arithmetic geometry: the Néron–Severi group
\`\\text{NS}(S) = \\text{Pic}(S) / P^0(k)$ is a finitely generated abelian group, so its torsion is finite), this gives:

> The $\ell$-primary component of $\pi^{ab}_{1}(S)$ for $\ell$ prime to$\\text{char}(k)$ is a module of finite type and
> rank `2g$ over `\mathbb{Z}_\ell$. It is **free** of rank`2g$ for all but finitely many `\ell$.

This is the famous result, used throughout arithmetic geometry, that the prime-to-`p$ part of`π_1^{ab}(S)$ of a smooth
projective variety is **controlled by the dimension of its Picard scheme**.

#### Application: Serre's semicontinuity argument.

As Serre observed (and as the SGA source notes): when
`X → S$ is flat and projective with the Picard scheme`\\text{Pic}\_{X/S}$ existing and its connected component proper (e.g., when the geometric fibres of `X → S$
are normal — sufficient by Mumford TIFR), then the Picard schemes of the fibres of
`X / S$ have **the same dimension**, i.e., the integer`g(s) = \\dim P^0_s$ is **locally constant** on `S$. The argument
uses **X.2.3** (semicontinuity, file 49) plus the Kummer–Picard sequence:
$H^{1}(X_{s}, \mu_{n})$ is constant in$s$ by X.2.3 (for `n$ prime to
`\text{char} $), hence`\\text{Pic}^0(X_s)\_n$ is constant in `s$, hence \`g(s)$ is constant.

> **Slogan.** *Kummer + Picard + X.2.3 + Néron–Severi torsion finiteness = control on the $\ell$-primary \`π_1^{ab}$ of
> any proper smooth family.*

______________________________________________________________________

## §XI.6.4 — Artin–Schreier sequence

<!-- source: XI.6.7 -->

We now move to characteristic `p > 0$. Recall:`S$ is a prescheme of **characteristic $p$**, i.e., $p \cdot
\mathcal{O}_{S} = 0$. In this setting, the `p$-th-power homomorphism on \`\\mathcal{O}\_S$ is **additive**:

```text
(a + b)^p = a^p + b^p \quad \text{(in char } p\text{)}.
```

So $t \mapsto t^{p}$ on$\\mathbb{G}\_{a, S} = \\text{Spec } \\mathcal{O}\_S[t]$ is a **group homomorphism**, called the
**Frobenius homomorphism**:

```text
F : \mathbb{G}_{a, S} \to \mathbb{G}_{a, S}.
```

Set

```text
w_p := \text{id} - F : \mathbb{G}_{a, S} \to \mathbb{G}_{a, S}.
```

This is the **Artin–Schreier endomorphism** of $\mathbb{G}_{a}$ in characteristic$p\`.

The constant group scheme `(\mathbb{Z}/p\mathbb{Z})_S$ embeds into`\\mathbb{G}\_{a, S}$ via the section of order
`p$:

```text
i : (\mathbb{Z}/p\mathbb{Z})_S \hookrightarrow \mathbb{G}_{a, S}, \qquad 1 \mod p \mapsto 1 \in \mathbb{G}_a.
```

### Proposition XI.6.7 — Artin–Schreier exact sequence

<!-- source: XI.6.7 -->

**Proposition XI.6.7.** Let `S$ be a prescheme of characteristic`p > 0$. The sequence

```text
0 \to (\mathbb{Z}/p\mathbb{Z})_S \xrightarrow{i} \mathbb{G}_{a, S} \xrightarrow{w_p} \mathbb{G}_{a, S} \to 0
```

is **exact** in the sense of XI.4 (file 55). This is the **Artin–Schreier exact sequence** over \`S$.

*This result says:* the Artin–Schreier sequence is the additive
(characteristic-`p$) analogue of the Kummer sequence — with`(\\mathbb{Z}/p\\mathbb{Z})_S$ replacing $\mu_{n}$,$\mathbb{G}_{a, S}$
replacing$\\mathbb{G}_{m, S}$, and$w_p = \text{id} - F$ replacing $t \mapsto t^{n}$.

**Proof.** It is enough to check exactness over the prime field
`k = \mathbb{F}_p$ (the general case follows by base change, since the sequence is constructed by base change from`\\mathbb{F}\_p$).
We must verify:

(i) `\ker(w_p) = (\mathbb{Z}/p\mathbb{Z})_S$ — sections`f$ of $\mathbb{G}_{a}$ satisfying$f^p = f$, i.e.,`f$ is a fixed
point of Frobenius. Over `\mathbb{F}_p$, this is exactly
`\mathbb{F}_p$ itself (by Fermat's little theorem), giving the constant group scheme`(\\mathbb{Z}/p\\mathbb{Z})\_S$. ✓

(ii)
`w_p : \mathbb{G}_a \to \mathbb{G}_a$ is **faithfully flat quasi-compact**. We check on the affine ring level:`w_p^\* :
k[t] \\to k[t]$, $t \mapsto t - t^{p}$, makes$k[t]$ a **free module of rank`p$** over `k[s]$ where $s = t - t^{p}$. The
basis is `1, t, t^2, \ldots, t^{p-1}$ — by Euclidean division on degrees modulo`p$. ✓

(iii) The morphism `w_p$ together with the kernel embedding`i$ makes `\mathbb{G}_a$ into a principal homogeneous bundle
over `\mathbb{G}_a$ under`(\\mathbb{Z}/p\\mathbb{Z})\_S$. This follows from (i) and (ii) by XI.4.2 (file 55). ✓

Hence the sequence is exact in the XI.4 sense. ∎

> **Slogan.** \*Artin–Schreier is the additive characteristic-`p$ analogue of Kummer.*`wp = id − F$ kills exactly
> `\mathbb{F}_p \subset \mathbb{G}_a$.

### Proposition XI.6.8 — six-term Artin–Schreier sequence

<!-- source: XI.6.8 -->

**Proposition XI.6.8.** With \`A = H^0(S, \\mathcal{O}\_S)$, the XI.4.5 six-term exact sequence (file 55) applied to the
Artin–Schreier exact sequence and combined with XI.5.3 (file 55) reads:

```text
0 \to H^0(S, \mathbb{Z}/p\mathbb{Z}) \to A \xrightarrow{w_p} A \to H^1(S, \mathbb{Z}/p\mathbb{Z})
   \to H^1(S, \mathcal{O}_S) \xrightarrow{w_p} H^1(S, \mathcal{O}_S).
```

Reducing:

```text
0 \to A / w_p(A) \to H^1(S, \mathbb{Z}/p\mathbb{Z}) \to H^1(S, \mathcal{O}_S)^F \to 0,
```

where the \*\*superscript `F$** denotes the **Frobenius-invariant subspace** of`H^1(S, \\mathcal{O}\_S)$ (i.e., the
kernel of $w_{p} = \text{id} - F$ on$H^1(S, \mathcal{O}_S)$, equivalently the eigenspace of`F$ with eigenvalue `1$).

*This result says:* a class in `H^1(S, \mathbb{Z}/p\mathbb{Z})$ is determined up to an`A/wp(A)$-class by an
`F$-invariant class in \`H^1(S, \\mathcal{O}\_S)$. This is **Artin–Schreier theory**.

### Corollary XI.6.9 — classical Artin–Schreier ($S$ affine)

<!-- source: XI.6.9 -->

**Corollary XI.6.9.** Suppose `H^1(S, \mathcal{O}_S)^F = 0$ — for example, when`S$ is an **affine** scheme (so
$H^{1}(S, \mathcal{O}_{S}) = 0$ by `serre-affine-vanishing`, file 17). Then:

```text
H^1(S, \mathbb{Z}/p\mathbb{Z}) \cong A / w_p(A) \quad \text{where } A = H^0(S, \mathcal{O}_S).
```

*This is **Artin–Schreier theory in its classical form**:* an
`\mathbb{F}_p$-torsor over an affine scheme is determined by a class`[a]$ modulo `a - a^p$.

### Corollary XI.6.10 — `S$ proper over alg-closed`k$

<!-- source: XI.6.10 -->

**Corollary XI.6.10.** Suppose `w_p(A) = A$ — for example, when`A$ is a composite of algebraically closed fields, OR
`S$ is **proper** over an algebraically closed field `k$ (so`A = k$ and `w_p$ is surjective on `k$ because the map`k
\\to k$, `a \mapsto a - a^p$, has cokernel a finite-dimensional `\mathbb{F}_p$-vector space — in fact trivial since`k$
is algebraically closed). Then:

```text
H^1(S, \mathbb{Z}/p\mathbb{Z}) \cong H^1(S, \mathcal{O}_S)^F.
```

*This is the form most useful in algebraic geometry over an algebraically closed field of characteristic $p$:* the
`p$-torsion of`\\pi_1^{ab}(S)$ is the Frobenius-invariant subspace of `H^1(S, \mathcal{O}_S)$.

#### Application: $p$-part of `π₁^{ab}$ for a proper smooth`S$.

For `S$ proper smooth connected over algebraically closed`k$ of characteristic `p$:

```text
\text{Hom}(π_1(S), \mathbb{Z}/p\mathbb{Z}) = H^1(S, \mathbb{Z}/p\mathbb{Z}) = H^1(S, \mathcal{O}_S)^F.
```

The Frobenius-invariant subspace of
`H^1(S, \mathcal{O}_S) = $ "first coherent cohomology of structure sheaf" is a finite-dimensional`\\mathbb{F}\_p$-vector
space. Hence the **`p$-torsion of \`\\pi_1^{ab}(S)$\*\* is finite.

Iterating with `\mathbb{Z}/p^n\mathbb{Z}$ in place of`\\mathbb{Z}/p\\mathbb{Z}$ (using the Witt-group scheme `W_n$ in
place of \`\\mathbb{G}\_a$ — see Remark XI.6.11), one gets:

```text
H^1(S, \mathbb{Z}/p^n\mathbb{Z}) = H^1(S, W_n)^F = (\text{Frobenius-invariant Witt cohomology}).
```

The `p$-primary`\\pi_1^{ab}(S)$ is then `\lim_n H^1(S, \mathbb{Z}/p^n\mathbb{Z})$, which is *not* always finitely
generated — the `p$-power growth can be unbounded. This contrasts sharply with the prime-to-`p$ case (Kummer + Picard)
where finite generation is automatic.

> **Slogan.** \*Artin–Schreier: the `p$-part of`\\pi_1^{ab}$ in char `p$ is the Frobenius-invariant subspace of
> `H^1(S, \mathcal{O}_S)$.* For proper smooth`S$, this is finite-dimensional but can grow unboundedly with `n$.

______________________________________________________________________

## §XI.6.5 — Remark XI.6.11: Cartier duality and the true $\pi_{1}$

<!-- source: XI.6.11 -->

### The Cartier-duality master formula

<!-- source: XI.6.11 -->

One formula classifies every principal bundle with finite commutative structure group on a proper scheme. The right-hand
side is the group of homomorphisms from the Cartier dual into the Picard scheme; the left-hand side is the first
cohomology of the group itself. Kummer is the case $G = \mu_{n}$; Artin–Schreier is the case
$G = \mathbb{Z}/p\mathbb{Z}$.

**Theorem XI.6.11 (Cartier–Grothendieck master formula).** Let `S$ be a proper scheme over algebraically closed`k$ with
`H^0(S, \mathcal{O}_S) = k$, and let `G$ be a **finite commutative group scheme** over`k$. Let `D(G) :=
\text{SheafHom}_{k\text{-grp}}(G, \mathbb{G}_m)$ be the **Cartier dual** of
`G$ (appendix [`cartier-duality\`\](appendix-black-boxes.md#cartier-duality)). Then there is a canonical isomorphism

```text
H^1(S, G) \cong \text{Hom}_{k\text{-grp}}(D(G), \text{Pic}_{S/k}),
```

functorial in `G$ and`S$, where `\text{Pic}_{S/k}$ is the **Picard scheme** of \`S/k$.

*This result says:* principal `G$-bundles over`S$ are classified by group-scheme homomorphisms from the Cartier dual
`D(G)$ into the Picard scheme. This is the **universal Kummer–Artin–Schreier–\`\\alpha_p$ formula**.

#### Specialisation 1 — Kummer ($G = \mu_{n}$).

The Cartier dual of $\mu_{n}$ is$D(\\mu_n) = (\\mathbb{Z}/n\\mathbb{Z})$ (Cartier-self-duality). The master formula
gives:

```text
H^1(S, \mu_n) \cong \text{Hom}_{k\text{-grp}}((\mathbb{Z}/n\mathbb{Z}), \text{Pic}_{S/k}) = \text{Pic}_{S/k}(k)[n]
   = \text{Pic}(S)[n],
```

recovering **XI.6.6** (file 56).

#### Specialisation 2 — Artin–Schreier ($G = \mathbb{Z}/p\mathbb{Z}$).

The Cartier dual of $(\mathbb{Z}/p\mathbb{Z})$ is$D((\\mathbb{Z}/p\\mathbb{Z})) = \\mu_p$ in characteristic `p$. In char
`p$, the group`\\mu_p$ is **infinitesimal** (its connected component is non-trivial: as a Hopf
algebra, `\mu_p = k[t]/(t^p - 1) = k[t]/(t-1)^p$, so \`\\mu_p^0 = \\mu_p$, all infinitesimal). The master formula gives:

```text
H^1(S, \mathbb{Z}/p\mathbb{Z}) \cong \text{Hom}_{k\text{-grp}}(\mu_p, \text{Pic}_{S/k}).
```

The right-hand side decomposes via the connected-component / étale-quotient sequence of
`\text{Pic}_{S/k}$. Recall that`\\text{Pic}\_{S/k}$ fits into

```text
0 \to \text{Pic}^0_{S/k} \to \text{Pic}_{S/k} \to \text{NS}(S/k) \to 0,
```

where `\text{NS}(S/k)$ is the Néron–Severi group (étale, finitely generated). Homomorphisms`\\mu_p \\to
\\text{Pic}\_{S/k}$ factor through the connected component `\text{Pic}^0_{S/k}$ (since \`\\mu_p$ is infinitesimal and
the NS quotient is étale), so:

```text
H^1(S, \mathbb{Z}/p\mathbb{Z}) \cong \text{Hom}_{k\text{-grp}}(\mu_p, \text{Pic}^0_{S/k}) = \text{Pic}^0_{S/k}[p]^{\mu_p},
```

which is exactly the \*\*`p$-torsion of the Picard scheme paired with`\\mu_p$** — and via XI.6.10 above, this is `H^1(S,
\mathcal{O}_S)^F$. The master formula thus **recovers XI.6.10** as the Cartier-dual specialisation.

#### Specialisation 3 — the infinitesimal group \`α_p$.

In characteristic `p$, the **kernel of Frobenius**`\\alpha_p := \\ker(F : \\mathbb{G}\_a \\to \\mathbb{G}\_a)$ is a
non-étale finite locally-free group scheme of order `p$, with `D(\alpha_p) = \alpha_p$ (self-dual). The exact sequence`0
\\to \\alpha_p \\to \\mathbb{G}\_a \\xrightarrow{F} \\mathbb{G}\_a \\to 0$ feeds into XI.4.5:

```text
H^1(S, \alpha_p) \cong \ker(F : H^1(S, \mathcal{O}_S) \to H^1(S, \mathcal{O}_S)).
```

Iterating with \`\\alpha\_{p^n} = \\ker(F^n)$:

```text
H^1(S, \alpha_{p^n}) \cong \ker(F^n : H^1(S, \mathcal{O}_S) \to H^1(S, \mathcal{O}_S)).
```

The master formula recovers this via `D(\alpha_p) = \alpha_p$ and the corresponding pairing with`\\text{Pic}^0[p]$.

#### Tie to the true fundamental group of file 53 §XI.2.5.

Recall (file 53, §XI.2.5) that the **Nori fundamental group scheme** $\pi^{N}_{1}(S, s)$ classifies principal$G$-bundles
for `G$ an arbitrary finite (possibly non-étale) commutative
`k$-group scheme. Its **abelianisation** is the maximal abelian quotient — call it`\\pi_1^{N, ab}(S, s)$.

By the master formula, \`\\pi_1^{N, ab}(S, s)$ is **dual** to the Picard scheme in the following precise sense:

```text
\pi_1^{N, ab}(S, s) = \lim_{P_i \subset \text{Pic}_{S/k} \text{ finite alg subgroup}} D(P_i)
                   = T_\cdot(\text{Pic}_{S/k}),
```

where \`T\_\\cdot$ denotes the "true Tate module" of the Picard scheme (the inverse limit of duals of finite algebraic
subgroups).

#### Abelian variety case: biduality recovers XI.2.1.

For `S = A$ an **abelian variety** of dimension`g$ over algebraically closed `k$, the Picard scheme is
\`\\text{Pic}\_{A/k} = A^\\vee$, the **dual abelian variety**. The master formula reads:

```text
H^1(A, G) = \text{Ext}^1(A, G) \cong \text{Hom}(D(G), A^\vee).
```

This is the **biduality formula** for abelian varieties (Mumford TIFR Ch. III; appendix
[`mumford-abelian-varieties`](appendix-black-boxes.md#mumford-abelian-varieties)). It generalises Serre's primitive-
elements theorem XI.2.1 (file 53, §XI.2.1).

The **true Tate module** of \`A$:

```text
T_\cdot(A) = \pi_1^{N, ab}(A, 0) = \lim_n {_nA} = T_\cdot(A^\vee) \quad (\text{by biduality } A^{\vee\vee} = A),
```

recovers exactly the file-53 §XI.2.6 identification: the abelianisation of
`\pi_1^N(A)$ is the inverse limit of multiplication-by-`n$ kernels of `A$ as **flat** group schemes, not just étale.

> **Slogan.** *Cartier duality + Picard scheme = the universal formula for principal
> `G$-bundles on a proper scheme`S$ over `k̄$.* The formula unifies Kummer, Artin–Schreier, \`\\alpha_p$, and
> abelian-variety biduality.

______________________________________________________________________

## §XI.6.6 — Closing pointers

<!-- source: XI.6 -->

The Cartier-duality master formula is the natural endpoint of Exposé XI's classical computational arc. It sits at the
bridge between **finite-group-scheme cohomology** (Exposé XI's framework) and **étale cohomology of $\ell$-adic
sheaves** (the SGA 4 framework). The natural next steps:

- **SGA 4 (étale topology and derived $H^{i}_{et}$).** The XI.4.5 six-term sequence extends to the full long exact
  sequence of derived étale cohomology $H^{i}(S, G) \to H^{i}(S, G') \to H^{i}(S, G/G') \to H^{i+1}(\ldots)$ for$G$
  abelian. The Kummer and Artin–Schreier sequences appear there as the universal source of $\ell$-adic and $p$-adic
  étale cohomology, respectively.

- **SGA 7 (vanishing cycles, monodromy filtration).** The monodromy filtration of $\ell$-adic sheaves uses the
  Kummer–Picard pairing as a key input in dim \`1$.

- **Gentle Exposés XII–XIII.** These remain as future gentle passes. XII is the GAGA / analytic-comparison theorem
    `π_1^{et}(X/\mathbb{C}) \cong \pi_1^{top}(X^{an})^{\widehat{}}$ for`X$ proper over `\mathbb{C}$ — the formal
    underpinning of the X.2.6 transcendental method (file 50, X.2.6). XIII is the proper cohomological base-change
    theorem `R^i f_*(\mathcal{F})$ for`\\mathcal{F}$ an étale sheaf, the universal foundation for the higher-`H^i$
    framework of SGA 4 V.

#### Closing remarks on what file 56 has accomplished.

We fed the Kummer exact sequence (XI.6.1) into the XI.4.5 six-term machine and read off:

- The **Kummer–Picard sequence** (XI.6.4), with two limit cases — classical Kummer over local/factorial bases (XI.6.5)
  and Picard-torsion over algebraically closed bases (XI.6.6).

We fed the Artin–Schreier exact sequence (XI.6.7) into the same machine and read off:

- The **Artin–Schreier sequence** (XI.6.8), with two limit cases — classical Artin–Schreier over affines (XI.6.9) and
  Frobenius-invariants over proper algebraically closed bases (XI.6.10).

We then unified both via the **Cartier-duality master formula** (XI.6.11), which generalises to any finite commutative
`k$-group scheme`G$ and ties back to the **abelianisation of the Nori fundamental group** of file 53, §XI.2.5.

The gentle SGA's Exposé XI is now complete in this five-file pass (files 52–56). Exposés XII and XIII remain as future
gentle passes.

> **Final slogan.** \*Kummer + Artin–Schreier + Cartier duality + Picard scheme = the classical computational framework
> for `\pi_1^{ab}$ of a proper scheme.* In characteristic 0 (or away from`p$), the Picard scheme
> controls everything via Kummer. In characteristic `p$, Artin–Schreier on
> `H^1(S, \mathcal{O}_S)$ and the infinitesimal$\\alpha_{p}$/$\mu_p$ flat fundamental group together control the
> \`p$-part. The Cartier-duality master formula unifies the two.

______________________________________________________________________

## Closing of file 56 (and of the gentle Exposé XI)

With this file, the gentle SGA pass through **Exposé XI — Examples and Complements** is complete (files 52–56):

- **File 52 (§XI.1)** — projective spaces are simply connected; rational and rationally connected varieties; the modern
  Kollár–Graber–Harris–Starr theory of rational connectedness.
- **File 53 (§XI.2)** — abelian varieties; the Serre–Lang theorem $\pi_{1}(A) \simeq T\cdot(A)$; Weil's structure of$T_ℓ$;
    the full gentle treatment of Nori's true fundamental group `π_1^N$.
- **File 54 (§XI.3)** — projective cones and the Fermat-surface Zariski counterexample to the X.1.3 / X.2.4 separability
  hypotheses.
- **File 55 (§§XI.4–XI.5)** — principal homogeneous bundles in the fpqc / descent-theoretic sense; the six-term
  cohomology exact sequence; $H^{1}(S, GL_{n}) = $ rank-$n$ vector bundles; `H^1(S, \mathbb{G}_m) = \text{Pic}(S)$.
- **File 56 (§XI.6)** — Kummer and Artin–Schreier theories; the Kummer–Picard exact sequence; the Cartier-duality master
  formula \`H^1(S, G) \\cong \\text{Hom}(D(G), \\text{Pic}\_{S/k})$.

The **gentle SGA project — as of files 52–56 — now covers Exposés I, II, III, IV, V, VI, VIII, IX, X, XI**. The gentle
pass through **Exposé XII (GAGA, analytic comparison)** is files 57–60:

- **File 57 (§XII.1)** — the analytification functor $X \mapsto X^{an}$ (representability, completion isomorphism, the
  inverse-image functor on coherent sheaves).
- **File 58 (§§XII.2–XII.3)** — the property dictionaries: eight scheme-level properties and seventeen morphism-level
  properties transfer between $X$ and $X^{an}$.
- **File 59 (§XII.4)** — relative cohomological GAGA: $(R^{p} f_{*} F)^{an} \simeq R^{p} f^{an}_{*}(F^{an})$ for proper
  $f$ and coherent $F$; equivalence of $Coh(X)$ and $Coh(X^{an})$ for proper $X$.
- **File 60 (§XII.5)** — the **Riemann existence theorem** and the comparison
  $\pi^{\acute{e}}_{1}t(X) \simeq \hat{\pi}^{top}_{1}(X^{an})$; the Grauert–Remmert covering-extension framework;
  Raynaud's 2003 remark on non-residually-finite topological $\pi_{1}$.

Exposé **XIII (proper cohomological base change)** of SGA 1 remains as a future gentle pass.
