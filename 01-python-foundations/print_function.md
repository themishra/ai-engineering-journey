# Python `print()` Function — Quick Reference

## Syntax
```python
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

---

## Parameters

| Parameter | Default | Purpose |
|-----------|---------|---------|
| `*objects` | — | One or more values to print |
| `sep` | `' '` (space) | Separator inserted **between** values |
| `end` | `'\n'` (newline) | Printed **after** the last value |
| `file` | `sys.stdout` | Output destination (console, file, stderr) |
| `flush` | `False` | If `True`, forces output immediately without buffering |

---

## Examples

### Default behavior — space as separator
```python
print("Hello", "World", "Python")
# Output: Hello World Python
```

### Custom `sep`
```python
print("2026", "05", "24", sep="-")
# Output: 2026-05-24
```

### Custom `end` — stay on same line
```python
print("Loading", end="...")
print("Done")
# Output: Loading...Done
```

### `file` — write to a file instead of console
```python
with open("log.txt", "w") as f:
    print("Hello, File!", file=f)
```

### `file=sys.stderr` — print to error stream
```python
import sys
print("Something went wrong", file=sys.stderr)
```

### `flush=True` — force immediate output
```python
import time
print("Processing", flush=True, end="")
time.sleep(2)
print(" Done!")
# "Processing" appears immediately, then " Done!" after 2 seconds
```

### All parameters together
```python
import sys
print("Vikram", "Accenture", "Vilnius", sep=" | ", end=" ✓\n", file=sys.stdout, flush=False)
# Output: Vikram | Accenture | Vilnius ✓
```

---

## Key Takeaways
- Multiple arguments in `print()` are separated by **space by default**
- Use `sep` to change the separator (e.g., `-`, `|`, `,`, `""`)
- Use `end` to control what happens after printing (e.g., stay on same line)
- `file=sys.stdout` is the default — change to `sys.stderr` or a file object to redirect output
- `flush=True` is useful in progress bars, real-time logs, or long-running scripts
- Always `import sys` when explicitly using `sys.stdout` or `sys.stderr`