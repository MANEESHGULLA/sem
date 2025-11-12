### Flooding (in Computer Networks)

Flooding is a packet forwarding technique used in computer networks where every incoming packet is sent out on all outgoing links — except the one it came from.

## 🔹 How Flooding Works

When a router receives a packet, it copies the packet and sends it to all its neighboring routers (except the one it received the packet from).

This continues until the packet reaches its destination — or until some limit is reached.

🔹 Problem

## If flooding continues blindly:

The same packet may circulate indefinitely, creating duplicate packets and network congestion.

This happens because each router keeps re-sending the same packet everywhere.

##🔹 Solution – Damping the Flood

To prevent infinite looping, routers must keep track of packets they’ve already seen.

## Methods to control flooding:

# 1.Sequence Numbers

  - Each packet gets a unique sequence number from the source router (for example, Packet #1, #2, #3, etc.).

  - Each router maintains a list (or table) for every source router.

  - The list stores which sequence numbers have already been received.

  - When a router gets a packet:

    - If the (source, sequence number) pair is new, it floods the packet further.

    - If it’s already seen, it discards the packet.

✅ This prevents sending the same packet multiple times.
