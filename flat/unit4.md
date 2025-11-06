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
