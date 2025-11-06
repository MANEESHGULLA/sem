# Context-Free Languages (CFL) – Important Concepts and Notes

---

## **Chomsky Normal Form (CNF)**

Chomsky Normal Form is a standardized (restricted) way of writing Context-Free Grammar rules.

A grammar is in **CNF** if every production is of the form:

```
A → BC        (A non-terminal produces exactly two non-terminals)
A → a         (A non-terminal produces a single terminal)
```
Additionally:
```
S → ε         (allowed only if the language contains ε)
```

### **Rules NOT allowed in CNF**

| Not Allowed Production | Reason |
|------------------------|--------|
| A → aB                 | Terminal must appear alone |
| A → BaC                | More than 2 symbols |
| A → abc                | Multiple terminals |
| A → ε                  | Except S → ε |
| A → B                  | Unit production |
| A → aBC                | More than 2 non-terminals |

---

### **Steps to Convert CFG to CNF**

#### **Step 1: Remove ε-productions**
Remove rules like `A → ε` except if `S → ε` is allowed.

#### **Step 2: Remove Unit Productions**
Remove rules like `A → B`, replace them by copying B’s productions into A.

#### **Step 3: Remove Useless Symbols**
Remove:
- Symbols that do not derive any terminal string
- Symbols that are never reachable from the start symbol

#### **Step 4: Convert Long Right-Hand Sides**
Break rules longer than 2 non-terminals:
```
A → B C D
```
Convert to:
```
A → B X1
X1 → C D
```

#### **Step 5: Ensure Terminals Appear Alone**
Convert mixed rules like `A → aB` into:
```
T_a → a
A → T_a B
```

---

## **Greibach Normal Form (GNF)**

A grammar is in **Greibach Normal Form** if every production is of the form:

```
A → aB₁B₂…Bₖ
```
Where:
- The first symbol **must be a terminal**
- The rest (if present) must be **non-terminals**
- No ε-productions (except optional start)
- No unit productions

### **Examples**

| Form | Valid? | Reason |
|------|--------|--------|
| A → aBC | ✅ Valid | Starts with terminal, then non-terminals |
| S → b | ✅ Valid | Only terminal |
| B → cA | ✅ Valid | Starts with terminal |
| A → BA | ❌ Invalid | Does not start with terminal |
| A → aBcd | ❌ Invalid | Terminals appear after the first |
| A → ε | ❌ Not allowed unless start symbol |

---
# Context-Free Grammar Transformations and Important Concepts

---

## 1) Eliminating **Epsilon (ε) Productions**

An **ε-production** is a rule of the form:
```
A → ε
```

### **Steps**
1. **Find all nullable variables**  
   A variable A is nullable if:
   - A → ε, or
   - A → α and all symbols in α are nullable.

2. **For every production containing a nullable variable**, create new productions where the nullable variable is removed (optional removal).

3. **Remove all ε-productions** (except `S → ε` if needed for the language).

---

### **Example**
```
S → AB | a
A → ε
B → b
```
A is nullable.

Add productions by removing A:
```
S → B
```
Final:
```
S → AB | B | a
A → (removed)
B → b
```

---

## 2) Eliminating **Unit Productions**

A **unit production** is of the form:
```
A → B
```
where both A and B are variables.

### **Steps**
1. For each unit pair (A → B), add all productions of B to A.
2. Remove the unit productions.

---

### **Example**
```
A → B
B → b | C
C → c
```
A gets `b` and `C`; C gives `c`.

Final:
```
A → b | c
B → b | c
C → c
```

---

## 3) **Chomsky Normal Form (CNF)**

A CFG is in CNF if all productions are of the form:
```
A → BC       (two non-terminals)
A → a        (single terminal)
S → ε        (only if ε in language)
```

### **Steps to Convert to CNF**
1. Remove ε-productions
2. Remove unit productions
3. Remove useless symbols
4. Convert rules with length > 2:
   ```
   A → B C D
   becomes:
   A → B X1
   X1 → C D
   ```
5. Replace terminals when mixed:
   ```
   A → aB   becomes   A → Ta B   with Ta → a
   ```

---

### **Example Conversion to CNF**
```
S → aAB
A → b
B → c
```

Introduce terminal variables:
```
Ta → a
Tb → b
Tc → c
```

Rewrite:
```
S → Ta A B
A → Tb
B → Tc
```

Binarize:
```
S → Ta X1
X1 → A B
```

Final CNF:
```
S → Ta X1
X1 → A B
A → Tb
B → Tc
Ta → a
Tb → b
Tc → c
```

---

## 4) **Greibach Normal Form (GNF)**

A grammar is in GNF if every rule is:
```
A → a B1 B2 ... Bk
```
- **First symbol must be terminal**
- Remaining symbols must be non-terminals
- No ε-productions (except start)
- No unit productions

---

### **Steps to Convert to GNF**
1. Convert grammar to **CNF** first.
2. Ensure LHS non-terminals are in numbered order (A1, A2, A3…).
3. Replace rules where RHS begins with a variable:
   ```
   A → Bγ  →  replace B with its terminal-starting rules
   ```
4. Continue until every RHS starts with a terminal.

---

### **Example Conversion to GNF**
Start with CNF:
```
S → A B
A → a
B → b
```
Replace:
```
S → aB
B → b
```
Final GNF:
```
S → aB
B → b
```

---

## Summary Table

| Form | Required Pattern | Allows ε? | Allows Unit? |
|-----|------------------|----------|--------------|
| **CNF** | A → BC or A → a | Only S → ε | ❌ No |
| **GNF** | A → aB₁B₂…Bₖ | Only S → ε | ❌ No |

---

This document now includes:
✅ Eliminating ε-productions  
✅ Eliminating unit productions  
✅ CNF definition & steps  
✅ GNF definition & steps  
✅ Examples for both  

---

**End of Notes – Exam Ready ✅**


## **Pumping Lemma for CFLs**

The **Pumping Lemma** is used to **prove that a language is NOT context-free**.

If L is a CFL, there exists `p` such that any string `s` with `|s| ≥ p` can be written as:

```
s = u v w x y
```

Such that:
1. `v x ≠ ε` (one of them must be non-empty)
2. `|vwx| ≤ p`
3. `uvⁱ w xⁱ y ∈ L` for all `i ≥ 0`

### **How to Use**
To show a language is **not CFL**:
1. Assume it is CFL.
2. Choose a string `s ∈ L` where `|s| ≥ p`.
3. Apply pumping rules.
4. Show pumped string is **not in L** → Contradiction.

### **Example**
```
L = { aⁿ bⁿ cⁿ | n ≥ 1 }
```
Equal counts cannot be maintained when pumped → **Not CFL**.

---

## **Closure Properties of CFLs**

| Operation | CFL Closed Under? | Notes |
|----------|------------------|------|
| Union (L1 ∪ L2) | ✅ Yes | Combine pushdown automata |
| Concatenation (L1L2) | ✅ Yes | Process sequentially |
| Kleene Star (L*) | ✅ Yes | Repeat structure |
| Reversal (Lᴿ) | ✅ Yes | Reverse productions |
| Substitution | ✅ Yes | Allow replacement by CFLs |
| Homomorphism | ✅ Yes | Mapping symbols allowed |
| Inverse Homomorphism | ✅ Yes | Preimage of language |
| Intersection with Regular Language | ✅ Yes | PDA + DFA = PDA |

| Operation | CFL Closed Under? | Reason |
|----------|------------------|--------|
| Intersection (L1 ∩ L2) | ❌ No | Would require two stacks |
| Complement (L′) | ❌ No | Depends on intersection |
| Difference (L1 − L2) | ❌ No | Requires complement |

---

## **Decision Properties of CFLs**

Decision properties determine what can be algorithmically checked.

### ✅ **Decidable Problems**

| Problem | Description | Why Decidable |
|--------|-------------|---------------|
| Membership Problem | Check if `w ∈ L(G)` | CYK Algorithm (O(n³)) |
| Emptiness Problem | Is `L(G)` empty? | Check if start derives any terminal |
| Finiteness Problem | Is `L(G)` finite? | Detect cycles in derivation graph |

### ❌ **Undecidable Problems**

| Problem | Description | Why Undecidable |
|---------|-------------|-----------------|
| Equivalence | `L(G₁) = L(G₂)` ? | No general algorithm |
| Universality | `L(G) = Σ*` ? | Requires complement |
| Inclusion / Subset | `L(G₁) ⊆ L(G₂)` ? | Requires complement + intersection |

---

### **End of Notes – Exam Ready ✅**

