# Categories, rings, and locality

## What this file is about

Take the polynomial functions on the real line — the expressions like three times t squared, minus five t, plus seven.
You can add them, multiply them, and plug in a number. That bundle of functions, together with its operations, is what
algebraists call a ring. The starting observation of modern algebraic geometry is that the line itself can be recovered
from this bundle: knowing which functions vanish at which points reconstructs the geometry from the algebra alone. So a
ring is the algebra of functions on a space, and operations on rings are secretly operations on spaces.

This file is the algebra-side warm-up. It introduces rings and the standard ways of building new ones from old, and it
labels each construction with the geometric move it stands for. Nothing here is geometry yet. The next file collects the
payoff.

To talk about étale morphisms we need a notion of "space" that is fluent in algebra. The reading guide pointed at the
destination — an algebraic substitute for a covering map. The route there starts on the algebra side: rings, ideals,
quotients, prime ideals, residue fields, localization, tensor products. Some of this is review. All of it carries a
hidden geometric meaning that we will cash in starting in the next file.

One sentence organizes everything:

> A ring is the algebra of functions on a space.

Once you see that, the operations on rings — quotient, localization, tensor product — become operations on spaces.
Algebra and geometry stop being two subjects; they become two views of the same subject. This file sets up the algebra
side of that dictionary so that the geometry side, in file 02, takes care of itself.

A short note on intuition. The material that follows will move between two registers: algebra (rings, ideals, modules)
and the geometry that algebra encodes. We assume the reader is at home in the first register and is meeting the second
for the first time.

#### Aside (Rust + type-theory analogy).

_Skip this paragraph if Rust trait resolution and dependent-type- theory substitution are not part of your background;
nothing later depends on it._

For readers with those backgrounds: a ring matches a trait describing what operations a type supports — the bundle of
`Add`, `Mul`, `Zero`, `One`, with the usual axioms. Ring homomorphisms reverse the direction of geometric morphisms the
same way substitutions $\Gamma \to \Delta$ in a dependent type theory run opposite to morphisms of contexts.
Localization adjusts a ring the way adding a typeclass instance for one specific value adjusts a type.

We start with a familiar object and look at it slowly.

## Polynomial rings as functions

Take the ring $\mathbb{R}[t]$ of polynomials in one variable with real coefficients. You have seen this many times. We
are going to look at it carefully because it is the simplest place where the algebra-as-geometry slogan is visible.

A polynomial like $3t^{2} - 5t + 7$ does two things at once. As an algebraic expression, it is a string of coefficients
tagged with powers of $t$. As a function, it sends each real number $a \in \mathbb{R}$ to the real number you get by
plugging in $a$:

$$
(3t^{2} - 5t + 7)(2) = 12 - 10 + 7 = 9.
$$

So every element of $\mathbb{R}[t]$ defines a function $\mathbb{R} \to \mathbb{R}$. Two polynomials that define the same
function are equal as polynomials (for $\mathbb{R}$, an infinite field, this is true; over finite fields it fails, and
we will be careful when it matters). The collection of all polynomials, with the obvious addition and multiplication of
functions, is a ring. We call this ring $\mathbb{R}[t]$.

The slogan in this case reads:

> $\mathbb{R}[t]$ is the algebra of polynomial functions on the real line $\mathbb{R}$.

The same idea works in more variables. The ring $\mathbb{R}[x, y]$ is the algebra of polynomial functions of two real
variables, defined on the plane $\mathbb{R}^{2}$. The ring $\mathbb{R}[x, y, z]$ is the algebra of polynomial functions
on three-dimensional space $\mathbb{R}^{3}$. And so on. In each case, the ring is "what you can compute pointwise" — the
operations of the ring are operations on functions, computed pointwise.

A few other rings we will use, with their geometric reading.

```text
ℤ        — functions on the geometric object Spec ℤ
ℝ[t]     — polynomial functions on the real line
ℂ[t]     — polynomial functions on the complex line
ℝ[x, y]  — polynomial functions on the real plane
ℝ[x, y]/(x² + y² − 1)  — polynomial functions on the unit circle
ℤ/n      — functions on a finite scheme of n points
```

Some of these we have not earned yet. $\operatorname{Spec} \mathbb{Z}$ and "scheme of $n$ points" are vocabulary from
later in this file and from file 02. $/(x^{2} + y^{2} - 1)$ involves taking a quotient, which we have not defined. We
will get to all of it. For now, just notice the pattern: every ring on this list pairs with a geometric object, and the
operations of the ring are the operations on functions on that object.

The discipline of algebraic geometry is to take this pairing seriously. Whatever ring you write down, **there is a
geometric object behind it**. We are going to build the language to make this precise.

## Notation: categories we use

This file assumes the categorical prerequisites listed in the reading guide: objects, morphisms, functors, natural
transformations, universal properties, limits and colimits, pullbacks. We will not redefine them. Four categories appear
throughout the file:

- **Set**: sets and functions.
- **Rng**: commutative rings with `1`, and ring homomorphisms.
- **A-Alg**: commutative $A$-algebras over a fixed ring $A$, and $A$-algebra homomorphisms.
- **A-Mod**: $A$-modules and $A$-linear maps.

The category of schemes, **Sch**, will appear in file 02.

## Ring homomorphisms: a refresher

The slogan pairs each ring with a space. Before we look at structure inside a single ring, we look at the maps that
connect rings to one another — and, by reversal, the maps that will connect their spaces.

A **ring homomorphism** $\phi : A \to B$ is a function from one ring $A$ to another ring $B$ that respects the ring
operations. Three conditions:

```text
φ(a + a') = φ(a) + φ(a'),
φ(a · a') = φ(a) · φ(a'),
φ(1_A) = 1_B.
```

So $\phi$ carries sums to sums, products to products, and the unit of $A$ to the unit of $B$. (Carrying `0` to `0`
follows automatically from the first condition.)

Three examples to recognize.

**Inclusion.** The inclusion $\mathbb{Z} \to \mathbb{R}$ of integers into the reals is a ring homomorphism. So is
$\mathbb{R} \to \mathbb{C}$. Whenever a smaller ring sits inside a larger one, the inclusion is a ring homomorphism.

**Evaluation.** Pick a real number $a$. The function

```text
ev_a : ℝ[t] → ℝ,    p(t) ↦ p(a)
```

that evaluates a polynomial at $a$ is a ring homomorphism. The sum-of-polynomials evaluates to the sum of the values;
the product-of-polynomials evaluates to the product of the values; the constant polynomial `1` evaluates to `1`. So
$ev_{a}$ respects all three structures.

There is one such homomorphism for every real number. Each "point of $\mathbb{R}$" gives a ring homomorphism
$\mathbb{R}[t] \to \mathbb{R}$. This is a hint — the points of the geometric line correspond to ring homomorphisms into
$\mathbb{R}$.

**Reduction.** Pick an integer $n > 0$. The function

```text
ℤ → ℤ/n,    a ↦ a mod n,
```

that reduces an integer modulo $n$ is a ring homomorphism. The target $\mathbb{Z}/n$ is the ring of integers mod $n$,
with operations inherited from $\mathbb{Z}$.

These three examples — inclusion, evaluation, reduction — cover most of the ring homomorphisms we will meet in this
file.

### A first hint of arrow-flipping

Look at evaluation again. $ev_{a} : \mathbb{R}[t] \to \mathbb{R}$ is a homomorphism **from the ring of functions on
$\mathbb{R}$** **to the value field $\mathbb{R}$**. Geometrically, what $ev_{a}$ does is: pick the single point $a$ of
$\mathbb{R}$, extract the value of every polynomial there.

So the ring homomorphism $ev_{a} : \mathbb{R}[t] \to \mathbb{R}$ corresponds, in geometric terms, to a single point
${a} \to \mathbb{R}$. The ring map runs from $\mathbb{R}[t]$ to $\mathbb{R}$. The geometric map runs from ${a}$ to
$\mathbb{R}$. Same direction at the geometric level (point to line), but the ring map runs the opposite way (functions
on the line to functions on the point).

This direction-flipping is the central feature of the ring-as-functions dictionary. We will see it many more times. The
slogan that goes with it:

> A ring map $A \to B$ is the algebraic shadow of a geometric map running
> $\operatorname{Spec} B \to \operatorname{Spec} A$, with the arrow flipped.

We have not defined `Spec` yet. Hold the slogan; we will return to it.

## Ideals: vanishing on a subset

Maps between rings gave us the first hint of arrow-flipping. They told us nothing yet about what lives inside a single
ring. The algebraic counterpart of a subset of the space turns out to be a particular kind of subset of the ring — the
**ideal**.

The motivation. Suppose we have a ring $A$ of functions on some space $X$ (think $A = \mathbb{R}[x, y]$ and
$X = \mathbb{R}^{2}$). Suppose $Z \subseteq X$ is a subset of the space (think the $x$-axis ${y = 0}$ inside
$\mathbb{R}^{2}$). A natural question: which functions on $X$ vanish identically on $Z$?

For our example: which polynomials in $\mathbb{R}[x, y]$ vanish on the $x$-axis? The answer is: polynomials with no
constant or $x$-only term — equivalently, polynomials of the form $y \cdot g(x, y)$ for some polynomial $g$.

Three things to notice about this collection.

1. The zero polynomial vanishes on the $x$-axis. So the collection contains `0`.
1. If $f$ and $f'$ both vanish on the $x$-axis, then so does $f + f'$. The collection is closed under addition.
1. If $f$ vanishes on the $x$-axis and $h$ is **any** polynomial, then $h \cdot f$ also vanishes on the $x$-axis
   (anything times zero is zero). The collection is closed under multiplication by arbitrary elements of the ring.

The third property is the surprising one. The collection of "vanishing functions" is closed under multiplication not
just by itself, but by **any** function in the ring. Multiplication by an arbitrary ring element absorbs into the
collection.

This is the algebraic essence of "vanishing on a subset," and we abstract it into a definition.

### The definition

An **ideal** of a ring $A$ is a subset $I \subseteq A$ satisfying three conditions:

1. $0 \in I$.
1. If $a \in I$ and $a' \in I$, then $a + a' \in I$.
1. If $a \in I$ and $h \in A$, then $h \cdot a \in I$.

An ideal is more than a sub-ring. A sub-ring is closed under sums and products with itself; an ideal is closed under
products with the **entire ambient ring**. That third condition is the whole point.

The geometric model behind this — vanishing on a subset — is the guide for everything we will do with ideals.

### Examples to anchor the definition

In $\mathbb{Z}$, the multiples of `5`,

$$
(5) := { 5n : n \in \mathbb{Z}} = { \cdots, -10, -5, 0, 5, 10, \cdots},
$$

form an ideal. They contain `0`; the sum of two multiples of `5` is a multiple of `5`; any integer times a multiple of
`5` is a multiple of `5`. Geometrically, this is the ideal of "functions on $\operatorname{Spec} \mathbb{Z}$" vanishing
at the prime `(5)`.

In $\mathbb{R}[x, y]$, the multiples of $y$,

```text
(y) := { y · g(x, y) : g ∈ ℝ[x, y] },
```

form an ideal. It is the ideal of polynomials vanishing on the $x$-axis.

In $\mathbb{R}[x, y]$, the multiples of $x^{2} + y^{2} - 1$ form an ideal $(x^{2} - y^{2} - 1)$. It is the ideal of
polynomials vanishing on the unit circle (the locus where $x^{2} + y^{2} = 1$).

These three examples follow a pattern. We have a single element of the ring; the ideal is "all multiples of that
element." Such an ideal is called a **principal ideal**, and the notation `(f)` means "the principal ideal generated by
$f$" — that is, ${ h \cdot f : h \in A}$.

### Generated by several elements

Sometimes one element is not enough. The ideal generated by elements $f_{1}, \cdots, f_{n} \in A$,

```text
(f₁, …, f_n) := { h₁ f₁ + … + h_n f_n : h_i ∈ A },
```

is the set of all $A$-linear combinations of the $f_{i}$. It is the smallest ideal containing all of
$f_{1}, \cdots, f_{n}$.

Examples.

In $\mathbb{Z}$, the ideal `(6, 10)` is the set of all integers of the form $6m + 10n$. By the Euclidean algorithm,
every such integer is a multiple of $gcd(6, 10) = 2$, and conversely every multiple of `2` is $6m + 10n$ for some
`m, n`. So `(6, 10) = (2)`, the multiples of `2`. In $\mathbb{Z}$, every ideal turns out to be principal — generated by
a single element.

In $\mathbb{R}[x, y]$, the ideal $(x, y)$ is the set of polynomials of the form $h_{1} x + h_{2} y$, equivalently the
polynomials with zero constant term. Geometrically, this is the ideal of polynomials vanishing at the origin `(0, 0)`.

In $\mathbb{R}[x, y]$, the ideal $(x - 1, y - 2)$ is the polynomials vanishing at the point `(1, 2)`.

### One ideal worth flagging

In $\mathbb{R}[t]$, take the ideal $(t^{2}) = { t^{2} \cdot g(t) : g \in \mathbb{R}[t]}$. This is the multiples of
$t^{2}$. Geometrically, what does it cut out?

Naively, it should cut out "where $t^{2} = 0$," which is just $t = 0$. So we might expect $(t^{2})$ to do the same job
as `(t)`. But it does not. The two ideals are different: $t \in (t)$ but $t \notin (t^{2})$. The ideal $(t^{2})$ is
strictly smaller than `(t)`.

Geometrically, $(t^{2})$ is "the origin, with one extra infinitesimal direction." We will see this more carefully in the
section on quotient rings. For now, hold this distinction: ideals can distinguish "the same subset" with different
multiplicities, and that distinction will turn out to encode infinitesimal data.

## Quotient rings

Ideals named the functions that vanish on a subset, but they have not yet given us the ring of functions on the subset
itself. The quotient construction supplies it.

Given a ring $A$ and an ideal $I \subseteq A$, the **quotient ring** $A/I$ is built in two steps. First, declare two
elements $a, a' \in A$ to be equivalent ($a \sim a'$) if $a - a' \in I$. Second, take the set of equivalence classes,
and inherit the ring operations from $A$.

Concretely, every element of $A/I$ is represented by some $a \in A$, and two representatives `a, a'` give the same
element of $A/I$ iff their difference is in $I$. We write `[a]` or $a + I$ for the equivalence class, or just $a$ when
context makes clear we are working in the quotient.

The geometric reading. If $I$ is the ideal of functions vanishing on a subset $Z \subseteq X$, then two functions on $X$
are equivalent modulo $I$ iff their difference vanishes on $Z$ iff they take the same values on $Z$. So $A/I$ is "the
ring of functions on $Z$," seen as a ring in its own right.

> **$A/I$ is the ring of functions on the subset cut out by $I$.**

The examples we have already met carry over.

**$\mathbb{Z}/(5) = \mathbb{Z}/5$.** The integers modulo `5`, with operations inherited from $\mathbb{Z}$. A finite ring
with five elements. Geometrically, this is "functions on the closed point $(5) \in \operatorname{Spec} \mathbb{Z}$," and
the five elements are the five possible "values" a function on that point can take.

**$\mathbb{R}[x, y]/(y) = \mathbb{R}[x]$.** Setting $y = 0$ reduces a polynomial in two variables to a polynomial in one
variable. Geometrically, this is the ring of polynomial functions on the $x$-axis, which is indeed $\mathbb{R}[x]$.

**$\mathbb{R}[x, y]/(x^{2} + y^{2} - 1)$.** The ring of polynomial functions on the unit circle. Two polynomials are
equivalent iff their difference vanishes on the circle.

### The infinitesimal twist

Now look at $\mathbb{R}[t]/(t^{2})$. Setting $t^{2} = 0$ does not collapse $\mathbb{R}[t]$ all the way down to
$\mathbb{R}$. Every element of the quotient is represented by some polynomial in $\mathbb{R}[t]$, modulo polynomials
divisible by $t^{2}$. After reducing, every element has the form

```text
a + bt    with    t² = 0,    a, b ∈ ℝ.
```

So $\mathbb{R}[t]/(t^{2})$ is a two-dimensional $\mathbb{R}$-vector space, with basis `1, t`. Multiplication is
$(a + bt)(a' + b't) = aa' + (ab' + ba')t$, since $t \cdot t = t^{2} = 0$.

The element $t \in \mathbb{R}[t]/(t^{2})$ is interesting. It is not zero in the quotient (because $t \notin (t^{2})$).
But it satisfies $t^{2} = 0$.

An element with this property — nonzero, but raised to a power equals zero — is called **nilpotent**. The ring
$\mathbb{R}[t]/(t^{2})$ has a nonzero nilpotent.

What does this look like geometrically? The ideal $(t^{2})$ cuts out "$t^{2} = 0$," which set-theoretically is just
$t = 0$ — the origin. But the **ring** $\mathbb{R}[t]/(t^{2})$ has more structure than the ring of functions on a single
point would have. Functions on a single point should form a copy of $\mathbb{R}$, not of
$\mathbb{R} \oplus \mathbb{R} \cdot t$.

The extra dimension is "an infinitesimal direction" at the origin. The nilpotent $t$ measures "first-order perturbation
away from the origin." This ring will turn out to be the universal model of "a single point with one infinitesimal
direction sticking out," and we will return to it many times.

The take-away for now: an ideal $I$ can have a richer ring $A/I$ than its set-theoretic vanishing locus would suggest.
Ideals carry more information than just "where things are zero." That extra information is what makes algebraic geometry
richer than naive set theory.

## The kernel of a ring homomorphism

Ideals and ring maps were introduced separately. They are the same notion, seen from two sides. Given a ring
homomorphism $\phi : A \to B$, the **kernel** is

```text
ker(φ) := { a ∈ A : φ(a) = 0 } ⊆ A.
```

The kernel is always an ideal. It contains `0` (because $\phi(0) = 0$); it is closed under addition
($\phi(a + a') = 0 + 0 = 0$); it is closed under multiplication by any $h \in A$
($\phi(h \cdot a) = \phi(h) \cdot 0 = 0$).

So every ring homomorphism $\phi : A \to B$ produces an ideal $\ker(\phi) \subseteq A$. Conversely, every ideal
$I \subseteq A$ is the kernel of the quotient map $A \to A/I$. Ideals and "kernels of ring homomorphisms" are the same
notion.

The example to remember. The evaluation homomorphism $ev_{a} : \mathbb{R}[t] \to \mathbb{R}$ has kernel "polynomials
vanishing at $a$." A polynomial $p(t)$ vanishes at $a$ iff $p(t)$ is divisible by $t - a$ (this is the factor theorem
from elementary algebra). So

$$
\ker(ev_{a}) = (t - a),
$$

the principal ideal generated by $t - a$. The first nontrivial example of "ideal = kernel of a ring map."

This identification is the algebraic-geometry version of the factor theorem: vanishing at a point is captured by the
ideal of multiples of $t - a$.

## Prime ideals

Every ideal cuts out something, but not everything an ideal cuts out deserves to be called a point. Two distinguished
classes — **prime** and **maximal** — are the ones that will. We meet primes first; the maximal case will fall out as a
strengthening.

A **prime ideal** of a ring $A$ is an ideal $\mathfrak{p} \subsetneq A$ (proper, not the whole ring) satisfying:

> If $a \cdot b \in \mathfrak{p}$, then $a \in \mathfrak{p}$ or $b \in \mathfrak{p}$.

Equivalently: the complement $A \ \mathfrak{p}$ is closed under multiplication. A product of two things outside
$\mathfrak{p}$ is again outside $\mathfrak{p}$.

The notation $\mathfrak{p}$ is a fraktur "p," typeset in fraktur in printed mathematics texts; we use the Unicode glyph.
There is nothing special about the typography. It is just a letter that flags "this is a prime."

Why "prime"? Because in $\mathbb{Z}$, the prime ideals are exactly the ones generated by prime numbers (plus the zero
ideal). The definition "if a product is in $\mathfrak{p}$ then one factor is" is the definition of "prime" for a number
$p$: if $p | ab$ then $p | a$ or $p | b$. The ideal-theoretic version generalizes the number-theoretic one.

### Examples

**$\mathbb{Z}$.** The prime ideals are `(0)` and `(p)` for each prime number $p$. The ideal `(0)` is prime because if
$ab = 0$ in $\mathbb{Z}$ then $a = 0$ or $b = 0$ ($\mathbb{Z}$ has no zero divisors). The ideal `(p)` is prime because
of the elementary primality property.

What about `(6)`? It is not prime. We have $2 \cdot 3 = 6 \in (6)$, but neither $2 \in (6)$ nor $3 \in (6)$. So `(6)`
fails the prime condition. (In fact $(6) = (2) \cap (3)$, an intersection of two primes.)

**$\mathbb{C}[t]$.** The prime ideals are `(0)` and $(t - a)$ for each $a \in \mathbb{C}$. `(0)` is prime because
$\mathbb{C}[t]$ has no zero divisors. Each $(t - a)$ is prime because if a product `pq` is divisible by $t - a$, then
evaluation at $a$ gives $p(a) q(a) = 0$, so $p(a) = 0$ or $q(a) = 0$, forcing $t - a$ to divide $p$ or $q$.

What about $(t^{2} - 1) = ((t - 1)(t + 1))$? It is not prime: the product $(t - 1)(t + 1) \in (t^{2} - 1)$, but neither
$(t - 1) \in (t^{2} - 1)$ nor $(t + 1) \in (t^{2} - 1)$ (each factor has degree 1, while elements of $(t^{2} - 1)$ have
degree at least 2 or are zero).

**$\mathbb{R}[t]$.** The prime ideals are `(0)`, $(t - a)$ for each $a \in \mathbb{R}$, and `(F)` for each monic
irreducible quadratic $F = t^{2} + bt + c$ with $b^{2} - 4c < 0$. The first two should be familiar; the third is new. A
monic quadratic with negative discriminant is irreducible over $\mathbb{R}$, and the corresponding ideal is prime by the
same argument: if a product `pq` is divisible by $F$, then irreducibility of $F$ forces it to divide $p$ or $q$.

### Why the zero ideal is interesting

For an integral domain $A$ (a ring with no zero divisors), the ideal `(0)` is prime. This is just unpacking the
definition: if $ab \in (0)$ then $ab = 0$, so $a = 0$ or $b = 0$, so $a \in (0)$ or $b \in (0)$.

Geometrically, the zero ideal corresponds to a special "point" of the geometric object behind $A$. We will call it the
**generic point**. For $\operatorname{Spec} \mathbb{Z}$, the generic point is `(0)`. For
$\operatorname{Spec} \mathbb{C}[t]$, the generic point is `(0)`.

The generic point is "every point at once," in a precise sense: its closure is the whole space. We will see exactly what
this means in the next file.

## Maximal ideals

Primes generalized "if it divides a product, it divides a factor" and gave us a candidate notion of point. The
strengthening promised above — the one that will give us _closed_ points and a residue field — is the maximal ideal.

A **maximal ideal** of a ring $A$ is a proper ideal $\mathfrak{m} \subsetneq A$ such that no other proper ideal strictly
contains $\mathfrak{m}$. Equivalently: if $I$ is an ideal with $\mathfrak{m} \subseteq I \subseteq A$, then either
$I = \mathfrak{m}$ or $I = A$.

The notation $\mathfrak{m}$ is a fraktur "m." Same as for $\mathfrak{p}$, just a letter flagging "this is a maximal
ideal."

### Equivalent definition: A/𝔪 is a field

Here is the cleanest equivalent characterization.

> An ideal $\mathfrak{m} \subsetneq A$ is maximal iff the quotient ring $A/\mathfrak{m}$ is a **field**.

The proof is short. If $A/\mathfrak{m}$ is a field, every nonzero element of $A/\mathfrak{m}$ is invertible. So if $I$
is an ideal strictly containing $\mathfrak{m}$, the image of any element of $I \ \mathfrak{m}$ is a nonzero element of
$A/\mathfrak{m}$, hence invertible. That forces $I/\mathfrak{m} = A/\mathfrak{m}$, hence $I = A$. Conversely, if no
proper ideal strictly contains $\mathfrak{m}$, take any $a \in A \ \mathfrak{m}$. The ideal $(a) + \mathfrak{m}$
strictly contains $\mathfrak{m}$, so it must be all of $A$. So $1 = h a + m$ for some $h \in A$ and
$m \in \mathfrak{m}$. Reducing mod $\mathfrak{m}$ gives $1 = [h] [a]$ in $A/\mathfrak{m}$, so `[a]` is invertible.

The take-away: **maximal ideals correspond to surjections onto fields.** Each maximal ideal $\mathfrak{m} \subset A$
gives a quotient field $A/\mathfrak{m}$, and conversely each surjection $A \twoheadrightarrow k$ onto a field has a
maximal ideal as kernel.

We will call $A/\mathfrak{m}$ the **residue field** at the maximal ideal $\mathfrak{m}$. The name comes from the
geometric reading: think of a maximal ideal as a "point" of the space behind $A$, and the residue field as "where values
at that point live."

### Maximal implies prime

Every maximal ideal is prime. The proof: if $\mathfrak{m}$ is maximal then $A/\mathfrak{m}$ is a field; fields have no
zero divisors; so if $ab = 0$ in $A/\mathfrak{m}$ then $a = 0$ or $b = 0$, which is exactly the prime condition for
$\mathfrak{m}$.

The converse fails. The ideal $(0) \subset \mathbb{Z}$ is prime ($\mathbb{Z}$ is an integral domain) but not maximal
($\mathbb{Z}/(0) = \mathbb{Z}$, which is not a field). So the prime ideals of $\mathbb{Z}$ strictly contain the maximal
ones: every `(p)` is both prime and maximal, but `(0)` is prime without being maximal.

This distinction — primes that are not maximal — is exactly the "generic point" phenomenon. We come back to it.

### Examples

**$\mathbb{Z}$.** The maximal ideals are `(p)` for each prime number $p$. The residue field at `(p)` is
$\mathbb{Z}/(p) = \mathbb{F}_{p}$, the finite field with $p$ elements. So each prime number gives a maximal ideal whose
residue field is the finite field with that prime number of elements.

**$\mathbb{C}[t]$.** The maximal ideals are $(t - a)$ for each $a \in \mathbb{C}$. The residue field at $(t - a)$ is
$\mathbb{C}[t]/(t - a) = \mathbb{C}$. The isomorphism $\mathbb{C}[t]/(t - a) \simeq \mathbb{C}$ sends a polynomial to
its value at $a$ — exactly the evaluation homomorphism $ev_{a}$.

So in $\mathbb{C}[t]$, maximal ideals correspond bijectively to points of $\mathbb{C}$. Each maximal ideal $(t - a)$
pairs with the point $a$, and the residue field is $\mathbb{C}$. The set of maximal ideals **is** $\mathbb{C}$, in
disguise.

This is the simplest case where "maximal ideals are points" works literally. Algebra reconstructs the geometry of the
line.

## The riddle of $\mathbb{R}[t]$

We can now state the puzzle that motivates the whole construction of algebraic geometry.

In $\mathbb{C}[t]$, maximal ideals correspond to points of $\mathbb{C}$. Clean.

In $\mathbb{R}[t]$, the maximal ideals are of two kinds.

**Real points.** For each $a \in \mathbb{R}$, the ideal $(t - a)$ is maximal, with residue field
$\mathbb{R}[t]/(t - a) = \mathbb{R}$. Each real number gives a maximal ideal whose residue field is $\mathbb{R}$.

**Conjugate-pair points.** For each monic irreducible quadratic $F = t^{2} + bt + c$ with $b^{2} - 4c < 0$, the ideal
`(F)` is maximal, with residue field $\mathbb{R}[t]/(F) \simeq \mathbb{C}$. The isomorphism sends $t$ to one of the two
conjugate complex roots of $F$ — but symmetrically: there is no algebraic preference between the two roots, so the ideal
`(F)` is most naturally identified with the **pair** of conjugate roots $\pm i\sqrt{(c - b^{2}/4)} - b/2$.

So the maximal ideals of $\mathbb{R}[t]$ are **the real numbers** plus **the conjugate pairs of non-real complex
numbers**. Together they cover all the algebraic data the ring $\mathbb{R}[t]$ "knows about."

The geometry of $\mathbb{R}$, on the other hand, only sees the real numbers. The maximal ideals corresponding to
conjugate complex pairs have no counterpart in the real line.

> **The algebra of $\mathbb{R}[t]$ sees points that the geometry of $\mathbb{R}$ does not.**

If we want geometry to track the algebra faithfully, we need a notion of "space" that includes the missing conjugate
pairs as honest points. That is what algebraic geometry provides.

## What `Spec` will do

We will define, in the next file, a geometric object $\operatorname{Spec} A$ attached to every ring $A$. Its **points**
will be the **prime ideals** of $A$. For $\mathbb{R}[t]$, the points of $\operatorname{Spec} \mathbb{R}[t]$ will be:

- the real numbers (one point per maximal ideal $(t - a)$),
- the conjugate-pair "points" (one per maximal ideal `(F)` for irreducible quadratic $F$ with negative discriminant),
- the generic point `(0)`.

The first two are closed points; the third is the generic point. For any ring, the prime ideals — not just the maximal
ones — make up the points of $\operatorname{Spec} A$. The maximal ones are closed points; the others are generic points
of various closed subschemes.

Why include the non-maximal primes? Because they are forced. A ring homomorphism does not, in general, pull back maximal
ideals to maximal ideals; it pulls back primes to primes. So if we want $\operatorname{Spec} A$ to be functorial in $A$,
we have to use all primes.

That is the construction the next file does. For the rest of this file, we collect the remaining algebra we will need:
modules, localization, tensor products, base change, fibers.

## A second example: $\mathbb{Z}[t]/(t^{2} - 2)$ and its primes

Meet the running example. The ring $B = \mathbb{Z}[t]/(t^{2} - 2)$ will reappear under every lens we build: as a
fiber-by-fiber description in this file, geometrically as $\operatorname{Spec} B \to \operatorname{Spec} \mathbb{Z}$ in
file 02, in calculus as the support of $\Omega^{1}$ in file 03, in the étale hierarchy in file 04, and in normalization
and Galois theory in file 06. Each return shows the same object refracted through whatever new structure we have just
defined.

As an abelian group, $B$ is free on the basis `1, t`, where $t$ satisfies $t^{2} = 2$. So every element of $B$ looks
like $a + bt$ with $a, b \in \mathbb{Z}$. This is "the integers, plus a square root of `2`." It is the ring of integers
in the number field $\mathbb{Q}(\sqrt{2})$.

The map $\mathbb{Z} \to B$ is the obvious inclusion. Geometrically, it gives a morphism
$\operatorname{Spec} B \to \operatorname{Spec} \mathbb{Z}$ (with the arrow flipped, as always).

We are not going to compute the prime ideals of $B$ from scratch. Instead, we will compute the **fibers** of
$\operatorname{Spec} B \to \operatorname{Spec} \mathbb{Z}$ over each prime of $\mathbb{Z}$ once we have the tensor
product set up. That is in a few sections. For now, just register the example: a ring extension
$\mathbb{Z} \to \mathbb{Z}[t]/(t^{2} - 2)$, with the geometric morphism running the other way.

## Where we are, halfway through

We have defined: rings, ring homomorphisms, ideals, quotient rings, kernels, prime ideals, maximal ideals, residue
fields. We have noticed that maximal ideals look like "points" and that the algebra often knows about more points than
the obvious geometry does.

The remaining algebra in this file: modules, localization (zoom into a point), local rings, tensor products (the
algebraic shadow of geometric pullback), base change, and fibers.

After that, the geometry — the actual construction of $\operatorname{Spec} A$ and the dictionary it builds — is in file
02.

## Modules: vector spaces over a ring

So far, "things over $A$" has meant other rings — $A$-algebras. Many of the constructions ahead want a looser notion:
data carrying an $A$-action, without any multiplication of its own. That notion is the **module**.

An $A$-**module** is an abelian group $M$ with a multiplication $A \times M \to M$, $(a, m) \mapsto am$, satisfying:

```text
1 · m = m,
(a + a') m = am + a'm,
a (m + m') = am + am',
(aa') m = a (a' m).
```

A module is a vector space with the field of scalars replaced by a ring. The flexibility lies in what $A$ is.

- When $A = k$ is a field, an $A$-module is exactly a $k$-vector space.
- When $A = \mathbb{Z}$, an $A$-module is exactly an abelian group. (The scaling $n \cdot m$ is just
  $m + m + \cdots + m$ repeated $n$ times.)
- When $A = k[t]$, an $A$-module is a $k$-vector space $V$ together with a $k$-linear endomorphism $T : V \to V$. (The
  scalar $t$ acts by $T$; the polynomial $p(t)$ acts by $p(T)$.)
- For any ring $A$, the ring $A$ is itself an $A$-module (the scaling is just multiplication in $A$).

Three familiar things, all instances of one notion. Modules unify "vector space," "abelian group," and "vector space
with a chosen endomorphism" into a single language.

For us, the most important fact about modules is **finite generation**. An $A$-module $M$ is **finitely generated** if
there exist $m_{1}, \cdots, m_{n} \in M$ such that every element of $M$ is some $A$-linear combination of them.
Equivalently, there is a surjection $A^{n} \twoheadrightarrow M$.

Two further adjectives for modules.

A module is **free** of **rank $n$** if $M \simeq A^{n}$. A free module is a "vector space" over $A$ in the most literal
sense: it has a basis.

A module is **flat** if tensoring with it (next section) preserves injections. Flatness is a "good behavior" condition;
we make it precise after we have tensor products. We use it in file 04.

The role of modules in our story. Whenever we have a ring map $A \to B$, we can view $B$ as an $A$-module (with $A$
acting via the map). Properties like "$B$ is finite over $A$" or "$B$ is flat over $A$" are then properties of $B$ as an
$A$-module, and they control how the geometric morphism $\operatorname{Spec} B \to \operatorname{Spec} A$ behaves.

## Localization: zoom in by inverting

Modules let us carry data over a fixed ring. The next operation changes the ring itself, in a way that pictures cleanly
as restriction to an open subset of the underlying space. It is the most overtly geometric of the algebraic operations
in this file.

The motivation. Take $\mathbb{R}[x, y]$, the polynomial functions on $\mathbb{R}^{2}$. Consider the function
$x \in \mathbb{R}[x, y]$. It vanishes on the $y$-axis and is nonzero everywhere else. On the open set where $x \neq 0$,
we can divide by $x$. The function $1/x$ is not in $\mathbb{R}[x, y]$, but on the open subset ${x \neq 0}$ it makes
perfect sense.

What is the right ring of functions on the open subset where $x \neq 0$? It should be $\mathbb{R}[x, y, 1/x]$ —
polynomial functions of $x, y, 1/x$, where we have allowed $1/x$.

This is the operation we call **localization**. It builds the smallest ring containing $A$ in which a chosen element is
invertible.

### The construction

For a ring $A$ and an element $f \in A$, the **localization of $A$ at $f$** is the set of formal fractions

```text
A[1/f] := { a / fⁿ : a ∈ A, n ≥ 0 } / ∼,
```

with two fractions $a/f^{n}$ and $a'/f^{m}$ declared equivalent iff there exists $k \geq 0$ such that
$f^{k} (f^{m} a - f^{n} a') = 0$ in $A$. The ring operations are the obvious "common denominator" ones.

The natural map $A \to A[1/f]$ sends $a \mapsto a/1$. It is a ring homomorphism, and its image is in the largest piece
of $A[1/f]$ that does not need any division by $f$.

The map is universal in the following sense: any ring homomorphism $A \to R$ that sends $f$ to a unit factors uniquely
through $A \to A[1/f]$. So $A[1/f]$ is "the smallest extension of $A$ in which $f$ is invertible."

### The geometric reading

We will see in the next file that

> **$A[1/f]$ is the ring of functions on the open subset of $\operatorname{Spec} A$ where $f$ does not vanish.**

In other words: localizing the algebra at $f$ is the algebraic shadow of restricting `Spec` to the open subset where
$f \neq 0$.

Three concrete cases to feel.

$\mathbb{Z}[1/2]$ is the ring of "rationals with denominator a power of `2`." Geometrically, it is the ring of functions
on the open subset of $\operatorname{Spec} \mathbb{Z}$ complementary to the closed point `(2)`. We have removed the
prime `2` from consideration.

$k[t][1/(t - a)]$ is the ring of polynomials in $t$ with denominators allowed to be powers of $t - a$. Geometrically,
the ring of functions on the open subset of $\operatorname{Spec} k[t]$ where $t - a \neq 0$, that is, the affine line
minus the point $a$.

$k[x, y][1/x]$ is the ring of polynomials in `x, y` with denominators allowed to be powers of $x$. Geometrically, the
ring of functions on the open subset ${x \neq 0}$ of the affine plane — the plane minus the $y$-axis.

### Localization at a multiplicative set

The same construction works for a whole **multiplicatively closed subset** $S \subseteq A$ (containing `1` and closed
under products). Define $S^{-1}A$ as fractions $a/s$ with $a \in A$, $s \in S$, with the analogous identification.
Localization at a single $f$ is the special case $S = {1, f, f^{2}, \cdots}$.

Two cases of $S$ matter.

$S = {1, f, f^{2}, \cdots}$ for a single $f \in A$: gives $A[1/f]$.

$S = A \ \mathfrak{p}$ for a prime ideal $\mathfrak{p} \subset A$: gives **$A_{\mathfrak{p}}$**, the **localization of
$A$ at $\mathfrak{p}$**. We invert everything not in $\mathfrak{p}$.

The second case is the one we use most. It deserves its own section.

## Localization at a prime: zoom in on a point

Take a prime $\mathfrak{p} \subset A$. The set $S = A \ \mathfrak{p}$ is multiplicatively closed (because the complement
of a prime ideal is closed under multiplication). The localization $A_{\mathfrak{p}} := S^{-1}A$ inverts every element
not in $\mathfrak{p}$.

What does this do? Algebraically: we adjoin inverses to every $s \in A$ whose image in the residue field
$A/\mathfrak{p}$ is nonzero. We are "throwing in inverses for everything visible at $\mathfrak{p}$."

The result is striking. **$A_{\mathfrak{p}}$ is a local ring with exactly one maximal ideal
$\mathfrak{p} A_{\mathfrak{p}}$.** The residue field at this maximal ideal is $Frac(A/\mathfrak{p})$.

The geometric reading:

> **$A_{\mathfrak{p}}$ is the ring of functions defined on _some_ open neighborhood of $\mathfrak{p}$, with two
> functions identified if they agree on a smaller neighborhood — equivalently, the stalk of the structure sheaf at
> $\mathfrak{p}$.**

Localizing at $\mathfrak{p}$ is "zooming in on the point $\mathfrak{p}$." Anything that was nonzero at $\mathfrak{p}$
becomes literally invertible. Anything that was zero at $\mathfrak{p}$ is still in the maximal ideal of the localized
ring.

### Examples

For $A = \mathbb{Z}$ and $\mathfrak{p} = (5)$:

```text
ℤ_(5) = { m/n ∈ ℚ : 5 ∤ n } = "rationals with denominator coprime to 5".
```

The maximal ideal is $(5) \subset \mathbb{Z}_{5}$ (the multiples of `5`). The residue field is
$\mathbb{Z}_{5} / (5) = \mathbb{Z}/5 = \mathbb{F}_{5}$.

For $A = \mathbb{Z}$ and $\mathfrak{p} = (0)$:

```text
ℤ_(0) = { m/n ∈ ℚ : n ≠ 0 } = ℚ.
```

The localization at the generic point gives back the field of fractions. (The notation $Frac(A)$ is the field of
fractions of an integral domain $A$.) Localizing at `(0)` always gives the field of fractions, when $A$ is a domain.

## Local rings: the algebra near a point

A **local ring** is a ring with exactly one maximal ideal. The unique maximal ideal we usually call $\mathfrak{m}$; the
residue field $A/\mathfrak{m}$ we call $\kappa$.

Most local rings of interest are localizations $A_{\mathfrak{p}}$. Other natural local rings include:

- Any field. The maximal ideal is `(0)` and the residue field is the field itself.
- The formal power series ring `k[[t]]` over a field $k$. The maximal ideal is `(t)`, the residue field is $k$.
- The $p$-adic integers $\mathbb{Z}_{p}$. The maximal ideal is `(p)`, the residue field is $\mathbb{F}_{p}$.

The slogan to hold:

> A local ring $(\mathcal{O}, \mathfrak{m})$ is the algebra of an "infinitesimal neighborhood" of one point. The maximal
> ideal $\mathfrak{m}$ is the ideal of functions vanishing at that point. The residue field
> $\kappa = \mathcal{O}/\mathfrak{m}$ is where the value at the point lives.

### Local homomorphisms

A **local homomorphism** between local rings is a ring map
$(\mathcal{O}, \mathfrak{m}) \to (\mathcal{O}', \mathfrak{m}')$ sending $\mathfrak{m}$ into $\mathfrak{m}'$.
Equivalently, the preimage of $\mathfrak{m}'$ is $\mathfrak{m}$. Equivalently, the induced map of residue fields
$\kappa \to \kappa'$ is well-defined.

The induced map of residue fields is called the **residue extension**. We will care about whether it is finite,
separable, trivial, and so on.

A great deal of Exposé I is about local homomorphisms. The art is to extract information about the global geometry from
a uniform statement about local homomorphisms.

## Tensor product: combining algebras over a base

Quotient and localization each modified one ring. We still need a way to combine two rings sitting over a common base —
the algebraic shadow of the geometric pullback we will eventually want. That combining operation is the **tensor
product**. We define it patiently because it is the place students most often lose footing.

The setup. Fix a ring $A$. We have two $A$-modules $M$ and $N$, and we want a "product" of them over $A$. The cartesian
product $M \times N$ is **not** the right answer. The cartesian product represents pairs, but most natural constructions
on modules are **bilinear**, not pair-shaped.

A **bilinear** map $M \times N \to P$ is a function that is $A$-linear in each argument separately:

```text
b(am + a'm', n) = a · b(m, n) + a' · b(m', n),
b(m, an + a'n') = a · b(m, n) + a' · b(m, n').
```

Bilinear maps are everywhere. Multiplication on a ring is bilinear. Dot product on a vector space is bilinear. The
pairing $M \times \operatorname{Hom}(M, P) \to P$ is bilinear. We want a single algebraic object that "represents" all
bilinear maps out of $M \times N$.

That object is the tensor product.

### Definition

The **tensor product** of $M$ and $N$ over $A$, denoted $M \otimes_{A} N$, is an $A$-module equipped with a bilinear map

```text
M × N → M ⊗_A N,    (m, n) ↦ m ⊗ n,
```

with the **universal property**: for every bilinear map $b : M \times N \to P$ (with $P$ an $A$-module), there is a
**unique** $A$-linear map $\tilde{b} : M \otimes_{A} N \to P$ such that $b(m, n) = \tilde{b}(m \otimes n)$ for all
`m, n`.

Concretely, $M \otimes_{A} N$ is generated by symbols $m \otimes n$ for $m \in M$, $n \in N$, modulo the bilinearity
relations:

```text
(m + m') ⊗ n = m ⊗ n + m' ⊗ n,
m ⊗ (n + n') = m ⊗ n + m ⊗ n',
(am) ⊗ n = m ⊗ (an) = a · (m ⊗ n).
```

The third relation lets $A$-scalars "move freely across the $\otimes$ symbol." This is what "over $A$" means.

### Bilinearity in practice

The third relation is the load-bearing one. Watch it move a scalar in $M \otimes_{\mathbb{Z}} N$:

```text
(2m) ⊗ n  =  2 · (m ⊗ n)  =  m ⊗ (2n).
```

The first equality is the third relation read left-to-right; the second is the same relation read right-to-left, this
time factoring the `2` through the right tensor argument. So $(2m) \otimes n$ and $m \otimes (2n)$ represent the _same_
element of $M \otimes_{\mathbb{Z}} N$.

This is what "scalars move freely across $\otimes$" means concretely: a scalar attached to either factor can be moved to
the other, or pulled out front. The same calculation runs over any base ring $A$: a scalar $a \in A$ can sit on the left
of $\otimes$, on the right of $\otimes$, or out front, and the three positions represent equal elements.

In practice we never compute inside a tensor product beyond moves like this. We use the universal property and a few
standard formulas.

### Tensor product of $A$-algebras

If $B$ and $C$ are $A$-algebras (rings with structure maps from $A$), the tensor product $B \otimes_{A} C$ inherits a
multiplication:

```text
(b ⊗ c) · (b' ⊗ c') = (bb') ⊗ (cc').
```

This makes $B \otimes_{A} C$ an $A$-algebra. There are two natural inclusions

```text
B → B ⊗_A C,    b ↦ b ⊗ 1,
C → B ⊗_A C,    c ↦ 1 ⊗ c.
```

Both compose with the structure maps from $A$ to give the same map $A \to B \otimes_{A} C$.

The **universal property as a coproduct**: for any $A$-algebra $R$ and any pair of $A$-algebra maps $B \to R$,
$C \to R$, there is a unique $A$-algebra map $B \otimes_{A} C \to R$ factoring them. So $B \otimes_{A} C$ is the
**coproduct** of $B$ and $C$ in the category of $A$-algebras.

This is the operation that, in the next file, will give the fibered product of schemes:

```text
Spec B ×_{Spec A} Spec C = Spec (B ⊗_A C).
```

Geometric pullback, on the algebra side, is the coproduct of algebras, which is the tensor product.

> **Memorize.** Geometric pullback corresponds to _coproduct_ of $A$-algebras — tensor product $B \otimes_{A} C$ — not
> to the category-theoretic pullback of rings. (The categorical pullback in **Rng** is pairs of ring elements with
> matching images, a different operation.) The reason is the arrow-flipping: limits in the category of schemes become
> colimits in the category of rings. This is the place where students slip; we will revisit it in file 02.

### Three patterns to internalize

Almost every concrete tensor-product computation in this file is one of three patterns, each reading the same universal
property through a different presentation of $B$.

Adjoining variables is the first. When $B = A[t_{1}, \cdots, t_{n}]$ is a polynomial ring, tensoring with $C$ carries
the variables along:

```text
B ⊗_A C = C[t₁, …, t_n].
```

The same operation, applied to a quotient, kills the same relations on the other side. If $B = A/I$, then

```text
B ⊗_A C = C / IC,
```

where `IC` is the ideal of $C$ generated by the image of $I$ under $A \to C$. Adding generators on the $B$ side and
imposing relations on the $B$ side both transfer cleanly to $C$. The pattern is the universal property doing its job: a
map out of $B \otimes_{A} C$ is exactly an $A$-algebra map out of $B$ together with a compatible map out of $C$, so
whatever presentation $B$ has — generators, relations, or both — gets reproduced over $C$.

The third pattern is the same construction read once more, this time with $B$ a localization. If $B = A[1/f]$, then

```text
B ⊗_A C = C[1/f].
```

Tensoring with a localization inverts the same element in $C$.

Three presentations, one universal property. When you see a tensor product, ask which of the three shapes one factor has
— polynomial ring, quotient, or localization — and apply the matching rule.

## Base change: changing the parameter space

The tensor product, once defined, immediately names a geometric operation we have not yet had words for: changing the
parameter space underneath a family. The algebraic name is **base change**. Suppose $A \to A'$ is a ring map and $B$ is
an $A$-algebra. Then

```text
B' := B ⊗_A A'
```

is an $A'$-algebra, with structure map $A' \to B'$ given by $a' \mapsto 1 \otimes a'$. This $B'$ is called the **base
change** of $B$ along $A \to A'$.

Geometrically: think of $\operatorname{Spec} A$ as the "parameter space" of a family of geometric objects
$\operatorname{Spec} B \to \operatorname{Spec} A$. A morphism $\operatorname{Spec} A' \to \operatorname{Spec} A$
provides a "new parameter space." Base change pulls the family back to the new parameter space.

Two cases of base change matter most.

**Localizing the family.** Take $A \to A_{\mathfrak{p}}$. Then $B \otimes_{A} A_{\mathfrak{p}}$ is "the family
$\operatorname{Spec} B \to \operatorname{Spec} A$, viewed near the point $\mathfrak{p}$."

**Passing to the fiber.** Take $A \to \kappa(\mathfrak{p}) = A_{\mathfrak{p}}/\mathfrak{p}A_{\mathfrak{p}}$. Then
$B \otimes_{A} \kappa(\mathfrak{p})$ is "the **fiber** of the family over the point $\mathfrak{p}$."

Both operations are tensor products. The notation $\kappa(\mathfrak{p})$ for the residue field $Frac(A/\mathfrak{p})$ of
a prime $\mathfrak{p} \subset A$ will be standard from now on.

## Fibers, computed

Base change told us that the fiber over a prime is a tensor product with a residue field. The running example was
waiting for exactly this tool. We turn it on now.

Recall the example: $B = \mathbb{Z}[t]/(t^{2} - 2)$ over $A = \mathbb{Z}$. The fiber of the geometric morphism
$\operatorname{Spec} B \to \operatorname{Spec} \mathbb{Z}$ over a prime $(p) \subset \mathbb{Z}$ is computed by base
change:

```text
B ⊗_ℤ 𝔽_p = ℤ[t]/(t² − 2) ⊗_ℤ 𝔽_p = 𝔽_p[t]/(t² − 2),
```

using the "killing relations" pattern.

So the fiber over `(p)` is $\operatorname{Spec} \mathbb{F}_{p}[t]/(t^{2} - 2)$, and its structure depends on how
$t^{2} - 2$ factors over $\mathbb{F}_{p}$. Three cases.

**$p = 7$.** The squares mod `7` are `{0, 1, 2, 4}` (compute: $3^{2} = 9 \equiv 2 mod 7$). So `2` is a square mod `7`,
and $t^{2} - 2 = (t - 3)(t + 3) mod 7$. The fiber is

```text
𝔽₇[t]/(t² − 2) = 𝔽₇[t]/(t − 3)(t + 3) ≃ 𝔽₇ × 𝔽₇
```

by the Chinese remainder theorem. Two distinct points, each with residue field $\mathbb{F}_{7}$. **Split.**

**$p = 5$.** The squares mod `5` are `{0, 1, 4}`. So `2` is not a square, $t^{2} - 2$ is irreducible, and the fiber is

$$
\mathbb{F}_{5}[t]/(t^{2} - 2) \simeq \mathbb{F}_{25},
$$

a finite field of `25` elements. One point, with residue field $\mathbb{F}_{25}$. **Extension.**

**$p = 2$.** Now $2 \equiv 0 mod 2$, so $t^{2} - 2 \equiv t^{2} mod 2$. The fiber is

$$
\mathbb{F}_{2}[t]/(t^{2} - 2) = \mathbb{F}_{2}[t]/(t^{2}),
$$

the "fat point" with $t^{2} = 0$. One point, with residue field $\mathbb{F}_{2}$, and a nilpotent direction $t$ sticking
out. **Ramified.**

The trichotomy:

```text
p = 7:  two distinct points        — split
p = 5:  one point, bigger field    — extension
p = 2:  one point, with nilpotent  — ramified
```

This three-way split is the central rhythm of arithmetic geometry, and the central thread of Exposé I. We will sharpen
it in file 04 into the trichotomy "étale (split or extension) versus ramified."

For now, hold the picture: a single morphism of schemes, three qualitatively different fiber behaviors at three
different primes.

## Noetherian: a finiteness condition

We close with the technical hypothesis that runs underneath all of Exposé I.

A ring $A$ is **noetherian** if every ascending chain of ideals $I_{1} \subseteq I_{2} \subseteq \cdots$ is eventually
constant. Equivalently: every ideal of $A$ is finitely generated.

Noetherianness rules out infinitely deep nesting of ideals. It is a "no pathologies" condition. Practically every ring
you meet in arithmetic geometry is noetherian: $\mathbb{Z}$, fields, polynomial rings over fields, quotients and
localizations of these, completions of noetherian local rings. Hilbert's basis theorem says that finitely generated
algebras over noetherian rings are noetherian. The standard nonexample is the polynomial ring in infinitely many
variables, $k[t_{1}, t_{2}, t_{3}, \cdots]$.

The source of Exposé I assumes "all preschemes are locally noetherian" from section I.2 onward. Concretely: every scheme
of interest has a covering by $\operatorname{Spec} A$'s with $A$ noetherian. This is invisible in practice; we mention
it once and move on.

## Where we have arrived

We have collected the algebra. The slogan that organized everything: a ring is the algebra of functions on a space, with
arrows reversed.

Here is the dictionary so far.

```text
algebra                          geometric meaning (cashed in file 02)
-----------------------          ------------------------------------
ring A                           the affine scheme Spec A
ring map A → B                   morphism Spec B → Spec A (arrow flipped)
ideal I ⊂ A                      a closed subscheme of Spec A
quotient A/I                     ring of functions on the closed subscheme
prime ideal 𝔭 ⊂ A                a point of Spec A
maximal ideal 𝔪 ⊂ A              a closed point of Spec A
residue field κ(𝔭) = Frac(A/𝔭)   the field of values at the point
nilpotent in A                   an infinitesimal direction
localization A[1/f]              open subscheme where f ≠ 0
localization A_𝔭                 local ring near the point 𝔭
tensor product B ⊗_A C           fibered product Spec B ×_{Spec A} Spec C
base change B ⊗_A A'             pulled-back family over Spec A'
B ⊗_A κ(𝔭)                       fiber over 𝔭
```

We started with the riddle that $\mathbb{R}[t]$ has maximal ideals not visible to the geometry of $\mathbb{R}$. We end
with a complete algebraic toolkit. The running example $B = \mathbb{Z}[t]/(t^{2} - 2)$ over $\mathbb{Z}$ showed the
trichotomy split / extension / ramified, which is the central rhythm of the rest of the project.

Geometry is next.
