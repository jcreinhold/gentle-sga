# Category-Theoretic Techniques

Use this file for proof method, not for a category theory survey.

## Prove by Universal Property

When an object is defined categorically, prefer its universal property to its construction.

Workflow:

1. State the representing problem or factorization problem.
1. Produce the required map.
1. Prove it is the unique map with that property.

This often replaces construction-level element chasing with one existence check and one uniqueness check.

## Uniqueness Up to Unique Isomorphism

When two objects satisfy the same universal property:

1. Use the first universal property to obtain a canonical map from the first object to the second.
1. Use the second to obtain the reverse map.
1. Show the composites are the unique endomorphisms compatible with the structure, hence identities.

Say “unique up to unique isomorphism” only when the isomorphism itself is forced uniquely.

## Reduce with Representability and Yoneda

Use representability or Yoneda when an object-level statement is really a statement about maps into or out of the
object.

Typical moves:

- replace comparison of objects by comparison of represented functors
- prove an isomorphism by producing a natural bijection of hom-sets
- test equality or isomorphism by how the object behaves against arbitrary probes

Do not invoke Yoneda as decoration. Say what representable functor or natural bijection you are actually using.

## Check Naturality by Squares

Naturality claims are not vibes. Write the square, state the morphism being tested, and check commutativity.

Typical pattern:

1. Fix a morphism `f`.
1. Write both composites around the square.
1. Show they agree, usually by functoriality, a defining formula, or a universal property.

For long arguments, say whether you are checking naturality in the source variable, the target variable, or both.

## Use Adjunctions as Transport

An adjunction lets you move a problem across a hom-set bijection.

Use it to:

- convert existence or uniqueness of one kind of map into another
- identify free or cofree constructions
- prove preservation of limits or colimits by the appropriate adjoint

When speaking about mates, say exactly which square or 2-cell is being transported. Do not use mate language if a direct
adjunction statement is clearer.

## Use Initial, Terminal, Free, and Cofree Reasoning

These are proof engines.

- initial object / algebra: prove uniqueness of maps out
- terminal object / coalgebra: prove uniqueness of maps in
- free object: prove statements by the universal property against forgetful functors
- cofree object: dual reasoning when it exists

If the object is free, many later proofs should reduce to what happens on generators.

## Check Functoriality and Natural Transformations Explicitly

To prove that something is a functor:

1. define the object map
1. define the morphism map
1. check identities
1. check composition

To prove that something is a natural transformation:

1. define the component at an arbitrary object
1. check the naturality square

Never stop at “this is clearly functorial”.

## Use Exactness and Factorization at the Right Level

For kernels, cokernels, images, pullbacks, pushouts, and exact sequences:

- state the exactness or factorization claim in the ambient category
- keep track of the zero morphism or mono/epi hypotheses being used
- distinguish image factorization from chosen subobject equality
- say when a pullback or pushout is being used as the mechanism behind the factorization

Do not collapse “factors through”, “is equal to”, and “is isomorphic to” into one phrase.

## Diagram Chase with Discipline

A clean chase names:

- the element or morphism being chased
- the square or triangle used at each step
- the conclusion after each move

If the chase is really a universal-property proof, rewrite it that way. If it is really an exactness proof, say which
exactness clause is active.

## Equality, Isomorphism, Equivalence

Keep the comparison species exact.

- equality: literal sameness in the ambient framework
- isomorphism: invertible morphism in a 1-category
- equivalence: weaker notion, often categorical or homotopical
- correspondence / bijection: relationship between sets of morphisms or objects, not sameness of objects

Many proof errors are comparison-species errors.
