# 📌 CLASS A

### 🔹 Range (First Octet)

```
1.0.0.0 – 126.255.255.255
```

(127.x.x.x is loopback)

### 🔹 Default Subnet Mask

```
255.0.0.0
```

### 🔹 Structure

```
Network | Host | Host | Host
```

---

### ✅ Numerical Example (Class A)

**IP Address**

```
10.20.30.40
```

**Network ID**

```
10.0.0.0
```

**Broadcast Address**

```
10.255.255.255
```

**Valid Host Range**

```
10.0.0.1 – 10.255.255.254
```

---

# 📌 CLASS B

### 🔹 Range (First Octet)

```
128.0.0.0 – 191.255.255.255
```

### 🔹 Default Subnet Mask

```
255.255.0.0
```

### 🔹 Structure

```
Network | Network | Host | Host
```

---

### ✅ Numerical Example (Class B)

**IP Address**

```
150.10.20.30
```

**Network ID**

```
150.10.0.0
```

**Broadcast Address**

```
150.10.255.255
```

**Valid Host Range**

```
150.10.0.1 – 150.10.255.254
```

---

# 📌 CLASS C

### 🔹 Range (First Octet)

```
192.0.0.0 – 223.255.255.255
```

### 🔹 Default Subnet Mask

```
255.255.255.0
```

### 🔹 Structure

```
Network | Network | Network | Host
```

---

### ✅ Numerical Example (Class C)

**IP Address**

```
192.168.1.10
```

**Network ID**

```
192.168.1.0
```

**Broadcast Address**

```
192.168.1.255
```

**Valid Host Range**

```
192.168.1.1 – 192.168.1.254
```

---

# 📌 CLASS D (Multicast)

### 🔹 Range

```
224.0.0.0 – 239.255.255.255
```

### 🔹 Purpose

```
Multicast (one-to-many)
```

### ❌ Important

* No Network ID
* No Host ID
* No Broadcast
* No Subnet Mask

---

### ✅ Numerical Example (Class D)

**IP Address**

```
230.10.10.10
```

✔ This is a **multicast group address**
❌ Network ID → Not applicable
❌ Host range → Not applicable
❌ Broadcast → Not applicable

---

# 📌 CLASS E (Reserved)

### 🔹 Range

```
240.0.0.0 – 255.255.255.255
```

### 🔹 Purpose

```
Reserved / Experimental
```

### ❌ Important

* No Network ID
* No Host ID
* No Broadcast
* Not used in real networks

---

### ✅ Numerical Example (Class E)

**IP Address**

```
250.1.1.1
```

❌ Network ID → Not defined
❌ Host range → Not defined
❌ Broadcast → Not defined

⚠ Special case:

```
255.255.255.255 → Limited Broadcast
```

---

# 🔥 ONE-SHOT COMPARISON TABLE (VERY IMPORTANT)

| Class | Range   | Network ID | Host Range | Broadcast |
| ----- | ------- | ---------- | ---------- | --------- |
| A     | 1–126   | ✔          | ✔          | ✔         |
| B     | 128–191 | ✔          | ✔          | ✔         |
| C     | 192–223 | ✔          | ✔          | ✔         |
| D     | 224–239 | ❌          | ❌          | ❌         |
| E     | 240–255 | ❌          | ❌          | ❌         |

---

# 🧠 SUPER EASY MEMORY RULE

* **A → 1 Network octet**
* **B → 2 Network octets**
* **C → 3 Network octets**
* **D → Multicast group**
* **E → Reserved**



---
---
---
---
---
---
---


# 📝 MIXED PRACTICE QUESTIONS (Classful Addressing)

---

## 🔹 Question 1

Given IP address:

```
10.50.60.70
```

Find:
1️⃣ Class
2️⃣ Network ID
3️⃣ Broadcast address
4️⃣ Host range

---

## 🔹 Question 2

Given IP address:

```
172.16.25.10
```

Find:
1️⃣ Class
2️⃣ Network ID
3️⃣ Broadcast address
4️⃣ Host range

---

## 🔹 Question 3

Given IP address:

```
192.168.5.200
```

Find:
1️⃣ Class
2️⃣ Network ID
3️⃣ Broadcast address
4️⃣ Host range

---

## 🔹 Question 4

Given IP address:

```
200.10.20.30
```

Find:
1️⃣ Class
2️⃣ Network ID
3️⃣ Broadcast address
4️⃣ Host range

---

## 🔹 Question 5

Given IP address:

```
230.5.6.7
```

Find:
1️⃣ Class
2️⃣ Network ID
3️⃣ Host range
4️⃣ Broadcast address

---

## 🔹 Question 6

Given IP address:

```
250.10.20.30
```

Find:
1️⃣ Class
2️⃣ Network ID
3️⃣ Host range
4️⃣ Broadcast address

---

---

# ✅ FULLY SOLVED ANSWERS (EXAM READY)

---

## ✅ Answer 1

**IP:** `10.50.60.70`

* First octet = 10 → **Class A**
* Default mask = `255.0.0.0`

**Network ID**

```
10.0.0.0
```

**Broadcast Address**

```
10.255.255.255
```

**Host Range**

```
10.0.0.1 – 10.255.255.254
```

---

## ✅ Answer 2

**IP:** `172.16.25.10`

* First octet = 172 → **Class B**
* Default mask = `255.255.0.0`

**Network ID**

```
172.16.0.0
```

**Broadcast Address**

```
172.16.255.255
```

**Host Range**

```
172.16.0.1 – 172.16.255.254
```

---

## ✅ Answer 3

**IP:** `192.168.5.200`

* First octet = 192 → **Class C**
* Default mask = `255.255.255.0`

**Network ID**

```
192.168.5.0
```

**Broadcast Address**

```
192.168.5.255
```

**Host Range**

```
192.168.5.1 – 192.168.5.254
```

---

## ✅ Answer 4

**IP:** `200.10.20.30`

* First octet = 200 → **Class C**

**Network ID**

```
200.10.20.0
```

**Broadcast Address**

```
200.10.20.255
```

**Host Range**

```
200.10.20.1 – 200.10.20.254
```

---

## ✅ Answer 5

**IP:** `230.5.6.7`

* First octet = 230 → **Class D**

❌ Network ID → Not applicable
❌ Host range → Not applicable
❌ Broadcast address → Not applicable

✔ Used as **multicast group address**

---

## ✅ Answer 6

**IP:** `250.10.20.30`

* First octet = 250 → **Class E**

❌ Network ID → Not defined
❌ Host range → Not defined
❌ Broadcast address → Not defined

✔ Reserved / Experimental

---

# 🧠 10-SECOND EXAM SHORTCUT (VERY IMPORTANT)

| First Octet | Class | Network Ends With |
| ----------- | ----- | ----------------- |
| 1–126       | A     | `.0.0.0`          |
| 128–191     | B     | `.0.0`            |
| 192–223     | C     | `.0`              |
| 224–239     | D     | ❌                 |
| 240–255     | E     | ❌                 |
