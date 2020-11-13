# Python cheatsheet

## Debugging
### Assert
    assert a > 0, 'a is less than zero but should not be'

### Triggering debugger
#### Then use s to step, n for next, r to return, c to continue, l to list stack
    breakpoint()


## Strings
### Check if in a string
    'rau' in 'Diogo Rau'.lower()

### Partition a string into 3 parts: the text before the matched part,
### the matched part, and the text after the matched part.
    'Hello world!'.partition(' ')

### Regular expressions
    re.sub(r'^`(.*)`.*$', r'    \1', l, flags=re.MULTILINE)

## Tuples and lists

### Creating
    t = tuple(['a', 'b'])

### Lengths and counts
    len((2, 3, 5)) # 3
    (2, 3, 5, 3, 3, 3).count(3) # 4

### Concatenating and repeating
    (1, 2, 3) + (4, 5, 6)
    (1, 2, 3) * 4

### Slicing
#### Get every third element
    l1[::3]

### Unpacking
    t = (0, 1, 2, (3, 4, 5, 6, 7, 8))
         a, b, _, (d, *e, f) = t

### Reversing in-place and not-in-place
    l1.reverse()
    l1[::-1]

### Enumerating
    for i, value in enumerate(l1):

### Zipping
    for a, b in zip(l1, l2):

### Sorting
    sorted([['foo', 3], ['bar', 8], ['baz', 5]],
           key = lambda x: x[1])

### Mapping
Generally, a list comprehension is better, but a list comprehension will do all at once, whereas map is lazy.

    map(str, range(10**100)) # OK for map, bad for comprehension.

## Dictionaries

### Check if key exists
    'foo' in d1

### Get value
    d1.get('foo')
    d1.get('soup', 'no soup for you')

### Remove
    d1.pop('bar', 'bar not found')

### Comprehend
    squares = { i: i**2 for i in range(1,10) }

### Merge (Python 3.9)
    d3 = d1 | d2


## Sets
    5 in (set(range(3)) | {3, 4, 5}) & {1, 5}

## Comprehensions

### Make a comprehension
    letters = [char for char in 'Diogo']

### Instead of using map:
    [name for name in ['foo', 'bar', 'baz'] if name.startswith('ba')]

### Instead of using filter:
    [name.capitalize() for name in ['foo', 'bar', 'baz']

## Generators
### Use parens instead of brackets to make a generator instead of a list:
    (x for x in range(1000))

## Dates and times
### Get current time
    datetime.datetime.now()

### Get timestamp
    datetime.datetime.now().timestamp()

### Convert timestamp
    datetime.datetime.fromtimestamp(1604012281)

### Print in ISO format, with a space
    datetime.datetime.now().isoformat(' ')

## Files
r = read, w = write, r+ = read+write, a = append,
b = binary, t = text

    with open('filename', 'r+') as f:
        lines = [l.strip() for l in f]
        f.seek(0)
        f.writelines(lines)
        file = f.read() # Or read entire file


## Objects
### Classes and instances
    class Person():
        def __init__(self):
            self.age = None

    person = Person()
    isinstance(person, Person) # True
    hasattr(person, 'age') # True

## Operating system
Many operating system commands with their Python counterparts

    os.system('echo "hello"')
    os.getcwd()
    os.listdir('.')
    os.mkdir('Docs')
    os.remove('filename')
    os.rmdir('Docs')
    os.rename('foo.txt', 'bar.txt')
    os.path.join('folder', 'filename')
    os.path.exists(path)
    os.path.basename(path)
    os.path.dirname(path)
    name, extension = os.path.splitext('file.txt')
