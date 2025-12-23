![](./image/Screenshot%202025-12-19%20232849.png)

---

## 📘 Given

* **Data rate (R)** = 100 Mbps
  \[
  R = 100 \times 10^6 \text{ bits/sec}
  \]

* **Cable length (L)** = 1 km

* **No repeaters** (important!)

* **Minimum frame size** = 1250 bytes

Convert frame size to bits:
\[
1250 \times 8 = 10000 \text{ bits}
\]

---

## 🧠 Key CSMA/CD Rule (Very Important)

For **CSMA/CD**, to detect a collision:

> **Frame transmission time ≥ 2 × propagation delay**

\[
T_{tx} \ge 2 \times T_{prop}
\]

Why?

* Worst case collision happens when two farthest nodes transmit.
* Collision signal must travel **to the other end and back** before transmission ends.

---

## ✏️ Step 1: Calculate Transmission Time

\[
T_{tx} = \frac{\text{Frame size}}{\text{Data rate}}
\]

\[
T_{tx} = \frac{10000}{100 \times 10^6}
\]

\[
T_{tx} = 1 \times 10^{-4} \text{ sec}
\]

---

## ✏️ Step 2: Express Propagation Delay

Let signal speed = **v km/sec**

One-way propagation delay:
\[
T_{prop} = \frac{1}{v}
\]

Round-trip propagation delay:
\[
2T_{prop} = \frac{2}{v}
\]

---

## ✏️ Step 3: Apply CSMA/CD Condition

\[
T_{tx} \ge 2T_{prop}
\]

\[
1 \times 10^{-4} \ge \frac{2}{v}
\]

---

## ✏️ Step 4: Solve for Signal Speed

\[
v \ge \frac{2}{1 \times 10^{-4}}
\]

\[
v \ge 20000 \text{ km/sec}
\]

---

## ✅ Final Answer

✔ **Signal speed = 20000 km/sec**

---

## 🎯 Correct Option

**D) 20000**