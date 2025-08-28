### **Network & Internet Overview**  

A **network** is a group of interconnected devices (computers, servers, routers, etc.) that communicate to share data. Networks can be **local** (LAN) or **wide-area** (WAN).  

The **Internet** is a massive global network of networks, connecting billions of devices worldwide using standardized communication protocols like **TCP/IP**.  

### **How It's Built**  
1. **Physical Infrastructure** – Fiber optic cables, satellites, cell towers, and routers form the backbone.  
2. **Protocols & Standards** – TCP/IP, DNS, HTTP, and BGP ensure structured communication.  
3. **Data Centers & Servers** – Store and manage websites, apps, and services.  
4. **ISPs (Internet Service Providers)** – Provide internet access to users and businesses.  

### **How It Works**  
- Devices send **data packets** using TCP/IP.  
- Packets travel through routers and switches to reach the destination.  
- DNS (Domain Name System) translates human-readable URLs into IP addresses.  
- Web content is retrieved from servers and displayed on browsers.  


---

### **Types of Networks: LAN, MAN, WAN**  

1. **LAN (Local Area Network)**  
   - Covers a small area like a home, office, or school.  
   - Uses Ethernet cables, Wi-Fi, and switches to connect devices.  
   - High-speed, low latency.  
   - Example: Home Wi-Fi, Office Network.  

2. **MAN (Metropolitan Area Network)**  
   - Covers a city or large campus.  
   - Connects multiple LANs using fiber optic cables.  
   - Medium speed, moderate latency.  
   - Example: City-wide Wi-Fi, ISP networks in a city.  

3. **WAN (Wide Area Network)**  
   - Covers large geographical areas (countries, continents).  
   - Uses satellites, fiber optics, and undersea cables.  
   - Slower than LAN due to long-distance communication.  
   - Example: The Internet, corporate networks connecting offices worldwide.  

---

### **How We Get Internet & Load a Website**  

1. **Connecting to an ISP (Internet Service Provider)**  
   - Your device connects to an ISP (Airtel, Jio, Comcast, etc.) via fiber, DSL, or cellular networks.  
   - The ISP assigns an **IP address** to your device.  

2. **DNS Lookup (Translating URL to IP Address)**  
   - When you enter a website (e.g., `www.google.com`), your browser asks a **DNS server** to find the IP address of Google's server.  

3. **Routing Data via the Internet Backbone**  
   - Data packets travel through routers and switches across networks (LAN → MAN → WAN → Internet).  
   - Undersea fiber optic cables and satellites handle global traffic.  

4. **Reaching the Web Server**  
   - The request reaches Google’s **data center**, and the server processes it.  

5. **Loading the Webpage**  
   - The server sends back **HTML, CSS, JavaScript** files.  
   - The browser renders the website on your screen.  

### **Final Flow:**  
**Your Device → Router → ISP → DNS → Internet Backbone → Web Server → Your Device**  


---

### **IP Address (Internet Protocol Address)**  
An **IP address** is a unique numerical label assigned to every device connected to a network. It helps identify and locate devices for communication.  

#### **Types of IP Addresses:**  
1. **IPv4 (e.g., 192.168.1.1)** – 32-bit, supports ~4.3 billion addresses.  
2. **IPv6 (e.g., 2001:db8::ff00:42:8329)** – 128-bit, supports trillions of addresses.  

#### **Types Based on Use:**  
- **Public IP** – Assigned by ISPs; used on the internet.  
- **Private IP** – Used within a local network (e.g., 192.168.x.x).  
- **Static IP** – Fixed address for servers, businesses.  
- **Dynamic IP** – Changes over time, assigned by ISPs.  

---

### **Browser**  
A **browser** is a software application used to access the internet and view web pages. It interprets HTML, CSS, and JavaScript to display websites.  

#### **Examples of Browsers:**  
- Google Chrome  
- Mozilla Firefox  
- Microsoft Edge  
- Safari  

#### **How Browsers Work?**  
1. You type a website URL (`https://example.com`).  
2. The browser sends a **DNS request** to find the server’s IP.  
3. The browser establishes a **connection (TCP/IP, HTTPS)**.  
4. The server sends back **HTML, CSS, JavaScript** files.  
5. The browser renders the webpage.  

---

### **Client & Server**  

1. **Client**  
   - A **client** is a device (computer, phone) or application (browser) that requests services from a server.  
   - Example: Your browser when accessing `google.com`.  

2. **Server**  
   - A **server** is a powerful computer or software that processes client requests and sends responses.  
   - Example: Google’s web server hosting `www.google.com`.  

#### **Client-Server Interaction:**  
- **Client (Your Browser)** → Sends request → **Server (Website’s Data Center)**  
- **Server** → Processes request → Sends data back → **Client displays webpage**  

---

### **Real-World Example: How Client & Server Work**  

Let's say you visit **`https://example.com`** on your browser (client). Here’s what happens step by step:  

---

### **Step-by-Step Breakdown**  

1. **Client (Browser) Sends a Request**  
   - You enter `https://example.com` in the browser.  
   - The browser sends a **request** to the server hosting `example.com`.  

2. **DNS Resolves the Domain to an IP Address**  
   - The browser contacts a **DNS server** to get the IP address of `example.com`.  
   - Example: `example.com` → `93.184.216.34`.  

3. **Client Establishes a Connection with the Server**  
   - The browser uses **TCP/IP** and **HTTPS** to connect to the server.  
   - The client and server perform an **SSL/TLS handshake** (for secure communication).  

4. **Server Processes the Request**  
   - The server looks for the requested webpage.  
   - Example: If the client requests `/home`, the server checks if `/home` exists.  

5. **Server Sends a Response**  
   - The server sends back **HTML, CSS, JavaScript** files.  
   - Example:  
     ```html
     <!DOCTYPE html>
     <html>
     <head>
       <title>Example Page</title>
     </head>
     <body>
       <h1>Welcome to Example.com</h1>
     </body>
     </html>
     ```  

6. **Browser Renders the Webpage**  
   - The browser **parses HTML** and loads CSS & JavaScript.  
   - The final webpage is displayed to the user.  

---

### **Code Example: Simple Client-Server in Node.js**  

#### **Server (Backend) - Using Express.js**
```javascript
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("<h1>Welcome to My Server!</h1>");
});

app.listen(3000, () => {
  console.log("Server running on http://localhost:3000");
});
```
📌 **This creates a simple web server that sends an HTML response.**  

#### **Client (Frontend) - Fetching Data from Server**
```javascript
fetch("http://localhost:3000")
  .then(response => response.text())
  .then(data => console.log(data));
```
📌 **This client script fetches the response from the server and logs it.**  

---

### **Final Flow in the Example:**  
1️⃣ **Client (Browser)** sends a request to `http://localhost:3000`.  
2️⃣ **Server (Express.js)** receives the request and responds with HTML.  
3️⃣ **Client (Browser)** displays the HTML content.  
