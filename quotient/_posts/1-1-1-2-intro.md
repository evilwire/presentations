
## Acknowledgement

Talk based entirely on the work of Michael A. Bender and co-authors:

http://vldb.org/pvldb/vol5/p1627_michaelabender_vldb2012.pdf

---

## What are quotient filters?

<span class="fragment">
Probabilistic data structure used to answer whether or not an
element (e.g. "bob") is in a set
</span>

<span class="fragment">
Comparable to the more well-known Bloom filter
</span>

---

### What problems does it solve?

#### Naive approach: `set`

```python
a = set()
a.add("Marlene")
a.add("Robert")

"Marlene" in a
## > True

"Bob" in a
## > False
```

---

### Good bits

<span class="fragment">
   Easy to understand
</span>

<span class="fragment">
   100% accurate
</span>

<span class="fragment">
   Reasonably fast in memory
</span>

---

### What's the problem with `set`?

<span class="fragment">
   Sets are implemented using hash maps
</span>

<span class="fragment">
   We are storing all the objects in memory
</span>

<span class="fragment">
   Storing `set`s on disk requires serializing *everything*
</span>

---

### Filtering: How do we trade space for accuracy?
<span class="fragment">
    Why do we need to store the objects when all we care about
    is membership?
</span>
