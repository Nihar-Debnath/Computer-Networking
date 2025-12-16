# ⭐ What is Circuit Switching?

**Circuit Switching** is a communication method where
👉 a **dedicated physical path**
is created **between sender and receiver**
👉 **before** any data is sent.

This entire path stays reserved **only for them** until the communication ends.

---

# 🔥 SUPER SIMPLE REAL-LIFE EXAMPLE

### Think of a **phone call (landline)**.

* When you call someone, the telephone company creates a dedicated line.
* Only **you two** use that line.
* Nobody else can use it until the call ends.
* If the line is busy, you cannot call.

This is exactly how **circuit switching** works.

---

# ⭐ Key Points (Beginner Level)

### 1️⃣ **Dedicated path is created**

A full path from **A → B** is set up first.

### 2️⃣ **No one else can use that path**

It's like booking the entire road for yourself.

### 3️⃣ **Guaranteed bandwidth**

Since the path is yours, no congestion.

### 4️⃣ **Wastes resources**

Even if you are silent (not sending anything),
the path is still reserved — no one else can use it.

### 5️⃣ **Used in old telephone systems**

Traditional PSTN uses circuit switching.

---

# 🔎 How It Works (3 Steps)

Circuit switching happens in **three phases**:

## **1. Circuit Establishment**

A path is created between sender and receiver.

```
A ---- Switch ---- Switch ---- B
```

## **2. Data Transfer**

Data flows continuously, with guaranteed bandwidth.

## **3. Circuit Termination**

Path is released after communication ends.

---

# ⭐ Very Easy Diagram

```
[ A ] ---X---X---X--- [ B ]

X = Reserved path (no one else can use it)
```

---

# ⭐ Advantages

* ✔ Guaranteed bandwidth
* ✔ No delay once the circuit is created
* ✔ Reliable, continuous communication
* ✔ Good for voice calls

---

# ⭐ Disadvantages

* ❌ Wastes bandwidth if no one is speaking
* ❌ Call cannot start if no path is available
* ❌ Not good for data networks with bursty traffic (like internet)

---

# ⭐ Where Circuit Switching Is Used?

* Old telephone systems (landlines)
* ISDN networks
* Some optical fiber networks

Not used for normal internet data — the internet uses **Packet Switching**, not circuit switching.


---
---
---

# ⭐ Total Time in Circuit Switching

When using circuit switching, the **total time** to send data is:

\[
\text{Total Time}
= \text{Setup Time} +
\text{Transmission Time} +
\text{Propagation Time}
\]

---

# 🔥 Breakdown (Beginner Level)

### 1️⃣ **Setup Time**

Time required to create the dedicated path (circuit) between sender and receiver.

### 2️⃣ **Transmission Time**

Time taken to push all the data into the link.

\[
\text{Transmission Time} = \frac{\text{Message Size}}{\text{Bandwidth}}
\]

### 3️⃣ **Propagation Time**

Time for the signal to travel from sender to receiver.

\[
\text{Propagation Time} = \frac{\text{Distance}}{\text{Propagation Speed}}
\]

---

# ⭐ So the final total time:

\[
\boxed{
T_{\text{total}} = T_{\text{setup}} + \frac{M}{B} + \frac{D}{S}
}
\]

Where:

* (M) = message size
* (B) = bandwidth
* (D) = distance
* (S) = signal speed (usually close to (2 \times 10^8) m/s)

---

# ⭐ Example (Super Simple)

Suppose:

* Setup time = 3 seconds
* Message size = 2 MB
* Bandwidth = 1 Mbps
* Propagation = 0.02 seconds

\[
T_{\text{total}} = 3 + \frac{2}{1} + 0.02 = 5.02\text{ seconds}
\]
