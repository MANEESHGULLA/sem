# Turing Machine

A **Turing Machine (TM)** is a mathematical model of computation proposed by **Alan Turing**.  
It is more powerful than finite automata and pushdown automata because it has **unlimited memory** in the form of a **tape**.

A Turing Machine can **simulate any computer program** and is used to define what it means for a function or problem to be **computable**.

---

## Why Turing Machine?

Finite automata and PDA have limited memory:

| Model | Memory Availability |
|-------|--------------------|
| FA    | No memory          |
| PDA   | Memory in form of stack (LIFO) |

But some languages and computations require **full read/write memory** — not just push/pop.

So, a Turing Machine uses:
- ✔ Infinite tape  
- ✔ Read and write head  
- ✔ Ability to move both **left and right**

Thus, it can perform **general computation** like a real computer.

---

## Structure of Turing Machine

A Turing Machine is defined as:

\[
M = (Q, Σ, Γ, δ, q_0, B, F)
\]

| Symbol | Meaning |
|--------|---------|
| Q      | Set of states |
| Σ      | Input alphabet |
| Γ      | Tape alphabet (includes input symbols + blank symbol) |
| δ      | Transition function |
| q₀     | Start state |
| B      | Blank symbol |
| F      | Set of accepting (final) states |

---

## Tape and Head

- The **tape** is divided into infinite cells.
- Each cell contains **one symbol**.
- The **read-write head** can:
  - **Read** a symbol
  - **Write** a symbol
  - Move **Left (L)** or **Right (R)**

---

## Transition Function

The transition function is written as:

\[
\delta(q, X) = (p, Y, D)
\]

Meaning:
- In state **q** reading **X**,
- Change state to **p**,
- Write **Y** on tape,
- Move head in direction **D** (L or R).

---

## How Turing Machine Works

1. Read the current symbol on tape.
2. Use δ to decide the next move.
3. Write a new symbol (if needed).
4. Move head left or right.
5. Change state.
6. Continue until it reaches a **final state**.

---

## Example Language

\[
L = \{ a^n b^n \mid n \ge 1 \}
\]

A TM can:
- Replace first `a` with `X`
- Find the matching `b`
- Replace it with `Y`
- Repeat until all are matched

This requires **general read/write memory**, which PDA cannot do reliably → So TM is needed.

---

## Key Points for Exam

- TM is the **most powerful** computational model.
- Uses **infinite tape** as memory.
- Can **read, write**, and **move head both left and right**.
- Can perform computations like a **real computer**.
- Used to define **decidability** and **computability**.

---
