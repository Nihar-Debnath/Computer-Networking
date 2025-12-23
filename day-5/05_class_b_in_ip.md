## 1️⃣ What is Classful IP Addressing (very basic)

In **IPv4**, an IP address is:

```
A.B.C.D
```

Each part is **1 byte (8 bits)**
Total = **32 bits**

Earlier, IP addresses were divided into **classes**:

* Class A
* **Class B**
* Class C
* Class D (multicast)
* Class E (reserved)

Today we focus **only on Class B**.

---

## 2️⃣ What is Class B IP Address?

👉 **Class B is used for medium-sized networks**

It balances:

* number of **networks**
* number of **hosts per network**

---

## 3️⃣ How to identify a Class B IP (MOST IMPORTANT)

### Rule 1: First octet range

If the **first number** of the IP address is between:

```
128 – 191
```

👉 It is **Class B**

### Examples:

| IP Address  | First Octet | Class         |
| ----------- | ----------- | ------------- |
| 130.10.5.6  | 130         | Class B       |
| 172.16.2.1  | 172         | Class B       |
| 191.255.1.1 | 191         | Class B       |
| 192.1.1.1   | 192         | ❌ Not Class B |

---

## 4️⃣ Binary Pattern of Class B (simple logic)

First octet (8 bits):

```
10xxxxxx
```

* Starts with **10**
* That binary range = **128 to 191**

That’s WHY Class B starts from **128**

---

## 5️⃣ Structure of Class B IP Address

```
| Network | Network | Host | Host |
```

Or in octets:

```
A.B.C.D
↑ ↑   ↑ ↑
N N   H H
```

* **First 2 octets → Network part**
* **Last 2 octets → Host part**

---

## 6️⃣ Default Subnet Mask of Class B

Subnet mask tells **which part is network and host**

### Class B default subnet mask:

```
255.255.0.0
```

In binary:

```
11111111.11111111.00000000.00000000
```

* `1` → Network
* `0` → Host

---

## 7️⃣ How many Networks in Class B?

### Network bits:

* First octet: fixed `10` + 6 bits
* Second octet: 8 bits

Total network bits = **14 bits**

### Formula:

```
Number of networks = 2^14
```

👉 **16,384 networks**

---

## 8️⃣ How many Hosts per Network?

### Host bits:

* Last two octets = 16 bits

But:

* All 0s → Network address ❌
* All 1s → Broadcast address ❌

### Formula:

```
Hosts = 2^16 − 2
```

👉 **65,534 hosts per network**

---

## 9️⃣ Real Example (Very Easy)

### Example IP:

```
172.16.5.10
```

### Step-by-step:

1️⃣ First octet = `172`
→ Between `128–191`
→ ✅ **Class B**

2️⃣ Default subnet mask:

```
255.255.0.0
```

3️⃣ Network part:

```
172.16.0.0
```

4️⃣ Host part:

```
5.10
```

5️⃣ Valid host range:

```
172.16.0.1  →  172.16.255.254
```

---

## 🔟 Summary Table (Easy to Remember)

| Feature           | Class B               |
| ----------------- | --------------------- |
| First Octet Range | 128 – 191             |
| Binary Start      | 10xxxxxx              |
| Network Bits      | 16                    |
| Host Bits         | 16                    |
| Default Mask      | 255.255.0.0           |
| Networks          | 16,384                |
| Hosts per Network | 65,534                |
| Usage             | Medium-sized networks |

---

## 1️⃣1️⃣ One-Line Memory Trick 🧠

> **“Class B = 2 octets Network + 2 octets Host”**



---
---
---
---
---
---



## 🔹 Example 1: `130.45.10.5`

### Step 1: Check first octet

```
130  → between 128–191
```

✅ **Class B**

### Step 2: Default subnet mask

```
255.255.0.0
```

### Step 3: Network & Host

```
Network part → 130.45
Host part    → 10.5
```

### Step 4: Network address

```
130.45.0.0
```

### Step 5: Broadcast address

```
130.45.255.255
```

### Step 6: Valid host range

```
130.45.0.1  to  130.45.255.254
```

---

## 🔹 Example 2: `172.16.50.100`

### Step 1: First octet

```
172 → Class B
```

### Step 2: Subnet mask

```
255.255.0.0
```

### Step 3: Network address

```
172.16.0.0
```

### Step 4: Broadcast address

```
172.16.255.255
```

### Step 5: Valid hosts

```
172.16.0.1  –  172.16.255.254
```

👉 **172.16.x.x is commonly used in private networks**

---

## 🔹 Example 3: `191.200.1.25`

### Step 1: First octet

```
191 → last possible Class B
```

✅ **Class B**

### Step 2: Network address

```
191.200.0.0
```

### Step 3: Broadcast address

```
191.200.255.255
```

### Step 4: Host range

```
191.200.0.1  –  191.200.255.254
```

---

## 🔹 Example 4 (NOT Class B – for clarity)

### IP: `192.168.1.1`

```
First octet = 192
```

❌ **Not Class B**
✅ This is **Class C**

---

## 🔹 Quick Practice (Try yourself)

Tell me the answers for this IP 👇

```
150.10.20.30
```
