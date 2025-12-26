# 🟢 ARP – Address Resolution Protocol

### (Network Layer)

---

## 1️⃣ First: Why do we even need ARP?

In a network, communication actually happens using **MAC addresses**, not IP addresses.

But applications use **IP addresses**.

So the problem is:

> ❓ **How do we find the MAC address of a device when we only know its IP address?**

👉 **ARP solves this problem.**

---

## 2️⃣ One-line definition (Exam Gold ⭐)

> **ARP (Address Resolution Protocol)** is used to map an **IP address** to its corresponding **MAC address** in a local network.

---

## 3️⃣ Simple real-world analogy 📞

Think of:

* **IP address** = Person’s name
* **MAC address** = Phone number

You know the **name**, but to call, you need the **phone number**.

👉 ARP is like **asking everyone: “Who has this name?”**

---

## 4️⃣ Where does ARP work?

✔ Works **inside a local network (LAN)**
✔ Works **between Network Layer and Data Link Layer**
✔ Used only when sender and receiver are in the **same network**

❌ ARP does **NOT work across the internet**

---

## 5️⃣ Why MAC address is required?

Ethernet frames require:

```
Source MAC address
Destination MAC address
```

Even if you know the IP address, **data cannot be sent without MAC address**.

---

## 6️⃣ Components involved in ARP

Every device has:

* **IP address**
* **MAC address**
* **ARP Cache (ARP Table)**

### ARP Cache stores:

```
IP address → MAC address
```

Example:

```
192.168.1.10 → 00:1A:2B:3C:4D:5E
```

---

## 7️⃣ How ARP works (Step by Step)

### Scenario:

Computer **A** wants to send data to Computer **B**

* A’s IP: `192.168.1.2`
* B’s IP: `192.168.1.5`
* B’s MAC: ❓ (unknown)

---

### 🔹 Step 1: Check ARP Cache

Computer A checks:

```
Do I already know MAC of 192.168.1.5?
```

* If **YES** → send data directly
* If **NO** → send ARP Request

---

### 🔹 Step 2: ARP Request (Broadcast)

Computer A sends an **ARP Request**:

```
Who has IP 192.168.1.5?
Tell 192.168.1.2
```

Important points:

* Destination MAC = **FF:FF:FF:FF:FF:FF** (broadcast)
* Every device in LAN receives it

---

### 🔹 Step 3: ARP Reply (Unicast)

Only Computer B replies:

```
192.168.1.5 is at AA:BB:CC:DD:EE:FF
```

* This reply is **unicast**
* Sent only to Computer A

---

### 🔹 Step 4: Update ARP Cache

Computer A stores:

```
192.168.1.5 → AA:BB:CC:DD:EE:FF
```

Now future communication is **fast**.

---

### 🔹 Step 5: Data Transmission

Computer A sends actual data using:

```
Destination MAC = B’s MAC
Destination IP  = B’s IP
```

---

## 8️⃣ ARP Packet Types

There are **two main ARP messages**:

| Type        | Purpose                 |
| ----------- | ----------------------- |
| ARP Request | Ask “Who has this IP?”  |
| ARP Reply   | Answer with MAC address |

---

## 9️⃣ Important characteristics of ARP

✔ Uses **broadcast + unicast**
✔ No authentication (security issue)
✔ Works automatically
✔ Temporary entries in ARP cache
✔ Part of **Network Layer support protocol**

---

## 🔟 Is ARP Network Layer or Data Link Layer?

This is a **VERY common exam question** ❗

👉 **ARP is a Network Layer protocol**,
but it **operates using MAC addresses (Data Link Layer)**.

So we say:

> **ARP lies between Network Layer and Data Link Layer**

---

## 1️⃣1️⃣ ARP Cache (ARP Table)

* Stores recent IP–MAC mappings
* Prevents repeated ARP requests
* Entries expire after some time

Command example (not exam-critical):

```
arp -a
```

---

## 1️⃣2️⃣ What happens if destination is outside LAN?

ARP **does NOT find remote hosts**.

Instead:

* Sender finds **MAC of default gateway**
* Router handles further routing

👉 ARP resolves **gateway MAC**, not destination MAC.

---

## 1️⃣3️⃣ Problems with ARP

### ❌ ARP Spoofing / Poisoning

Attacker sends fake ARP replies:

```
“I am the gateway”
```

Results:

* Man-in-the-middle attack
* Packet sniffing
* Data theft

---

## 1️⃣4️⃣ One-line disadvantages

❌ No security
❌ Vulnerable to spoofing
❌ Broadcast overhead

---

## 1️⃣5️⃣ One-line exam answer ⭐

> ARP is used to resolve an IP address into a MAC address by broadcasting an ARP request and receiving a unicast ARP reply within a local network.

---

## 1️⃣6️⃣ Key sentence to remember forever

> **IP is logical, MAC is physical — ARP connects the two.**



---
---
---
---
---

![](./images/ARP-Green-768.png)




# 🟢 ARP Header Explained (Field by Field)

The **ARP packet** is used to map:

> **IP address → MAC address**

This header is carried **inside an Ethernet frame**.

---

## 🔹 Overall ARP Header Structure

* ARP header is **not fixed-size**
* Size depends on:

  * Hardware address length
  * Protocol address length
* For **Ethernet + IPv4**, total ARP packet size = **28 bytes**

---

## 1️⃣ Hardware Type (HTYPE) – 16 bits

### What it means

Tells **which hardware/network technology** is being used.

### Common values

| Value | Meaning                |
| ----- | ---------------------- |
| 1     | Ethernet (most common) |

### Example

```
Hardware Type = 1 → Ethernet
```

👉 Means ARP is resolving **MAC addresses**.

---

## 2️⃣ Protocol Type (PTYPE) – 16 bits

### What it means

Specifies **which protocol’s address is being resolved**.

### Common value

| Hex    | Meaning |
| ------ | ------- |
| 0x0800 | IPv4    |

### Example

```
Protocol Type = 0x0800 → IPv4
```

👉 Means ARP is resolving **IPv4 → MAC**.

---

## 3️⃣ Hardware Address Length (HLEN) – 8 bits

### What it means

Length of **hardware (MAC) address** in bytes.

### Ethernet MAC

```
MAC = 6 bytes
```

So:

```
HLEN = 6
```

---

## 4️⃣ Protocol Address Length (PLEN) – 8 bits

### What it means

Length of **protocol (IP) address** in bytes.

### IPv4

```
IPv4 = 32 bits = 4 bytes
```

So:

```
PLEN = 4
```

---

## 5️⃣ Operation (OPER) – 16 bits

### What it means

Specifies **ARP message type**.

| Value | Meaning     |
| ----- | ----------- |
| 1     | ARP Request |
| 2     | ARP Reply   |

### Example

```
OPER = 1 → “Who has this IP?”
OPER = 2 → “I have this IP”
```

---

## 6️⃣ Sender Hardware Address (SHA)

### What it means

MAC address of the **sender**.

### Size

```
HLEN bytes (usually 6 bytes)
```

### Example

```
Sender MAC = 00:1A:2B:3C:4D:5E
```

---

## 7️⃣ Sender Protocol Address (SPA)

### What it means

IP address of the **sender**.

### Size

```
PLEN bytes (usually 4 bytes)
```

### Example

```
Sender IP = 192.168.1.10
```

---

## 8️⃣ Target Hardware Address (THA)

### What it means

MAC address of the **target**.

### Important behavior

* In **ARP Request** → **UNKNOWN**
* Filled with **00:00:00:00:00:00**

### Example

```
Target MAC = 00:00:00:00:00:00
```

---

## 9️⃣ Target Protocol Address (TPA)

### What it means

IP address whose MAC is being requested.

### Example

```
Target IP = 192.168.1.20
```

---

## 🔁 Putting It All Together (ARP Request Example)

Computer A wants MAC of `192.168.1.20`

```
HTYPE = 1        (Ethernet)
PTYPE = 0x0800  (IPv4)
HLEN  = 6
PLEN  = 4
OPER  = 1       (Request)

SHA = A’s MAC
SPA = A’s IP
THA = 00:00:00:00:00:00
TPA = 192.168.1.20
```

Meaning:

> “Who has IP 192.168.1.20? Tell me your MAC.”

---

## 🔁 ARP Reply Example

```
OPER = 2 (Reply)

SHA = B’s MAC
SPA = B’s IP
THA = A’s MAC
TPA = A’s IP
```

Meaning:

> “192.168.1.20 is at AA:BB:CC:DD:EE:FF”

---

## 🔑 Very Important Exam Points ⭐

✔ ARP header size (Ethernet + IPv4) = **28 bytes**
✔ ARP Request → **Broadcast**
✔ ARP Reply → **Unicast**
✔ Target MAC unknown only in **Request**
✔ ARP works only in **LAN**

---

## 📝 One-Line Exam Answer

> The ARP header contains hardware type, protocol type, address lengths, operation code, and sender/target MAC and IP addresses used to resolve IP addresses into MAC addresses.
