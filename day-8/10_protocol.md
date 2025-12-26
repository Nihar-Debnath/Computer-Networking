# 🌐 Application Layer Protocols

## HTTP, FTP, SMTP, POP (POP3)

---

## 1️⃣ HTTP – HyperText Transfer Protocol

---

### 🔹 What is HTTP?

> **HTTP is an Application Layer protocol used to transfer web pages and web data between a client and a server.**

It is the **foundation of the World Wide Web**.

---

### 🔹 Why HTTP is needed

When you open a website:

* Browser needs a rule to **request data**
* Server needs a rule to **respond**

👉 HTTP defines these rules.

---

### 🔹 How HTTP works (step-by-step)

Example: Opening `http://example.com`

1️⃣ Browser sends HTTP request:

```
GET /index.html HTTP/1.1
Host: example.com
```

2️⃣ Server processes request

3️⃣ Server sends HTTP response:

```
HTTP/1.1 200 OK
Content-Type: text/html

<html>...</html>
```

4️⃣ Browser displays webpage

---

### 🔹 Key characteristics of HTTP

* **Stateless**
  Server does not remember previous requests
* **Request–Response protocol**
* Uses **TCP**
* Plain text (❌ not secure)

---

### 🔹 Port number

```
HTTP → Port 80
```

---

### 🔹 Real-world example

* Websites
* Blogs
* News portals

---

### 🔹 Exam points

* Stateless protocol
* Application Layer
* Uses TCP
* Port 80

---

## 2️⃣ FTP – File Transfer Protocol

---

### 🔹 What is FTP?

> **FTP is an Application Layer protocol used to transfer files between a client and a server.**

Used for:

* Uploading files
* Downloading files

---

### 🔹 Why FTP is special

FTP uses **two separate connections**.

---

### 🔹 FTP working (step-by-step)

1️⃣ Control connection (commands)

```
Port 21
```

Commands:

```
USER
PASS
LIST
GET
PUT
```

2️⃣ Data connection (file transfer)

```
Port 20
```

Actual file data flows here.

---

### 🔹 FTP architecture

* Client–Server model
* Requires login (username/password)

---

### 🔹 Why FTP is insecure

* Credentials sent in **plain text**
* Data not encrypted

---

### 🔹 Port numbers

```
FTP Control → 21
FTP Data → 20
```

---

### 🔹 Real-world example

* Legacy file servers
* Old web hosting uploads

---

### 🔹 Exam points

* Uses TCP
* Two connections
* Insecure protocol

---

## 3️⃣ SMTP – Simple Mail Transfer Protocol

---

### 🔹 What is SMTP?

> **SMTP is an Application Layer protocol used for sending emails.**

Important:

> SMTP is used for **sending**, not receiving emails.

---

### 🔹 Why SMTP is needed

Email delivery requires:

* Reliable transfer
* Server-to-server communication

SMTP defines:

* How mail servers talk to each other

---

### 🔹 SMTP working (step-by-step)

Example: Sending an email

1️⃣ Mail client connects to SMTP server
2️⃣ SMTP server contacts recipient’s mail server
3️⃣ Email is transferred

SMTP uses **push mechanism**.

---

### 🔹 SMTP commands

```
HELO
MAIL FROM
RCPT TO
DATA
QUIT
```

---

### 🔹 Port numbers

```
SMTP → 25 (traditional)
SMTP Secure → 587
```

---

### 🔹 Real-world example

* Gmail sending email
* Outlook sending email

---

### 🔹 Exam points

* Used only for sending emails
* Push protocol
* Uses TCP

---

## 4️⃣ POP (POP3) – Post Office Protocol v3

---

### 🔹 What is POP3?

> **POP3 is an Application Layer protocol used for receiving emails from a mail server.**

---

### 🔹 Why POP3 is needed

After email is sent using SMTP:

* Receiver needs a way to **download emails**

POP3 solves this.

---

### 🔹 POP3 working (step-by-step)

1️⃣ Client connects to POP3 server
2️⃣ Emails are downloaded
3️⃣ Emails are deleted from server (by default)

---

### 🔹 POP3 behavior

* Emails stored **locally**
* Server inbox becomes empty
* Not good for multiple devices

---

### 🔹 Port numbers

```
POP3 → 110
POP3 Secure → 995
```

---

### 🔹 Real-world example

* Old email clients
* Offline email reading

---

### 🔹 Exam points

* Receive emails
* Download-and-delete model
* Simple protocol

---

## 🔥 SMTP + POP3 (Together)

| Protocol | Purpose       |
| -------- | ------------- |
| SMTP     | Send email    |
| POP3     | Receive email |

👉 **SMTP pushes**, **POP3 pulls**

---

## 📊 Comparison Table (EXAM GOLD ⭐)

| Feature           | HTTP             | FTP           | SMTP       | POP3          |
| ----------------- | ---------------- | ------------- | ---------- | ------------- |
| Purpose           | Web pages        | File transfer | Send email | Receive email |
| Uses TCP          | ✔                | ✔             | ✔          | ✔             |
| Secure by default | ❌                | ❌             | ❌          | ❌             |
| Port              | 80               | 21 / 20       | 25 / 587   | 110 / 995     |
| Model             | Request–Response | Client–Server | Push       | Pull          |
| Stateful          | No               | Yes           | Yes        | Yes           |

---

## 🧠 Easy memory tricks

* 🌍 **HTTP** → Website
* 📂 **FTP** → Files
* 📤 **SMTP** → Send Mail
* 📥 **POP3** → Pull Mail

---

## ✍️ Exam-ready definitions

* **HTTP**: Protocol for transferring web resources.
* **FTP**: Protocol for transferring files between systems.
* **SMTP**: Protocol for sending electronic mail.
* **POP3**: Protocol for receiving electronic mail.

---

## 🔚 One-line summary

> **HTTP handles web communication, FTP handles file transfer, SMTP sends emails, and POP3 retrieves emails — all operating at the Application Layer.**
