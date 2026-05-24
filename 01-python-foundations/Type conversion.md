# Python Type Conversion — Quick Reference

## What is Type Conversion?
When you read data from a file, API, or user input — everything arrives as a **string**.
Type conversion (also called **casting**) lets you change a value from one type to another.

```python
age = "30"        # this is a string — you can't do math with it
age = int(age)    # now it's an integer — you can do math
```

---

## Conversion Functions

| Function | Converts to | Example | Result |
|----------|------------|---------|--------|
| `int()` | Whole number | `int("30")` | `30` |
| `float()` | Decimal number | `float("99.5")` | `99.5` |
| `str()` | Text | `str(100)` | `"100"` |
| `bool()` | True / False | `bool(1)` | `True` |

---

## Examples

### String → Integer
```python
age = "30"
age = int(age)
print(age + 5)     # 35
print(type(age))   # <class 'int'>
```

### String → Float
```python
salary = "99.5"
salary = float(salary)
print(salary + 0.5)   # 100.0
print(type(salary))   # <class 'float'>
```

### Integer → String
```python
score = 100
score = str(score)
print("Your score: " + score)   # Your score: 100
print(type(score))               # <class 'str'>
```

### Integer → Float and back
```python
x = 10
x = float(x)    # 10.0
x = int(x)      # 10
```

---

## `bool()` Conversion Rules

| Value | Converts to |
|-------|------------|
| `0` | `False` |
| `1` or any non-zero number | `True` |
| `""` (empty string) | `False` |
| `"any text"` | `True` |
| `None` | `False` |

```python
print(bool(0))      # False
print(bool(1))      # True
print(bool(""))     # False
print(bool("hi"))   # True
print(bool(None))   # False
```

---

## Common Mistakes

### Adding string and int without converting
```python
# ❌ Wrong
age = "30"
print(age + 5)       # TypeError: can only concatenate str (not "int") to str

# ✅ Correct
age = int("30")
print(age + 5)       # 35
```

### Converting invalid value
```python
# ❌ Wrong
age = int("thirty")   # ValueError: invalid literal for int()

# ✅ Correct — only convert if the string actually contains a number
age = int("30")       # works fine
```

### Losing decimal on int() conversion
```python
price = 99.9
price = int(price)
print(price)   # 99 ← decimal is lost, not rounded
```

---

## Real World Example — Reading pipeline config

```python
# Data read from a config file comes as strings
rows_str    = "10000"
threshold   = "0.95"
is_active   = "1"

# Convert to correct types before using
batch_size  = int(rows_str)
confidence  = float(threshold)
active_flag = bool(int(is_active))

print(f"Batch: {batch_size} | Confidence: {confidence} | Active: {active_flag}")
# Output: Batch: 10000 | Confidence: 0.95 | Active: True
```

---

## Key Takeaways
- Data from files, APIs, and `input()` always arrives as a **string**
- Use `int()`, `float()`, `str()`, `bool()` to convert between types
- Converting an invalid value (e.g. `int("abc")`) raises a `ValueError`
- `int()` on a float **drops the decimal** — it does not round
- `bool(0)`, `bool("")`, `bool(None)` all return `False`