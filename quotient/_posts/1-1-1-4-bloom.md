# Bloom Filters

--

## Idea

<span class="fragment">
We have a collection of functions `hashes = [h_1,...,h_k]`
with signatures 
</span>

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

<span class="fragment">
(and by "=", I mean naturally equivalent.)
</span>

--

### Categories in CS (Concrete Types)

<ul>
    <li class="fragment">
        objects are the universe of data structures
    </li>

    <li class="fragment">
        morphisms are methods to convert one data structure to another
    </li>
</ul>

--

### Monads (less math, a little less abstract)

<span class="fragment">
A monad $M$ is a way to associate any given data structure $A$
with another data structure $M[A]$ that allows us to:
</span>

<ul>
    <li class="fragment">
        create an instance of $M[A]$ from a given instance of $A$ for any data
        structure $A$ (embed)
    </li>

    <li class="fragment">
        obtain an instance of $M[A]$ from a given instance of $M[M[A]]$ for any
        data structure $A$ (flatmap)
    </li>
</ul>

--

### Monads (continued)

<span class="fragment">
If there is a function that transforms $A$ into $B$, then
the monad must "lift" the transformation. "Lift" must be
compatible with `return` and `bind`.
</span>

--

## Relations to the literature

<ul>
    <li class="fragment">
        "embed" is the same as "return" in literature
    </li>

    <li class="fragment">
        "flatmap" + naturality of monads is "bind" in literature
    </li>
</ul>

--

## Why are Monads Useful (version 1)

<ul>
    <li class="fragment">
        Elevates you from an engineer to an engineer with jargon #sarcasm
    </li>

    <li class="fragment">
        A unified way of looking at the problem of "getting things"
    </li>

    <li class="fragment">
        Forms the backbone of pure functional programming
    </li>
</ul>