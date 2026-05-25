# Python Data Structures — Complete Quick Reference

> Four structures. Know when to use which. Master them all.

---

## The Big Picture

```python
my_list  = [1, 2, 3, 2]          # ordered, changeable, allows duplicates
my_tuple = (1, 2, 3, 2)          # ordered, LOCKED, allows duplicates
my_dict  = {"a": 1, "b": 2}      # key-value pairs, changeable
my_set   = {1, 2, 3, 2}          # unique items only → {1, 2, 3}
```

| Structure | Ordered | Changeable | Duplicates | Access By |
|-----------|:-------:|:----------:|:----------:|:---------:|
| List `[]`   | ✅ | ✅ | ✅ | Index `[0]` |
| Tuple `()`  | ✅ | ❌ | ✅ | Index `[0]` |
| Dict `{:}`  | ✅ | ✅ | Keys: ❌ | Key `["k"]` |
| Set `{}`    | ❌ | ✅ | ❌ | — |

---

---

# 📋 LIST

## What is it?
An ordered, changeable collection. Like a shopping cart — add, remove, reorder freely.

```python
fruits = ["apple", "banana", "cherry", "date", "elderberry"]
#index:      0         1         2        3          4
#neg index: -5        -4        -3       -2         -1
```

---

## Indexing
```python
fruits[0]    # "apple"       ← first item
fruits[-1]   # "elderberry"  ← last item
fruits[-2]   # "date"        ← second from last
```

---

## Slicing — `list[start : stop : step]`

| Part | Meaning | Default |
|------|---------|---------|
| `start` | Where to begin | `0` (first item) |
| `stop` | Where to end — **NOT included** | end of list |
| `step` | Jump size | `1` (every item) |

```python
fruits = ["apple", "banana", "cherry", "date", "elderberry"]

fruits[1:3]    # ["banana", "cherry"]      start=1, stop=3 (not included)
fruits[:2]     # ["apple", "banana"]       start defaults to 0
fruits[2:]     # ["cherry","date","elderberry"]  stop defaults to end
fruits[::2]    # ["apple", "cherry", "elderberry"]  every 2nd item
fruits[::3]    # ["apple", "date"]         every 3rd item
fruits[::-1]   # ["elderberry","date","cherry","banana","apple"]  REVERSED!
fruits[3:0:-1] # ["date", "cherry", "banana"]  reverse from index 3 to 1
```

> 💡 **`step=-1` reverses the list** — the most used trick you'll see in ML code.

---

## Modifying
```python
fruits = ["apple", "banana", "cherry"]

fruits[1] = "blueberry"          # change item        → ["apple","blueberry","cherry"]
fruits.append("date")            # add to END         → [..., "date"]
fruits.insert(1, "avocado")      # add at index 1
fruits.remove("apple")           # remove by VALUE    ← error if not found
fruits.pop()                     # remove LAST item, returns it
fruits.pop(0)                    # remove at index 0, returns it
del fruits[0]                    # delete at index 0
fruits.clear()                   # empty the list     → []
```

---

## Useful Methods
```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]

len(numbers)          # 8         ← total items
numbers.count(1)      # 2         ← how many times 1 appears
numbers.index(5)      # 4         ← index of first 5
numbers.sort()        # [1,1,2,3,4,5,6,9]  sorts IN PLACE
numbers.reverse()     # reverses IN PLACE
sorted(numbers)       # returns NEW sorted list, original unchanged
```

---

## List Comprehension
```python
# Old way
squares = []
for n in range(5):
    squares.append(n ** 2)

# ✅ Comprehension — same result, one line
squares = [n**2 for n in range(5)]
print(squares)   # [0, 1, 4, 9, 16]

# With condition
evens = [n for n in range(10) if n % 2 == 0]
print(evens)     # [0, 2, 4, 6, 8]
```

---

## Looping
```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:                    # simple loop
    print(fruit)

for i, fruit in enumerate(fruits):     # with index
    print(f"{i}: {fruit}")
# 0: apple  1: banana  2: cherry
```

---

## Critical Rules
```python
# ✅ Lists can hold mixed types
mixed = [1, "hello", True, 3.14, [1, 2]]

# ✗ IndexError — index out of range
fruits[99]

# remove() vs pop()
fruits.remove("apple")   # by VALUE
fruits.pop(0)            # by INDEX
```

---

---

# 📦 TUPLE

## What is it?
An ordered, **immutable** (locked) collection. Once created — it cannot change.
Use it for data that should never be modified.

```python
rgb      = (255, 128, 0)       # color — never changes
location = (28.6139, 77.2090)  # GPS coords — fixed
```

---

## Indexing & Slicing
Identical to lists — same zero-based indexing.
```python
rgb = (255, 128, 0)

rgb[0]     # 255
rgb[-1]    # 0
rgb[1:]    # (128, 0)
rgb[::-1]  # (0, 128, 255)   ← reversed tuple
```

---

## Critical Rule — IMMUTABLE
```python
point = (3, 5)
point[0] = 10   # ✗ TypeError: 'tuple' object does not support item assignment
```

---

## Single Item Tuple — The Gotcha
```python
single     = (42,)   # ✅ tuple  ← comma is required!
not_a_tuple = (42)   # ✗ just an integer

print(type(single))      # <class 'tuple'>
print(type(not_a_tuple)) # <class 'int'>
```

---

## Tuple Unpacking
```python
point = (3, 5)
x, y = point
print(x)   # 3
print(y)   # 5

# Swap variables — Pythonic way
a, b = 10, 20
a, b = b, a
print(a, b)   # 20 10

# Unpack with *rest
first, *rest = (1, 2, 3, 4, 5)
print(first)   # 1
print(rest)    # [2, 3, 4, 5]
```

---

## Returning Multiple Values
```python
def min_max(numbers):
    return min(numbers), max(numbers)   # returns a tuple

low, high = min_max([3, 1, 7, 2, 9])
print(low, high)   # 1  9
```

---

## What you CAN do
```python
t = (3, 1, 4, 1, 5)

len(t)          # 5
t.count(1)      # 2     ← how many times 1 appears
t.index(4)      # 2     ← index of 4
min(t)          # 1
max(t)          # 5
t + (9, 2)      # (3,1,4,1,5,9,2)  ← creates NEW tuple
```

---

## List vs Tuple — Quick Decision
```python
# Use LIST when data changes
cart = ["milk", "eggs"]
cart.append("bread")          # ✅

# Use TUPLE when data is fixed
IMAGE_SIZE  = (224, 224)      # ML model input — never changes
TRAIN_SPLIT = (0.8, 0.2)
```

---

---

# 📖 DICTIONARY

## What is it?
A collection of **key: value** pairs. Look up any value instantly using its key.
Like a real dictionary — look up a word (key) to get its definition (value).

```python
person = {"name": "Vikram", "age": 30, "city": "Delhi"}
```

---

## Accessing Values
```python
person = {"name": "Vikram", "age": 30, "city": "Delhi"}

person["name"]                  # "Vikram"  ← direct access
person.get("age")               # 30        ← safe access
person.get("email")             # None      ← no error if missing
person.get("email", "N/A")      # "N/A"    ← default if missing

# ✗ person["email"]  → KeyError if key doesn't exist
```

> 💡 **Always prefer `.get()` over `[]`** when key might not exist.

---

## Adding & Updating
```python
person = {"name": "Vikram", "age": 30}

person["city"] = "Delhi"                       # add new key
person["age"]  = 31                            # update existing
person.update({"age": 32, "job": "Engineer"}) # update multiple
```

---

## Removing
```python
person = {"name": "Vikram", "age": 30, "city": "Delhi"}

person.pop("city")    # removes & RETURNS value → "Delhi"
del person["age"]     # deletes key-value pair
person.clear()        # empties entire dict → {}
```

---

## Checking Keys
```python
person = {"name": "Vikram", "age": 30}

"name"  in person      # True
"email" in person      # False
"age"   not in person  # False
```

---

## Useful Methods
```python
person = {"name": "Vikram", "age": 30, "city": "Delhi"}

person.keys()     # dict_keys(["name", "age", "city"])
person.values()   # dict_values(["Vikram", 30, "Delhi"])
person.items()    # dict_items([("name","Vikram"), ("age",30), ("city","Delhi")])
len(person)       # 3
```

---

## Looping
```python
person = {"name": "Vikram", "age": 30, "city": "Delhi"}

for key in person:                    # loop keys
    print(key)

for value in person.values():         # loop values
    print(value)

for key, value in person.items():     # loop both ← most common
    print(f"{key}: {value}")
# name: Vikram
# age: 30
# city: Delhi
```

---

## Nested Dictionary
```python
users = {
    "u001": {"name": "Alice", "role": "admin"},
    "u002": {"name": "Bob",   "role": "viewer"},
}

users["u001"]["name"]   # "Alice"
users["u002"]["role"]   # "viewer"
```

---

## Dictionary Comprehension
```python
squares = {n: n**2 for n in range(1, 6)}
print(squares)   # {1:1, 2:4, 3:9, 4:16, 5:25}

# With condition
even_sq = {n: n**2 for n in range(1, 6) if n % 2 == 0}
print(even_sq)   # {2:4, 4:16}
```

---

## Critical Rules
```python
# Keys must be UNIQUE — duplicates overwrite
d = {"a": 1, "a": 2}
print(d)   # {"a": 2}  ← first value gone!

# Keys must be IMMUTABLE — strings, ints, tuples only
d = {[1,2]: "val"}   # ✗ TypeError — list can't be a key
d = {(1,2): "val"}   # ✅ tuple key is fine
```

---

---

# 🔵 SET

## What is it?
An unordered collection of **unique** items. Duplicates are automatically removed.

```python
tags = {"python", "ml", "ai", "python"}
print(tags)   # {"ml", "ai", "python"}  ← duplicate removed!
```

---

## Creating a Set
```python
s = {1, 2, 3}                  # literal
s = set([1, 2, 2, 3, 3, 3])   # from list → {1, 2, 3}
s = set("hello")               # from string → {'h','e','l','o'}

# ⚠️ Empty set
empty = set()   # ✅ correct
empty = {}      # ✗ this is an empty DICT, not a set!
```

---

## Critical Rule — UNORDERED, NO INDEX
```python
s = {3, 1, 4, 1, 5}
print(s)    # {1, 3, 4, 5}  ← order not guaranteed, no duplicates

s[0]        # ✗ TypeError — sets have no index
```

---

## Adding & Removing
```python
skills = {"python", "sql"}

skills.add("ml")                  # add one item
skills.update(["git", "docker"])  # add multiple

skills.remove("sql")    # ✗ KeyError if not found
skills.discard("sql")   # ✅ safe — no error if missing
skills.pop()            # removes a RANDOM item
skills.clear()          # empties the set
```

---

## Set Operations — The Superpower

```python
a = {1, 2, 3, 4, 5}
b = {4, 5, 6, 7, 8}
```

```
a = [ 1  2  3  4  5 ]
b =          [ 4  5  6  7  8 ]
```

```python
a | b   # UNION         → {1,2,3,4,5,6,7,8}   everything from both
a & b   # INTERSECTION  → {4,5}                only what's in BOTH
a - b   # DIFFERENCE    → {1,2,3}              in a but NOT in b
a ^ b   # SYM.DIFF      → {1,2,3,6,7,8}        in ONE but NOT both
```

---

## Subset & Superset
```python
a = {1, 2, 3}
b = {1, 2, 3, 4, 5}

a.issubset(b)      # True  ← all of a is inside b
b.issuperset(a)    # True  ← b contains all of a
a.isdisjoint({6})  # True  ← no items in common
```

---

## Membership Check — Sets are FAST
```python
allowed = {"alice", "bob", "charlie"}

"alice"   in allowed   # True
"mallory" in allowed   # False

# ✅ Sets are faster than lists for `in` checks
# Especially important with large data
```

---

## Useful Methods
```python
s = {3, 1, 4, 1, 5, 9}

len(s)        # 5
min(s)        # 1
max(s)        # 9
sum(s)        # 22
sorted(s)     # [1, 3, 4, 5, 9]  ← returns a LIST
```

---

---

# 🤖 AI/ML Connection

```python
# LIST — training data, predictions, batch results
labels  = ["cat", "dog", "cat", "bird"]
scores  = [0.91,  0.87,  0.95,  0.76]
for label, score in zip(labels, scores):
    print(f"{label}: {score}")

# TUPLE — fixed config that should never change
IMAGE_SIZE   = (224, 224)
TRAIN_SPLIT  = (0.8, 0.2)

# DICT — model config, label maps, JSON/API responses
model_config = {"lr": 0.001, "epochs": 50, "optimizer": "adam"}
label_map    = {"cat": 0, "dog": 1, "bird": 2}

# Count word frequency (NLP)
text = "the cat sat on the mat the cat"
freq = {}
for word in text.split():
    freq[word] = freq.get(word, 0) + 1
# {"the": 3, "cat": 2, "sat": 1, "on": 1, "mat": 1}

# SET — vocabulary building, deduplication
tokens = ["the", "cat", "sat", "on", "the", "mat", "the"]
vocab  = set(tokens)
# {"the", "cat", "sat", "on", "mat"}

# Find missing features between train and test
train_cols = {"age", "income", "credit_score", "loan_amount"}
test_cols  = {"age", "income", "credit_score", "zipcode"}
missing    = train_cols - test_cols   # {"loan_amount"}
extra      = test_cols - train_cols   # {"zipcode"}
```

---

## When to Use What — Final Cheatsheet

| Situation | Use |
|-----------|-----|
| Ordered items that change | `list` |
| Fixed/constant data | `tuple` |
| Return multiple values from function | `tuple` |
| Key-value lookup | `dict` |
| Count occurrences | `dict` |
| Remove duplicates from list | `set` |
| Check membership fast | `set` |
| Compare two collections | `set` operations |
| Store ML config | `dict` |
| Store training labels | `list` |