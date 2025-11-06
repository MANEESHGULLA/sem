# Pushdown Automaton (PDA)

A **Pushdown Automaton (PDA)** is similar to a finite automaton but uses a **stack** as extra memory.  
This stack allows the PDA to recognize **Context-Free Languages (CFLs)** which cannot be recognized by regular finite automata.

---

## Why Do We Need a Stack?

Some languages require counting or matching patterns.  
Example:

**L = { aⁿ bⁿ | n ≥ 1 }**  
This means equal number of `a` and `b`.

- Finite Automata **cannot** remember how many `a`s occurred.
- PDA can **push** each `a` onto the stack and **pop** for each `b`.

---

## Structure of a PDA

A PDA is defined as:

**P = ( Q, Σ, Γ, δ, q₀, Z₀, F )**

| Symbol | Meaning |
|-------|---------|
| Q     | Set of states |
| Σ     | Input alphabet |
| Γ     | Stack alphabet |
| δ     | Transition function |
| q₀    | Start state |
| Z₀    | Initial stack symbol |
| F     | Set of accepting states |

---

## How PDA Works

At each step, the PDA looks at:

1. Current **state**
2. Current **input symbol**
3. **Top** of the stack

Then it may:

- **Push** a symbol to stack
- **Pop** a symbol from stack
- **Change** state
- **Read** next input symbol

---
## Construct PDA
PDA for L = { a^n b^n | n ≥ 1 }

M = (Q, Σ, Γ, δ, q0, Z0, F)

Q   = { q0, q1, q_accept }
Σ   = { a, b }
Γ   = { Z, A }                 ; Z = bottom marker, A = count of a’s
q0  = q0
Z0  = Z
F   = { q_accept }             ; accept by final state

Intuition:
- In q0, read all a’s and push A for each a.
- On the first b, move to q1 and start popping one A per b.
- Accept iff input ends with only Z left (counts matched and n ≥ 1).

Transitions δ (written δ(state, input, top) = (state’, stack-rewrite)):
1) Push a’s (stay in q0)
   δ(q0, a, Z) = (q0, AZ)      ; first a: push A over Z
   δ(q0, a, A) = (q0, AA)      ; more a’s: push A

2) First b switches to popping phase
   δ(q0, b, A) = (q1, ε)       ; start matching: pop one A

3) Keep popping for remaining b’s (stay in q1)
   δ(q1, b, A) = (q1, ε)       ; pop one A per b

4) Accept at end if exactly matched
   δ(q1, ε, Z) = (q_accept, Z) ; input finished and only Z remains → accept

Notes:
- No transition on b with top Z (prevents starting with b or having n=0).
- Strings with extra a’s or b’s leave unmatched A or need a pop when none exists → reject.
---

## Graphical PDA (Text State Diagram)

            (start)
              |
              v
           +------+
           |  q0  |
           +------+
            |  ^ 
   a, Z→AZ  |  |  a, A→AA
            |  |
            v  |
           (loop on q0)
           
            |
            |  b, A→ε     (first b switches to q1)
            v
           +------+
           |  q1  |
           +------+
            ^   |
            |   |
        b, A→ε  |
            |   |
            +---+  (loop on q1 for b's)

            |
            |  ε, Z→Z
            v
        +-----------+
        | q_accept  |
        +-----------+

---

## Transition Format
(input symbol, stack_top → stack_action)

| Transition | Meaning |
|-----------|---------|
| a, Z → AZ | On `a` with `Z` on stack, push `A` |
| a, A → AA | On `a` with `A` on stack, push another `A` |
| b, A → ε  | On `b` with `A` on stack, pop `A` |
| ε, Z → Z  | Input ends & only Z remains → move to accept |

---

## Explanation
- In **q0**, push `A` for each `a`.
- On first `b`, move to **q1** and begin popping `A`.
- For every `b`, pop one `A`.
- If input ends and only `Z` remains on stack, move to `q_accept`.

---
# PDA Concepts with Examples

## 1) Instantaneous Description (ID) of a PDA

An **Instantaneous Description (ID)** represents the **current status of a PDA**.

It is written as:(q, w, α)

| Symbol | Meaning |
|--------|---------|
| `q`    | Current state |
| `w`    | Remaining input string |
| `α`    | Current stack contents (top on left) |

### Example ID (q0, abb, AZ)
Meaning:
- PDA is in **state** `q0`
- Remaining **input** is `abb`
- **Stack** has `A` (top), followed by `Z` (bottom)

### Transition Rule Format (q, a w, X β) ⊢ (p, w, γ β)
| Symbol | Meaning |
|--------|---------|
| `q`    | current state |
| `a`    | next input symbol |
| `w`    | remaining string |
| `X`    | symbol on top of stack |
| `γ`    | new symbol(s) to push |
| `⊢`    | means "yields in one step" |

---

## Example Step-by-Step ID for string `aabb` in PDA for a^n b^n
Execution:
(q0, aabb, Z)
- ⊢ (q0, abb, AZ)
- ⊢ (q0, bb, AAZ)
- ⊢ (q1, b, AZ)
- ⊢ (q1, ε, Z)

---

