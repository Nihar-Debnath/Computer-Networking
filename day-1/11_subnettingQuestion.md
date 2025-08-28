> **Q> Find the network id and broadcast if of this ip address: 192.168.225.212/27**


---

## 🟢 Step 1: Understand `/27`

* `/27` means subnet mask is **255.255.255.224**
* Last octet = `224`


### Block size (per subnet)

Block = 256 − 224 = **32**

---

## 🟢 Step 2: Find the subnet range

We look at the **last octet (212)** in decimal and see where it fits.
Block size = 32 → subnets go like:

```
0–31, 32–63, 64–95, 96–127, 128–159, 160–191, 192–223, 224–255
```

👉 `212` falls inside the range **192–223**.

---

## 🟢 Step 3: Network ID and Broadcast

* **Network ID** = first address of block = `192.168.225.192`
* **Broadcast ID** = last address of block = `192.168.225.223`

---

## 🟢 Step 4: Host range

* Usable hosts = between them → `192.168.225.193 – 192.168.225.222`

---

✅ **Final Answer**:

* **Network ID**: `192.168.225.192`
* **Broadcast ID**: `192.168.225.223`
* **Usable hosts**: `192.168.225.193 – 192.168.225.222`
