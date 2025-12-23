# 📡 Medium Access Control (MAC) Protocols

**(Data Link Layer – Computer Networks)**

---

## 🔹 What is Medium Access Control?

In a network, **many devices share the same communication medium** (wire, cable, air).

📌 **Problem**:
If two devices transmit at the same time → **collision** → data loss.

👉 **MAC protocols decide:**

* **Who can transmit**
* **When they can transmit**
* **How collisions are handled or avoided**

---

## 🔹 Why MAC Protocols are needed?

* Shared medium (bus, wireless, etc.)
* Multiple nodes want to send data
* Prevent collisions
* Improve efficiency & fairness

---

# 🔹 Classification of MAC Protocols

MAC protocols are broadly divided into **3 categories**:

\[
\text{MAC Protocols} =
\begin{cases} 
\text{Channel Partitioning} -
\text{Random Access} -
\text{Controlled Access}
\end{cases}
\]

---

# 🟢 1. Channel Partitioning Protocols

👉 **Divide the channel into pieces** and give each node a fixed part.

### 🔸 Idea

* No collision
* Wasted bandwidth if node is idle

---

## ✅ (a) TDMA – Time Division Multiple Access

### 🔹 Concept

* Time is divided into **slots**
* Each node gets **one fixed time slot**

### 🔹 Example

| Time Slot | Node |
| --------- | ---- |
| T1        | A    |
| T2        | B    |
| T3        | C    |

If node B has no data → **slot wasted** ❌

### 🔹 Advantages

* No collision
* Simple

### 🔹 Disadvantages

* Inefficient for bursty traffic

---

## ✅ (b) FDMA – Frequency Division Multiple Access

### 🔹 Concept

* Channel bandwidth divided into **frequency bands**
* Each node gets a separate frequency

### 🔹 Example

* Radio channels
* Old telephone systems

### 🔹 Advantages

* No collision
* Continuous transmission

### 🔹 Disadvantages

* Wastage if node inactive

---

## ✅ (c) CDMA – Code Division Multiple Access

### 🔹 Concept

* All nodes transmit **at the same time**
* Each node uses a **unique code**
* Receiver extracts data using that code

### 🔹 Used in

* 3G mobile communication

### 🔹 Advantage

* High efficiency
* Secure

### 🔹 Disadvantage

* Complex hardware

---

# 🔴 2. Random Access Protocols

👉 Nodes transmit **whenever they want**
👉 Collisions are **allowed**, then handled

---

## ✅ (a) ALOHA

### 🔹 Pure ALOHA

* Send data anytime
* If collision → retransmit after random time

📉 **Efficiency ≈ 18%**

---

### 🔹 Slotted ALOHA

* Time divided into slots
* Transmission only at slot start

📈 **Efficiency ≈ 37%**

---

## ✅ (b) CSMA – Carrier Sense Multiple Access

### 🔹 Key Idea

> **“Listen before talk”**

---

### 🔸 1. CSMA/CD (Collision Detection)

Used in **Ethernet (wired)**

### Working:

1. Sense channel
2. Transmit if idle
3. If collision detected → stop + retry

### 🔹 Limitation

❌ Not suitable for wireless

---

### 🔸 2. CSMA/CA (Collision Avoidance)

Used in **Wi-Fi (wireless)**

### Why not CD in wireless?

* Sender can’t detect collision while sending

### Extra mechanisms:

* RTS (Request to Send)
* CTS (Clear to Send)
* ACK

---

## ✅ (c) Backoff Algorithm

After collision:

* Wait random time
* Retry transmission

Prevents repeated collisions

---

# 🔵 3. Controlled Access Protocols

👉 Nodes **take turns** to transmit

---

## ✅ (a) Polling

### 🔹 Concept

* Central controller polls each node

### 🔹 Example

```
Master → "A, send?"
Master → "B, send?"
```

### 🔹 Drawback

* Delay
* Single point of failure

---

## ✅ (b) Token Passing

### 🔹 Concept

* A token circulates
* Only token holder can transmit

### 🔹 Used in

* Token Ring
* FDDI

### 🔹 Advantage

* No collision

### 🔹 Disadvantage

* Token loss problem

---

# 🔹 Comparison Table (Very Important for Exams)

| Protocol Type | Collision | Efficiency       | Example    |
| ------------- | --------- | ---------------- | ---------- |
| TDMA          | No        | Low (idle slots) | GSM        |
| FDMA          | No        | Low              | Radio      |
| ALOHA         | Yes       | Very low         | Satellite  |
| CSMA/CD       | Yes       | High             | Ethernet   |
| CSMA/CA       | Avoided   | High             | Wi-Fi      |
| Polling       | No        | Medium           | Bluetooth  |
| Token Passing | No        | Medium           | Token Ring |

---

# 🔹 Quick Exam Memory Trick 🧠

* **Partition → No collision, wasted bandwidth**
* **Random → Collision allowed**
* **Controlled → Turn-by-turn access**

---

# 🔹 One-Line Definition (For Exams)

> **Medium Access Control protocols determine how multiple nodes share a common communication channel efficiently and fairly in the Data Link Layer.**
