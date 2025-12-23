# 🔹 What is Hamming Code?

**Hamming Code** is a technique used in **Computer Networks / Digital Communication** to:

* ✅ **Detect errors**
* ✅ **Correct single-bit errors**

It works by adding **extra bits** (called **parity bits**) to the original data.

---

## 🔹 Why do we need Hamming Code?

Suppose you send this data:

```
1011
```

During transmission, **1 bit may flip**:

```
1011  →  1001  ❌
```

Normal parity can **detect** an error but **cannot tell which bit is wrong**.

👉 **Hamming Code can tell exactly which bit is wrong and fix it.**

---

# 🔹 Key Idea (Very Important)

Hamming Code uses **parity bits placed at positions that are powers of 2**:

\[
2^0, 2^1, 2^2, 2^3, ...
\]

So parity bit positions are:

```
1, 2, 4, 8, 16, ...
```

---

# 🔹 Step 1: How many parity bits are needed?

Formula:

\[
2^r \ge m + r + 1
\]

Where:

* ( m ) = number of data bits
* ( r ) = number of parity bits

---

### Example

Data bits = **4**

Try ( r = 3 ):

\[
2^3 = 8 \ge 4 + 3 + 1 = 8
\]

✅ So we need **3 parity bits**

---

# 🔹 Step 2: Place data & parity bits

Let data bits be:

```
D = 1011
```

Positions:

| Position | 1  | 2  | 3  | 4  | 5  | 6  | 7  |
| -------- | -- | -- | -- | -- | -- | -- | -- |
| Bit type | P1 | P2 | D1 | P4 | D2 | D3 | D4 |
| Value    | ?  | ?  | 1  | ?  | 0  | 1  | 1  |

---

# 🔹 Step 3: Parity Bit Rules

Each parity bit checks **specific positions**.

### 🔸 P1 (position 1)

Checks positions where **binary position has 1 in LSB**:

```
1, 3, 5, 7
```

### 🔸 P2 (position 2)

Checks positions where **2nd bit is 1**:

```
2, 3, 6, 7
```

### 🔸 P4 (position 4)

Checks positions where **3rd bit is 1**:

```
4, 5, 6, 7
```

We use **Even Parity**.

---

# 🔹 Step 4: Calculate Parity Bits

### ✅ P1 checks: 3, 5, 7

```
1, 0, 1  → total = 2 (even)
So P1 = 0
```

### ✅ P2 checks: 3, 6, 7

```
1, 1, 1 → total = 3 (odd)
So P2 = 1
```

### ✅ P4 checks: 5, 6, 7

```
0, 1, 1 → total = 2 (even)
So P4 = 0
```

---

# 🔹 Final Hamming Code (Sent Data)

```
Position:  1 2 3 4 5 6 7
Bits:      0 1 1 0 0 1 1
```

### ✅ Transmitted Code:

```
0110011
```

---

# 🔹 Error Detection & Correction

Now suppose **one bit gets corrupted** during transmission.

### ❌ Received Code:

```
0110001
```

(Bit at position **6** flipped)

---

# 🔹 Step 5: Recalculate parity at receiver

### Check P1 → error? → ❌

### Check P2 → error? → ✅

### Check P4 → error? → ✅

Write error bits in reverse order:

```
P4 P2 P1
 1  1  0
```

### Binary → Decimal:

\[
110_2 = 6
\]

---

# 🔹 Step 6: Correct the Error

Error is at **position 6**
Flip the bit:

```
0 → 1
```

✔ Corrected successfully!

---

# 🔹 Summary (Very Easy Words)

| Feature          | Hamming Code             |
| ---------------- | ------------------------ |
| Extra bits used  | Parity bits              |
| Detect errors    | Yes                      |
| Correct errors   | **Single-bit only**      |
| Parity positions | Powers of 2              |
| Error position   | Found using binary value |

---

# 🔹 One-Line Memory Trick 🧠

> **“Parity bits sit at powers of 2 and their check results tell the wrong bit in binary.”**
