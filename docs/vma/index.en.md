---
icon: material/script-text
---

# VMA Script

VMA (Vimina Macro Automation) is Vimina's scripting language for writing automation tasks.

## Overview

VMA is a concise scripting language designed for desktop automation:

- **Simple Syntax** - Python-like concise syntax
- **Rich Functions** - Built-in mouse, keyboard, window operations
- **Control Flow** - Supports conditions, loops, functions
- **Compilable** - Can be compiled to standalone exe files

## Quick Example

```vma
// Auto login example
click(200, 150)      // Click username input
sleep(100)
type("admin")        // Type username

click(200, 200)      // Click password input
sleep(100)
type("password123")  // Type password

click(200, 250)      // Click login button
log("Login completed")
```

## Basic Structure

VMA script is a collection of commands, one command per line:

```vma
// This is a comment
click(100, 100)      // Click operation
sleep(500)           // Wait
type("Hello World")  // Type text
```

## Data Types

| Type | Description | Example |
|------|-------------|---------|
| `int` | Integer | `42`, `-10` |
| `float` | Float | `3.14`, `-0.5` |
| `string` | String | `"Hello"`, `'World'` |
| `bool` | Boolean | `true`, `false` |

## Variables

Declare variables using `var`:

```vma
var name = "Vimina"
var count = 10
var pi = 3.14
var enabled = true
```

## Detailed Documentation

See the following sections for detailed syntax and functions:

- [Syntax Reference](syntax.md) - Complete syntax description
- [Built-in Functions](functions.md) - All built-in functions
- [Script Examples](examples.md) - Practical script examples
