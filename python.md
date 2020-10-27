# Python cheatsheet

## Tuples and lists
### Unpacking
`
t = (0, 1, 2, (3, 4, 5, 6, 7, 8))
a, b, _, (d, e, *f) = t
`

### Enumerating
`for i, value in enumarate(l1):`

### Zipping
`for a, b in zip(l1, l2):`

## Dictionaries

### Check if key exists
`'foo' in d1`

### Get value
`d1.get('foo')`

### Remove
`d1.pop('bar', 'bar not found')`

### Comprehend
`squares = { i: i**2 for i in range(1,10) }`

### Merge (Python 3.9)
`d3 = d1 | d2`

## Files
`with open('filename', 'r') as f:
  file = f.read()`
