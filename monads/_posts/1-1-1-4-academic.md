# The Academic Stuff

(yay) {% fragment %}

--

## Abstract Categories

- a "class" of objects {% fragment %}

- for any two objects, there is a "class" of arrows called
  morphisms (each representing a type of relationship between these two
  objects) {% fragment %}

- the pair of objects and morphisms form a category if morphisms
  satisfy four main axioms (i.e. there is an identity morphism, there's
  composition, composition is associative, etc) {% fragment %}

--

## Functors

<span class="fragment">
$F: \mathcal{C} \rightarrow \mathcal{D}$ is a functor if for
every $C$ in $\mathcal{C}$, $F(C)$ is an object in $\mathcal{D}$, and
for every morphism $f: C \rightarrow C'$ in $\mathcal{C}$,
$F(f): F(C) \rightarrow F(C')$ is a morphism in $\mathcal{D}$.
</span>

--

## Natural Transformations

<span class="fragment">
For two functors $F, G: \mathcal{C} \rightarrow \mathcal{D}$, a natural
transformation $\mu$ from $F$ to $G$ is a choice of one morphism
$\mu_C: F(C) \rightarrow G(C)$ for each $C$ such that for any morphism
$f: C \rightarrow D$ in $\mathcal{C}$,
$$
G(f) \circ \mu_C = \mu_D \circ G(f)
$$
</span>

--

### Monads in the language of categories

<span class="fragment">
A monad is an endofunctor $M$ on a category $\mathcal{C}$ is an
endofunctor $M: \mathcal{C} \rightarrow \mathcal{C}$ together with
natural transformations:
$$
\mu: 1_T \longrightarrow M,\;\;\; \nu: M^2 \longrightarrow M
$$
<br \>
such that
<br \>
$$
\nu \circ \mu M = \nu \circ M \mu,\;\;\; \nu \circ M^2 \nu = \nu \circ \nu M^2
$$
</span>

(and by "=", I mean naturally equivalent.) {% fragment %}

--

### Categories in CS

#### Concrete Types {% fragment %}
<ul>
<li class="fragment">
objects are the universe of data structures (e.g.
`String`, `Int`, `CheckingAccount[? >: Person]`)
</li>
<li class="fragment">
morphisms are methods to convert one data structure to another
(e.g. `len(s: String): Int`, `buyStuff(money: NonNegativeInt): Thing`)
</li>
<ul>

--

### Monads (less math, a little less abstract)

A monad $M$ is a way to associate any given data structure $A$
with another data structure $M[A]$ that allows us to: {% fragment %}

<ol>
<li class="fragment">
create an instance of $M[A]$ from a given instance of $A$ for any data
structure $A$ (embed)
</li>

<li class="fragment">
obtain an instance of $M[A]$ from a given instance of $M[M[A]]$ for any
   data structure $A$ (flatmap)
</li>
</ol>

--

### Monads (continued)

<span class="fragment">
If there is a function that transforms $A$ into $B$, then
the monad must "lift" the transformation. "Lift" must be
compatible with `return` and `bind`.
</span>

--

### What does it mean when Scala folks say `Option[?]` is a monoid?

`Option` associates a type `T` with `Option[T]` and:

- embed: `Some`
- flatmap: `_.flatMap[T](_.get)`

Via `map`, any `T` function is lifted to a function on `Option[T]`

--

## Relations to the literature

- "embed" is the same as "return" in literature
- "flatmap" + naturality of monads is "bind" in literature

--

## Why are Monads Useful (version 1)

- Elevates you from an engineer to an engineer with jargon #sarcasm {% fragment %}
- A unified way of looking at the problem of "getting things" {% fragment %}
- Forms the backbone of pure functional programming {% fragment %}