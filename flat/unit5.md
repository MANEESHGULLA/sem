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

