# **Stop and Wait ARQ Protocol | Data Link Layer**

**Stop-and-Wait ARQ** (Automatic Repeat reQuest) is the simplest error-control protocol used in the **Data Link Layer** and **Transport Layer**.
It ensures **reliable data transmission** by sending **one frame at a time** and waiting for an acknowledgment (ACK) before sending the next frame.

---

## **How it Works (Step-by-Step)**

1. **Sender sends one frame** to the receiver.
2. **Sender stops and waits** until it receives an **ACK** from receiver.
3. If the receiver gets the frame correctly → it sends **ACK**.
4. If the frame is **lost** or **damaged**, the sender **waits until timeout**.
5. After timeout → the sender **retransmits the same frame**.
6. This process continues until the receiver acknowledges successfully.

---

## **Key Features**

### ✔ **Reliability**

Any lost/damaged frame is retransmitted.

### ✔ **Uses sequence numbers**

Since frames may get duplicated due to retransmissions, frames are labeled with a **1-bit sequence number**:

* 0
* 1

This helps the receiver identify:

* **New frame**
* **Duplicate frame**

### ✔ **Simple but Slow**

Because the sender sends only **one frame at a time**, the link is idle most of the time → **low efficiency**.

---

## **Flow Diagram (Simple)**

```
Sender                     Receiver
  | -------- Frame 0 ------> |
  | <--------- ACK 0 ------- |
  | -------- Frame 1 ------> |
  | <--------- ACK 1 ------- |
```

If ACK does not arrive:

```
Sender waits → Timeout → Resend Frame
```

---

## **Types of Errors Handled**

* Lost data frame
* Lost ACK
* Damaged frame
* Damaged ACK

---

## **Advantages**

* Very simple to implement
* Works well for small data transfer or slow links

---

## **Disadvantages**

* **Very inefficient** on fast networks or long-distance communication
* Only one frame in transit → bandwidth is wasted

---

## **Real-Life Example**

Imagine sending a message to a friend and waiting for them to reply “OK” before sending the next message.
If they **don’t reply**, you send the same message again.

---

## **Summary**

* Stop-and-Wait ARQ is a **reliable error-control protocol**.
* Sends **one frame at a time** and waits for **ACK**.
* Uses **timeouts and retransmission**.
* Very **simple** but **inefficient** for high-speed networks.


---
---
---

![](./images/Stop-and-Wait-ARQ-7.png)


# ✅ **Explanation of the Diagram (Step by Step)**

We have two devices:

* **A = Sender**
* **B = Receiver**

Time flows **downwards**.

Only **one frame is sent at a time**, and A waits for ACK before sending the next frame.

---

# **🔷 PART 1 — Normal Transmission**

### **1️⃣ A → Frame 0 → B**

A sends **Frame 0**.

### **2️⃣ B → Ack 1 → A**

Why ACK 1?
Because Stop-and-Wait uses **next expected frame number** as ACK.

* B has received `Frame 0`
* Next frame expected is `Frame 1`
* So B sends **Ack 1**

### **3️⃣ A → Frame 1 → B**

A sends next frame: **Frame 1**

### **4️⃣ B → Ack 0 → A**

Now B expects next frame to be **0**, so it sends **Ack 0**.

Everything is normal so far.

---

# **🔷 PART 2 — Frame Lost (First Red X)**

### **5️⃣ A → Frame 0 → (lost)**

A tries to send **Frame 0**, but it gets **lost** (shown by red X).

### **6️⃣ A waits… no ACK arrives → Timeout**

Sender waits for ACK 1, but nothing comes.
So **timeout occurs**.

### **7️⃣ A retransmits → Frame 0**

A resends **Frame 0**.

### **8️⃣ B receives Frame 0 → sends Ack 1**

Receiver gets Frame 0 again (first time, since earlier was lost).
So B sends **Ack 1**.

---

# **🔷 PART 3 — ACK Lost (Second Red X)**

### **9️⃣ A → Frame 1 → B**

A sends **Frame 1**.

### **🔟 B receives Frame 1 → sends Ack 0**

Receiver expects Frame 0 next → so it sends **Ack 0**.

### **1️⃣1️⃣ Ack 0 → (lost)**

The ACK gets **lost** (second red X).

### **1️⃣2️⃣ A waits… no ACK → Timeout**

A waits for Ack 0, but doesn’t get it → **timeout**.

### **1️⃣3️⃣ A retransmits → Frame 1**

A thinks maybe the receiver never got Frame 1.
So it **resends Frame 1**.

### **1️⃣4️⃣ B receives duplicate Frame 1**

But B had **already received Frame 1 earlier**.

Because Stop-and-Wait uses **sequence numbers (0 and 1)**:

* B sees **Frame 1** again
* Realizes it's a **duplicate**
* **B discards the duplicate frame**

### **1️⃣5️⃣ B sends Ack 0 again**

Receiver still expects Frame 0, so it replies with **Ack 0**.

A receives the ACK and transmission continues normally.

---

# ✅ **WHY THIS WORKS**

Stop-and-Wait uses:

* **Sequence numbers** (0,1)
* **ACK numbers** (which indicate the *next expected frame*)
* **Timeout + Retransmission**

This ensures:

* Lost frames are resent
* Lost ACKs are tolerated
* Duplicate frames are discarded safely

---

# 🎯 **Final Summary of the Diagram**

| Event               | What Happened        | Why                               | Result                          |
| ------------------- | -------------------- | --------------------------------- | ------------------------------- |
| **Frame lost**      | Frame 0 lost         | Receiver never got it             | Sender times out → retransmits  |
| **ACK lost**        | Ack 0 lost           | Sender thinks frame never arrived | Sender retransmits Frame 1      |
| **Duplicate frame** | B gets Frame 1 again | ACK was lost earlier              | B discards it + sends ACK again |

This is exactly how **Stop-and-Wait ARQ ensures reliable communication**.
