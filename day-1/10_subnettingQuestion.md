## 🟢 The Question 

> Requirements:
>
> 1. **Create 3 sub-networks**
> 2. **Use a Class-C IP address: 192.168.1.0**
> 3. **Determine the network ID and broadcast ID of all the subnets**

---

## 🟢 What This Means in Plain Words

* You are given **one big network**: `192.168.1.0` (this is a **Class C private IP**).
* Normally, this Class C network can have **256 addresses** (from `192.168.1.0` to `192.168.1.255`).

👉 But the company (or school, or lab, etc.) doesn’t want **one big network**.
They want to **divide it into 3 smaller groups** (called **subnets**).

Each subnet must have its own:

* **Network ID** → “the name of that subnet” (first address).
* **Broadcast ID** → “the loudspeaker address” (last address).

So, the question is basically:
💡 “Take 192.168.1.0 and cut it into 3 smaller networks. Then tell me the first address (network ID) and the last address (broadcast ID) of each subnet.”

---

## 🟢 Why This is Useful in Real Life?

Example:

* A college has 3 departments: **IT**, **Accounts**, **Library**.
* You don’t want their computers to be mixed up in the same network.
* So you split 192.168.1.0 into **3 subnets** (one per department).

---
---
---


Now let’s go through the **solution process slowly** so you see exactly how I solved it.


# 🟢 Step 1: Recall the given information

* Base network = **192.168.1.0** (Class C)
* Class C default subnet mask = **255.255.255.0** or `/24`
* Requirement = **3 subnets**

---

# 🟢 Step 2: Find how many bits we must borrow

We have to cut the big network into **3 parts**.
Subnetting works by “borrowing” bits from the host portion of the IP.

Formula: `2^n ≥ required subnets`

* For 3 subnets → borrow **2 bits** (because 2² = 4 ≥ 3).

So now, the network mask becomes:

* Default `/24` → after borrowing 2 → **/26**
* Subnet mask: `255.255.255.192`

---

# 🟢 Step 3: Find Block Size

Block size = `256 – 192 = 64`
👉 That means each subnet will cover **64 addresses**.

---

# 🟢 Step 4: Divide the network

We start from `192.168.1.0` and keep jumping in steps of **64**:

1. `192.168.1.0 – 192.168.1.63`

   * Network ID = `192.168.1.0`
   * Broadcast ID = `192.168.1.63`
   * Hosts = `192.168.1.1 – 192.168.1.62`

2. `192.168.1.64 – 192.168.1.127`

   * Network ID = `192.168.1.64`
   * Broadcast ID = `192.168.1.127`
   * Hosts = `192.168.1.65 – 192.168.1.126`

3. `192.168.1.128 – 192.168.1.191`

   * Network ID = `192.168.1.128`
   * Broadcast ID = `192.168.1.191`
   * Hosts = `192.168.1.129 – 192.168.1.190`

4. (extra, not needed but available)
   `192.168.1.192 – 192.168.1.255`

---

# 🟢 Step 5: Pick 3 Subnets

Since the question asked only **3**, we take the first three:

* Subnet 1 → `192.168.1.0/26` → Broadcast `192.168.1.63`
* Subnet 2 → `192.168.1.64/26` → Broadcast `192.168.1.127`
* Subnet 3 → `192.168.1.128/26` → Broadcast `192.168.1.191`

---

✅ **Final Result**:

* You successfully divided `192.168.1.0/24` into **3 subnets**.
* Each subnet has **62 usable host IPs**.

---
---
---
---

## 🟢 Step 4 explained in more details: Range calculation

Start at `192.168.1.0`, keep adding 64:

1. `192.168.1.0 – 192.168.1.63`

   * First address = Network ID (`192.168.1.0`)
   * Last address = Broadcast (`192.168.1.63`)
   * Hosts are between them (1–62)

2. Next block → `192.168.1.64 – 192.168.1.127`

   * Network ID = `192.168.1.64`
   * Broadcast = `192.168.1.127`
   * Hosts = (65–126)

3. Next block → `192.168.1.128 – 192.168.1.191`

   * Network ID = `192.168.1.128`
   * Broadcast = `192.168.1.191`
   * Hosts = (129–190)

4. Next block → `192.168.1.192 – 192.168.1.255`

   * Network ID = `192.168.1.192`
   * Broadcast = `192.168.1.255`
   * Hosts = (193–254)

---

## 🟢 Step 5: Why exactly those numbers?

Because the **broadcast address is always the last IP of the block**, and the **network ID is always the first IP of the block**.

Example:

* First block starts at `0`, block size = 64 → last = `63`.
* Second block starts at `64`, block size = 64 → last = `127`.
* Third block starts at `128`, block size = 64 → last = `191`.

And so on.