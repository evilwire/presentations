# Monads Defined

<span class="fragment">
    (yet again)
</span>

--

## Code Patterns

For a container `C[T]` of type $T$ (e.g. List, Burrito)

```scala
/** create a container from a single object */
def wrap(t: T): C[T]

/** apply foo to each object in c and put in a new container */
def map(c: C[T], foo: T => S): C[S]

/** break open each container and pour the content into a container
    of type T */
def flatten(cc: C[C[T]]): C[T]
```

--

## Monoid (More Concretely)

Monoids of a type `T` is a containing data structure which is equipped
with the methods described above, such that

```scala
map(wrap(a), foo) = wrap(foo(a))

// def flatMap = flatten(map(_, _))
map(dbWrapped, flatMap(_, foo)) = flatMap(dbWrapped, foo)
```

--

## How are these definitions related?

<ul>
    <li class="fragment">
        `map` is the method that enforces "functoriality"
    </li>

    <li class="fragment">
        `wrap` and `flatten` define the two natural transformations
    </li>

    <li class="fragment">
        `map(wrap(a), foo) = wrap(foo(a))` ensures the naturality of wrap
    </li>

    <li class="fragment">
        `flatMap(wrap(a), wrap(foo(_))) = wrap(foo(a))` enforces the naturality
        of `flatten`
    </li>
</ul>