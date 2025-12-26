# 🌐 Subnetting in Classful Addressing (Fully Explained)

## 1️⃣ First: What is Subnetting?

**Subnetting** means:

> **Dividing one large network into smaller logical networks (sub-networks)**

Why we do it:

* Reduce **wasted IP addresses**
* Improve **network performance**
* Improve **security**
* Make **network management easier**

---

## 2️⃣ What is Classful Addressing?

In **classful addressing**, IP addresses are divided into fixed classes:

| Class | Range                     | Default Subnet Mask | Network Bits | Host Bits |
| ----- | ------------------------- | ------------------- | ------------ | --------- |
| A     | 1.0.0.0 – 126.0.0.0       | 255.0.0.0 (/8)      | 8            | 24        |
| B     | 128.0.0.0 – 191.255.0.0   | 255.255.0.0 (/16)   | 16           | 16        |
| C     | 192.0.0.0 – 223.255.255.0 | 255.255.255.0 (/24) | 24           | 8         |

⚠️ In classful addressing:

* **Subnet mask is fixed**
* **Subnetting is optional**
* You can only borrow bits from **host part**

---

## 3️⃣ Why Subnetting is Needed in Classful Addressing?

### Example Problem

Class B network gives:

```
Hosts = 2^16 − 2 = 65,534 hosts
```

But what if:

* You need **5 departments**
* Each department needs **2,000 hosts**

❌ Without subnetting → **Huge wastage**

✅ With subnetting → Efficient use

---

## 4️⃣ Basic Subnetting Rule (VERY IMPORTANT)

### 🔑 Formulae to Remember

1️⃣ **Number of Subnets**

```
= 2^n
```

(where `n` = borrowed bits)

2️⃣ **Hosts per Subnet**

```
= 2^h − 2
```

(where `h` = remaining host bits)

3️⃣ **Subnet Mask**

* Add borrowed bits to default mask

---

## 5️⃣ Subnetting a Class C Network (Detailed Example)

### Example:

**IP Address:** `192.168.1.0`
**Class:** C
**Default Mask:** `255.255.255.0 (/24)`

---

### Requirement:

👉 Create **4 subnets**

---

### Step 1: Calculate Borrowed Bits

```
2^n ≥ 4
n = 2
```

So we borrow **2 bits** from host part.

---

### Step 2: New Subnet Mask

Original:

```
/24
```

New:

```
/26  (24 + 2)
```

Binary:

```
11111111.11111111.11111111.11000000
```

Decimal:

```
255.255.255.192
```

---

### Step 3: Calculate Hosts per Subnet

Host bits left:

```
8 − 2 = 6
```

Hosts:

```
2^6 − 2 = 62 hosts
```

---

### Step 4: Find Block Size

```
Block Size = 256 − 192 = 64
```

---

### Step 5: List All Subnets

| Subnet No | Network ID    | First Host | Last Host | Broadcast |
| --------- | ------------- | ---------- | --------- | --------- |
| 1         | 192.168.1.0   | .1         | .62       | .63       |
| 2         | 192.168.1.64  | .65        | .126      | .127      |
| 3         | 192.168.1.128 | .129       | .190      | .191      |
| 4         | 192.168.1.192 | .193       | .254      | .255      |

✔️ Subnetting done successfully

---

## 6️⃣ Subnetting a Class B Network (Numerical Example)

### Given:

**IP:** `172.16.0.0`
**Class:** B
**Default Mask:** `255.255.0.0 (/16)`

---

### Requirement:

👉 Create **8 subnets**

---

### Step 1: Borrow Bits

```
2^n ≥ 8
n = 3
```

---

### Step 2: New Subnet Mask

```
/16 + 3 = /19
```

Binary:

```
11111111.11111111.11100000.00000000
```

Decimal:

```
255.255.224.0
```

---

### Step 3: Hosts per Subnet

Remaining host bits:

```
16 − 3 = 13
```

Hosts:

```
2^13 − 2 = 8190
```

---

### Step 4: Block Size

```
256 − 224 = 32
```

---

### Step 5: Subnet Ranges

| Subnet | Network ID   |
| ------ | ------------ |
| 1      | 172.16.0.0   |
| 2      | 172.16.32.0  |
| 3      | 172.16.64.0  |
| 4      | 172.16.96.0  |
| 5      | 172.16.128.0 |
| 6      | 172.16.160.0 |
| 7      | 172.16.192.0 |
| 8      | 172.16.224.0 |

Each subnet supports **8190 hosts**

---

## 7️⃣ Subnetting a Class A Network (Quick Example)

### Given:

**IP:** `10.0.0.0`
**Default Mask:** `/8`

### Borrow 4 bits:

```
Subnets = 2^4 = 16
New Mask = /12
```

Hosts per subnet:

```
2^(24 − 4) − 2 = 1,048,574
```

---

## 8️⃣ Important Notes (Exam Gold ⭐)

✔️ Network ID → **All host bits = 0**
✔️ Broadcast Address → **All host bits = 1**
✔️ First usable IP → Network + 1
✔️ Last usable IP → Broadcast − 1

---

## 9️⃣ Limitations of Subnetting in Classful Addressing

❌ Fixed subnet masks
❌ Large IP wastage
❌ No flexibility
❌ Led to **IPv4 exhaustion**

➡️ This problem led to **CIDR (Classless Addressing)**

---

## 🔟 Final Summary

| Concept        | Meaning                                  |
| -------------- | ---------------------------------------- |
| Subnetting     | Dividing a network into smaller networks |
| Classful       | Fixed default masks                      |
| Borrowing bits | Taken from host part                     |
| Formula        | `Subnets = 2^n`, `Hosts = 2^h − 2`       |
| Used in        | Old networks, exams, fundamentals        |




---
---
---
---
---
---
---
---
---


# 🔢 Subnetting in Classful Addressing – Exam Numerical Problems

---

## ✅ QUESTION 1 (Very Common – Class C)

**Given IP:** `192.168.10.0`
**Class:** C
**Requirement:** Create **8 subnets**

### Step 1️⃣ Default Information

* Class C → Default mask = `/24`
* Host bits = 8

---

### Step 2️⃣ Borrow Bits

We need **8 subnets**

```
2^n ≥ 8
n = 3
```

Borrow **3 bits** from host part.

---

### Step 3️⃣ New Subnet Mask

```
/24 + 3 = /27
```

Binary:

```
11111111.11111111.11111111.11100000
```

Decimal:

```
255.255.255.224
```

---

### Step 4️⃣ Hosts per Subnet

Remaining host bits:

```
8 − 3 = 5
```

```
Hosts = 2^5 − 2 = 30
```

---

### Step 5️⃣ Block Size

```
256 − 224 = 32
```

---

### Step 6️⃣ Subnet Table (EXAM ANSWER)

| Subnet | Network ID     | First Host | Last Host | Broadcast |
| ------ | -------------- | ---------- | --------- | --------- |
| 1      | 192.168.10.0   | .1         | .30       | .31       |
| 2      | 192.168.10.32  | .33        | .62       | .63       |
| 3      | 192.168.10.64  | .65        | .94       | .95       |
| 4      | 192.168.10.96  | .97        | .126      | .127      |
| 5      | 192.168.10.128 | .129       | .158      | .159      |
| 6      | 192.168.10.160 | .161       | .190      | .191      |
| 7      | 192.168.10.192 | .193       | .222      | .223      |
| 8      | 192.168.10.224 | .225       | .254      | .255      |

✔️ **Full marks answer**

---

## ✅ QUESTION 2 (Hosts Given – Class C)

**Given IP:** `192.168.5.0`
**Requirement:** Minimum **50 hosts per subnet**

---

### Step 1️⃣ Decide Host Bits

```
2^h − 2 ≥ 50
```

Try:

```
2^6 − 2 = 62 ✅
```

So host bits = **6**

---

### Step 2️⃣ Borrow Bits

Class C has 8 host bits:

```
Borrowed bits = 8 − 6 = 2
```

---

### Step 3️⃣ Subnets & Mask

```
Subnets = 2^2 = 4
Mask = /26
```

Decimal:

```
255.255.255.192
```

---

### Step 4️⃣ Block Size

```
256 − 192 = 64
```

---

### Step 5️⃣ Subnet Ranges

| Subnet | Network ID    | Hosts | Broadcast |
| ------ | ------------- | ----- | --------- |
| 1      | 192.168.5.0   | 62    | .63       |
| 2      | 192.168.5.64  | 62    | .127      |
| 3      | 192.168.5.128 | 62    | .191      |
| 4      | 192.168.5.192 | 62    | .255      |

---

## ✅ QUESTION 3 (Class B – Very Important)

**Given IP:** `172.16.0.0`
**Requirement:** **16 subnets**

---

### Step 1️⃣ Default Info

* Class B → `/16`
* Host bits = 16

---

### Step 2️⃣ Borrow Bits

```
2^n ≥ 16
n = 4
```

---

### Step 3️⃣ New Mask

```
/16 + 4 = /20
```

Decimal:

```
255.255.240.0
```

---

### Step 4️⃣ Hosts per Subnet

```
Remaining host bits = 12
Hosts = 2^12 − 2 = 4094
```

---

### Step 5️⃣ Block Size

```
256 − 240 = 16
```

---

### Step 6️⃣ Subnet IDs

```
172.16.0.0
172.16.16.0
172.16.32.0
172.16.48.0
...
172.16.240.0
```

(16 total subnets)

---

## ✅ QUESTION 4 (Find Network, Broadcast, Hosts)

**Given:** `192.168.1.130/26`

---

### Step 1️⃣ Understand Mask

```
/26 → 255.255.255.192
Block size = 64
```

---

### Step 2️⃣ Identify Subnet Range

Subnets:

```
0–63
64–127
128–191  ← 130 lies here
192–255
```

---

### Step 3️⃣ Final Answer

| Field      | Value         |
| ---------- | ------------- |
| Network ID | 192.168.1.128 |
| First Host | 192.168.1.129 |
| Last Host  | 192.168.1.190 |
| Broadcast  | 192.168.1.191 |

---

## ✅ QUESTION 5 (Tricky – Mixed)

**Given:** `10.0.0.0`
**Requirement:** At least **1000 subnets**

---

### Step 1️⃣ Default Info

Class A:

* Default mask = `/8`
* Host bits = 24

---

### Step 2️⃣ Borrow Bits

```
2^n ≥ 1000
```

```
2^10 = 1024 ✅
```

Borrow **10 bits**

---

### Step 3️⃣ New Mask

```
/8 + 10 = /18
```

Decimal:

```
255.255.192.0
```

---

### Step 4️⃣ Hosts per Subnet

```
Remaining host bits = 14
Hosts = 2^14 − 2 = 16382
```

---

## 🧠 EXAM SHORTCUTS (VERY IMPORTANT)

### 🔑 Block Size Trick

```
Block Size = 256 − subnet_mask_octet
```

### 🔑 Network ID

> The **nearest multiple of block size ≤ given IP**

### 🔑 Broadcast

```
Next Network − 1
```

---

## 📌 What Examiners Expect

✔️ Correct class
✔️ Borrowed bits shown
✔️ Subnet mask
✔️ Formula usage
✔️ At least 2–3 subnet ranges
