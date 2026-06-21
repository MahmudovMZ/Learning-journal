# CS50 — Week 0: Scratch

## Overview
First week of Harvard's CS50x. Focused on foundational computer science concepts using Scratch, a visual block-based programming language, before moving into text-based languages like C, Python, and SQL later in the course.

---

## Core Concepts

### How Computers Represent Data
- Computers understand only **binary code** (0, 1) — a *binary digit* is called a **bit**
- **8 bits = 1 byte** → range: 0–255
- All input (numbers, letters, video, images, etc.) is converted by the computer into binary machine code

**Example — encoding the letter "A":**
01000001 = 65
128 64 32 16 8 4 2 1  ← bit place values
### Character Encoding
- **ASCII** — standard used to convert letters and symbols into binary
- **Unicode** — extended encoding format that supports emojis and other complex symbols beyond ASCII's range

**ASCII examples:**
| Binary | Decimal | Character |
|---|---|---|
| 00100001 | 33 | `!` |
| 01001001 | 73 | `I` |
| 01001000 | 72 | `H` |

### Color Representation
Colors are transmitted through machine code using **RGB** (Red, Green, Blue):

| R | G | B | Color |
|---|---|---|---|
| 72 | 73 | 33 | Yellow |
| 255 | 255 | 255 | White |
| 0 | 0 | 0 | Black |

---

## Programming Fundamentals

### Algorithm
A step-by-step process for solving a problem. The goal of an algorithm is to solve a problem using the **minimum amount of resources** (CPU, time, money).

### Pseudocode
Code written in human-readable language to aid basic understanding, used to design an algorithm efficiently before implementation.

### Compiler
A program that translates one language (e.g., Python) into another (e.g., machine code).

### Scratch
A visual programming language used to teach core programming logic without syntax. [scratch.mit.edu](https://scratch.mit.edu)

---

## Key Building Blocks

| Concept | Definition |
|---|---|
| **Function** | An action — a reusable block of logic |
| **Function Arguments / Parameters** | The input data a function works with |
| **Boolean Expression** | A value that evaluates to `true` or `false` |
| **Conditional (If / Else)** | Logic that branches based on a condition |
| **Loop (Cycle)** | Repeats an action while a condition holds true |
| **Side Effect** | The visible result/output of a function — what the user can observe |
| **Return** | The value a function gives back, used by other parts of the code (not directly seen by the user) |

---

## Mapping to Go

| Scratch / CS50 Concept | Go Equivalent |
|---|---|
| Loops | `for` |
| Conditionals (If/Else) | `if` / `else` |
| Variables | `var` / `:=` |

---

## Takeaways
- Programming logic (loops, conditionals, variables, functions) is universal — it transfers directly across languages, including Go
- Understanding binary, ASCII, and how computers represent data builds the foundation for everything that comes later (memory, data types, encoding)
- Scratch removes syntax friction so the focus stays purely on **algorithmic thinking**
