# 🌐 Class A IP Addressing

**(Classful Addressing | Network Layer)**

---

## 1️⃣ First: What is Classful Addressing?

In **Classful IP addressing**, IPv4 addresses are divided into **5 classes**:

| Class   | Use                 |
| ------- | ------------------- |
| Class A | Very large networks |
| Class B | Medium networks     |
| Class C | Small networks      |
| Class D | Multicast           |
| Class E | Experimental        |

📌 Today we are focusing only on **Class A**.

---

## 2️⃣ IPv4 Address Structure (Foundation)

An **IPv4 address**:

* Is **32 bits long**
* Divided into **4 octets**
* Each octet = **8 bits**

```
IP Address = 32 bits
           = 8 bits . 8 bits . 8 bits . 8 bits
```

Example:

```
64.15.23.10
```

---

## 3️⃣ How Class A is Identified (MOST IMPORTANT)

### 🔹 Fixed Bit Rule

In **Class A**:

* **First bit of the first octet is always `0`**

```
0xxxxxxx . xxxxxxxx . xxxxxxxx . xxxxxxxx
```

📌 Routers look at this **first bit** to identify **Class A**.

---

## 4️⃣ First Octet Range of Class A

Because the **first bit is 0**, the first octet range becomes:

```
00000000 → 01111111
```

In decimal:

```
0  → 127
```

### ✅ Class A Range:

```
0.0.0.0  to  127.255.255.255
```

---

## 5️⃣ Network ID and Host ID in Class A

### Bit Distribution

| Part       | Bits                    |
| ---------- | ----------------------- |
| Network ID | 8 bits (1st octet)      |
| Host ID    | 24 bits (last 3 octets) |

```
| Network ID | Host ID |
|  8 bits    | 24 bits |
```

Example:

```
64.10.20.30
↑
Network ID = 64
Host ID    = 10.20.30
```

---

## 6️⃣ Number of Networks in Class A

### Step-by-Step Logic

* Network ID uses **8 bits**
* But **1 bit is fixed as 0**
* So usable bits = **7 bits**

### Calculation:

[
2^7 = 128 \text{ networks}
]

---

### ❌ Reserved Networks (NOT usable)

| Network     | Reason                          |
| ----------- | ------------------------------- |
| `0.0.0.0`   | Default / current network       |
| `127.0.0.0` | Loopback (testing, diagnostics) |

📌 `127.0.0.1` = **localhost**

---

### ✅ Usable Class A Networks

[
128 - 2 = \boxed{126 \text{ usable networks}}
]

---

## 7️⃣ Number of Hosts in One Class A Network

### Host ID bits:

* **24 bits**

### Total hosts:

[
2^{24} = 16,777,216
]

---

### ❌ Reserved Host Addresses (in every network)

| Address           | Meaning           |
| ----------------- | ----------------- |
| All host bits = 0 | Network Address   |
| All host bits = 1 | Broadcast Address |

---

### ✅ Usable Hosts per Network

[
2^{24} - 2 = \boxed{16,777,214 \text{ hosts}}
]

---

## 8️⃣ Example (Very Important for Exams)

### Example IP:

```
64.15.20.30
```

### Step 1: Identify Class

* First octet = 64
* Range 0–127 → **Class A**

---

### Step 2: Network Address

```
64.0.0.0
```

(All host bits = 0)

---

### Step 3: Broadcast Address

```
64.255.255.255
```

(All host bits = 1)

---

### Step 4: Valid Host Range

```
64.0.0.1  to  64.255.255.254
```

---

## 9️⃣ Default Subnet Mask of Class A

### What is Default Mask?

It tells:

* Which part is **network**
* Which part is **host**

---

### Class A Default Mask:

```
255.0.0.0
```

Binary:

```
11111111.00000000.00000000.00000000
```

---

## 🔟 Why Mask is Important (AND Operation)

To find **Network ID**, router does:

```
IP Address  AND  Subnet Mask
```

Example:

```
64.15.20.30
AND 255.0.0.0
=   64.0.0.0
```

---

## 🔁 Quick Summary Table (Perfect for Revision)

| Feature              | Class A             |
| -------------------- | ------------------- |
| First bit            | 0                   |
| First octet range    | 0 – 127             |
| Network bits         | 8                   |
| Host bits            | 24                  |
| Default mask         | 255.0.0.0           |
| Usable networks      | 126                 |
| Usable hosts/network | 16,777,214          |
| Usage                | Very large networks |

---

## 🎯 One-Line Exam Definition

> **Class A addressing is a classful IP addressing scheme where the first bit is 0, the first octet represents the network ID, and each network supports a very large number of hosts.**

---

## 🧠 Memory Trick (Easy Recall)

* **A = Amount of Hosts is HUGE**
* **A = 255.0.0.0**
* **A = First bit 0**
