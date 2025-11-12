# 🌐 Flooding (in Computer Networks)

Flooding is a **packet forwarding technique** used in computer networks where **every incoming packet** is sent out on **all outgoing links — except the one it came from**.

---

## 🔹 How Flooding Works

When a router receives a packet:
- It **copies the packet**.
- Sends it to **all neighboring routers**, except the one it received it from.

This process continues until the packet:
- **Reaches its destination**, or  
- **Reaches a specified limit**.

---

## 🔹 Problem

If flooding continues **blindly**,  
the **same packet may circulate indefinitely**, creating:
- Duplicate packets  
- Network congestion  

👉 This happens because routers keep **re-sending the same packet** again and again.

---

## 🔹 Solution – Damping the Flood

To prevent **infinite looping**, routers must **track packets** they’ve already seen.

---

## 🔹 Methods to Control Flooding

### 1. Sequence Numbers

- Each packet is assigned a **unique sequence number** by the source router (e.g., Packet #1, #2, #3, etc.).
- Each router maintains a **list (or table)** for every source router.
- The list stores **which sequence numbers** have already been received.

**When a router receives a packet:**
1. If the **(source, sequence number)** pair is **new** → it **floods** the packet further.  
2. If it has **already seen** the pair → it **discards** the packet.

✅ **This prevents sending the same packet multiple times.**

---
# 🛰️ Distance Vector Routing (DVR) – Point-wise Explanation

---

## 🔹 1. Definition

**DVR (Distance Vector Routing)** is a **routing algorithm** where each router **periodically shares its routing information (distance vector)** with its **immediate neighbors**.  
It is based on the **Bellman-Ford Algorithm**.

---

## 🔹 2. Purpose

To help routers **find the shortest path** to all other routers in the network.

---

## 🔹 3. Information Stored by Each Router

- **Router ID** – Unique identifier for each router.  
- **Link Cost** – Cost (or metric) of each directly connected link (can be static or dynamic).  
- **Distance Vector Table** – Contains:
  - Distance from itself to every destination node.
  - The next hop (neighbor) used to reach that destination.

---

## 🔹 4. Initialization of Distance Vector Table

- Distance to itself = **0**  
- Distance to all other routers = **∞ (infinity)** (unknown initially)

---

## 🔹 5. Working / Algorithm Steps

**Step 1:** Each router sends its **distance vector (routing table)** to all its **direct neighbors**.  
**Step 2:** Each router receives the **distance vectors** from its neighbors.  
**Step 3:** The router updates its own distance vector using the **Bellman-Ford Equation**:

\[
D_x(y) = \min \{ C(x,v) + D_v(y) \}
\]

where:  
- \( D_x(y) \): Distance from router **x** to **y**  
- \( C(x,v) \): Cost from **x** to neighbor **v**  
- \( D_v(y) \): Distance from **v** to destination **y**

**Step 4:** If the newly computed distance is **smaller** than the old one, the routing table is **updated**.  
**Step 5:** This process repeats **periodically** or when a **topology change** occurs (like a link failure).

---

## 🔹 6. Trigger for Recalculation

A router recalculates its distance vector when:
- It receives a **new or changed distance vector** from a neighbor.  
- A **link goes down** or becomes unavailable.

---

## 🔹 7. Periodic Updates

Routers periodically send their **current distance vectors** to neighbors,  
even if no change occurs — to **maintain consistency**.

---

## 🔹 8. Example

Consider 3 routers: **X, Y, Z** connected as a triangle.

Each router maintains a table with distances to all others.

Suppose:  
- Direct cost **X–Y = 2**, **Y–Z = 3**, **X–Z = 7**

Now, router **X** receives **Y’s table** and finds that:  
- Going **X → Y → Z** costs **2 + 3 = 5**,  
  which is **less than 7 (direct path)**.

✅ **X updates its table:**
- Distance to **Z = 5 via Y**

---

## 🔹 9. Advantages

- Simple to implement.  
- Requires less computational power and memory.

---

## 🔹 10. Disadvantages

- **Slow convergence** (takes time to reflect changes).  
- **Count-to-infinity problem** (looping updates when a link fails).  
- **Periodic updates** cause unnecessary network traffic.

---

