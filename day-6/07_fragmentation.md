![](./images/IPv4-Datagram-Header.jpg)

## 🟩 SECOND ROW OF IPv4 HEADER (Fragmentation Row)

From the diagram, **2nd row looks like this**:

```
| Identification (16 bits) | Flags (3 bits) | Fragment Offset (13 bits) |
```

👉 This entire row exists **ONLY** because of **fragmentation**.

---

# 🌍 First: What is Fragmentation? (Real world first)

### Real-world analogy 📦✂️

Imagine:

* You want to send a **big table** through a courier.
* Courier company allows **only small boxes**.

So you:

* Cut the table into **pieces**
* Put them in **multiple boxes**
* Send them separately

👉 This breaking of one big thing into smaller pieces is **fragmentation**.

In networking:

* **Big IP packet**
* **Small network capacity (MTU)**
* Packet is **broken into fragments**

---

# Now explain EACH FIELD with REAL WORLD meaning

---

## 1️⃣ Identification (16 bits)

### 🧾 *Which pieces belong together?*

### Real-world analogy 🏷️

Each broken table piece has:

* **Same order number** written on it

Example:

```
Order ID: 4587
```

So when pieces arrive:

> “All boxes with ID 4587 belong to the same table.”

### In IPv4:

* Identification is a **unique number**
* Same for **all fragments of one packet**

📌 Without this:
Receiver would not know **which fragments belong together**

---

## 2️⃣ Flags (3 bits)

### 🚦 *Can I break it? Are more pieces coming?*

Flags control **how fragmentation behaves**.

Diagram shows **3 flag bits**:

---

### 🔹 (a) Reserved Bit (1 bit)

* Always **0**
* Kept for future use

👉 Ignore in exams unless asked.

---

### 🔹 (b) DF – Don’t Fragment

### Real-world analogy 🚫✂️

Sender writes on box:

> ❌ “DO NOT CUT THIS ITEM”

### In IPv4:

* **DF = 1** → packet must NOT be fragmented
* If router cannot send it → packet is **dropped**

📌 Used for **Path MTU Discovery**

---

### 🔹 (c) MF – More Fragments

### Real-world analogy 📦📦📦

Courier writes:

> “More boxes are coming…”

### In IPv4:

* **MF = 1** → more fragments will follow
* **MF = 0** → this is the **last fragment**

📌 Receiver waits until MF = 0 is seen

---

## 3️⃣ Fragment Offset (13 bits)

### 📍 *Where does this piece fit?*

### Real-world analogy 🧩

Imagine puzzle pieces numbered:

* Piece starts at position 0
* Next piece starts at position 8
* Next at 16…

This tells:

> “Where does this piece go in the original item?”

### In IPv4:

* Fragment Offset tells **position of fragment**
* Measured in **8-byte blocks**

Example:

* Offset = 0 → first fragment
* Offset = 185 → starts at byte `185 × 8`

📌 Helps receiver **rebuild packet in correct order**

---

# 🧠 How These 3 Work Together (VERY IMPORTANT)

Let’s see one full real-world flow:

### Example:

* Original packet = **4000 bytes**
* Network allows only **1500 bytes**

### What happens?

* Packet is broken into **3 fragments**
* All fragments have:

  * Same **Identification**
  * DF = 0
  * MF = 1 (except last)
  * Different Fragment Offsets

Receiver:

1. Groups fragments using **Identification**
2. Orders them using **Fragment Offset**
3. Stops when **MF = 0**

---

## 🧠 ONE-LINE EXAM SUMMARY (MUST MEMORIZE)

> **IPv4 fragmentation uses Identification to group fragments, Flags to control fragmentation, and Fragment Offset to correctly reassemble the original datagram.**

---

## ⚠️ VERY IMPORTANT NOTE (EXAM + REAL WORLD)

* Fragmentation is **bad for performance**
* Modern networks try to **avoid fragmentation**
* IPv6 **removes router-side fragmentation**



---
---
---
---



![](./images/3.png)


## 📘 GIVEN (from the question)

* **Total Datagram size** = **3000 bytes**
* **IP Header** = **20 bytes**
* **IP Payload (Data)** = **2980 bytes**
* **MTU of next link** = **500 bytes**

👉 MTU means:

> **Maximum size of ONE packet that can go on the link**

---

## 🧠 KEY RULES YOU MUST REMEMBER

### Rule 1️⃣

Each **fragment must fit in MTU**

```
Fragment Total Length ≤ MTU
```

---

### Rule 2️⃣

Each fragment needs its **own IP header**

So usable **data per fragment** is:

```
MTU − IP Header
= 500 − 20
= 480 bytes (max data per fragment)
```

---

### Rule 3️⃣

**Fragment Offset is in multiples of 8 bytes**

✔ 480 is divisible by 8 → GOOD
(480 ÷ 8 = 60)

---

## ✂️ STEP 1: How many fragments?

Total data = **2980 bytes**

Each fragment can carry **480 bytes**

```
2980 ÷ 480 = 6.208
```

So:

* 6 full fragments
* 1 last smaller fragment

✅ **Total fragments = 7**

---

## ✂️ STEP 2: Data size of each fragment

| Fragment | Data size                        |
| -------- | -------------------------------- |
| 1–6      | 480 bytes each                   |
| 7 (last) | 2980 − (6 × 480) = **100 bytes** |

---

## 📦 STEP 3: Total Length of each fragment

```
Total Length = IP Header + Fragment Data
```

| Fragment | Data | Header | Total Length  |
| -------- | ---- | ------ | ------------- |
| 1–6      | 480  | 20     | **500 bytes** |
| 7        | 100  | 20     | **120 bytes** |

---

## 🚦 STEP 4: MF (More Fragment) bit

### Rule:

* **MF = 1** → more fragments coming
* **MF = 0** → last fragment

| Fragment | MF |
| -------- | -- |
| 1–6      | 1  |
| 7        | 0  |

---

## 📍 STEP 5: Fragment Offset calculation

### Rule:

```
Fragment Offset = (starting byte of data) ÷ 8
```

| Fragment | Data starts at (bytes) | Offset           |
| -------- | ---------------------- | ---------------- |
| 1        | 0                      | 0                |
| 2        | 480                    | 480 ÷ 8 = **60** |
| 3        | 960                    | **120**          |
| 4        | 1440                   | **180**          |
| 5        | 1920                   | **240**          |
| 6        | 2400                   | **300**          |
| 7        | 2880                   | **360**          |

---

## ✅ FINAL ANSWER (EXAM-READY TABLE)

| Fragment | Data (B) | Total Length (B) | MF | Fragment Offset |
| -------- | -------- | ---------------- | -- | --------------- |
| 1        | 480      | 500              | 1  | 0               |
| 2        | 480      | 500              | 1  | 60              |
| 3        | 480      | 500              | 1  | 120             |
| 4        | 480      | 500              | 1  | 180             |
| 5        | 480      | 500              | 1  | 240             |
| 6        | 480      | 500              | 1  | 300             |
| 7        | 100      | 120              | 0  | 360             |

---

## 🧠 ONE-LINE MEMORY FORMULA (VERY IMPORTANT)

> **Fragment Data = MTU − IP Header,
> Offset = (Bytes sent so far) ÷ 8,
> MF = 0 only for last fragment**
