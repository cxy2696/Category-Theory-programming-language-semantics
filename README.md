# Categories

A category $\mathcal{C}$ consists of:
A collection of objects (e.g., types in a programming language).

For each pair of objects $A, B \in \mathcal{C}$, a set of morphisms $\text{Hom}_{\mathcal{C}}(A, B)$ (e.g., functions $A \to B$).

Composition $\text{Hom}{\mathcal{C}}(B, C) \times \text{Hom}_{\mathcal{C}}(A, B) \to \text{Hom}_{\mathcal{C}}(A, C)$.

For each object $A$, an identity morphism $\text{id}A \in \text{Hom}{\mathcal{C}}(A, A)$
These satisfy:

Associativity: For $f: A \to B$, $g: B \to C$, $h: C \to D$, $(h \circ g) \circ f = h \circ (g \circ f)$.

Identity: For $f: A \to B$, $f \circ \text{id}_A = f = \text{id}_B \circ f$.

In Hask, objects are Haskell types (e.g., Int, Bool), and morphisms are functions (e.g., length :: String -> Int). Composition is function composition, e.g., (length . show) :: Int -> Int.
Goal (a): Categories model programming language structure, enabling semantic definitions.

Goal (d): Programs are interpreted as morphisms in denotational semantics.

# Functors

A functor $F: \mathcal{C} \to \mathcal{D}$ maps:

Objects: $A \in \mathcal{C} \mapsto F(A) \in \mathcal{D}$.

Morphisms: $f: A \to B \mapsto F(f): F(A) \to F(B)$.
Satisfying:

Identity: $F(\text{id}A) = \text{id}{F(A)}$.

Composition: $F(g \circ f) = F(g) \circ F(f)$.

The Maybe functor in Hask maps a type A to Maybe A and a function f :: A -> B to:

fmap f :: Maybe A -> Maybe B

fmap f Nothing = Nothing

fmap f (Just x) = Just (f x)

Theorem: Functor Laws

For a functor $F: \mathcal{C} \to \mathcal{D}$:

$F(\text{id}A) = \text{id}{F(A)}$.

$F(g \circ f) = F(g) \circ F(f)$.

Proof
Identity: By functor definition, $F$ preserves identities, so $F(\text{id}A) = \text{id}{F(A)}$.

Composition: For $f: A \to B$, $g: B \to C$, functoriality ensures $F(g \circ f) = F(g) \circ F(f)$, as $F$ respects composition in $\mathcal{C}$.

Goal (a): Functors model type constructors (e.g., Maybe, List) for data transformations.

Goal (b): Proofs verify functor properties.

Goal (c): Supports denotational semantics for functional transformations.


A natural transformation $\eta: F \to G$ between functors $F, G: \mathcal{C} \to \mathcal{D}$ is a family of morphisms $\eta_A: F(A) \to G(A)$ for each $A \in \mathcal{C}$, such that for any $f: A \to B$

Goal (a): Models polymorphic transformations in semantics.

Goal (b): Naturality proofs build rigor.

Goal (c): Ensures type-consistent program transformations.

