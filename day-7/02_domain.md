## 1️⃣ What is a *Domain* in Networking?

A **domain** (technically called an **Autonomous System – AS**) is:

> A group of networks and routers **managed by one organization** and following **one routing policy**.

### Examples:

* A university network
* An ISP network
* A company’s private network

Each domain (AS) has:

* One administrative control
* One routing policy

---

## 2️⃣ Intra-domain Routing

### 🔹 Definition

**Intra-domain routing** is routing **within a single domain (AS)**.

📌 Routers inside the same organization.

---

### 🔹 Real-world analogy 🏢

Inside **one company building**:

* You move between departments
* Same management
* Same internal rules

---

### 🔹 Characteristics

* Focus on **efficiency**
* Chooses **shortest / fastest path**
* Uses metrics like:

  * Hop count
  * Bandwidth
  * Delay

---

### 🔹 Protocols used (IGP)

* RIP
* OSPF
* IS-IS

These are called **Interior Gateway Protocols**.

---

### 🔹 Example

University routers routing packets:

* Host → lab → server
  All within university network.

---

## 3️⃣ Inter-domain Routing

### 🔹 Definition

**Inter-domain routing** is routing **between different domains (ASs)**.

📌 Routers of **different organizations**.

---

### 🔹 Real-world analogy 🌍

Shipping between **different countries**:

* Each country has its own rules
* You must follow agreements

---

### 🔹 Characteristics

* Focus on **policy**, not just shortest path
* Path chosen based on:

  * Business agreements
  * Security
  * Cost

---

### 🔹 Protocol used (EGP)

* **BGP (Border Gateway Protocol)**

📌 BGP is the **only inter-domain routing protocol** on the Internet.

---

### 🔹 Example

* Your ISP → Google ISP → Google server
  Multiple autonomous systems involved.

---

## 4️⃣ Intra-domain vs Inter-domain (EXAM TABLE)

| Feature        | Intra-domain        | Inter-domain           |
| -------------- | ------------------- | ---------------------- |
| Scope          | Within one AS       | Between multiple ASs   |
| Control        | Single organization | Multiple organizations |
| Focus          | Performance         | Policy                 |
| Protocol type  | IGP                 | EGP                    |
| Examples       | RIP, OSPF           | BGP                    |
| Routing metric | Hop, cost           | AS path, policies      |

---

## 5️⃣ How they work together (IMPORTANT)

When you open a website:

1. **Intra-domain routing** sends packet to ISP border router
2. **Inter-domain routing (BGP)** finds path across ISPs
3. **Intra-domain routing** inside destination network delivers packet

📌 Both are needed for the Internet to work.

---

## 🧠 One-line exam answers

### Intra-domain routing:

> Routing that takes place within a single autonomous system using IGPs like RIP and OSPF.

### Inter-domain routing:

> Routing that occurs between multiple autonomous systems using BGP and is based on routing policies.
