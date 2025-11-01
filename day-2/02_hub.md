## 🧠 What is a Hub?

A **Hub** is a **Physical Layer device (Layer 1)** used to **connect multiple computers (nodes)** in a **local area network (LAN)**.

> In simple words:
> A **hub** is like a **multi-port repeater** — it takes the signal from one computer and **broadcasts it to all the other connected computers**.

---

## ⚙️ Example Scenario

Imagine 4 computers connected to a **Hub**:

```
PC1 —|
PC2 —|--- HUB --- Network
PC3 —|
PC4 —|
```

If **PC1** sends data to **PC3**,
➡️ The **Hub** will forward that data to **ALL** the ports (PC2, PC3, PC4)
➡️ But **only PC3** will actually accept it; others will ignore it.

This is called **broadcast transmission**.

---

## 🧩 Characteristics of a Hub

| Feature               | Description                                                    |
| --------------------- | -------------------------------------------------------------- |
| **OSI Layer**         | Physical Layer (Layer 1)                                       |
| **Ports**             | Multiple (commonly 4, 8, 12, or 24)                            |
| **Device Type**       | Multi-port Repeater                                            |
| **Transmission Type** | Broadcasts data to all ports                                   |
| **Collision Domain**  | Single (all connected devices share the same collision domain) |
| **MAC Address Table** | ❌ No (Hub doesn’t understand MAC addresses)                    |
| **Bandwidth Sharing** | All devices share total bandwidth                              |
| **Speed**             | Usually 10 Mbps or 100 Mbps (half duplex)                      |

---

## 🧠 How Does a Hub Work? (Step-by-Step)

1. One device (say PC1) sends data into the hub.
2. The hub **receives the signal**.
3. The hub **amplifies and regenerates** the signal.
4. The hub **forwards (broadcasts)** that signal to **all other connected ports**.

💡 It does not know **which computer** the data is meant for — it just sends it everywhere.

---

## 🔌 Types of Hubs

| Type                | Description                                                                         |
| ------------------- | ----------------------------------------------------------------------------------- |
| **Active Hub**      | Has power; amplifies and regenerates signals before sending. Works like a repeater. |
| **Passive Hub**     | No amplification; only distributes the signal (acts like a connector).              |
| **Intelligent Hub** | Has some management features like traffic monitoring (rare, more advanced).         |

---

## 🏆 Advantages of Hub

✅ Simple to install and use
✅ Low cost
✅ Connects multiple devices in a network
✅ Extends network range (active hubs act as repeaters)

---

## ⚠️ Disadvantages of Hub

❌ Works only on **Physical Layer** – cannot understand data (no filtering or routing)
❌ **Broadcasts to all devices** – causes **unnecessary traffic**
❌ **Collisions** are frequent (since all devices share the same collision domain)
❌ **Inefficient** for large networks
❌ **Half-duplex** communication only (no simultaneous send/receive)

---

## 🆚 Hub vs Switch (for clarity)

| Feature                 | **Hub**                | **Switch**                           |
| ----------------------- | ---------------------- | ------------------------------------ |
| **OSI Layer**           | Physical (Layer 1)     | Data Link (Layer 2)                  |
| **Data Forwarding**     | Broadcast to all ports | Unicast (only to target MAC address) |
| **Collision Domain**    | One (shared)           | Each port has its own                |
| **Speed**               | Slower                 | Faster                               |
| **Intelligence**        | Dumb device            | Smart device                         |
| **Full Duplex Support** | ❌ No                   | ✅ Yes                                |

---

## 🏁 Summary

| Aspect                    | Details                                          |
| ------------------------- | ------------------------------------------------ |
| **Device Name**           | Hub                                              |
| **OSI Layer**             | Physical Layer (Layer 1)                         |
| **Purpose**               | Connects multiple devices and broadcasts signals |
| **Type of Communication** | Broadcast                                        |
| **Collision Domain**      | One                                              |
| **Example**               | 8-port Ethernet hub                              |
