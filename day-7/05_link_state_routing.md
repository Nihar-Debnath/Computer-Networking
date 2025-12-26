# 🔵 Link State Routing

### (Computer Networks)

---

## 1️⃣ First: Why do we need Link State Routing?

In routing, every router must answer:

> **“What is the best path to every destination in the network?”**

Earlier you learned **Distance Vector Routing**, where:

* Routers know **only neighbors**
* Bad news travels slowly
* Problems like **count-to-infinity** occur

👉 **Link State Routing** was designed to **solve these problems**.

---

## 2️⃣ One-line definition (Exam Gold ⭐)

> **Link State Routing** is a routing technique in which each router discovers the full network topology and independently computes the shortest path using Dijkstra’s algorithm.

---

## 3️⃣ Core Idea (Very Important)

👉 **Every router knows the complete network map.**

Unlike Distance Vector:

* Routers do **not depend blindly on neighbors**
* Each router makes **its own decisions**

Think of it like **Google Maps**:

* You have the full map
* You calculate the best route yourself

---

## 4️⃣ What does “Link State” mean?

* **Link** → Connection between routers
* **State** → Status of that link (up/down, cost, bandwidth)

Each router keeps information about:

* Who its neighbors are
* Cost of each link
* Whether links are working

---

## 5️⃣ What information does a router maintain?

Each router maintains **three main things**:

### 1️⃣ Neighbor table

List of directly connected routers

### 2️⃣ Link State Database (LSDB)

Complete topology of the network (same for all routers)

### 3️⃣ Routing table

Best paths calculated from the LSDB

---

## 6️⃣ How Link State Routing works (Step by Step)

This is the **most important part**.

---

### 🔹 Step 1: Neighbor discovery

Each router sends **HELLO messages** to:

* Discover neighbors
* Check if links are alive

Example:

```
Router A discovers B and C
```

---

### 🔹 Step 2: Measure link cost

Router measures cost of each link, such as:

* Bandwidth
* Delay
* Cost value

Example:

```
A → B = 1
A → C = 4
```

---

### 🔹 Step 3: Create Link State Advertisement (LSA)

Each router creates an **LSA**, containing:

* Router ID
* List of neighbors
* Cost to each neighbor

Example (Router A’s LSA):

```
A → B cost 1
A → C cost 4
```

---

### 🔹 Step 4: Flood LSAs to all routers

* LSAs are **flooded** to **every router** in the network
* Not just neighbors
* Each router stores LSAs in the **LSDB**

👉 Result:

> **All routers now have the same network topology**

---

### 🔹 Step 5: Build network graph

Using the LSDB, each router builds a **graph**:

* Routers = nodes
* Links = edges
* Costs = weights

---

### 🔹 Step 6: Run Dijkstra’s Algorithm

Each router independently runs:

> **Shortest Path First (SPF) / Dijkstra’s Algorithm**

This computes:

* Shortest path to every destination
* Best next-hop router

---

### 🔹 Step 7: Create routing table

The shortest paths are converted into:

```
Destination → Next Hop → Cost
```

---

## 7️⃣ Small Example (Conceptual)

Assume network:

```
A ——1—— B ——1—— C
 \        |
  \4      |2
   \      |
     —— D —
```

* All routers flood LSAs
* Every router learns full topology
* Each router runs Dijkstra
* All routers compute **optimal paths**

No guessing, no loops.

---

## 8️⃣ Which algorithm is used?

👉 **Dijkstra’s Algorithm**

* Also called **Shortest Path First (SPF)**
* Time complexity ≈ **O(n²)** (basic version)

---

## 9️⃣ Famous Link State Protocol

### ⭐ OSPF (Open Shortest Path First)

* Uses link state routing
* Uses Dijkstra algorithm
* Very fast convergence
* Used in large real-world networks

(Protocol example: OSPF)

---

## 🔟 Advantages of Link State Routing

✅ Fast convergence
✅ No count-to-infinity problem
✅ No routing loops
✅ Accurate routing decisions
✅ Suitable for large networks

---

## 1️⃣1️⃣ Disadvantages of Link State Routing

❌ High memory usage (stores full topology)
❌ More CPU usage (Dijkstra computation)
❌ More complex to implement
❌ Flooding causes overhead

---

## 1️⃣2️⃣ Distance Vector vs Link State (Quick)

| Feature           | Distance Vector | Link State |
| ----------------- | --------------- | ---------- |
| Network knowledge | Partial         | Complete   |
| Algorithm         | Bellman-Ford    | Dijkstra   |
| Convergence       | Slow            | Fast       |
| Count-to-Infinity | Yes             | No         |
| Routing loops     | Possible        | Rare       |
| Example protocol  | RIP             | OSPF       |

---

## 1️⃣3️⃣ Key Sentence to Remember Forever ⭐

> **Distance Vector trusts neighbors; Link State trusts itself using full topology knowledge.**

---

## 1️⃣4️⃣ Exam-ready short answer

> Link State Routing is a routing method where routers exchange link information through flooding and compute shortest paths using Dijkstra’s algorithm, resulting in faster and loop-free routing.
