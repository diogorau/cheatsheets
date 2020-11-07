# Numpy cheatsheet

## General
`np.uniques([1, 3, 2, 3, 1, 2, 3, 5])

## Statistics
### Sum rows and columns
`a.sum(axis = 0)`
`a.sum(axis = 1)`

### Count positives
`(a > 0).sum()`

## Random

### Generate a random 5 x 7 matrix
`np.random.randn(5, 7)`
`np.random.normal(size = (5, 7))`

### Generate a 3 x 5 matrix of zeros or ones or identities
`np.zeros((3, 5))`
`np.ones((3, 5))`
`no.eyes((3, 5))`

### Generate a sequence or a 5 x 2 matrix from 0 to 10
`np.arange(11)`
`np.arange(11).reshape(5, 2)`

### Shuffle
`np.random.permutation(['a', 'b', 'c'])`

## Linear algebra
### Transpose matrix X
`X.T`

### Multiply matrices
`np.dot(X.T, X)`
`X.T.dot(X)`
`X.T @ X`

### Take ternary, vectorized, e.g., get sign
`np.where(a >= 0, 1, -1)`
