# Go Core — Week 1: Data Types

## 4 Groups of Data Types

---

### Group 1 — Basic Types

| Type | Size | Zero Value | Notes |
|---|---|---|---|
| bool | 1 byte | false | |
| int | 8 bytes | 0 | 64-bit systems |
| int8 | 1 byte | 0 | range: -128 to 127 |
| int16 | 2 bytes | 0 | |
| int32 | 4 bytes | 0 | |
| int64 | 8 bytes | 0 | |
| float32 | 4 bytes | 0 | |
| float64 | 8 bytes | 0 | |
| string | 16 bytes | "" | header: pointer + len |
| byte | 1 byte | 0 | alias for uint8 |
| rune | 4 bytes | 0 | alias for int32, Unicode |

---

### Group 2 — Composite Types

| Type | Size | Zero Value |
|---|---|---|
| array | element size × length | zeros |
| slice | 24 bytes (ptr + len + cap) | nil |
| map | ~8 bytes (pointer) | nil |
| struct | sum of fields + padding | zero values of fields |

> **Interview trap:** What happens if you write to a nil map?
> **Answer:** Panic. Reading from a nil map returns zero value — no panic.

---

### Group 3 — Reference Types

- `pointer`
- `slice`
- `map`
- `channel`
- `function`

Reference types store not the value itself, but the **memory address** where the data lives.
Unlike basic types which copy the value on assignment, reference types copy only the address —
meaning changes through one variable are visible through all variables pointing to the same address.

> **Interview trap:** Is a slice passed by reference?
> **Answer:** No — passed by value, but that value *contains a pointer* to the underlying array.
> Modifying elements is visible outside the function. `append` is not — it modifies a local copy of the slice header.

---

### Group 4 — Abstract Types (Interfaces)

| Type | Size | Zero Value |
|---|---|---|
| interface{} | 16 bytes (type + data) | nil |

An interface is a **"fat pointer"** consisting of two fields:
- Pointer to type metadata / method table → 8 bytes
- Pointer to the actual data → 8 bytes
- Total: **16 bytes**, always, regardless of what's stored inside

> **Interview trap:**
> ```go
> var p *MyStruct = nil
> var i interface{} = p
> fmt.Println(i == nil) // false — why?
> ```
> **Answer:** The interface has a type field set to `*MyStruct` — even though the value is nil.
> An interface is `nil` only when **both** fields (type AND value) are nil.

---

## Topics to Revisit Later
- Dependency Inversion
- Dependency Injection

*(Relevant to interfaces and patterns — scheduled for Week 4–5)*
