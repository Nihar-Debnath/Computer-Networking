![](./images/IPv4-Datagram-Header.jpg)


# 🟩 3️⃣ THIRD ROW OF IPv4 HEADER

From the diagram, **3rd row** is:

```
| Time To Live (8 bits) | Protocol (8 bits) | Header Checksum (16 bits) |
```

Think of this row as **“how to safely deliver and hand over the parcel”**.

---

## 1️⃣ Time To Live (TTL) – *How long can this packet travel?*

### 🌍 Real-world analogy 🚌

Imagine you give a **bus pass** with:

* **10 stops allowed**

At every stop:

* 1 stop is crossed out

If stops = 0 → passenger must get down.

### In IPv4:

* TTL = number of routers packet can pass
* Each router **decreases TTL by 1**
* TTL = 0 → packet **discarded**

📌 Why needed?

> To stop packets from **circling forever** if routing is wrong.

---

## 2️⃣ Protocol – *Who should receive the data inside?*

### 🌍 Real-world analogy 🏢

Courier reaches a **big company building**.
Now question is:

> “Which department should get this package?”

* HR
* Finance
* IT

### In IPv4:

Protocol field tells:

* **Which transport protocol** should receive the data

Examples:

| Number | Meaning |
| ------ | ------- |
| 6      | TCP     |
| 17     | UDP     |
| 1      | ICMP    |

📌 Without this, OS wouldn’t know **how to process data**.

---

## 3️⃣ Header Checksum – *Is the instruction label damaged?*

### 🌍 Real-world analogy 🔍

Courier checks:

> “Is the address label readable or damaged?”

If damaged:

* Parcel is rejected

### In IPv4:

* Checksum checks **only header**
* Recalculated at **every router**
* If checksum fails → packet dropped

📌 Data is NOT checked here (transport layer does that).

---

# 🟩 4️⃣ FOURTH ROW OF IPv4 HEADER

```
| Source IP Address (32 bits) |
```

---

## Source IP Address – *Who sent this packet?*

### 🌍 Real-world analogy 🏠

Every courier parcel has:

* **Sender address**

So receiver knows:

* Who sent it
* Where to reply

### In IPv4:

* Source IP = sender’s IP address
* Example:

```
192.168.1.10
```

📌 Needed for:

* Replies
* Error messages (ICMP)
* Logging

---

# 🟩 5️⃣ FIFTH ROW OF IPv4 HEADER

```
| Destination IP Address (32 bits) |
```

---

## Destination IP Address – *Who should receive this packet?*

### 🌍 Real-world analogy 📍

Courier parcel has:

* **Delivery address**

Every courier hub checks this to forward parcel.

### In IPv4:

* Destination IP = receiver’s IP
* Routers use this field to **forward packet**

Example:

```
8.8.8.8
```

📌 This is the **MOST IMPORTANT routing field**

---

# 🧠 HOW THESE 3 ROWS WORK TOGETHER (BIG PICTURE)

| Row | Purpose                                                |
| --- | ------------------------------------------------------ |
| 3rd | Control packet life, protocol handover, error checking |
| 4th | Identify sender                                        |
| 5th | Decide where to send                                   |

---

## 🧠 ONE-LINE EXAM SUMMARY (MUST REMEMBER)

> **The 3rd row controls packet lifetime, protocol delivery, and header integrity, while the 4th and 5th rows define the sender and receiver IP addresses used for routing and replies.**