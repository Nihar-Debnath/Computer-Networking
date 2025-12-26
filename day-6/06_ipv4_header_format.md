## First tell me this 👇

When data goes from **your computer → another computer**, it is **NOT sent as one big thing**.

It is sent like this:

> **Data + some information attached to it**

That **attached information** is called the **IPv4 HEADER**.

Think like this 👇
📦 **Courier box**

* **Header** → address, sender, instructions
* **Data** → item inside the box

---

## So what is IPv4 Header?

👉 It is a **small control part** added **before data**
👉 Routers read **ONLY the header**, not your data

---

## IPv4 Header has FIXED QUESTIONS it answers

Every IPv4 header answers these questions 👇

---

## 1️⃣ Which IP version is this?

**Field:** Version
**Answer:** IPv4 → value is **4**

Router sees **4** → “Okay, IPv4 packet”

---

## 2️⃣ How big is the header?

**Field:** IHL

Why needed?
Because header can be **small or big** (options may exist)

* Minimum header = **20 bytes**
* IHL tells exact header size

---

## 3️⃣ Is this important data or normal data?

**Field:** DSCP / ToS

Used to decide **priority**

* Video call → high priority
* Email → low priority

---

## 4️⃣ How big is the whole packet?

**Field:** Total Length

Includes:

* Header
* Data

So receiver knows:

> “Packet ends here”

---

## 5️⃣ What if packet breaks into pieces?

Large packet may be **broken into fragments**

To handle this, IPv4 uses **3 fields together**:

---

### a) Identification

Same number for **all fragments** of one packet

👉 Like **roll number** for pieces

---

### b) Flags

Controls fragmentation

* **DF** = Don’t break packet
* **MF** = More pieces coming

---

### c) Fragment Offset

Tells:

> “This piece belongs at position X”

So receiver can **rebuild original packet**

---

## 6️⃣ How long can packet stay alive?

**Field:** TTL (Time To Live)

* Each router reduces TTL by **1**
* If TTL becomes **0** → packet destroyed

Why?
👉 To stop **infinite looping**

---

## 7️⃣ Which protocol is inside the data?

**Field:** Protocol

Tells OS what to do next

Examples:

* **6** → TCP
* **17** → UDP
* **1** → ICMP

---

## 8️⃣ Is header damaged?

**Field:** Header Checksum

* Checks **header only**
* If error → packet dropped

---

## 9️⃣ Who sent the packet?

**Field:** Source IP Address

Example:

```
192.168.1.5
```

---

## 🔟 Who should receive the packet?

**Field:** Destination IP Address

Example:

```
8.8.8.8
```

Routers use this to forward packet.

---

## 1️⃣1️⃣ Extra instructions (optional)

**Field:** Options

Rarely used
Makes header bigger

---

## 1️⃣2️⃣ Padding

Just fills empty space
So header size becomes **proper**

---

## 🧠 ONE-SENTENCE SUMMARY (VERY IMPORTANT)

> **IPv4 header is like an address slip attached to data that tells routers where to send it, how long it can live, and how to rebuild it if broken.**

---
---
---
---
---
---




![](./images/IPv4-Datagram-Header.jpg)


## 🔹 First thing to understand (VERY IMPORTANT)

* **Each horizontal row = 32 bits = 4 bytes**
* IPv4 header minimum = **5 rows = 20 bytes**
* Maximum = **15 rows = 60 bytes**

That’s why on the **right side** it shows:

* **32 bits = 4 bytes**
* **Min Header = 20B**
* **Max Header = 60B**

---

## 🟩 ROW 1 (Top Row)

### **Version (4 bits)**

👉 Tells **which IP version**

* Value = **4** → IPv4

---

### **HLEN / IHL (4 bits)**

👉 Header Length

* Says **how many 32-bit rows** header has
* Minimum value = **5** → `5 × 4 = 20 bytes`

---

### **Type of Service (8 bits)**

👉 Priority of packet

* High priority → video, voice
* Low priority → email, normal data

---

### **Total Length (16 bits)**

👉 **Entire packet size**

Includes:

* Header
* Data

Range:

* **20 bytes to 65535 bytes**

---

## 🟩 ROW 2

### **Identification (16 bits)**

👉 Used when packet is **broken into fragments**

* All fragments of **same packet** have **same ID**

---

### **Flags (3 bits)**

Shown in diagram as:

* **Res (1 bit)** → always 0
* **DF (Don’t Fragment)**

  * 1 → do NOT break packet
* **MF (More Fragment)**

  * 1 → more fragments coming

---

### **Fragment Offset (13 bits)**

👉 Tells **position of this fragment**

* Helps receiver **reassemble packet**
* Measured in **8-byte units**

---

## 🟩 ROW 3

### **Time To Live (8 bits)**

👉 Packet life

* Each router **reduces TTL by 1**
* TTL = 0 → packet dropped

Prevents **infinite looping**

---

### **Protocol (8 bits)**

👉 What’s inside the data?

Examples:

* **6 → TCP**
* **17 → UDP**
* **1 → ICMP**

---

### **Header Checksum (16 bits)**

👉 Error checking **for header only**

* Recalculated at every router
* If wrong → packet dropped

---

## 🟩 ROW 4

### **Source IP Address (32 bits)**

👉 Sender’s IP address

Example:

```
192.168.1.10
```

---

## 🟩 ROW 5

### **Destination IP Address (32 bits)**

👉 Receiver’s IP address

Routers use this to **forward packet**

---

## 🟩 OPTIONAL ROWS

### **Options (0 to 40 bytes)**

👉 Extra features (rarely used)

Examples:

* Security
* Route recording

If options exist:

* Header size increases
* HLEN value increases

---

### **Padding**

👉 Added to make header size **multiple of 32 bits**

---

## 🟦 DATA SECTION (Bottom)

### **DATA**

👉 Actual message being sent

* Size = **20 bytes to 65536 bytes**
* Routers **do NOT read data**
* Only end device reads it

---

## 🧠 ONE-LINE DIAGRAM SUMMARY (EXAM GOLD)

> **The IPv4 header is arranged in 32-bit rows, starting with version and size, handling fragmentation in the middle, routing and protocol info next, and ending with source & destination IP addresses.**


---
---
---
---
---



## 🟩 FIRST ROW OF IPv4 HEADER (Real-World Explanation)

First row has **4 fields**:

```
| Version | HLEN | Type of Service | Total Length |
```

Think of this row as the **“front label of a courier box”** 📦

---

## 1️⃣ Version (4 bits) – *Which rulebook is used?*

### Real-world analogy 🛣️

Imagine roads have **different driving rules**:

* India → left side
* USA → right side

Before driving, you must know **which country’s rules apply**.

### In IPv4:

* **Version = 4** → use IPv4 rules
* **Version = 6** → use IPv6 rules

📌 Router reads this FIRST and decides:

> “Which rulebook should I follow?”

---

## 2️⃣ HLEN / IHL (4 bits) – *How big is the instruction label?*

### Real-world analogy 📄

Courier box has:

* **Small label** → just address
* **Big label** → address + special instructions

Before reading data, the worker must know:

> “Where does the label end and the box content start?”

### In IPv4:

* HLEN tells **header size**
* Value = number of **4-byte blocks**

Example:

* HLEN = 5 → `5 × 4 = 20 bytes` (minimum header)
* HLEN = 6 → `24 bytes` (extra options)

📌 Without this, receiver wouldn’t know **where data begins**

---

## 3️⃣ Type of Service (ToS) – *How urgent is this packet?*

### Real-world analogy 🚑

On roads:

* Ambulance 🚑 → highest priority
* Bus → medium
* Bicycle → lowest

Traffic police decide **who moves first**.

### In IPv4:

ToS tells routers:

* High priority → voice call, video
* Low priority → email, download

📌 Helps routers give **better service to important traffic**

---

## 4️⃣ Total Length (16 bits) – *How big is the whole box?*

### Real-world analogy 📦

Courier worker asks:

> “How big is this box including label?”

So they know:

* Where this box ends
* Where the next box starts

### In IPv4:

Total Length includes:

* Header
* Data

Range:

* Minimum → 20 bytes
* Maximum → 65,535 bytes

📌 Receiver uses this to know **packet boundary**

---

## 🧠 ONE-LINE REAL-WORLD SUMMARY (EXAM READY)

> **The first row of the IPv4 header acts like a courier label telling the router which rules to use, how big the label is, how urgent the packet is, and how large the entire packet is.**
