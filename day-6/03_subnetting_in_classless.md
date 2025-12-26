# 🌐 Subnetting in CIDR Addressing

## (Classless Inter-Domain Routing)

---

## 1️⃣ What is CIDR?

### 🔹 Definition

**CIDR (Classless Inter-Domain Routing)** is an IP addressing method where:

> **IP addresses are not divided into fixed classes (A, B, C)**
> Instead, **any number of network bits can be used**.

CIDR is written as:

```
IP-address / prefix-length
```

Example:

```
192.168.1.0/26
```

---

## 2️⃣ Why CIDR Was Introduced?

### Problems with Classful Addressing

❌ Fixed subnet masks
❌ Huge IP address wastage
❌ No flexibility
❌ IPv4 exhaustion

### CIDR Solution

✅ Variable subnet sizes
✅ Efficient IP utilization
✅ Supports VLSM
✅ Smaller routing tables

---

## 3️⃣ Key Difference: Classful vs CIDR

| Feature      | Classful     | CIDR         |
| ------------ | ------------ | ------------ |
| Network size | Fixed        | Flexible     |
| Subnet mask  | Default only | Any length   |
| VLSM         | ❌ No         | ✅ Yes        |
| Routing      | Class-based  | Prefix-based |
| Efficiency   | Poor         | High         |

---

## 4️⃣ CIDR Subnetting – Core Idea (VERY IMPORTANT)

In CIDR:

* There is **no class**
* Subnetting is done by **choosing a prefix**
* Prefix decides:

  * Network bits
  * Host bits
  * Number of hosts

### Formulas (Same as before)

* **Hosts per subnet**

```
2^host_bits − 2
```

* **Block size**

```
256 − subnet_mask_octet
```

---

## 5️⃣ Example 1: Basic CIDR Subnetting

### Given:

```
192.168.1.0/26
```

---

### Step 1️⃣ Find Subnet Mask

```
/26 → 255.255.255.192
```

---

### Step 2️⃣ Host Bits

```
32 − 26 = 6 host bits
```

---

### Step 3️⃣ Number of Hosts

```
2^6 − 2 = 62 hosts
```

---

### Step 4️⃣ Block Size

```
256 − 192 = 64
```

---

### Step 5️⃣ Subnet Ranges

| Subnet | Network ID    | First Host | Last Host | Broadcast |
| ------ | ------------- | ---------- | --------- | --------- |
| 1      | 192.168.1.0   | .1         | .62       | .63       |
| 2      | 192.168.1.64  | .65        | .126      | .127      |
| 3      | 192.168.1.128 | .129       | .190      | .191      |
| 4      | 192.168.1.192 | .193       | .254      | .255      |

✔️ Same calculation style, but **no class restriction**

---

## 6️⃣ Example 2: CIDR with Host Requirement (Very Common)

### Given:

```
Network: 192.168.10.0/24
Requirement: At least 30 hosts per subnet
```

---

### Step 1️⃣ Find Host Bits

```
2^h − 2 ≥ 30
```

```
h = 5  →  2^5 − 2 = 30
```

---

### Step 2️⃣ Prefix Length

```
32 − 5 = /27
```

---

### Step 3️⃣ Subnet Mask

```
/27 → 255.255.255.224
```

---

### Step 4️⃣ Block Size

```
256 − 224 = 32
```

---

### Step 5️⃣ Subnet Ranges

```
192.168.10.0 – 31
192.168.10.32 – 63
192.168.10.64 – 95
...
192.168.10.224 – 255
```

✔️ Each subnet has **30 usable hosts**

---

## 7️⃣ Example 3: Find Network, Broadcast (CIDR Style)

### Given IP:

```
192.168.1.77/27
```

---

### Step 1️⃣ Block Size

```
/27 → 255.255.255.224
Block size = 32
```

---

### Step 2️⃣ Find Range

Multiples of 32:

```
0–31
32–63
64–95  ← 77 lies here
```

---

### Step 3️⃣ Final Answer

| Field      | Value        |
| ---------- | ------------ |
| Network ID | 192.168.1.64 |
| First Host | 192.168.1.65 |
| Last Host  | 192.168.1.94 |
| Broadcast  | 192.168.1.95 |

---

## 8️⃣ CIDR + VLSM Example (REAL WORLD)

### Given:

```
Network: 10.0.0.0/24
```

### Requirements:

| Dept | Hosts |
| ---- | ----- |
| A    | 100   |
| B    | 50    |
| C    | 20    |

---

### Step 1️⃣ Sort

```
100 → 50 → 20
```

---

### Step 2️⃣ Subnet Sizes

| Hosts | Prefix |
| ----- | ------ |
| 100   | /25    |
| 50    | /26    |
| 20    | /27    |

---

### Step 3️⃣ Allocate

#### Dept A

```
10.0.0.0/25 → 0–127
```

#### Dept B

```
10.0.0.128/26 → 128–191
```

#### Dept C

```
10.0.0.192/27 → 192–223
```

✔️ **CIDR + VLSM working together**

---

## 9️⃣ CIDR Route Aggregation (IMPORTANT THEORY)

### Without CIDR:

```
192.168.0.0/24
192.168.1.0/24
192.168.2.0/24
192.168.3.0/24
```

### With CIDR:

```
192.168.0.0/22
```

✔️ One route instead of four
✔️ Smaller routing tables
✔️ Faster routing

---

## 🔟 Advantages of CIDR Subnetting

✅ No class limitation
✅ Supports VLSM
✅ Efficient IP usage
✅ Route aggregation
✅ Prevents IPv4 exhaustion

---

## 1️⃣1️⃣ Disadvantages of CIDR

❌ More complex than classful
❌ Needs skilled planning
❌ Misconfiguration causes routing errors

---

## 🧠 One-Line Exam Answers (Write Directly)

**Q:** What is CIDR?
**A:** CIDR is a classless IP addressing scheme that allows flexible subnet masks.

**Q:** Why CIDR is better than classful?
**A:** It reduces IP wastage and supports VLSM.

**Q:** CIDR notation?
**A:** IP address followed by prefix length (e.g., /26).

---

## 🔚 Final Summary

| Concept     | Meaning                 |
| ----------- | ----------------------- |
| CIDR        | Classless IP addressing |
| Subnetting  | Based on prefix length  |
| Flexibility | Very high               |
| Used with   | VLSM                    |
| Replaced    | Classful addressing     |

---
---
---
---
---
---
---


# ❓ “Isn’t CIDR subnetting the same as Classful subnetting?”

### 🔴 **Short answer**

👉 **Mathematically: YES (formulas look the same)**
👉 **Conceptually & practically: NO (they are very different)**

Now let’s **separate what is SAME vs what is DIFFERENT**.

---

## 1️⃣ Why formulas look identical (IMPORTANT TRUTH)

Subnetting is **binary math**.

Binary math does **not change** whether:

* Classful
* CIDR
* VLSM

So these stay **the same everywhere**:

```
Hosts = 2^h − 2
Block size = 256 − subnet mask
Network ID = all host bits 0
Broadcast = all host bits 1
```

📌 **That’s why you feel “this is the same”**
And **you are correct**.

---

## 2️⃣ Then WHAT ACTUALLY CHANGES? (Core Difference)

### 🔥 The REAL difference is NOT the math

### 🔥 The REAL difference is **WHO DECIDES THE MASK**

---

## 3️⃣ Classful Subnetting (STRICT RULE)

In **classful addressing**:

| Class | Default Mask |
| ----- | ------------ |
| A     | /8           |
| B     | /16          |
| C     | /24          |

### 🚫 Rule:

> You **MUST start** with the default mask
> You can **ONLY borrow bits from the host part**

### Example (Class C)

```
192.168.1.0  → MUST be /24 first
```

You **cannot** say:

```
192.168.1.0/20 ❌
```

Why?
Because **Class C networks don’t allow it**.

---

## 4️⃣ CIDR Subnetting (NO RULES 😈)

In **CIDR**:

> ❌ No class
> ❌ No default mask
> ❌ No fixed boundary

You can write:

```
192.168.1.0/20
192.168.1.0/26
192.168.1.0/30
```

All are **100% valid**.

✔️ CIDR allows **any prefix length from /0 to /32**

---

## 5️⃣ SAME MATH, DIFFERENT FREEDOM (Key Insight)

Let me show you **same subnet**, different meaning.

---

### 🔹 Example A (Classful)

```
192.168.1.0/26
```

Meaning:

* Started from `/24` (Class C)
* Borrowed **2 bits**
* Still inside Class C rules

---

### 🔹 Example B (CIDR)

```
192.168.1.0/26
```

Meaning:

* No class assumed
* Prefix chosen directly
* No borrowing concept

📌 **Numerically same**
📌 **Conceptually different**

---

## 6️⃣ Where Classful FAILS and CIDR WINS (CRITICAL)

### ❌ Classful cannot do this:

```
172.16.0.0/20
10.0.0.0/18
192.168.0.0/22
```

Because:

* Class B must start at /16
* Class A must start at /8
* Class C must start at /24

---

### ✅ CIDR CAN:

```
172.16.0.0/20  ✔
10.0.0.0/18    ✔
192.168.0.0/22 ✔
```

This is **the real power**.

---

## 7️⃣ Routing Difference (MOST IMPORTANT IN REAL WORLD)

### 🔴 Classful Routing (OLD)

* Routers **do not carry subnet mask**
* They assume default class mask
* ❌ VLSM impossible

### 🟢 CIDR Routing (MODERN)

* Routers carry **prefix length**
* Supports **VLSM**
* Supports **route aggregation**

---

## 8️⃣ Example that Classful CANNOT solve

### Requirement:

```
Network: 192.168.0.0
Need 4 subnets of different sizes
```

❌ Classful:

* All subnets MUST be same size
* Impossible

✅ CIDR:

```
192.168.0.0/25
192.168.0.128/26
192.168.0.192/27
192.168.0.224/28
```

---

## 9️⃣ One Sentence That Clears Everything (EXAM GOLD)

> **Classful subnetting changes the host bits inside a fixed class boundary, whereas CIDR allows choosing any prefix length independent of class.**

---

## 🔚 Final Mental Model (Remember This)

Think like this:

🧱 **Classful** = building with fixed-size bricks
🧩 **CIDR** = cutting bricks any way you want

Math stays same.
Freedom changes.

---

## ✅ So your understanding is CORRECT

You noticed:
✔ Same formulas
✔ Same subnet masks
✔ Same calculations

But now you know:
🔥 **CIDR removes the class boundary**
🔥 **CIDR enables VLSM + aggregation**
🔥 **CIDR is why the internet scales**
