# 🚀 **Cyclic Redundancy Check (CRC) — Simple Explanation**

**CRC is an error detection method** used in computer networks.
It checks whether data got corrupted during transmission.

Think of CRC like a **math checksum** using **binary division**.

---

# ⭐ **How CRC Works (Very Simple)**

1. **Sender Side**

   * Take the data bits.
   * Divide them by a fixed binary number called **generator (divisor)**.
   * Division is done using **XOR** (not normal division).
   * The **remainder** = CRC bits.
   * Sender sends:

     ```
     data + CRC
     ```

2. **Receiver Side**

   * Receiver again divides **(data + CRC)** by the same generator.
   * If remainder = **0 → no error**
   * If remainder ≠ **0 → error detected**

CRC only **detects** errors, it does not correct them.

---

# 🎯 **Small Example (Very Clear)**

### Data = `1001`

### Generator = `1101` (4 bits → degree = 3)

Step 1: Append 3 zeros to data:

```
1001 000
```

Step 2: Divide `1001000` by `1101` using XOR.

I’ll show the division cleanly:

```
1101 ) 1001000
        ↓ XOR
        0100
        → bring next bit
        01000
        ↓ XOR
        00101
        → bring next bit
        001010
        ↓ XOR
        000111   ← remainder
```

### ✔ Remainder (CRC) = **111**

So sender transmits:

```
1001 111
```

---

# 🧠 Receiver Side

Receiver gets:

```
1001111
```

Divides by `1101`.

If result remainder = `000` → **NO ERROR**
If remainder ≠ 0 → **ERROR DETECTED**

---

# 🔥 **In One Line**

CRC = “Divide using XOR → send remainder → receiver checks remainder = 0 or not.”

---
---
---

# ✅ **What is Cyclic Redundancy Check (CRC)?**

**Cyclic Redundancy Check (CRC)** is an **error-detecting** technique used in networks and data communication.
It uses **binary division** to detect if the data received has any error.

CRC **does not correct errors** (unless combined with other techniques).
Its main job is **to detect** accidental changes in raw data.

---

# 🔥 **Why is CRC used?**

CRC is popular because:

* Very high error detection accuracy
* Easy to implement with hardware shift registers
* Detects:

  * Single-bit errors
  * Double-bit errors
  * Burst errors
  * Odd number of bit errors

---

# 🧠 **Basic Concepts Behind CRC**

CRC uses:

* **Data bits** → the message you want to send
* **Generator Polynomial (Divisor)** → a fixed binary number
* **CRC Code (Remainder)** → added at the end of data
* Receiver divides again → If remainder = **0**, no error

### If remainder ≠ 0 → **Error detected**

---

# ⭐ Steps in CRC Error Detection

### 1️⃣ Choose **Data** and **Generator Polynomial**

Example:

```
Data: 11010011101100  
Generator (Divisor): 1011
```

Let:

* Data = ( D )
* Generator = ( G )
* Degree of generator (number of bits − 1) = 4 − 1 = 3

We append **3 zeros** (because degree = 3) to data:

```
Appended Data = 11010011101100 000
```

---

### 2️⃣ Perform **binary division** (XOR based)

We divide:

```
11010011101100 000
by
1011
```

> XOR rules:
>
> * 1 ⊕ 1 = 0
> * 0 ⊕ 0 = 0
> * 1 ⊕ 0 = 1

We take the first 4 bits because the divisor has 4 bits:

```
1101 ÷ 1011 → XOR → 0110
```

Bring next bit down → continue division.

---

# 🔍 **FULL LONG-DIVISION (Easy Format)**

(Appended data)

```
11010011101100000
1011 )11010011101100000
      ↓ XOR
      0111
        ↓ bring next bit
        01100
        1011 → XOR → 00111
           ↓ bring next bit
           001111
           1011 → XOR → 000100
              ↓ bring next bit
              0001001
              1011 → XOR → 0000110
                ↓ bring next bit
                00001100
                1011 → XOR → 00000111  (remainder)
```

### ✔ Remainder (CRC bits) = **111**

---

# 3️⃣ Append Remainder to Original Data

```
Transmitted frame = Original Data + CRC
= 11010011101100 111
```

This is sent to receiver.

---

# 4️⃣ Receiver Side

Receiver receives:

```
11010011101100111
```

Receiver divides by same generator (1011):

### If remainder = **0** → no error

### If remainder ≠ **0** → error detected

---

# 🎯 **Example of Error Detection**

Suppose 1 bit flips during transmission:

Sent:

```
11010011101100111
```

Received (error bit in red):

```
1101**1**0011101100111
```

Divide again with 1011:

**Remainder ≠ 000 → ERROR detected**

---

# ✨ Final Summary

| Concept     | Explanation                                       |
| ----------- | ------------------------------------------------- |
| CRC         | Error detection method using polynomial division  |
| Uses        | Data → appended with zeros → divided by generator |
| Output      | Remainder = CRC code                              |
| At receiver | If dividing received bits gives 0 → no error      |
| Detects     | Single, double, burst errors                      |

---

# 🔥 **Short Exam Answer (You can copy-paste)**

**Cyclic Redundancy Check (CRC)** is an error-detecting method used in computer networks. The sender divides the data by a fixed binary number called the **generator polynomial** using XOR-based binary division. The **remainder** of this division is called the **CRC code** and is appended to the data before transmission.
At the receiver side, the data along with CRC is divided by the same generator; **if the remainder is zero, the data is error-free**, otherwise an error is detected.

**Example:**
Data = 11010011101100
Generator = 1011
Appended zeros (degree 3) → 11010011101100000
After division, remainder = **111**
Transmitted frame = **11010011101100111**
If receiver gets a non-zero remainder, an error is detected.
