# 🌐 **Unicast, Broadcast & Multicast**

These are **types of data communication** methods used for sending data across networks.

---

# 🟢 **1️⃣ Unicast**

### **One-to-One communication**

Data is sent from **one sender** to **one specific receiver**.

```
Sender (A)  --->  Receiver (B)
```

💡 **Example**

* Opening a website page in a browser
* Sending an email to a single person
* WhatsApp personal chat

📍 **Real-life example**
You call one friend on their mobile phone → only they receive your voice.

✔️ Efficient for individual communication
❌ Not good when many users need the same data

---

# 🔵 **2️⃣ Broadcast**

### **One-to-All communication**

Data is sent from **one sender** to **all devices** in the same network.

```
Sender (A)  --->  Everyone in the network
```

💡 **Example**

* ARP Request in IPv4: “Who has this IP?”
* Sending announcements in local network
* Sharing information in LAN classrooms

📍 **Real-life example**
Speaking through a **loudspeaker** in a school assembly → everyone hears it.

✔️ Useful for mass delivery
❌ Wastes bandwidth (even those who don’t need data will receive it)
❌ Not supported on Internet (only LAN)

🖥 **Broadcast Address Example**

```
255.255.255.255  → Limited Broadcast
192.168.1.255    → Directed Broadcast
```

---

# 🟣 **3️⃣ Multicast**

### **One-to-Group communication**

Data is sent from **one sender** to **a selected group** of receivers.

```
Sender (A)  --->  Group of interested receivers (G1, G2, G3)
Not everyone in network receives it
```

💡 **Examples**

* Online live video streaming (YouTube Live classroom session)
* IPTV / Web TV
* Video conferencing (Zoom webinar)
* Multiplayer gaming

📍 **Real-life example**
Teacher speaking only to students who joined a special WhatsApp group.

✔️ Saves bandwidth
✔️ Best for group communication
❌ Complex to manage groups

🖥 **Multicast IP Range**

```
224.0.0.0 to 239.255.255.255
```

---

# ⚡ **Quick Comparison Table**

| Method        | Communication Type  | Who Receives Data           | Example             |
| ------------- | ------------------- | --------------------------- | ------------------- |
| **Unicast**   | One-to-One          | Specific single device      | Email to one person |
| **Broadcast** | One-to-All          | Every device in the network | ARP, Loudspeaker    |
| **Multicast** | One-to-Many (Group) | Group of selected users     | Live streaming      |

---

# ✨ Simple Visual Representation

```
UNCAST:
 A → B

BROADCAST:
 A → B, C, D, E, F (everyone)

MULTICAST:
 A → B, D, F (selected group)
```

---

# 🧠 Memory Trick

| Word      | Meaning         |
| --------- | --------------- |
| **Uni**   | one             |
| **Multi** | many            |
| **Broad** | wide / everyone |

---

# 🎯 Final Summary

> **Unicast** is single-target communication, **Broadcast** is everybody communication, and **Multicast** is selective group communication.
