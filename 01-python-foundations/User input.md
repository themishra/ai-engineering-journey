# Python User Input — Quick Reference

## What is `input()`?
The `input()` function pauses the program and waits for the user to type something.
Whatever the user types is stored in a variable.

```python
name = input("Enter your name: ")
print(f"Hello, {name}!")
# Terminal: Enter your name: Vikram
# Output:   Hello, Vikram!
```

---

## Syntax
```python
variable = input("Message to show user: ")
```
- The text inside `input()` is the **prompt** — shown to the user
- The user's response is stored in the variable

---

## Critical Rule — `input()` ALWAYS returns a string

Even if the user types a number, it comes back as a string:

```python
age = input("Enter your age: ")
print(type(age))   # <class 'str'>  ← always string!
print(age + 1)     # ❌ TypeError — can't add string and int
```

**Always convert immediately after input:**

```python
age = int(input("Enter your age: "))
print(type(age))   # <class 'int'>
print(age + 1)     # ✅ works fine
```

---

## Examples

### String input (no conversion needed)
```python
name = input("Enter your name: ")
city = input("Enter your city: ")
print(f"{name} lives in {city}")
# Output: Vikram lives in Vilnius
```

### Integer input
```python
age = int(input("Enter your age: "))
print(f"In 10 years you will be {age + 10}")
# Output: In 10 years you will be 40
```

### Float input
```python
salary = float(input("Enter your salary: "))
bonus  = salary * 0.10
print(f"Your bonus is {bonus}")
# Output: Your bonus is 9950.0
```

---

## Multiple Inputs

```python
name   = input("Enter name: ")
age    = int(input("Enter age: "))
salary = float(input("Enter salary: "))

print(f"Name: {name} | Age: {age} | Salary: {salary}")
# Output: Name: Vikram | Age: 30 | Salary: 99500.0
```

---

## Common Mistakes

### Forgetting to convert input to int
```python
# ❌ Wrong
num = input("Enter a number: ")
print(num * 2)     # "55" instead of 10 — string repetition, not math!

# ✅ Correct
num = int(input("Enter a number: "))
print(num * 2)     # 10
```

### Adding string input to a number
```python
# ❌ Wrong
score = input("Enter score: ")
total = score + 100    # TypeError

# ✅ Correct
score = int(input("Enter score: "))
total = score + 100    # works
```

---

## Real World Example — Pipeline config from terminal

```python
# Instead of hardcoding values, take them as input at runtime
table_name = input("Enter source table name: ")
batch_size = int(input("Enter batch size: "))
env        = input("Enter environment (dev/prod): ")

print(f"Starting {env} pipeline...")
print(f"Loading {batch_size} rows from {table_name}")

# Terminal:
# Enter source table name: raw.orders
# Enter batch size: 10000
# Enter environment (dev/prod): prod
#
# Output:
# Starting prod pipeline...
# Loading 10000 rows from raw.orders
```

---

## Key Takeaways
- `input()` always returns a **string** — no exceptions
- Always convert with `int()` or `float()` when expecting a number
- The text inside `input("...")` is just the prompt — it doesn't affect the value
- Use `input()` to make scripts dynamic instead of hardcoding values
- Combine with type conversion for clean, usable data