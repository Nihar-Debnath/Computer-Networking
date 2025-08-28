# 🟢 What is Subnetting (Super Simple)?

Subnetting = **Breaking a big road into smaller streets** so traffic is easier to manage.

* An **IP network** = a big road (all cars can drive everywhere, traffic jam happens).
* **Subnetting** = dividing that road into smaller streets (cars only drive where they should).

So, subnetting is just **splitting a large network into smaller mini-networks**.

---

# 🟢 Why do we need Subnetting?

1. **Avoid Waste**
   Imagine you own a colony with **1000 houses**, but one family only needs **10 houses**.
   → Without subnetting, you give them all 1000 = waste.
   → With subnetting, you cut only 10 and keep the rest for others.

2. **Organize Departments**
   In a company:

   * HR Dept gets one subnet
   * IT Dept gets another subnet
   * Finance gets another
     → Now, traffic is **separated & secure**.

3. **Better Performance**
   Without subnetting = all devices shout to everyone (“Who has printer?”).
   With subnetting = they only shout within their small group.

---

# 🟢 Real-World Example

Suppose you are given **192.168.1.0 – 192.168.1.255** (256 IPs).

* But you have 3 offices:

  * Office A = 100 computers
  * Office B = 50 computers
  * Office C = 25 computers

👉 Without subnetting:

* All 175 computers are in one big group (too noisy).
* Waste: You gave them 256 IPs, though only 175 are needed.

👉 With subnetting:

* Office A → gets 128 IPs
* Office B → gets 64 IPs
* Office C → gets 32 IPs
* Rest left unused → for future.

Now:

* Each office has its own “mini-network” (subnet).
* Less broadcast, more control.

---

# 🟢 Analogy

Think of a **school**:

* Without subnetting: All 1000 students are in one hall shouting = chaos.
* With subnetting: Students are divided into **Class 1, Class 2, Class 3…**
  → Easy to manage, less noise, teacher can control better.

---

✅ **So final one-liner:**
**Subnetting is dividing one big network into smaller, organized networks so IPs are not wasted, traffic is reduced, and security improves.**




---
---
---



The **“borrowing table”** (sometimes called **subnetting table**) is basically a **cheat sheet** that shows how many bits you borrow from the **host portion** of an IP address to create more **subnets**.

Let me explain this step by step:

---

# 🔹 1. First, Recall IP Address Parts

Every IP address has 2 parts:

* **Network part** (fixed)
* **Host part** (can be used for devices)

👉 Example: `192.168.1.0/24`

* `/24` → first 24 bits are for **network**
* Remaining 8 bits (last octet) → for **hosts**

So, without subnetting:

* Network = `192.168.1.0`
* Host bits = 8 → `2^8 – 2 = 254` usable hosts

---

# 🔹 2. What Does Borrowing Mean?

When we **subnet**, we “borrow” some **host bits** and use them as **network bits**.

* Borrowing bits → increases **number of subnets**
* But decreases **hosts per subnet**

⚖️ It’s a trade-off: More networks = Fewer hosts in each.

---

# 🔹 3. The Borrowing (Subnetting) Table

Here’s a **basic Class C (/24)** example (256 total IPs).

![imagetable](./images/3.png)

| Borrowed Bits | New Prefix | Subnets  | Hosts  |
| ------------- | ---------- | -------- | ------ |
| 0             | /24        | 1        | 254    |
| 1             | /25        | 2        | 126    |
| 2             | /26        | 4        | 62     |
| 3             | /27        | 8        | 30     |
| 4             | /28        | 16       | 14     |
| 5             | /29        | 32       | 6      |
| 6             | /30        | 64       | 2      |

📌 Notice:

* More borrowed bits → more subnets.
* But fewer hosts per subnet.

---

# 🔹 4. Real-World Example

Suppose you own `192.168.1.0/24` (256 IPs).

* You need **4 subnets**.

👉 Look at the table:

* Borrow **2 bits** → /26
* That gives **4 subnets**, each with 62 hosts.

Resulting networks:

* `192.168.1.0 – 192.168.1.63`
* `192.168.1.64 – 192.168.1.127`
* `192.168.1.128 – 192.168.1.191`
* `192.168.1.192 – 192.168.1.255`

Now you’ve got 4 neat networks instead of one giant mess.

---

# 🔹 5. Analogy (Borrowing in Real Life)

Imagine you have a **big classroom (256 chairs)**.

* If you don’t divide → everyone sits in one room (crowded).
* If you **borrow part of the chairs** and make walls (subnets),

  * 2 rooms of 126 chairs
  * or 4 rooms of 62 chairs
  * or 8 rooms of 30 chairs

👉 You "borrow chairs" from the big room to make smaller rooms.

---

✅ **So, the Borrowing Table = a guide that shows how many bits you take from the host part, what subnet mask you get, how many subnets you create, and how many hosts fit inside each subnet.**


