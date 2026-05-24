# Python Variables — Quick Reference

## What is a Variable?
A variable is a **named container** that stores a value in memory.
Think of it like a labeled box — you put something in it and refer to it by name.

```python
name = "Vikram"   # box labeled 'name' contains "Vikram"
age  = 30         # box labeled 'age' contains 30
```

---

## Syntax
```python
variable_name = value
```
- `=` is the **assignment operator** — it puts the value into the variable
- No need to declare type — Python figures it out automatically

---

## Data Types Python Assigns Automatically

| Value assigned | Type | Example |
|---------------|------|---------|
| Text | `str` (string) | `name = "Vikram"` |
| Whole number | `int` (integer) | `age = 30` |
| Decimal number | `float` | `salary = 99.5` |
| True / False | `bool` (boolean) | `is_employed = True` |

```python
name        = "Vikram"      # str
age         = 30            # int
salary      = 99.5          # float
is_employed = True          # bool
```

---

## Check the Type
```python
print(type(name))        # <class 'str'>
print(type(age))         # <class 'int'>
print(type(salary))      # <class 'float'>
print(type(is_employed)) # <class 'bool'>
```

---

## Printing Variables

```python
name = "Vikram"
city = "Vilnius"
age  = 30

# Using comma
print("Name:", name, "| City:", city, "| Age:", age)
# Output: Name: Vikram | City: Vilnius | Age: 30

# Using f-string (most common in real world)
print(f"Name: {name} | City: {city} | Age: {age}")
# Output: Name: Vikram | City: Vilnius | Age: 30
```

---

## Updating a Variable
A variable can be reassigned anytime — the old value is replaced.

```python
city = "Mumbai"
print(city)   # Mumbai

city = "Vilnius"
print(city)   # Vilnius
```

---

## Multiple Assignment

```python
# Assign same value to multiple variables
x = y = z = 0
print(x, y, z)   # 0 0 0

# Assign different values in one line
name, city, age = "Vikram", "Vilnius", 30
print(name, city, age)   # Vikram Vilnius 30
```

---

## Naming Rules

| Rule | Example |
|------|---------|
| ✅ Letters, numbers, underscore | `user_name`, `age1` |
| ✅ Must start with letter or `_` | `_name`, `name` |
| ❌ Cannot start with number | ~~`1name`~~ |
| ❌ No spaces | ~~`user name`~~ |
| ❌ No special characters | ~~`user@name`~~ |
| ❌ Cannot use Python keywords | ~~`if`, `for`, `while`~~ |

---

## Naming Conventions (Best Practice)

```python
# snake_case — recommended for variables in Python
first_name = "Vikram"
total_rows = 50000
is_active  = True

# Avoid single letters except in loops
x = 10          # ❌ not meaningful
row_count = 10  # ✅ clear and readable
```

---

## Constants (By Convention)
Python has no built-in constant type — but ALL_CAPS signals "do not change this":

```python
MAX_RETRIES = 3
DB_HOST     = "snowflake.accenture.com"
```

---

## Common Mistakes

### Using a variable before assigning it
```python
# ❌ Wrong
print(score)   # NameError: name 'score' is not defined

# ✅ Correct
score = 100
print(score)   # 100
```

### Case sensitivity — Python treats these as different variables
```python
name = "Vikram"
Name = "Mishra"
NAME = "VM"

print(name)   # Vikram
print(Name)   # Mishra
print(NAME)   # VM
```

### Confusing `=` (assignment) with `==` (comparison)
```python
age = 30      # assigns 30 to age
age == 30     # checks if age equals 30 → returns True or False
```

---

## Real World Example — Data Pipeline

```python
source_table   = "raw.orders"
target_table   = "prod.orders_clean"
batch_size     = 10000
is_incremental = True

print(f"Loading {batch_size} rows from {source_table} to {target_table}")
# Output: Loading 10000 rows from raw.orders to prod.orders_clean
```

---

## Key Takeaways
- Variables store values and are created the moment you assign them
- Python automatically detects the type — no need to declare it
- Use `snake_case` for naming
- Variable names are **case sensitive**
- Use `type()` to check what type Python assigned
- ALL_CAPS = convention for constants
- Always assign before using — otherwise `NameError`