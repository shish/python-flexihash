flexihash-py
============

![Unit Tests](https://github.com/shish/flexihash-py/workflows/Unit%20Tests/badge.svg)

A python port of https://github.com/pda/flexihash , aiming for 1:1 compatibility


Usage Example
-------------

```
import flexihash

hash = flexihash.Flexihash()

# bulk add
hash.addTargets(['cache-1', 'cache-2', 'cache-3'])

# simple lookup
hash.lookup('object-a')  # "cache-1"
hash.lookup('object-b')  # "cache-2"

# add and remove
hash \
  .addTarget('cache-4') \
  .removeTarget('cache-1')

# lookup with next-best fallback (for redundant writes)
hash.lookupList('object', 2)  # ["cache-2", "cache-4"]

# remove cache-2, expect object to hash to cache-4
hash.removeTarget('cache-2')
hash.lookup('object')  # "cache-4"
```
