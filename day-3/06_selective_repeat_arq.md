# **Selective Repeat ARQ (Automatic Repeat Request) | Data Link Layer**

**Selective Repeat ARQ** is an error-control protocol that improves efficiency by **retransmitting only the frames that were lost or damaged**, instead of going back and resending everything like Go-Back-N.

---

# ✅ **Key Features**

### ✔ 1. **Sender window and receiver window are both large**

Unlike Go-Back-N (receiver window = 1), Selective Repeat allows both sides to have:

[
\text{Window size} \le \frac{2^m}{2}
]

### ✔ 2. **Out-of-order frames are ACCEPTED and stored**

Receiver **buffers** frames that arrive out of order.

### ✔ 3. **Individual ACKs**

Each frame has its own ACK.
If frame 2 is lost, only frame 2 is retransmitted.

### ✔ 4. **Highest efficiency among ARQ protocols**

---

# ⭐ How Selective Repeat Works (Step-by-Step)

Assume:

* **Window size = 4**
* Frames sent: 0, 1, 2, 3, 4, 5, 6…

---

## **STEP 1 — Sender sends multiple frames**

Sender window:

```
[0, 1, 2, 3]
```

Sender sends:

```
0 → OK  
1 → OK  
2 → (lost)  
3 → OK
```

---

## **STEP 2 — Receiver behavior**

Receiver EXPECTS frame 0 first.

### It receives:

* Frame 0 ✔ (accepted)
* Frame 1 ✔ (accepted)
* Frame 3 ✔ (accepted but OUT-OF-ORDER → buffer it)
* Frame 2 ✘ lost

Receiver has:

```
✔ 0, 1  
✔ 3 → buffered  
✘ 2 → missing
```

Receiver sends ACKs only for what it receives:

```
ACK 0  
ACK 1  
ACK 3
```

---

## **STEP 3 — Sender sees missing ACK**

Sender notices:

* ACK 2 NEVER arrived
* But ACK 0, ACK 1, and ACK 3 arrived

Therefore, only **Frame 2 is missing**.

---

## **STEP 4 — Sender retransmits ONLY Frame 2**

Sender sends:

```
2 → Receiver
```

Receiver accepts 2 → now it has:

```
0, 1, 2, 3
```

Receiver now delivers them to upper layer in correct order.

---

## **STEP 5 — Window slides forward**

After receiving 0,1,2,3 the window moves:

Sender window becomes:

```
[4, 5, 6, 7]
```

Sender continues transmitting normally.

---

# ⭐ Key Difference From Go-Back-N

| Feature         | Go-Back-N ARQ                  | Selective Repeat ARQ          |
| --------------- | ------------------------------ | ----------------------------- |
| Frame lost      | Resend **lost + all after it** | Resend **only that frame**    |
| Receiver buffer | ❌ No buffering                 | ✔ Buffers out-of-order frames |
| Efficiency      | Medium                         | Very high                     |
| Receiver window | Size = 1                       | Same size as sender window    |
| Problem         | Wastes bandwidth               | More memory needed            |

---

# ✨ Real-Life Example of Selective Repeat

### Example: Video streaming

When downloading a video:

* If chunk #12 is lost
* But chunks #13, #14, #15 arrive fine

The system **keeps 13–15 in buffer**
and only re-downloads chunk **12**.

---

# 🎯 Exam-Ready Short Definition

**Selective Repeat ARQ** is an error-control protocol of the data link layer where the sender retransmits **only the specific frames that are lost or damaged**, while the receiver **buffers out-of-order arriving frames** and acknowledges each frame individually. This increases efficiency compared to Go-Back-N.


---
---
---

![](./images/Sliding-Window-Protocol.jpg)

# ⭐ **Selective Repeat ARQ – Diagram Explanation**

This diagram represents:

* Sender window
* Receiver window
* Frame loss
* Individual retransmission (only lost frame)

Window size looks like **4** (frames 0,1,2,3).

---

# ✅ **STEP 1 — Sender sends Frame 0**

Sender window:

```
[0 1 2 3]
 S
```

Sender transmits:

```
Frame 0 → Receiver
```

Receiver accepts **Frame 0** and stores it in correct order.

Receiver window also moves to expect next frame.

---

# ✅ **STEP 2 — Sender sends Frame 1**

Sender sends:

```
Frame 1 → Receiver
```

Receiver accepts **Frame 1**.
Receiver now has:

```
0, 1
```

It sends back **ACK 2** meaning:

> “I have received 0 and 1. Next I expect Frame 2.”

---

# ⭐ **Important:**

In Selective Repeat, ACK numbers mean **next expected frame**.

---

# ❌ **STEP 3 — Frame 2 is LOST in the network**

Sender sends:

```
Frame 2 → (lost)
```

Receiver does NOT receive Frame 2.

---

# ❗ **STEP 4 — Sender sends Frame 3**

Even though Frame 2 was lost, sender still sends frame 3 because in Selective Repeat:

* Sender does **not** stop sending next frames.
* Sender only tracks frames using a timer.

So:

```
Frame 3 → Receiver
```

---

# ❌ **STEP 5 — Receiver gets Frame 3 OUT-OF-ORDER**

Receiver expects:

```
Expected frame = 2
```

But Frame 3 arrives.

### Selective Repeat behavior:

✔ It **accepts** Frame 3
✔ It **buffers** it
❗ Receiver sees frame 2 is missing

So it sends:

```
NAK 2 (Negative Acknowledge for frame 2)
```

NAK 2 means:

> “I didn’t get Frame 2 — please resend it.”

This is shown in diagram as **NAK 2** going back to Sender.

---

# ⏳ **STEP 6 — Sender receives NAK 2**

Sender now knows:

* Frame 2 is missing
* Frame 3 was received earlier
* Only Frame 2 must be retransmitted

So Sender retransmits ONLY:

```
Resent → Frame 2
```

This is the essential benefit of Selective Repeat:

✔ Only the lost frame is resent
✔ Not the whole window (unlike Go-Back-N)

---

# 👍 **STEP 7 — Receiver accepts retransmitted Frame 2**

Receiver gets Frame 2:

* It already has buffered Frame 3
* Now it places Frame 2 in correct place

Receiver buffer becomes:

```
0, 1, 2, 3   ✔ (all in order)
```

Receiver window slides forward and delivers frames to upper layer.

---

# 🎯 Summary of What the Diagram Shows

| Step | Event                                        | Explanation                |
| ---- | -------------------------------------------- | -------------------------- |
| 1    | Frame 0 sent                                 | Accepted                   |
| 2    | Frame 1 sent                                 | Accepted                   |
| 3    | ACK 2 sent                                   | Receiver expects Frame 2   |
| 4    | Frame 2 lost                                 | main issue                 |
| 5    | Frame 3 received                             | Out-of-order → buffered    |
| 6    | Receiver sends NAK 2                         | “Missing frame 2”          |
| 7    | Sender retransmits only Frame 2              | Selective repeat advantage |
| 8    | Receiver accepts frame 2 and arranges buffer | Frame order restored       |

---

# ⭐ Key Concept Shown in Diagram

✔ Selective Repeat **accepts out-of-order frames**
✔ Receiver **buffers** Frame 3
✔ Receiver **does not discard** out-of-order frames
✔ Receiver sends **NAK for missing frame**
✔ Sender **retransmits only Frame 2**
✔ High efficiency
✔ No need to retransmit frames 3 again (saved bandwidth)