# Syntax Reference

## Comments

```vma
// Single line comment

/*
Multi-line comment
Can span multiple lines
*/
```

## Variables

### Declare Variables

```vma
var name = "Vimina"
var count = 10
var pi = 3.14
var enabled = true
```

### Explicit Types

```vma
var count: int = 10
var name: string = "Vimina"
var pi: float = 3.14
var enabled: bool = true
```

### Variable Assignment

```vma
var x = 10
x = 20          // Reassign
x = x + 5       // Operation assignment
```

---

## Operators

### Arithmetic Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `+` | Addition | `a + b` |
| `-` | Subtraction | `a - b` |
| `*` | Multiplication | `a * b` |
| `/` | Division | `a / b` |
| `%` | Modulo | `a % b` |

### Comparison Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `==` | Equal | `a == b` |
| `!=` | Not equal | `a != b` |
| `>` | Greater than | `a > b` |
| `<` | Less than | `a < b` |
| `>=` | Greater or equal | `a >= b` |
| `<=` | Less or equal | `a <= b` |

### Logical Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `and` | And | `a and b` |
| `or` | Or | `a or b` |
| `not` | Not | `not a` |

---

## Control Flow

### Conditional

```vma
if condition
    // code block
else
    // code block
end
```

**Example:**

```vma
var count = 10

if count > 5
    log("Greater than 5")
else
    log("Less than or equal to 5")
end
```

**Multiple Conditions:**

```vma
var score = 85

if score >= 90
    log("Excellent")
else if score >= 60
    log("Pass")
else
    log("Fail")
end
```

---

### Loop

Fixed iterations:

```vma
loop 5
    log("Execute once")
endloop
```

---

### For Loop

```vma
for i = 1 to 10
    log(i)
end
```

**Step:**

```vma
for i = 1 to 10 step 2
    log(i)  // 1, 3, 5, 7, 9
end
```

---

### While Loop

```vma
var count = 0
while count < 10
    log(count)
    count = count + 1
end
```

---

### Break and Continue

```vma
for i = 1 to 10
    if i == 5
        break      // Exit loop
    end
    log(i)
end
```

```vma
for i = 1 to 10
    if i == 5
        continue   // Skip this iteration
    end
    log(i)
end
```

---

## Functions

### Define Function

```vma
function greet(name)
    log("Hello, " + name)
end
```

### Call Function

```vma
greet("Vimina")
```

### Return Value

```vma
function add(a, b)
    return a + b
end

var result = add(1, 2)
log(result)  // Output: 3
```

---

## String Operations

### String Concatenation

```vma
var s1 = "Hello"
var s2 = "World"
var s3 = s1 + " " + s2  // "Hello World"
```

### String Functions

```vma
var s = "Hello World"

var length = len(s)           // 11
var sub = substr(s, 0, 5)     // "Hello"
var parts = split(s, " ")     // ["Hello", "World"]
```

---

## Arrays

### Create Array

```vma
var arr = [1, 2, 3, 4, 5]
var names = ["Alice", "Bob", "Charlie"]
```

### Access Elements

```vma
var first = arr[0]    // 1
var second = arr[1]   // 2
```

### Iterate Array

```vma
for item in arr
    log(item)
end
```
