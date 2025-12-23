# 🌐 Class C in IP Addressing

**(Classful Addressing – Network Layer)**

---

## 1️⃣ What is Class C?

👉 **Class C is used for small networks**

It is designed for:

* **Few hosts**
* **Many networks**

Example use:

* Small offices
* Labs
* Home networks (older systems)

---

## 2️⃣ How to Identify a Class C IP (MOST IMPORTANT)

### Rule: First octet range

If the **first number** of the IP address is between:

```
192 – 223
```

👉 It is **Class C**

### Examples:

| IP Address  | First Octet | Class         |
| ----------- | ----------- | ------------- |
| 192.168.1.1 | 192         | Class C       |
| 200.10.5.1  | 200         | Class C       |
| 223.1.1.1   | 223         | Class C       |
| 224.1.1.1   | 224         | ❌ Not Class C |

---

## 3️⃣ Binary Pattern of Class C (simple idea)

First octet starts with:

```
110xxxxx
```

That binary pattern produces the range:

```
192 – 223
```

---

## 4️⃣ Structure of Class C IP Address

```
| Network | Network | Network | Host |
```

Or:

```
A.B.C.D
↑ ↑ ↑   ↑
N N N   H
```

* **First 3 octets → Network part**
* **Last octet → Host part**

---

## 5️⃣ Default Subnet Mask of Class C

```
255.255.255.0
```

Binary:

```
11111111.11111111.11111111.00000000
```

* Network bits → 24
* Host bits → 8

---

## 6️⃣ How Many Networks in Class C?

Network bits:

* 21 variable bits (after fixed `110`)

### Formula:

```
2^21
```

👉 **2,097,152 networks**

---

## 7️⃣ How Many Hosts per Network?

Host bits = **8**

But:

* All 0s → Network address ❌
* All 1s → Broadcast address ❌

### Formula:

```
2^8 − 2
```

👉 **254 hosts per network**

---

## 8️⃣ Example 1 (Very Easy)

### IP Address:

```
192.168.1.10
```

### Step 1: Identify class

```
192 → Class C
```

### Step 2: Subnet mask

```
255.255.255.0
```

### Step 3: Network address

```
192.168.1.0
```

### Step 4: Broadcast address

```
192.168.1.255
```

### Step 5: Valid host range

```
192.168.1.1 – 192.168.1.254
```

---

## 9️⃣ Example 2

### IP Address:

```
200.50.10.25
```

### Network address:

```
200.50.10.0
```

### Broadcast address:

```
200.50.10.255
```

### Valid hosts:

```
200.50.10.1 – 200.50.10.254
```

---

## 🔟 Example 3 (Private Class C Range)

Private IP range:

```
192.168.0.0 – 192.168.255.255
```

Common home router IP:

```
192.168.1.1
```

Used in:

* Wi-Fi routers
* Home networks
* LANs

---

## 1️⃣1️⃣ Summary Table

| Feature           | Class C        |
| ----------------- | -------------- |
| First Octet Range | 192 – 223      |
| Binary Start      | 110xxxxx       |
| Network Bits      | 24             |
| Host Bits         | 8              |
| Default Mask      | 255.255.255.0  |
| Hosts / Network   | 254            |
| Usage             | Small networks |

---

## 🧠 One-Line Memory Trick

> **Class C → First THREE octets = Network**

---

## 🎯 Quick Practice (Try This)

For IP:

```
205.100.50.10
```

Answer:
1️⃣ Is it Class C?
2️⃣ Network address?
3️⃣ Broadcast address?

I’ll check your answers 👍




---
---
---
---
---
---
---
---
---
---
---
---



## 🔹 Example 1

**IP:** `192.168.1.25`

* First octet = `192` → **Class C**
* Default subnet mask → `255.255.255.0`

**Network address:**

```
192.168.1.0
```

**Broadcast address:**

```
192.168.1.255
```

**Valid hosts:**

```
192.168.1.1 – 192.168.1.254
```

---

## 🔹 Example 2

**IP:** `200.10.20.30`

* First octet = `200` → **Class C**
* Subnet mask → `255.255.255.0`

**Network address:**

```
200.10.20.0
```

**Broadcast address:**

```
200.10.20.255
```

**Valid hosts:**

```
200.10.20.1 – 200.10.20.254
```

---

## 🔹 Example 3

**IP:** `223.1.5.100`

* First octet = `223` → **Class C (last possible)**

**Network address:**

```
223.1.5.0
```

**Broadcast address:**

```
223.1.5.255
```

**Valid hosts:**

```
223.1.5.1 – 223.1.5.254
```

---

## 🔹 Example 4 (Private Class C)

**IP:** `192.168.10.50`

**Network address:**

```
192.168.10.0
```

**Broadcast address:**

```
192.168.10.255
```

**Valid hosts:**

```
192.168.10.1 – 192.168.10.254
```

👉 Used in **home / Wi-Fi networks**

---

## 🔹 Example 5 (NOT Class C – for clarity)

**IP:** `224.10.1.5`

* First octet = `224`
  ❌ **Not Class C** (this is Class D)

---

## 🧠 One Rule to Remember

> **Class C → A.B.C.0 (network)**
> **Class C → A.B.C.255 (broadcast)**

---

### Want practice like before?

Try this 👇

```
210.50.60.70
```

Tell me:
1️⃣ Class?
2️⃣ Network address?
3️⃣ Broadcast address?
