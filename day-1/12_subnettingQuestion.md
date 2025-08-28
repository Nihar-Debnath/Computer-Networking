# Question (written exactly)

Design a network with **3 networks**: **Marketing**, **Sales**, **Management**

* Marketing requires **60** computers
* Sales requires **100** computers
* Management requires **34** computers

---

# What the question asks (plain English)

You must take one address block (a Class-C network is implied) and **divide it** so each department gets its own subnet that can hold its required number of hosts. The goal is to assign subnets efficiently so there is **no/least wasted addresses**. This is exactly what **VLSM (Variable Length Subnet Masking)** is for: give bigger subnets where you need many hosts and smaller subnets where you need fewer, rather than forcing all groups to use the same fixed-size subnet.

Assumption I’ll use (common for such problems): **base network = 192.168.1.0/24** (a Class-C private block). If your instructor gave a different base network, replace the base and apply the same technique.

---

# Quick VLSM reminder

* **VLSM** = allocate different subnet sizes inside one major network.
* Method: sort groups by **largest requirement first**, pick the smallest CIDR that fits that requirement (`2^h − 2 ≥ required hosts`), allocate that block, then continue with the remaining address space.

---

# Step-by-step solution (largest → smallest)

### Step 1: Understand the requirement

We need **3 subnets** inside one Class C network (`192.168.1.0/24` = 256 IPs total):

* Sales → 100 hosts
* Marketing → 60 hosts
* Management → 34 hosts

---

### Step 2: Find subnet sizes

Subnet sizes always come in powers of 2, minus 2 (for Network ID + Broadcast).

Formula:

$$
\text{Usable Hosts} = 2^{\text{host bits}} - 2
$$

* **Sales (100 hosts)**

  * Needs ≥100 usable.
  * $2^7 - 2 = 126$ → fits.
  * So host bits = 7 → prefix = 32 − 7 = `/25`
  * Block size = 128 addresses.

* **Marketing (60 hosts)**

  * Needs ≥60 usable.
  * $2^6 - 2 = 62$ → fits.
  * So prefix = `/26`
  * Block size = 64 addresses.

* **Management (34 hosts)**

  * Needs ≥34 usable.
  * $2^5 - 2 = 30$ → too small.
  * So we go with 6 host bits again → `/26`
  * Block size = 64 addresses.

So:

* Sales → `/25` (128 addresses)
* Marketing → `/26` (64 addresses)
* Management → `/26` (64 addresses)

---

### Step 3: Allocate subnets (largest first to avoid overlap)

Start with the `/24` (192.168.1.0 – 192.168.1.255).

1. **Sales** → `/25` → block size 128 → first range = `192.168.1.0 – 192.168.1.127`

   * Network ID = `192.168.1.0`
   * Broadcast = `192.168.1.127`

2. **Marketing** → next `/26` → block size 64 → `192.168.1.128 – 192.168.1.191`

   * Network ID = `192.168.1.128`
   * Broadcast = `192.168.1.191`

3. **Management** → next `/26` → `192.168.1.192 – 192.168.1.255`

   * Network ID = `192.168.1.192`
   * Broadcast = `192.168.1.255`

---

✅ That’s how the solution came.
The “borrowing” idea is hidden in Step 2 → when we reduced the host bits (borrowed some for network).
