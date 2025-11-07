# Relationship of AI, ML, and DL

## Artificial Intelligence (AI)
- AI refers to the simulation of human-like intelligence in machines.
- The goal of AI is to enable machines to **think, learn, and make decisions** like humans.
- AI is the **broadest concept** under which ML and DL fall.

## Machine Learning (ML)
- ML is a **subset of AI**.
- It enables systems to **learn patterns from data** without being explicitly programmed.
- ML improves performance as the system is exposed to more data.

## Deep Learning (DL)
- DL is a **subset of ML**.
- It uses **Artificial Neural Networks (ANNs)** with many layers (hence “deep”).
- DL can automatically **extract features** from raw data (no manual feature engineering required).
- DL is especially powerful for **images, audio, video, and natural language**.

### Venn Diagram Relationship
AI
└── ML
└── DL

---

# What is Deep Learning?

Deep Learning is a class of machine learning algorithms that:
- Use **multiple layers** of **nonlinear processing units** for **feature extraction and transformation**.
- Each layer’s **output becomes input for the next layer**.
- Can learn in:
  - **Supervised** manner (e.g., classification, regression)
  - **Unsupervised** manner (e.g., pattern discovery)
- Learn **multiple levels of representation**, forming a **hierarchy of abstraction**.

---

# Neural Networks

## Biological Neural Networks
- Human brain contains **billions of interconnected neurons**.
- Each neuron receives signals, processes them, and sends signals forward.
- Communication happens through **synapses**.
- The brain processes **information in parallel**.

### A Biological Neuron Has:
| Part | Function |
|------|----------|
| **Dendrite** | Receives signals from other neurons |
| **Synapse** | Connection point where signal passes to another neuron |
| **Soma (Cell Body)** | Processes the received signals |
| **Axon** | Transmits the output to other neurons |

## How The Brain Works (Simplified)
1. Sense organs capture information.
2. Information is passed to **neurons**.
3. Some neurons **activate (fire)** and forward the signal.
4. Signals propagate through **multiple layers of neurons**.
5. A meaningful **response** is produced.

- The brain has **~100 billion neurons**.
- Neurons are arranged in **layers and hierarchies**.
- Higher layers process **more abstract concepts**.

### Example in Visual Processing (Hierarchy Example)
| Layer (Brain Area) | Function |
|--------------------|----------|
| Retina | Receives patterns of light |
| V1 | Detects edges and lines |
| V2 | Detects shapes and contours |
| AIT (Anterior Temporal Region) | Recognizes complex objects (e.g., faces) |

---

# Artificial Neural Networks (ANN)

## What is an ANN?
- An **Artificial Neural Network** is a mathematical function inspired by biological neural networks.
- It consists of:
  - **Neurons (Nodes)**: units that process information.
  - **Weights**: numerical values that determine signal strength between neurons.

## Layers in an ANN
| Layer | Function |
|-------|----------|
| **Input Layer** | Receives raw data |
| **Hidden Layer(s)** | Performs computations and feature extraction |
| **Output Layer** | Produces final result (e.g., label prediction) |

---

# Why Neural Networks?

Neural Networks are useful because they:
- Can **learn complex and non-linear relationships**.
- **Automatically extract features** from data (no manual feature engineering needed).
- Handle **high-dimensional and unstructured data** (e.g., images, audio, text).
- Perform extremely well with **large datasets** and **modern GPUs/TPUs**.
- Power **state-of-the-art systems** in:
  - Computer Vision (e.g., self-driving cars)
  - Natural Language Processing (e.g., ChatGPT, translation)
  - Robotics
  - Speech recognition

---

# Why is it called a Neuron?
- The structure and function are inspired by **biological neurons** in the brain.
- Therefore:
Biological Neuron ≈ Artificial Neuron
Neural Cell ≈ Neural Processing Unit

- The goal is to **mimic how the brain learns** using interconnected processing units.

---

# Summary Table

| Concept | Meaning | Example |
|--------|---------|---------|
| **AI** | Making machines intelligent | Siri, Chess AI |
| **ML** | Machines learning from data | Spam detection |
| **DL** | Learning with neural networks (multi-layered) | Facial recognition, ChatGPT |

---

# McCulloch-Pitts Neuron Model

The **McCulloch-Pitts Neuron** was proposed by **Warren McCulloch (neuroscientist)** and **Walter Pitts (logician)** in **1943**.  
It is a highly simplified computational model of a **biological neuron**.

In this model:

- `g` is the **aggregation function** which sums the inputs.
- `f` is the **activation function** which decides whether the neuron **fires (1)** or **does not fire (0)** based on a **threshold**.

The output of the neuron is always:
y ∈ {0, 1}

---

## McCulloch-Pitts Neuron for OR Logic Function

### Logic Rule
| x1 | x2 | x1 OR x2 |
|----|----|----------|
| 0  | 0  | 0        |
| 0  | 1  | 1        |
| 1  | 0  | 1        |
| 1  | 1  | 1        |

### Threshold Condition
The neuron **fires** when:
x1 + x2 ≥ 1

---

## Python Implementation

```python
# McCulloch-Pitts OR Function
def mcCullochPitts_OR(x1, x2):
    # Summation of inputs (aggregation)
    S = x1 + x2
    
    # Threshold for activation
    if S >= 1:
        return 1  # Neuron fires
    else:
        return 0  # Neuron does not fire


# Testing the OR function
inputs = [(0, 0), (0, 1), (1, 0), (1, 1)]
print("OR Function using McCulloch-Pitts Neuron")

for x1, x2 in inputs:
    output = mcCullochPitts_OR(x1, x2)
    print(f"Input: ({x1}, {x2}) -> Output: {output}")
OR Function using McCulloch-Pitts Neuron
```
Output
Input: (0, 0) -> Output: 0
Input: (0, 1) -> Output: 1
Input: (1, 0) -> Output: 1
Input: (1, 1) -> Output: 1

### Summary

The McCulloch-Pitts neuron is the foundation of artificial neural networks.

It uses binary inputs, summation, and a threshold activation.

Simple logical operations like 
- AND -> x1 + x2 ≥ 2
- OR -> x1 + x2 ≥ 1
### NOT:
```python
# McCulloch-Pitts NOT Function
def mcCullochPitts_NOT(x1):
    # Inversion of input
    return 1 - x1


# Testing the NOT function
inputs = [0, 1]
print("\nNOT Function using McCulloch-Pitts Neuron")

for x in inputs:
    output = mcCullochPitts_NOT(x)
    print(f"Input: ({x}) -> Output: {output}")
```
--- 

# The Perceptron Model

The **Perceptron** was proposed by **Frank Rosenblatt (1958)**.  
It is a more general and powerful model than the **McCulloch-Pitts Neuron**.

## Key Ideas
- Inspired by the **biological neuron**.
- A perceptron **associates numerical weights** to inputs and uses a **threshold (bias)** to make decisions.
- Inputs can be **real-valued**, not just 0/1.
- The perceptron **can learn weights** from training data.
- A single perceptron can only represent **linearly separable functions**.

---

## Mathematical Representation

A perceptron computes a **weighted sum** of inputs:

\[
y = f(w_1x_1 + w_2x_2 + .... + w_nx_n + b)
\]

Where:
- \( x_i \): Inputs
- \( w_i \): Weights (importance of each input)
- \( b \): Bias (shifts decision boundary)
- \( f() \): Activation function (usually **step function**)

### Activation Rule
$$
y =
\begin{cases}
1, & \text{if } (w \cdot x + b) \ge 0 \\
0, & \text{otherwise}
\end{cases}
$$
The **bias** acts as a **threshold controller**:
- Large **negative** bias → Harder to output **1**
- Large **positive** bias → Easier to output **1**

---

# Example: Decision Making Using Perceptron

**Question:** Should you go to watch a movie this weekend?

### Inputs
| Condition | Variable | Value |
|----------|----------|-------|
| Extra lecture this weekend? | \( x_1 \) | 1 |
| Friend wants to join? | \( x_2 \) | 0 |
| Assignments pending? | \( x_3 \) | 1 |

### Weights
| Input | Weight |
|-------|--------|
| \( x_1 \) | \( w_1 = 5 \) |
| \( x_2 \) | \( w_2 = 3 \) |
| \( x_3 \) | \( w_3 = 2 \) |

### Case 1 — Bias = **-8**
\[
z = (5 \cdot 1) + (3 \cdot 0) + (2 \cdot 1) + (-8) = 5 + 0 + 2 - 8 = -1
\]

Since \( z < 0 \), **Output = 0 → Do NOT go for the movie**.

---

### Case 2 — Bias = **-3**
\[
z = (5 \cdot 1) + (3 \cdot 0) + (2 \cdot 0) + (-3) = 5 - 3 = 2
\]

Since \( z > 0 \), **Output = 1 → Go for the movie**.

### Conclusion
- **Bias controls the decision boundary**.
- Decreasing the negative bias made it easier to output 1.

---

# Implementing Logical Gates Using Perceptron

| Gate | Weights | Bias | Condition Implemented |
|------|---------|------|----------------------|
| **OR** | \( w_1 = 5, w_2 = 3 \) | \( b = -2 \) | Fires if at least one input is 1 |
| **AND** | \( w_1 = 5, w_2 = 3 \) | \( b = -6 \) | Fires only when both inputs are 1 |
| **NOT** | \( w_1 = -3 \) | \( b = 2 \) | Inverts the input |
| **NAND** | \( w_1 = -5, w_2 = -3 \) | \( b = 6 \) | Opposite of AND |

---

## Python Implementation of Perceptron Gate

```python
def perceptron(x1, x2, w1, w2, b):
    z = w1*x1 + w2*x2 + b
    return 1 if z >= 0 else 0

# Example: AND Gate
print("AND Gate using Perceptron")
for inputs in [(0,0), (0,1), (1,0), (1,1)]:
    x1, x2 = inputs
    output = perceptron(x1, x2, w1=5, w2=3, b=-6)
    print(f"Input: {inputs} -> Output: {output}")
```
### Important Limitation of a Single Perceptron

A **single perceptron** can only learn **linearly separable** functions.

| Function | Can a Single Perceptron Learn It? | Reason |
|---------|-----------------------------------|--------|
| AND     | ✅ Yes                             | Linearly separable |
| OR      | ✅ Yes                             | Linearly separable |
| NAND    | ✅ Yes                             | Linearly separable |
| XOR     | ❌ No                              | **Not** linearly separable |

---
### (a) OR Gate

Weights: \( w_1 = 5, \; w_2 = 3 \)  
Bias: \( b = -2 \)  
Logic: Output = 1 if **any** input = 1  

| x₁ | x₂ | Sum = \(5x₁ + 3x₂ - 2\) | Output |
|----|----|------------------------|--------|
| 0  | 0  | -2                     | 0      |
| 0  | 1  | 1                      | 1      |
| 1  | 0  | 3                      | 1      |
| 1  | 1  | 6                      | 1      |

✔️ Works as OR gate.
---
### (b) AND Gate

Weights: \( w_1 = 5, \; w_2 = 3 \)  
Bias: \( b = -6 \)  
Logic: Output = 1 **only if both** inputs = 1  

| x₁ | x₂ | Sum = \(5x₁ + 3x₂ - 6\) | Output |
|----|----|------------------------|--------|
| 0  | 0  | -6                     | 0      |
| 0  | 1  | -3                     | 0      |
| 1  | 0  | -1                     | 0      |
| 1  | 1  | 2                      | 1      |

✔️ Works as AND gate.
---
### (c) NOT Gate

Weight: \( w_1 = -3 \)  
Bias: \( b = 2 \)  
Logic: Output = 1 when input = 0  

| x₁ | Sum = \(-3x₁ + 2\) | Output |
|----|--------------------|--------|
| 0  | 2                  | 1      |
| 1  | -1                 | 0      |

✔️ Works as NOT gate.
---
### (d) NAND Gate

Weights: \( w_1 = -5, \; w_2 = -3 \)  
Bias: \( b = 6 \)  
Logic: NAND = NOT(AND)  

| x₁ | x₂ | Sum = \(-5x₁ - 3x₂ + 6\) | Output |
|----|----|--------------------------|--------|
| 0  | 0  | 6                        | 1      |
| 0  | 1  | 3                        | 1      |
| 1  | 0  | 1                        | 1      |
| 1  | 1  | -2                       | 0      |

✔️ Works as NAND gate.

----

# Sigmoid Activation Function and Perceptron with Real-Valued Output

## Why Sigmoid?
The classical perceptron uses a **step function** for activation, where the output is either **0 or 1**.  
However, sometimes we want the output to be **smooth** and represent a **probability** rather than a binary yes/no.

To achieve this, we introduce the **Sigmoid Neuron**, where the activation function is much smoother.

---

## The Sigmoid (Logistic) Activation Function

The sigmoid function is defined as:

\[
y = \frac{1}{1 + \exp(-(w_0 + \sum_{i=1}^{n} w_i x_i))}
\]

Where:
- \( x_i \) are inputs
- \( w_i \) are weights
- \( w_0 \) is bias
- Output \( y \) is always in the range **(0, 1)**

### Key Properties
✅ Smooth curve (no sharp jumps)  
✅ Output is **continuous** and can be interpreted as **probability**  
✅ Used in neural networks and logistic regression  

---

## Example Neuron (2-Input Sigmoid Neuron)

Given:
\[
w = [0, 1], \quad b = 4
\]

Input:
\[
x = [2, 3]
\]

### Step 1: Compute Weighted Sum
\[
(w \cdot x) + b = (0 \cdot 2) + (1 \cdot 3) + 4 = 7
\]

### Step 2: Apply Sigmoid Function
\[
f(z) = \frac{1}{1 + e^{-z}}
\]

Substitute \( z = 7 \):
\[
f(7) = \frac{1}{1 + e^{-7}}
\]

Since:
\[
e^{-7} \approx 0.0009119
\]

\[
f(7) = \frac{1}{1 + 0.0009119} \approx 0.99909
\]

### Output Interpretation
\[
y \approx 0.999 \Rightarrow \text{High probability (≈ 99.9%)}
\]

This means the neuron strongly **activates** for this input.

---

## Coding a Simple Sigmoid Neuron (Feedforward Only)

```python
import numpy as np

# Activation function: Sigmoid
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

# Neuron class
class Neuron:
    def __init__(self, weights, bias):
        self.weights = weights
        self.bias = bias
    
    def feedforward(self, inputs):
        # Weighted sum + bias
        total = np.dot(self.weights, inputs) + self.bias
        # Pass through activation
        return sigmoid(total)

# Define weights and bias
weights = np.array([0, 1])   # w1 = 0, w2 = 1
bias = 4                      # b = 4

# Create neuron
n = Neuron(weights, bias)

# Input vector
x = np.array([2, 3])
```
# Output
print(n.feedforward(x))      # 0.9990889488055994
