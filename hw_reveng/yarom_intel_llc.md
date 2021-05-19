## Background


## Problems

- Modern Intel processors use undisclosed hash functions to map blocks into LLC slices.
- Knowing the mapping will help the attacker to mount an attack and the defender to do
page coloring.
- Recover the hash function for a 6-core processor.

## Insights

- For processors with a core count of a power of 2, the hash function does not depend on
the set index bits. This, however, does not hold true for non-power-of-two cases.
- Use access timing variations.

## Approach

- Evict the line from L1 and L2 before measuring.

## Takeaway


## Questions

