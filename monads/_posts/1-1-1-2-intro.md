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
<li class="fragment">They are special types of wrappers of datetypes</li>
<li class="fragment">They are programmable semi-colons</li>
</ol>

(These two aspects capture 90% of what monads are.*) {% fragment %}

\* the other 10% is nonsense anyway, as you will see. {% fragment %}

---

### Why are there so many sucky definitions of monads on the web?

- Monads come from category theory {% fragment %}
- Enter CS through $\lambda$-calculus (Church) {% fragment %}
- Play a significant role only in functional programming {% fragment %}
- Operates implicitly in languages like OCamel, Scheme, or Scala {% fragment %}

To understand Monads, we'll have to be at least a little academic. {% fragment %}

---

### A more concrete problem to frame this talk:

#### Writing code to get values from other values. {% fragment %}

- arithmetic operations on an input {% fragment %}
- reading values from a HashMap {% fragment %}
- executing queries from a database {% fragment %}
- batching API calls from a network service {% fragment %}

---

### Why are getting things hard?

1. they could trigger errors {% fragment %}
2. the output could have "no value" {% fragment %}
3. the output could have multiple values {% fragment %}
4. the output could take a long time (and I want to fork
   threads to do it) {% fragment %}

In each cases, we are writing the same code again and again and
again that obfuscates the underlying logic. {% fragment %}
