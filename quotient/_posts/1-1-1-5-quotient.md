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

Given  `h` that hashes objects to `m`-bits,
a quotient filter consists of a hash map with 
$q$-bit binary values as keys and `set`s of $r$-bit 
binary values as values

```python
class QuotientFilter:
  def constructor(hash, quotient_size, remainder_size)
    this.hash = hash
    this.quotient_size = quotient_size 
    this.remainder_size = remainder_size
    
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
    hashed_value = this.hash(val)  
    
    quotient = hashed_value >> this.quotient_size
    remainder = hashed_value - quotient << this.quotient_size

    if quotient not in this.rep:
      this.rep[quotient] = set()
     
    this.rep[quotient].add(remainder)
```   

--

## Quotient Filter: checking membership

something


--

## Quotient Filter: Shrink/Expand

--

## Quotient Filter: Merge
