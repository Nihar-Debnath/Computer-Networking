# ⚡ **Types of Cables in Computer Networks**

At the **Physical Layer**, data travels as **signals (electrical, light, or electromagnetic)** through physical media.
The 3 main **guided (wired)** transmission media are:

1. 🧵 **Twisted Pair Cable**
2. 📺 **Coaxial Cable**
3. 💡 **Fiber Optic Cable**

---

# 🧵 1️⃣ **Twisted Pair Cable**

---

### 🔹 **Structure:**

* Consists of **two copper wires** twisted around each other.
* One wire carries the signal, and the other is a **ground/reference**.
* Twisting reduces **electromagnetic interference (EMI)** and **crosstalk**.

```
  [==== Twisted Pair Cable ====]
   (Wire A) ~~~~~~~~
   (Wire B) ~~~~~~~~
```

---

### 🔹 **Types of Twisted Pair:**

There are **two main types** 👇

| Type                              | Shielding                      | Example           | Use Case                   |
| --------------------------------- | ------------------------------ | ----------------- | -------------------------- |
| **UTP (Unshielded Twisted Pair)** | No extra shielding             | Cat5, Cat6 cables | LAN, home Ethernet         |
| **STP (Shielded Twisted Pair)**   | Foil or braid around each pair | IBM Type 1 cable  | Industrial/EMI-prone areas |

---

### 🔹 **Categories of UTP Cables:**

| **Category** | **Speed**       | **Bandwidth** | **Use**                |
| ------------ | --------------- | ------------- | ---------------------- |
| Cat3         | 10 Mbps         | 16 MHz        | Old telephone networks |
| Cat5         | 100 Mbps        | 100 MHz       | Basic LANs             |
| Cat5e        | 1 Gbps          | 100 MHz       | Modern LANs            |
| Cat6         | 10 Gbps (short) | 250 MHz       | Data centers           |
| Cat6a / Cat7 | 10 Gbps         | 500+ MHz      | High-speed networks    |

---

### 🔹 **Connector:**

* Uses **RJ45 connectors** (Registered Jack)

```
[ PC ] ——(RJ45 Plug)====(UTP Cable)====(RJ45 Plug)——[ Switch ]
```

---

### 🔹 **Advantages:**

✅ Cheap and easy to install
✅ Lightweight and flexible
✅ Commonly used in LANs

### 🔹 **Disadvantages:**

❌ Limited distance (up to 100 meters)
❌ Prone to noise and interference over long runs

---

### 🔹 **Typical Use:**

* Ethernet networks in homes/offices
* Telephone systems

---

# 📺 2️⃣ **Coaxial Cable**

---

### 🔹 **Structure:**

A **single copper conductor** in the center, surrounded by:

* **Insulating layer**
* **Metallic shield (braided mesh)**
* **Outer plastic cover**

```
|==== Coaxial Cable ====|
| Outer Insulation      |
| Braided Shield        |
| Dielectric Insulator  |
| Center Copper Wire    |
```

So the signal travels in the **center wire**, while the shield prevents **external noise**.

---

### 🔹 **Types of Coaxial Cables:**

| Type         | Impedance | Use                              |
| ------------ | --------- | -------------------------------- |
| RG-6         | 75 Ω      | Cable TV, CCTV, Internet         |
| RG-59        | 75 Ω      | Short distance CCTV              |
| RG-11        | 75 Ω      | Long-distance TV signal          |
| RG-8 / RG-58 | 50 Ω      | Ethernet (older 10Base5/10Base2) |

---

### 🔹 **Connectors:**

* Common connectors: **BNC**, **F-type**, **N-type**

```
[ Modem ]—(BNC Plug)===(Coaxial Cable)===(BNC Plug)—[ TV/Router ]
```

---

### 🔹 **Advantages:**

✅ Less noise/interference than UTP
✅ Higher bandwidth and longer distance
✅ Durable

### 🔹 **Disadvantages:**

❌ Thicker, harder to install
❌ More expensive than twisted pair
❌ Mostly replaced by fiber for high-speed use

---

### 🔹 **Typical Use:**

* Cable TV connections
* CCTV and broadband Internet
* Old Ethernet (10Base2, 10Base5)

---

# 💡 3️⃣ **Fiber Optic Cable**

---

### 🔹 **Structure:**

Transmits data as **light signals** instead of electrical signals.

It has:

1. **Core** – Thin glass fiber where light travels
2. **Cladding** – Reflects light back into the core
3. **Buffer coating** – Protective outer layer

```
   [==== Fiber Optic Cable ====]
   | Outer Jacket |
   | Cladding     |
   | Core (light path) |
```

---

### 🔹 **Working Principle:**

Uses **Total Internal Reflection (TIR)** to keep light bouncing inside the core.

💡 Light pulse ON = bit 1
💡 Light pulse OFF = bit 0

---

### 🔹 **Types of Fiber Optic Cables:**

| **Type**                    | **Core Diameter** | **Light Source** | **Distance** | **Use**                    |
| --------------------------- | ----------------- | ---------------- | ------------ | -------------------------- |
| **Single-Mode Fiber (SMF)** | ~9 µm             | Laser            | Up to 100 km | Long-distance WAN, telecom |
| **Multi-Mode Fiber (MMF)**  | 50–62.5 µm        | LED              | Up to 2 km   | LAN, data centers          |

---

### 🔹 **Connectors:**

* Common ones: **SC**, **ST**, **LC**, **FC**

```
[ Switch ]—(LC Plug)===(Fiber Cable)===(LC Plug)—[ Router ]
```

---

### 🔹 **Advantages:**

✅ Extremely high bandwidth (Tbps range)
✅ Very long distance (up to 100 km)
✅ Immune to electromagnetic interference
✅ Very secure (difficult to tap)

### 🔹 **Disadvantages:**

❌ Expensive
❌ Fragile (glass core)
❌ Complex installation and repair

---

### 🔹 **Typical Use:**

* Backbone of ISPs, data centers, telecom networks
* High-speed WAN and 5G infrastructure

---

# 🧮 **Comparison Table**

| Feature          | **Twisted Pair** | **Coaxial**        | **Fiber Optic**        |
| ---------------- | ---------------- | ------------------ | ---------------------- |
| **Signal Type**  | Electrical       | Electrical         | Light                  |
| **Speed**        | Up to 10 Gbps    | Up to 1 Gbps       | Up to Tbps             |
| **Distance**     | ≤ 100 m          | Up to 500 m        | Up to 100 km           |
| **Interference** | High             | Moderate           | None                   |
| **Cost**         | Low              | Medium             | High                   |
| **Durability**   | Moderate         | Good               | Excellent              |
| **Used In**      | LANs, Ethernet   | TV, CCTV, Internet | Backbone, WAN, Telecom |
| **Connector**    | RJ45             | BNC/F-type         | SC/ST/LC               |

---

# 🔍 **Real-Life Analogy**

| Cable Type            | Analogy          | Explanation                                   |
| --------------------- | ---------------- | --------------------------------------------- |
| **Twisted Pair**      | Small local road | Great for short distances, simple and cheap   |
| **Coaxial Cable**     | City highway     | Handles heavier traffic, moderate distance    |
| **Fiber Optic Cable** | Super expressway | Very fast, very long distances, high capacity |

---

# 💡 Summary Visualization

```
            [Twisted Pair]
PC ----(RJ45)====(Switch)====(Router)
          Short distance LAN

           [Coaxial Cable]
TV ==== (BNC Cable) ==== (Modem)
          Medium distance

           [Fiber Optic Cable]
ISP ==== (Fiber) ==== (Data Center)
          Long distance backbone
```

---

✅ **In short:**

* **Twisted Pair** → Cheap, short-range, used in LAN
* **Coaxial** → Medium-range, used in TV/CCTV
* **Fiber Optic** → Long-range, very high-speed, used in WAN/backbone