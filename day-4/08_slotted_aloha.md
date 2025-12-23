# 📡 What is Slotted ALOHA?

**(MAC Layer Protocol | Data Link Layer)**

---

## 🔹 First in very easy words

👉 **Slotted ALOHA** is an improved version of **Pure ALOHA**.

> Devices are allowed to send data **only at fixed time slots**,
> **not anytime**.

This **reduces collisions**.

---

## 🔹 Why Slotted ALOHA was introduced?

### Problem in Pure ALOHA:

* Devices send data **anytime**
* Collisions happen very often
* Efficiency is very low (**18%**)

👉 **Solution:**
Divide time into **small equal slots**
➡ allow transmission **only at slot start**

---

## 🔹 How Slotted ALOHA works (Step by Step)

### Step 1: Time is divided into slots

* Each slot = time to send **one frame**

```
| Slot 1 | Slot 2 | Slot 3 | Slot 4 |
```

---

### Step 2: Devices wait for slot boundary

* A device can transmit **only at the beginning of a slot**
* If it misses the slot → waits for next one

---

### Step 3: Collision condition

* Collision happens **only if two devices start in the same slot**

✔ Fewer chances of collision than Pure ALOHA

---

### Step 4: ACK & Retransmission

* ACK received → success
* No ACK → collision
* Wait **random number of slots**
* Retransmit

---

## 🔹 Vulnerable Time in Slotted ALOHA

* Only **1 frame time**

\[
\text{Vulnerable Time} = T
\]

📌 (Pure ALOHA vulnerable time = (2T))

---

## 🔹 Efficiency of Slotted ALOHA

\[
\text{Maximum Efficiency} = 37%
\]

✔ Almost **double** of Pure ALOHA

---

## 🔹 Simple Example (Classroom)

### Pure ALOHA:

* Students shout answers **anytime**
* Noise & overlap ❌

### Slotted ALOHA:

* Students can answer **only when bell rings**
* Less overlap ✔

---

# 🔴 Difference: Pure ALOHA vs Slotted ALOHA

| Feature          | Pure ALOHA (PA) | Slotted ALOHA (SA) |
| ---------------- | --------------- | ------------------ |
| Time slots       | ❌ No            | ✔ Yes              |
| When to send     | Anytime         | Only at slot start |
| Collision chance | Very high       | Lower              |
| Vulnerable time  | (2T)            | (T)                |
| Max efficiency   | 18%             | 37%                |
| Synchronization  | Not needed      | Required           |
| Complexity       | Very simple     | Slightly complex   |

---

## 🔹 One-line Exam Definitions

**Pure ALOHA:**

> Devices transmit data at any time without checking the channel, causing high collisions.

**Slotted ALOHA:**

> Time is divided into slots and devices transmit only at slot boundaries to reduce collisions.

---

## 🔹 Memory Trick 🧠

> **Pure = Anytime**
> **Slotted = Slot time only**

---
---
---






# 📡 Efficiency Derivation of ALOHA Protocols

**(MAC Layer – Data Link Layer)**

---

## 🔹 First: What does “Efficiency” mean?

👉 **Efficiency (η)** =

> Fraction of time the channel is used to send **successful data frames**

\[
\text{Efficiency} = \frac{\text{Successful transmission time}}{\text{Total \time}}
]

---

## 🔹 Some Common Assumptions (Very Important)

For **both Pure & Slotted ALOHA**, we assume:

* Infinite number of nodes
* Each node sends frames randomly
* Frame transmission time = **T**
* Collisions destroy frames
* Retransmissions happen after random time

---

# 🔴 1. Efficiency of Pure ALOHA

---

## 🔹 Step 1: Vulnerable Time in Pure ALOHA

In **Pure ALOHA**, a frame can collide if another frame is sent:

* **T before it starts**
* **T after it starts**

So total **vulnerable time**:

\[
\text{Vulnerable Time} = 2T
\]

---

## 🔹 Step 2: Let G = offered load

* ( G ) = average number of frames transmitted per frame time
* Includes **new frames + retransmissions**

---

## 🔹 Step 3: Probability of NO collision

For a frame to be successful:

* **No other frame** should be transmitted during **2T**

Using Poisson distribution:

\[
P(\text{no collision}) = e^{-2G}
\]

---

## 🔹 Step 4: Throughput / Efficiency Formula

\[
\eta_{\text{Pure}} = G \cdot e^{-2G}
\]

---

## 🔹 Step 5: Maximum Efficiency

To find max efficiency, differentiate:

\[
\eta = G e^{-2G}
\]

Max value occurs at:

\[
G = \frac{1}{2}
\]

Substitute:

\[
\eta_{\max} = \frac{1}{2} e^{-1} = \frac{1}{2e}
\]

\[
\eta_{\max} \approx 0.18 = 18%
\]

---

## ✅ Final Result (Pure ALOHA)

\[
\boxed{\eta_{\max} = 18%}
\]

---

# 🟢 2. Efficiency of Slotted ALOHA

---

## 🔹 Step 1: Vulnerable Time in Slotted ALOHA

* Time divided into slots
* Transmission allowed **only at slot start**
* Collision only if **two frames choose same slot**

\[
\text{Vulnerable Time} = T
\]

---

## 🔹 Step 2: Probability of NO collision

Only need no other frame in **same slot**:

\[
P(\text{no collision}) = e^{-G}
\]

---

## 🔹 Step 3: Efficiency Formula

\[
\eta_{\text{Slotted}} = G \cdot e^{-G}
\]

---

## 🔹 Step 4: Maximum Efficiency

Max value occurs at:

\[
G = 1
\]

Substitute:

\[
\eta_{\max} = e^{-1}
\]

\[
\eta_{\max} \approx 0.37 = 37%
\]

---

## ✅ Final Result (Slotted ALOHA)

\[
\boxed{\eta_{\max} = 37%}
\]

---

# 🔵 Comparison Summary (Very Important for Exams)

| Feature             | Pure ALOHA  | Slotted ALOHA |
| ------------------- | ----------- | ------------- |
| Vulnerable time     | (2T)        | (T)           |
| Efficiency formula  | (G e^{-2G}) | (G e^{-G})    |
| G at max efficiency | (0.5)       | (1)           |
| Max efficiency      | **18%**     | **37%**       |
| Performance         | Poor        | Better        |

---

## 🔹 One-Line Memory Trick 🧠

> **Pure ALOHA wastes double time → half efficiency**
> **Slotted ALOHA halves collision → double efficiency**

---

## 🔹 One-Line Exam Answer 📝

* **Pure ALOHA efficiency:** ( \eta = G e^{-2G} ), max = **18%**
* **Slotted ALOHA efficiency:** ( \eta = G e^{-G} ), max = **37%**
