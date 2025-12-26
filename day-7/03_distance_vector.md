## 1️⃣ First: What problem are we solving?

In a **network**, routers must decide:

> **“Which path should I use to send a packet to a destination network?”**

To decide this, routers need **routing information**.

There are two big families of routing algorithms:

* **Distance Vector**
* **Link State**

👉 You asked about **Distance Vector Routing Algorithm**.

---

## 2️⃣ What is Distance Vector Routing? (One-line idea)

> Each router **knows only**:
>
> * how far (distance) a destination is
> * and **which neighbor** to send the packet to

That’s it.

Routers **do NOT know the full network topology**.

---

## 3️⃣ Why is it called “Distance Vector”?

Because each router stores a table where each entry has:

| Term         | Meaning                       |
| ------------ | ----------------------------- |
| **Distance** | Cost to reach the destination |
| **Vector**   | Direction (next-hop router)   |

So every routing table is a **distance vector**.

---

## 4️⃣ What information does a router maintain?

Each router maintains a **Routing Table** with entries like:

```
Destination | Distance (Cost) | Next Hop
```

Example (Router A):

```
Network X | 3 | Router B
Network Y | 1 | Router C
```

Meaning:

* To reach **Network X**, cost = 3, send via **B**
* To reach **Network Y**, cost = 1, send via **C**

---

## 5️⃣ How does a router learn routes?

Distance Vector works using **neighbor communication**.

### Key rule:

> **Routers only talk to their directly connected neighbors**

They **never talk to all routers**.

---

## 6️⃣ Step-by-step working (core logic)

### 🔹 Step 1: Initialization

* Each router knows:

  * Distance to **itself = 0**
  * Distance to **direct neighbors = link cost**
  * Distance to **others = ∞ (infinity)**

Example (Router A):

```
A → A = 0
A → B = 1
A → C = ∞
```

---

### 🔹 Step 2: Share routing table with neighbors

Periodically, each router sends **its entire routing table** to **its neighbors**.

Example:

* Router A sends its table to B
* Router B sends its table to A and C

---

### 🔹 Step 3: Update using Bellman–Ford equation

This is the **heart** of Distance Vector.

### Bellman–Ford formula:

```
D(A → X) = min [ cost(A → N) + D(N → X) ]
```

Meaning:

> “To reach destination X, check all neighbors N,
> choose the neighbor that gives minimum cost.”

---

### 🔹 Step 4: Table update

If a **shorter path** is found:

* Update distance
* Update next-hop

If not:

* Keep old value

---

### 🔹 Step 5: Repeat forever

This process keeps repeating:

* Exchange tables
* Recalculate distances
* Update routes

Until the network **converges** (no more changes).

---

## 7️⃣ Simple real-world analogy 🚚

Think of **delivery offices**:

* Each office only knows:

  * How far other cities are
  * Which nearby office to forward parcels to
* Offices **share info with nearby offices**
* They don’t know the entire country map

Over time, everyone learns the **best routes**.

---

## 8️⃣ Example (very small network)

Suppose:

```
A ---1--- B ---1--- C
```

### Initial tables:

**Router A**

```
A = 0
B = 1
C = ∞
```

**Router B**

```
A = 1
B = 0
C = 1
```

**Router C**

```
A = ∞
B = 1
C = 0
```

---

### After exchanging tables:

Router A learns:

```
A → B → C = 1 + 1 = 2
```

So A updates:

```
C = 2 via B
```

Network converges ✔️

---

## 9️⃣ What metric is used for distance?

Depends on protocol:

* **Hop count** (number of routers)
* **Delay**
* **Bandwidth**
* **Cost**

Most basic Distance Vector protocols use **hop count**.

---

## 🔟 Famous protocol using Distance Vector

### RIP (Routing Information Protocol)

* Uses **hop count**
* Maximum hops = **15**
* Hop count 16 = unreachable
* Simple but limited

---

## 1️⃣1️⃣ Advantages of Distance Vector

✅ Simple to understand
✅ Easy to implement
✅ Less CPU and memory usage
✅ Suitable for small networks

---

## 1️⃣2️⃣ Disadvantages (VERY IMPORTANT)

### ❌ Count-to-Infinity Problem

* Bad news spreads **slowly**
* Routers keep increasing distance endlessly

Example:

```
A thinks path to C is via B
B thinks path to C is via A
→ infinite loop
```

---

### ❌ Slow convergence

* Takes time to adapt to network changes

---

### ❌ Routing loops

* Packets can circulate endlessly

---

## 1️⃣3️⃣ Solutions to problems (brief)

Distance Vector protocols use techniques like:

* **Split Horizon**
* **Poison Reverse**
* **Hold-down timers**
* **Triggered updates**

(If you want, we can deep-dive each one)

---

## 1️⃣4️⃣ One-line exam definition ⭐

> **Distance Vector Routing Algorithm** is a routing algorithm in which each router shares its routing table with neighbors and calculates the shortest path using the Bellman–Ford algorithm based on distance and next-hop information.

---
---
---
---
---
---
---
---
---
---



## 🔹 Network Example

Assume this network (numbers are **cost / hop count**):

```
A ——1—— B ——1—— C
```

Routers: **A, B, C**

---

## 🔹 Rule Reminder (very important)

Each router:

* Knows distance to **itself = 0**
* Knows distance to **direct neighbors**
* Knows **nothing else (∞)**
* Shares its **routing table only with neighbors**
* Uses **Bellman–Ford formula**

```
New Distance = cost(to neighbor) + neighbor’s distance
```

---

## 1️⃣ Step 1: Initial Routing Tables (Initialization)

### 📍 Router A

| Destination | Distance | Next Hop |
| ----------- | -------- | -------- |
| A           | 0        | —        |
| B           | 1        | B        |
| C           | ∞        | —        |

---

### 📍 Router B

| Destination | Distance | Next Hop |
| ----------- | -------- | -------- |
| A           | 1        | A        |
| B           | 0        | —        |
| C           | 1        | C        |

---

### 📍 Router C

| Destination | Distance | Next Hop |
| ----------- | -------- | -------- |
| A           | ∞        | —        |
| B           | 1        | B        |
| C           | 0        | —        |

---

## 2️⃣ Step 2: Routers Exchange Tables

* A sends its table to B
* B sends its table to A and C
* C sends its table to B

---

## 3️⃣ Step 3: Table Update Using Bellman–Ford

### 📍 Router A receives B’s table

Router B says:

```
B → C = 1
```

Router A calculates:

```
A → B → C = 1 (A→B) + 1 (B→C) = 2
```

👉 A **updates** its table because `2 < ∞`

### Updated Router A Table

| Destination | Distance | Next Hop |
| ----------- | -------- | -------- |
| A           | 0        | —        |
| B           | 1        | B        |
| C           | 2        | B        |

---

### 📍 Router C receives B’s table

Router B says:

```
B → A = 1
```

Router C calculates:

```
C → B → A = 1 + 1 = 2
```

👉 C **updates** its table

### Updated Router C Table

| Destination | Distance | Next Hop |
| ----------- | -------- | -------- |
| A           | 2        | B        |
| B           | 1        | B        |
| C           | 0        | —        |

---

## 4️⃣ Step 4: Convergence (No More Changes)

Now if routers exchange tables again:

* No router finds a **shorter path**
* Tables remain unchanged

✅ **Network has converged**

---

## 🔹 Final Routing Tables (Stable State)

### Router A

| Destination | Distance | Next Hop |
| ----------- | -------- | -------- |
| A           | 0        | —        |
| B           | 1        | B        |
| C           | 2        | B        |

### Router B

| Destination | Distance | Next Hop |
| ----------- | -------- | -------- |
| A           | 1        | A        |
| B           | 0        | —        |
| C           | 1        | C        |

### Router C

| Destination | Distance | Next Hop |
| ----------- | -------- | -------- |
| A           | 2        | B        |
| B           | 1        | B        |
| C           | 0        | —        |

---

## 🔹 What did we learn from this example?

✔ Routers **don’t know full topology**
✔ They only trust **neighbor information**
✔ Shortest path is found using **cost + neighbor distance**
✔ Algorithm repeats until **no changes occur**

---

## 🔑 Exam Tip (Very Important)

If asked:

> *“Explain Distance Vector routing with example”*

Always show:

1. Initial tables
2. Exchange of tables
3. Bellman–Ford calculation
4. Final converged tables
