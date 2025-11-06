# Context-Free Languages (CFL) – Complete Exam Notes

This document covers **all major concepts** of CFLs including:
- Chomsky Normal Form (CNF)
- Greibach Normal Form (GNF)
- Eliminating Epsilon and Unit Productions
- Pumping Lemma for CFLs
- Closure Properties
- Decision Properties

---

## **1) Chomsky Normal Form (CNF)**

A grammar is in **CNF** if every production is of the form:
```
A → BC        (two non-terminals)
A → a         (single terminal)
S → ε         (only if ε is in the language)
```

### **Rules NOT allowed in CNF**
| Form | Reason |
|------|--------|
| A → aB | Terminal must be single |
| A → BaC | More than 2 symbols |
| A → abc | Multiple terminals |
| A → ε (except S) | ε removed except start |
| A → B | Unit production |
| A → aBC | More than 2 non-terminals |

### **Steps to Convert CFG to CNF**
1. **Remove ε-productions**
2. **Remove unit productions**
3. **Remove useless symbols**
4. **Break long RHS chains**  
   Example:  
   `A → B C D` becomes:  
   `A → B X1`  
   `X1 → C D`
5. **Replace terminals in mixed RHS**  
   `A → aB` becomes:  
   `T_a → a`  
   `A → T_a B`

---

## **2) Greibach Normal Form (GNF)**

A grammar is in **GNF** if every production is:
```
A → aB₁B₂…Bₖ
```
- Must **start with a terminal**
- Followed only by **non-terminals**
- No ε-productions (except start)
- No unit productions

### **Examples**
| Production | Valid? | Reason |
|-----------|--------|--------|
| A → aBC   | ✅ Valid | Starts with terminal |
| S → b     | ✅ Valid | Terminal only |
| A → BA    | ❌ Invalid | Does not start with terminal |
| A → aBcd  | ❌ Invalid | Terminals appear after first |

### **Steps to Convert CFG to GNF**
1. Convert grammar to **CNF**
2. Order variables (A1, A2, A3...)
3. Replace productions beginning with a variable using its terminal-leading rules
4. Continue until all RHS start with terminals

### **Example (Simple)**
From CNF:
```
S → A B
A → a
B → b
```
Convert:
```
S → aB
B → b
```
GNF:
```
S → aB
B → b
```

---

## **3) Eliminating ε-Productions**

An ε-production is:
```
A → ε
```

### **Steps**
1. Identify **nullable variables**
2. For each production containing them, create versions **with and without** nullable variables
3. Remove ε-productions (except S → ε if needed)

### **Example**
```
S → AB | a
A → ε
```
A is nullable → add:
```
S → B
```

Result:
```
S → AB | B | a
```

---

## **4) Eliminating Unit Productions**

A **unit production** is:
```
A → B
```
where both are non-terminals.

### **Steps**
1. For each unit rule `A → B`, add all productions of B to A.
2. Remove the unit production.

### **Example**
```
A → B
B → b | C
C → c
```
Result:
```
A → b | c
B → b | c
C → c
```

---

## **5) Pumping Lemma for CFLs**

Used to **prove a language is NOT CFL**.

If L is CFL, any long enough string `s` can be written as:
```
s = u v w x y
```
such that:
1. `vx ≠ ε`
2. `|vwx| ≤ p`
3. `uv^i w x^i y ∈ L` for all `i ≥ 0`

### **Use Steps**
1. Assume language is CFL
2. Choose a long string `s`
3. Break into `u v w x y`
4. Pump `i = 0 or 2`
5. If result ∉ L → contradiction → **Not CFL**

### **Example Not CFL**
```
L = { a^n b^n c^n | n ≥ 1 }
```
Pumping breaks equal counts → Not CFL.

---

## **6) Closure Properties of CFLs**

| Operation | Closed? | Notes |
|----------|--------|-------|
| Union | ✅ Yes | PDA chooses |
| Concatenation | ✅ Yes | Execute sequentially |
| Kleene Star | ✅ Yes | Repeat PDA |
| Reversal | ✅ Yes | Reverse grammar |
| Intersection with Regular Language | ✅ Yes | PDA + DFA |
| Intersection (CFL ∩ CFL) | ❌ No | Needs 2 stacks |
| Complement | ❌ No | Derived from intersection failure |
| Difference | ❌ No | Needs complement |

---

## **7) Decision Properties of CFLs**

| Property | Decidable? | Reason |
|---------|-----------|--------|
| Membership (`w ∈ L?`) | ✅ Yes | CYK Algorithm |
| Emptiness (`L = ∅?`) | ✅ Yes | Check generating symbols |
| Finiteness (`L` finite?) | ✅ Yes | Detect cycles in grammar |
| Equivalence (`L1 = L2?`) | ❌ No | No general algorithm |
| Universality (`L = Σ*?`) | ❌ No | Needs complement |
| Inclusion (`L1 ⊆ L2?`) | ❌ No | Needs complement + intersection |

---

## **End of Notes – Fully Exam Ready ✅**

