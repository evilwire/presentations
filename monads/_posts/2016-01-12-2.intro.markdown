---
categories: monads
---

## What are monads?

<span class="fragment">
A monad (in $\lambda$-calculus) is an endofunctor from the category
of concrete types, together with two natural transformations blah,
blah, blah, yammer, yammer, yammer. It won't fit on this slide
anyway.
</span>

---

## What are they really?

### Two short answers:

<ol>
    <li class="fragment">
        They are special types of wrappers of datetypes
    </li>

    <li class="fragment">
        They are programmable semi-colons
    </li>
</ol>

<span class="fragment">
    (These two aspects capture 90% of what monads are.*)
</span>

<span class="fragment">
    \* the other 10% is nonsense anyway, as you will see.
</span>

---

### Why are there so many sucky definitions of monads on the web?

<ul>
    <li class="fragment">
        Monads come from category theory
    </li>

    <li class="fragment">
        Enter CS through $\lambda$-calculus (Church)
    </li>

    <li class="fragment">
        Play a significant role only in functional programming
    </li>

    <li class="fragment">
        Operates implicitly in languages like OCamel, Scheme, or Scala
    </li>
</ul>

<span class="fragment">
    To understand Monads, we'll have to be at least a little academic
</span>

---

### A more concrete problem to frame this talk:

#### Writing code to get values from other values.

<ul>
    <li class="fragment">
        arithmetic operations on an input
    </li>

    <li class="fragment">
        reading values from a HashMap
    </li>

    <li class="fragment">
        executing queries from a database
    </li>

    <li class="fragment">
        batching API calls from a network service
    </li>
</ul>

---

### Why are getting things hard?

<ul>
    <li class="fragment">
        they could trigger errors
    </li>

    <li class="fragment">
        the output could have "no value"
    </li>

    <li class="fragment">
        the output could have multiple values
    </li>

    <li class="fragment">
        the output could take a long time
    </li>
</ul>

<span class="fragment">
    In each cases, we are writing the same code again and again and
    again that obfuscates the underlying logic.
</span>
