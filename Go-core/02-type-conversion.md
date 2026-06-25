# Go Core — Type Conversion

## The Main Rule

Go has **no implicit conversion**. Ever.
This is a deliberate language design decision — safety over convenience.

```go
var a int32 = 10
var b int64 = a       // compile error
var b int64 = int64(a) // correct
```

---

## 1. Numeric Conversions

```go
var a int32 = 100
var b int64 = int64(a) // widening — safe
var c int8  = int8(a)  // narrowing — data loss possible
```

**Overflow behavior:**
```go
var a int32 = 300
var b int8  = int8(a)
fmt.Println(b) // 44 — no panic, just silent bit truncation
```

> **Interview trap:** Go does NOT panic on overflow — it silently truncates bits.
> The result is wrong but the program keeps running.

---

## 2. int and float

```go
var f float64 = 3.99
var i int = int(f)
fmt.Println(i) // 3 — truncation, not rounding
```

> **Interview trap:** `int(3.99)` → `3`, not `4`.
> Go truncates the decimal part, it does not round.

---

## 3. string ↔ []byte / []rune

```go
s := "hello"
b := []byte(s)  // string → bytes (UTF-8 encoded)
r := []rune(s)  // string → Unicode code points
s2 := string(b) // []byte → string
```

**When to use which:**
- `[]byte` — networking, files, binary data
- `[]rune` — text with Unicode characters (Cyrillic, emoji, CJK)

---

## 4. int → string (classic trap)

```go
var i int = 65
s  := string(i)           // "A"  — treats i as a Unicode code point
s2 := fmt.Sprintf("%d", i) // "65" — correct if you want the digit
s3 := strconv.Itoa(i)      // "65" — most idiomatic way
```

> **Interview trap:** `string(65)` returns `"A"`, not `"65"`.
> Go interprets the integer as a Unicode code point, not a digit string.

---

## 5. Type Assertion — interface{} → concrete type

### What is Type Assertion?

Type assertion is how you check and extract the **concrete value** stored inside an `interface{}` variable.

An `interface{}` variable is like a **sizeless box** — it can hold any type: `string`, `int`, `bool`, your own structs. Go allows this because the empty interface has no method requirements whatsoever.

When you need to work with the actual value inside (measure its length, do arithmetic, call methods), you must tell the compiler: *"I know what's inside this box — extract it so I can use it as that specific type."* That's exactly what type assertion does.

```go
var i interface{} = "hello"
// At this point, i is a "box" containing the string "hello"
```

**Unsafe — panics if type doesn't match:**
```go
s := i.(string) // works here, but panics if i held an int
```

**Safe — always use this form:**
```go
s, ok := i.(string)
if ok {
    fmt.Println(s) // safe to use
} else {
    // type didn't match — handle gracefully
}
```

The safe form returns two values:
- `s` — the extracted value (zero value of the type if `ok` is false)
- `ok` — `true` if the type matched, `false` otherwise

> **Rule:** Always use the `v, ok` form unless you are 100% certain of the type.
> Blind assertion is a panic waiting to happen.

---

## 6. strconv Package

```go
// string → int
n, err := strconv.Atoi("42")

// int → string
s := strconv.Itoa(42)

// string → float
f, err := strconv.ParseFloat("3.14", 64)

// bool → string
s := strconv.FormatBool(true) // "true"
```

> Always handle `err` — if the string is not a valid number, you get an error, not a panic.

---

## 7. fmt.Sprintf for Conversion

```go
n  := 42
s  := fmt.Sprintf("%d", n)    // int → string
f  := 3.14
s2 := fmt.Sprintf("%.2f", f)  // float → string with 2 decimal places
```

> Slower than `strconv`. Use when you need formatting, not just conversion.

---

## Interview Cheatsheet

| Question | Answer |
|---|---|
| Does Go have implicit conversion? | No — never |
| What happens on int32 → int8 overflow? | No panic — silent bit truncation, wrong result |
| What does `int(3.99)` return? | `3` — truncation, not rounding |
| What does `string(65)` return? | `"A"` — Unicode code point, not `"65"` |
| What is type assertion? | Extracting a concrete value from an interface{} |
| Safe way to do type assertion? | `v, ok := i.(Type)` — always use the two-value form |
| Difference between `string(65)` and `strconv.Itoa(65)`? | `"A"` vs `"65"` |
