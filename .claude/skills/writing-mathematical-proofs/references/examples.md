# Examples

Use these as shape guides, not as templates to copy blindly.

## Iff Proof

```md
**Proposition.** Let f : X → Y be a function. Then f is injective if and only if, for all subsets A, B ⊆ X, the equality f(A ∩ B) = f(A) ∩ f(B) holds.

**Proof.** Assume first that f is injective. The inclusion f(A ∩ B) ⊆ f(A) ∩ f(B) holds for every function. For the reverse inclusion, let y ∈ f(A) ∩ f(B). Then y = f(a) = f(b) for some a ∈ A and b ∈ B. Injectivity gives a = b, so a ∈ A ∩ B, hence y ∈ f(A ∩ B).

Conversely, assume f(A ∩ B) = f(A) ∩ f(B) for all A, B ⊆ X. Let x, x′ ∈ X with f(x) = f(x′). Apply the hypothesis to A = {x} and B = {x′}. Then f(A) ∩ f(B) ≠ ∅, so f(A ∩ B) ≠ ∅. Hence A ∩ B ≠ ∅, which implies x = x′. Therefore f is injective.
```

## Existence and Uniqueness

```md
**Lemma.** Let G be a group and g ∈ G. There exists a unique element h ∈ G such that hg = e.

**Proof.** Existence is immediate: h = g⁻¹ satisfies hg = e. For uniqueness, suppose h′ ∈ G also satisfies h′g = e. Then

h′ = h′e = h′(gg⁻¹) = (h′g)g⁻¹ = eg⁻¹ = g⁻¹ = h.

Thus the element is unique.
```

## Universal-Property Proof

```md
**Lemma.** Products in a category are unique up to unique isomorphism.

**Proof.** Let (P, π₁, π₂) and (P′, π₁′, π₂′) be products of X and Y. Since P is a product, there is a unique morphism u : P → P′ such that π₁′u = π₁ and π₂′u = π₂. Since P′ is also a product, there is a unique morphism v : P′ → P such that π₁v = π₁′ and π₂v = π₂′.

Now vu : P → P satisfies π₁(vu) = π₁ and π₂(vu) = π₂. By uniqueness in the universal property of P, we must have vu = id_P. Similarly uv = id_P′. Hence u is an isomorphism, and its defining equations force it uniquely.
```
