# ⭐ Topic: **Flow Control in Data Link Layer**

Flow control ensures:

> “Sender should not send data faster than the receiver can handle.”

To solve this, 3 protocols exist:

1. **Stop & Wait**
2. **Go-Back-N (GBN)**
3. **Selective Repeat (SR)**

The whiteboard compares these three.

---

# ⭐ Before Everything — Basic Terms

### **Frame**

A small packet of data.

### **Window**

Number of frames the sender/receiver can handle at a time.

### **TP**

Propagation Time
(How long a signal takes to travel through the wire.)

### **TT or Tt**

Transmission Time
(How long it takes to put bits on the wire.)

### **x**

\[
x = \frac{T_P}{T_t}
\]

This ratio tells how “slow or fast” the link is.

### **Utilization (η or U)**

Efficiency of the sender:

\[
η = \text{Actual Data Sending Time} ; / ; \text{Total Time}
\]

---

# -----------------------------------------

# 🟥 1) **STOP & WAIT**

# -----------------------------------------

### **Idea**

Sender sends **only 1 frame**, then **waits** for ACK.

### **Whiteboard Content Explained**

### ✔ "Only 1 frame transmit"

Sender sends ONE frame at a time.

### ✔ Sender Window = 1

Sender is allowed to send **only 1** frame.

### ✔ Receiver Window = 1

Receiver can accept **only 1** frame.

### ✔ Formula: Utilization

\[
η = \frac{1}{1 + 2x}
\]

Because sender sends for 1 frame time
and waits for **2 × propagation time** (forward + ACK return).

### ✔ Retransmission = 1

If a frame is lost, resend ONLY that frame.

### ✔ ASN (Available Sequence Numbers)

\[
ASN = W_S + W_R = 1 + 1 = 2
\]

Meaning Stop & Wait uses **2 sequence numbers** (0,1).

**Simple 5-year-old example:**

You throw a paper ball to your friend.
You wait until your friend shouts “OK!”.
Then you throw the next one.

---

# -----------------------------------------

# 🟧 2) **GO-BACK-N (GBN)**

# -----------------------------------------

### **Idea**

Sender sends **multiple frames continuously** using a “window”.

If one frame is lost → sender **restarts** sending from that frame.

### **Whiteboard Content Explained**

### ✔ "Multiple frames"

Sender is allowed to send many frames before waiting.

### ✔ K = number of bits for sequence number

Example:
K = 3 bits → numbers: 0 to 7 → total **8 sequence numbers**.

\[
2^3 = 8
\]

### ✔ Sender Window = (2^k - 1)

Example:
\[
2^3 - 1 = 7
\]

So sender can send **7 frames at a time**.

### ✔ Receiver Window = 1

GBN receiver accepts only the **next expected frame**.

### ✔ Utilization (η)

\[
η = \frac{(2^k - 1) \cdot 1}{1 + 2x}
\]

Multiplying by window size increases efficiency.

### ✔ Cumulative ACK

ACK number "5" means:

* Frames 1,2,3,4,5 received.

### ✔ Retransmission = (2^k - 1)

Worst case: sender resends the whole window.

### ⭐ Easy analogy:

Teacher says:
“Send me homework pages 1,2,3,4,5,6,7.”

If page 3 is missing,
the teacher asks you to resend **3,4,5,6,7** (go back to 3).

---

# -----------------------------------------

# 🟩 3) **SELECTIVE REPEAT (SR)**

# -----------------------------------------

### **Idea**

Sender sends many frames (like GBN),
BUT
receiver **stores out-of-order frames** and sender **retransmits only wrong frames**.

### **Whiteboard Content Explained**

### ✔ K = number of bits

Example: K = 3 → 0–7 → total 8 sequence numbers.

### ✔ Sender Window = (2^{k-1})

Example:
\[
2^{3-1} = 4
\]
So window size = **4**.

### ✔ Receiver Window = (2^{k-1})

Receiver can store 4 frames in memory.

### ✔ Allows "Out of order"

Receiver accepts frames even if 3 is missing but 4,5,6 arrive.

### ✔ Utilization:

\[
η = \frac{2^{k-1}}{1+2x}
\]

### ✔ ACK type:

* Cumulative ACK
* Independent ACK (individual acknowledgements)

### ✔ Retransmission = 1

Only the missing frame is resent.

### ⭐ Simple analogy:

Teacher says:
"Send me pages 1 to 4."

You send 1,2,3,4.

If page 2 is missing:
Teacher says: "Only resend page 2."
(But she already accepted pages 3 and 4.)

---

# ⭐ FINAL SUPER-SIMPLE SUMMARY

| Feature                        | Stop & Wait | Go-Back-N       | Selective Repeat |
| ------------------------------ | ----------- | --------------- | ---------------- |
| Frames sent                    | 1           | Many (7 if K=3) | Many (4 if K=3)  |
| Receiver accepts out-of-order? | ❌ No        | ❌ No            | ✅ Yes            |
| Retransmission                 | 1 frame     | All after error | Only wrong one   |
| Sender window                  | 1           | (2^k - 1)       | (2^{k-1})        |
| Receiver window                | 1           | 1               | (2^{k-1})        |
| Efficiency                     | Low         | Medium          | High             |
