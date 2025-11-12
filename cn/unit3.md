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

