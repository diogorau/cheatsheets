# Jupyter cheatsheet

## Magic commands

### Run
`%run script.py arg1`

### Load and view
`%load script.py`
`%pycat script.py`

### Export
`%%writefile script.py`

### Time a single line
`%timeit foo()`

### Time a whole cell
`%%timeit`

### See namespace
#### You can show just the strings, or get all in a variable, or get all in a detailed table
`%who`
`%who str`
`%who_ls`
`%whos`

### Get and set environment variables
`%env`
`%env var`
`%env var value`

### List the magic functions
`%magic`
`%quickref`

### Paste from clipboard
`%paste`
`%cpaste`
