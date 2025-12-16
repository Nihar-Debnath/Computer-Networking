# 🚀 **Packet Switching**

Packet switching is a method of sending data across a network by breaking it into **small packets**.
Each packet travels independently through the network and may take different routes.

Packet switching can be done in **two ways**:

# 1️⃣ **Datagram Switching**

# 2️⃣ **Virtual Circuit Switching**

Your board image shows exactly this comparison.



---

# 🔵 **1️⃣ DATAGRAM SWITCHING (Connectionless Packet Switching)**

Used in the **Internet (IP networks)**

---

## ⭐ **1. Connectionless**

There is **no setup** between sender and receiver.
You **simply start sending packets immediately**.
The network does *not* establish or maintain any path for you.

✔️ Like sending many small letters through a post office—no need to call the postal service first.

---

## ⭐ **2. No Reservation**

No part of the network (bandwidth, memory, path) is reserved for your packets.

✔️ Your packets compete with everyone else’s packets using the network at that time.

If the network is busy → your packet may be delayed or dropped.

---

## ⭐ **3. Out of Order Delivery**

Since each packet chooses **its own path**, all packets may be delivered in **different order**.

Example:

```
Packet 1 takes route A → B → C → D  
Packet 2 takes route A → E → F → D  
Packet 3 takes route A → H → C → D
```

Arrival order might be: Packet 3, Packet 1, Packet 2.

✔️ Your device at the receiver side must **rearrange** the packets.

---

## ⭐ **4. High Overhead**

Every packet must carry **full destination information**, like:

* destination address
* source address
* sequence number
* error check bits
* routing information

Why?
Because each packet is independent, routers must know where to send it.

✔️ More header data → more overhead.

---

## ⭐ **5. Packet Loss ↑**

If the network is congested:

* Routers may drop packets.
* Some packets may never reach the destination.

✔️ Higher chance of loss compared to virtual circuits.

---

## ⭐ **6. Used in Internet**

The **entire Internet uses Datagram switching** through the **IP protocol**.

Why?
Because it is:

* fast
* flexible
* scalable
* supports billions of devices

---

# 🔴 **2️⃣ VIRTUAL CIRCUIT SWITCHING (Connection-Oriented Packet Switching)**

Used in older telecom technologies like **X.25 and ATM**.

---

## ⭐ **1. Connection-Oriented**

Before sending data:

* The network sets up a **fixed path** between sender and receiver.
* Routers agree on the path.
* A “virtual circuit” is established.

✔️ Similar to making a phone call → connection is created first.

---

## ⭐ **2. Reservation**

Certain network resources are reserved for your connection, such as:

* bandwidth
* buffers (memory in routers)
* a fixed path

✔️ This reduces congestion and packet loss.

✔️ Guarantees better performance.

---

## ⭐ **3. Same Order Delivery**

Since all packets take **the same path**, they always arrive **in the correct order**.

```
Packet 1 → same route  
Packet 2 → same route  
Packet 3 → same route
```

The receiver does **not** need to reorder anything.

---

## ⭐ **4. Less Overhead**

Only the **first packet** needs full information.

After the connection is set, packets only carry a **short circuit number**, not the full address.

✔️ Headers are smaller
✔️ Faster processing

---

## ⭐ **5. Packet Loss ↓**

Because resources are reserved and path is fixed:

* Less congestion
* Very few packets are dropped

✔️ High reliability.

---

## ⭐ **6. Examples: X.25, ATM**

These are older technologies used by:

* Banking networks
* Telephone networks
* Early broadband systems

Today, mainly replaced by IP networks.

---

# 📌 **Final Comparison (Fully Explained)**

| Feature         | Datagram Switching                 | Virtual Circuit Switching      |
| --------------- | ---------------------------------- | ------------------------------ |
| **Connection**  | No connection setup                | Connection setup required      |
| **Reservation** | No resource reservation            | Bandwidth & path reserved      |
| **Path**        | Dynamic, different for each packet | Fixed, same for all packets    |
| **Order**       | Packets may arrive out of order    | Always arrive in correct order |
| **Overhead**    | High (full address every time)     | Low (short circuit number)     |
| **Packet Loss** | High chance                        | Very low                       |
| **Speed**       | Faster start (no setup)            | Slower start (setup needed)    |
| **Examples**    | Internet (IP)                      | X.25, ATM                      |

---

# 🎉 **Super Simple Real-World Example**

### 📮 Datagram = Sending letters through post office

* Each letter may take different routes.
* They may arrive in random order.
* No guaranteed speed.
* You can send immediately (no setup).

### 🚆 Virtual Circuit = Booking a whole train compartment

* Setup (booking) needed before travel.
* All people travel the same path.
* Order and reliability are high.