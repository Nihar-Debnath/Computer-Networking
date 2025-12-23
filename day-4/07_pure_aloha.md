# 📡 What is Pure ALOHA?

**(MAC Layer Protocol | Data Link Layer)**

---

## 🔹 First, in the easiest words

👉 **Pure ALOHA** is a **Medium Access Control (MAC) protocol** where:

> **Any device can send data at any time**
> **without checking whether the channel is free or busy**

There are **no rules about timing**.

---

## 🔹 Why do we need Pure ALOHA?

In a network:

* Many computers share **one common channel**
* All want to send data

📌 Problem:
If two computers send data **at the same time**, their data **collides** and is lost.

Pure ALOHA was created as a **very simple solution** to allow communication.

---

## 🔹 How Pure ALOHA works (Step by Step)

### Step 1: Send immediately

* A device sends data **whenever it wants**
* It does **not wait**
* It does **not listen** to the channel

---

### Step 2: Collision may happen

* If two devices send at the same time
  ➡ **Collision occurs**

```
Device A  ---->
Device B  ---->   ❌ Collision
```

---

### Step 3: Wait for acknowledgment (ACK)

* Receiver sends **ACK** if data is received correctly
* If sender **does not get ACK**, it assumes:

  > “My data was destroyed due to collision”

---

### Step 4: Retransmit after random time

* Sender waits for a **random time**
* Then sends the data again

This random waiting reduces repeated collisions.

---

## 🔹 Important Point: Vulnerable Time

In Pure ALOHA:

* Data can collide **before or after** it is sent
* Total vulnerable time = **2 × frame time**

\[
\text{Vulnerable Time} = 2T
\]

Where:

* ( T ) = time to send one frame

---

## 🔹 Efficiency of Pure ALOHA

❌ Very low efficiency

\[
\text{Maximum Efficiency} = 18%
\]

This means:

* Only **18%** of the channel is used successfully
* **82%** is wasted due to collisions

---

## 🔹 Example (Very Easy)

Imagine:

* Students shouting answers in a classroom
* Anyone can shout **anytime**

Result:

* Voices overlap ❌
* Teacher cannot understand

That is **Pure ALOHA**.

---

## 🔹 Advantages of Pure ALOHA

✔ Very simple
✔ Easy to implement
✔ Useful for small or satellite networks

---

## 🔹 Disadvantages of Pure ALOHA

❌ Too many collisions
❌ Very low efficiency
❌ Not suitable for heavy traffic

---

## 🔹 Where is Pure ALOHA used?

* Early satellite communication
* Historical importance (base of other protocols)

---

## 🔹 One-line exam definition 📝

> **Pure ALOHA is a random access MAC protocol in which devices transmit data whenever they want without checking the channel, and collisions are handled by retransmission.**

---

## 🔹 Memory Trick 🧠

> **Pure ALOHA = Send anytime + No checking + Many collisions**
