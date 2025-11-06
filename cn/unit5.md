# Domain Name System (DNS)

## 🔹 Definition
DNS (Domain Name System) is a **distributed database** that maps human-friendly domain names (e.g., `www.google.com`) to machine-friendly IP addresses (e.g., `142.250.190.14`).  
It converts **names → numbers**.

---

## 🔹 Purpose
- Humans remember **names**
- Computers communicate using **IP addresses**
- DNS acts like the **phonebook of the Internet**

---

## 🔹 Working of DNS

1. User enters a URL in the browser.
2. Browser calls the **Resolver**.
3. Resolver queries the **Local DNS Server**.
4. If not found:
   - Local DNS contacts **Root Server**
   - Then **TLD Server**
   - Then **Authoritative DNS Server**
5. Authoritative server returns the **IP address**.
6. Local DNS caches the result.
7. Browser connects to the server using the returned IP.

### 🔁 Flow Diagram
Client → Resolver → Local DNS Server → Root Server → TLD Server → Authoritative Server → Client (IP Returned)
---

## 🔹 DNS Namespace (Hierarchy)

          (Root)
             |
           TLD (.com, .in)
             |
       Second Level (google, nitk)
             |
       Subdomain (www, mail)

### 🏷 Types of Top-Level Domains (TLDs)

| Type | Examples | Meaning |
|------|----------|---------|
| Generic TLD (gTLD) | .com , .org , .net , .edu | Global usage |
| Country Code TLD (ccTLD) | .in , .us , .uk | Country-specific |

**Managed by:** ICANN (Internet Corporation for Assigned Names and Numbers)

---

## 🔗 Delegation (Who controls what?)
| Domain Part | Managed By |
|------------|------------|
| `.in` | NIXI (India) |
| `ac.in` | Academic Registry |
| `nitk.ac.in` | NITK Server |

---

## 📄 DNS Resource Records (RR)

Every DNS entry has **5 fields**:

| Field | Meaning | Example |
|------|---------|---------|
| Name | Domain Name | www.nitk.ac.in |
| TTL | Cache time | 3600s |
| Class | Usually `IN` (Internet) | IN |
| Type | Record type (A, MX, CNAME, etc.) | A |
| Value | Actual data (IP, server name, etc.) | 14.139.155.13 |

### Record Types

| Type | Meaning | Example | Explanation |
|------|---------|---------|-------------|
| A | Domain → IPv4 | `www.nitk.ac.in → 14.139.155.13` | Like name → phone number |
| AAAA | Domain → IPv6 | `google.com → 2606:4700:4700::1111` | Same as A but IPv6 |
| NS | Name Server | `nitk.ac.in → ns1.nitk.ac.in` | Shows who manages DNS |
| MX | Mail Server | `nitk.ac.in → mail.nitk.ac.in` | Where to deliver emails |
| CNAME | Alias (Nickname) | `www → nitk.ac.in` | Points one name to another |
| PTR | Reverse Lookup | `14.139.155.13 → www.nitk.ac.in` | IP → Name |

---

## 🔄 Reverse Lookup
Used to find **hostname from IP** using `PTR` records.  
Example: `14.190.250.142.in-addr.arpa`

---

## 🔌 Ports and Protocols
| Use | Protocol | Port |
|-----|----------|------|
| DNS Queries | UDP | **53** |
| Zone Transfers | TCP | **53** |

---

## ✅ Example
User Types: www.nitk.ac.in

DNS Resolves: 14.139.155.13
Browser Connects → Website Opens ✅

---
# Electronic Mail (E-Mail)

## 🔹 Definition
E-mail is a service that allows users to **send and receive messages** (text, image, audio, video) over the Internet.

---

## 🔹 Architecture

### 1. **User Agents (UA)**
- Applications used to compose, read, and manage emails.
- Examples: **Gmail**, **Outlook**, **Thunderbird**

### 2. **Message Transfer Agents (MTA)**
- Responsible for **sending and transferring** messages between mail servers.
- Example: **Sendmail**, **Postfix**

---

## 🔹 Mail Flow Process
Sender UA → Sender MTA → Internet → Receiver MTA → Receiver UA

---

## 🔹 Protocols Used

| Purpose | Protocol | Port |
|--------|----------|------|
| Sending Email | **SMTP** (Simple Mail Transfer Protocol) | **25** (server-to-server), **587** (mail submission) |
| Receiving Email (download and delete) | **POP3** (Post Office Protocol v3) | **110** |
| Receiving Email + folder management (keeps mail on server) | **IMAP** (Internet Message Access Protocol) | **143** |

---

## 🔹 Message Format

### **1. Header**
Contains control information:
- To
- From
- Date
- Subject
- Message-ID
- Content-Type

### **2. Body**
- The **actual content** of the email.

### **MIME (Multipurpose Internet Mail Extensions)**
Allows emails to include:
- Images
- Audio
- Video
- PDF / DOC files  
*(i.e., attachments & multimedia content)*

---

## 🔹 Working Steps

1. User composes message in **User Agent (UA)**.
2. UA sends message to **SMTP Server (Sender MTA)**.
3. SMTP transfers message through the **Internet** to Receiver's **Mail Server (Receiver MTA)**.
4. Receiver uses **POP3** or **IMAP** via UA to read message.

---

## 🔹 Diagram (Flow)
Alice (UA) → SMTP Server → Internet → Bob's Mail Server (MTA) → Bob's UA (IMAP/POP3)

---

## 🧠 Quick Revision

| Concept | Meaning |
|--------|---------|
| **SMTP** | Used for **sending** mails |
| **POP3** | Used for **downloading** mails (removes from server) |
| **IMAP** | Used for **reading** mails while keeping them stored on server |
| **MIME** | Enables **attachments** and multimedia content in emails |

---

