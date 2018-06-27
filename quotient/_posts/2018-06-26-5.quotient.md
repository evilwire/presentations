# Quotient Filter

--

## History

Michael Bender formalised the approach as a way to address some 
of Bloom filter's short-comings:

<ul>
    <li class="fragment">multiple hash functions</li>
    <li class="fragment">cannot dynamically resize</li>
    <li class="fragment">storing on SSDs</li>
</ul>

--

## Quotient Filter

Given hash function `h` that hashes objects to $m$-bits,
a quotient filter consists of a hash map with 
$q$-bit binary values as keys and `set`s of $r$-bit 
binary values as values

```python
class QuotientFilter:
  const hash = h;

  def constructor(quotient_size):
    this.quotient_size = quotient_size

    # a map where the keys are m-bit binary value (e.g. integers)
    # values are sets of r-bit binary value
    this.rep = {}
```

--

## Quotient Filter: Adding 

```python
class QuotientFilter:
  # other lines of code

  def add(val):
    quotient, remainder = this.get_fingerprint(this.hash(val))
    this.insert(quotient, remainder)

  def get_fingerprint(hashed_value):
    quotient = hashed_value >> this.quotient_size
    remainder = hashed_value - (quotient << this.quotient_size)
    return quotient, remainder

  def insert(quotient, remainder):
    if quotient not in this.rep:
      this.rep[quotient] = set()

    this.rep[quotient].add(remainder)
```

--

## Quotient Filter: checking membership

```python
class QuotientFilter:
  # other lines of code

  def is_in?(val):
    # check to see if the quotient is in the dictionary and
    # the remainder is in set
    quotient, remainder = this.get_fingerprint(this.hash(val))

    return quotient in this.rep and \
           remainder in this.rep[quotient]
```

--

## Quotient Filter: Observations

<ul>
  <li class="fragment">no false negatives</li>
  <li class="fragment">false positives depend on *hard* collisions</li>
  <li class="fragment">
    hard collision happens with probability

    $$
    1 - \left(1 - \frac{1}{2^p}\right)^n \leq 2^{-r}
    $$
  </li>
  <li class="fragment">
    size is $2^q \cdot 2^r \cdot r$
  </li>
</ul>

--

## Quotient Filter: Resize

```python
class QuotientFilter:
  # other lines

  def insert(hash_val):
    quotient, remainder = this.get_fingerprint(hash_val)

    if quotient not in this.rep:
      this.rep[quotient] = set()

    this.rep[quotient].add(remainder)
```

--

## Quotient Filter: Resize Continued...

```python
class QuotientFilter:

  def resize(quotient_size):
    qf = new QuotientFilter(quotient_size)

    for quotient in this.rep:
      for remainder in this.rep[quotient]
        hash_val = quotient << sizeof(remainder) + remaineder
        new_quotient, new_remainder = qf.get_fingerprint(hash_val)
        qf.insert(new_quotient, new_remainder)

    return qf
```

--

## Quotient Filter: Unions and Intersections

```python
def copy(from QuotientFilter, to QuotientFilter):
  # assume same size
  for quotient, remainders in from.rep:
    if quotient not in to.rep:
      to.rep = set()

    to.rep[quotient] = union(to.rep, remainders)

def union(other QuotientFilter) QuotientFilter:
  qf = new QuotientFilter(this.quotient_size)
  resized_other = other.resize(this.quotient_size)
  copy(from: resized_other, to: qf)

  return qf
```

<span class="fragment">
We can similarly define intersections.
</span>

--

## Quotient Filter: The Good Bits

<ul>
  <li class="fragment">needs only one hash function - faster</li>
  <li class="fragment">scale up/down depending on capacity</li>
  <li class="fragment">can compute size estimates of set</li>
  <li class="fragment">can achieve *data locality*</li>
</ul>

--

## Quotient Filter: Limitations

<ul>
  <li class="fragment">in general, QF requires more storage
    than Bloom Filters (~20% in a control study)</li>
  <li class="fragment">performance degrades as number of elements increases</li>
  <li class="fragment">*probably* still can't delete</li>
</ul>
