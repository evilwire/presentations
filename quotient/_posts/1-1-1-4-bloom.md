# Bloom Filters

--

## History

Invented by Burton Bloom in 1970 as a proposal to resolve
problems of hyphenation rules of around 500K words

--

## Idea

We start with a collection of hash functions

`hashes = [h_1,...,h_k]`

--

## Bloom Filter: under the hood

<span class="fragment">
A bloom filter is a collection of $k$ `set`s
$S_1, S_2,...,S_k$
</span>

--

```python
class BloomFilter(object):
  def constructor(hashes, dictionaries):
    this.hashes = hashes
    this.sets = [
      set()
      for i from 1 to len(hashes)
    ]
```
<span class="fragment">
*the above is not python
</span>

--

### Bloom Filter: adding

```python
class BloomFilter(object):
  # other lines of code

  def add(val):
    # for each hash function...
    for hash, index in this.hashes:

      # use it to hash the value
      hashed_value = hash(val)

      # store the hashed value in the dictionary
      this.sets[index].add(hashed_value)

```

--

### Bloom Filter: checking membership

```python
class BloomFilter(object):
  # other lines of code

  def is_in?(val):
    # true if the value is in all the sets;
    # false otherwise
    for set in this.sets:
      if val not in set:
        return False

    return True
```

<span class="fragment">
we can likewise derive the union and intersection
of bloom filters
</span>

--

### Bloom Filter: Observations

<ul>
  <li class="fragment">
    no false negatives
  </li>
  <li class="fragment">
    false positives depends on hash collisions
  </li>
  <li class="fragment">
    a collision happens with probability $p = m/2^n$
  </li>
</ul>

--

### Bloom Filter: trade-offs

<ul>
  <li class="fragment">more hash functions = more accurate</li>
  <li class="fragment">more hash functions = slower</li>
  <li class="fragment">more bytes per hash = more accurate</li>
  <li class="fragment">more bytes per hash = more space</li>
</ul>

--

### Bloom Filter Optimality

We want Bloom filter with $n$ elements with an error
rate $e$

$$
hello
$$

--

### Bloom Filter: The Good Bits

<ul>
  <li class="fragment">need more hash functions</li>
  <li class="fragment">cannot dynamically resize</li>
  <li class="fragment">cannot dynamically resize</li>
</ul>

--

## Bloom Filter: Limitations

<ul>
  <li class="fragment">need more hash functions</li>
  <li class="fragment">cannot dynamically resize</li>
  <li class="fragment">cannot dynamically resize</li>
</ul>