
## Acknowledgement

Talk based entirely on the work of Michael A. Bender and co-authors:

http://vldb.org/pvldb/vol5/p1627_michaelabender_vldb2012.pdf

---

## What are quotient filters?

<span class="fragment">
Probabilistic data structure used to test *with errors* whether or not an
element (e.g. "bob") is in a collection of elements
</span>

<span class="fragment">
Comparable to the more well-known "Bloom filter"
</span>

---

### What problems does it solve?

#### Naive approach

```python
# adding an element
a = set()
a.add("Marlene")
a.add("Robert")

# determine if
"Marlene" in a
## > True

"Bob" in a
## > False
```

---

### What's the problem with `set`?

<span class="fragment">
   Sets are maps
</span>

<span class="fragment">
   Space complexity is $O(n)$ where $n$ is size of the set
</span>

---

### How do we trade space for accuracy?
<span class="fragment">
    Why do we need to store the objects when all we care about
    is membership?
</span>
