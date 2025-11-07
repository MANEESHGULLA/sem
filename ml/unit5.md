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

Simple logical operations like AND, OR, and NOT can be implemented.


