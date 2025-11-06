# Application Layer

## 🔹 Definition
Top layer of OSI model that **provides services directly to the user** for network communication.

---

## 🔹 Role
- Interface between **user applications and network**.
- Supports web browsing, email, file transfer, remote login.

---

## 🔹 Main Protocols

| Protocol | Purpose |
|---------|---------|
| **HTTP / HTTPS** | Web browsing |
| **FTP** | File transfer |
| **SMTP** | Sending emails |
| **POP3 / IMAP** | Receiving emails |
| **DNS** | Domain name → IP address |

---

## 🔁 Example
User opens browser → HTTP/HTTPS is used to request and view webpages.

---

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
- Client → Resolver → Local DNS Server → Root Server → TLD Server → Authoritative Server → Client (IP Returned)
---

## 🔹 DNS Namespace (Hierarchy)
- Hierarchical tree structure of domains.

- Top Level Domains (TLDs):
• Generic (.com , .edu , .org , .net)
• Country (.in , .us , .uk)

- Managed by ICANN (Internet Corporation for Assigned Names and Numbers).

- Each subdomain delegates responsibility to lower domains.

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
![alt text](https://signaturesatori.com/wp-content/uploads/image-31.png.webp)

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

# World Wide Web (WWW)

## 🔹 Definition
The **World Wide Web (WWW)** is a system of **interlinked documents** (web pages) accessible over the Internet.  
Pages are connected using **hyperlinks** and identified using **URLs**, and accessed via web browsers.

---

## 🔹 Key Components

| Component | Role | Examples |
|----------|------|----------|
| **Web Browser** | Requests, interprets, and displays web pages | Chrome, Firefox, Edge |
| **Web Server** | Stores & serves web pages | Apache, Nginx, IIS |
| **HTTP/HTTPS** | Communication protocol for transferring web data | Port **80 / 443** |
| **HTML** | Formatting language for webpage content | Tags, text, images, links |

---

## 🔹 URL (Uniform Resource Locator)
Example URL:http://www.phdcomics.com/comics.php


| Part | Meaning |
|------|---------|
| **http** | Protocol |
| **www.phdcomics.com** | Server (Domain name) |
| **/comics.php** | Resource path (file/page) |

### Common URL Protocols
| Name | Used For | Example |
|------|---------|---------|
| **http** | Hypertext pages | `http://example.com` |
| **https** | Secure hypertext | `https://bank.com` |
| **ftp** | File transfer | `ftp://ftp.cs.vu.nl/README` |
| **file** | Local file access | `file:///C:/user/data` |
| **mailto** | Send email | `mailto:john@example.com` |
| **rtsp** | Streaming media | `rtsp://media.com/video.mpg` |
| **sip** | Internet calls | `sip:user@server.com` |
| **about** | Browser info pages | `about:plugins` |

---

## 🔹 How a Web Page is Accessed (Client Side Steps)

1. User enters a **URL** in the browser.
2. Browser determines **protocol** (e.g., HTTP).
3. Browser queries **DNS** to get the server’s **IP address**.
4. Browser opens a **TCP connection** with the server (Port **80** or **443**).
5. Browser sends an **HTTP GET request**.
6. Server sends back the **HTML page**.
7. Browser downloads additional resources (images, CSS, JS).
8. Browser **renders** the page for display.

---

## 🔹 How a Web Server Responds (Server Side Steps)

1. Accept **TCP connection** from browser.
2. Read the **requested page**.
3. **Check cache** (optional).
4. Fetch file from disk **or run script** (e.g., PHP).
5. Determine **content type** using **MIME types**.
6. Send **HTTP response** back to browser.
7. Write entry to **server log**.
8. Close idle TCP connection.

---

## 🔹 HTTP Protocol (HyperText Transfer Protocol)

| Feature | Description |
|--------|-------------|
| **Type** | Request-Response protocol (Client ⇄ Server) |
| **Transport** | Runs **on top of TCP** |
| **Default Port** | **80** (HTTP), **443** (HTTPS) |
| **Headers** | Human-readable **ASCII** text |
| **Content Types** | Identified using **MIME Types** |
| **Pipelining** | Can send **multiple requests** in same connection |
| **Caching** | Allows storing responses to reduce repeated server hits |

---

## 🔹 MIME Types (Content Identification Examples)
| MIME Type | Meaning |
|----------|---------|
| `text/html` | Web page |
| `image/png` | Image file |
| `video/mp4` | Video content |
| `application/pdf` | PDF document |

---
![alt text](https://image.slidesharecdn.com/presentation-140905091245-phpapp01/85/The-Application-Layer-31-320.jpg)
## 🔹 Cookies (Maintaining State in Web)
HTTP is **stateless**, meaning it does not remember users across requests.  
**Cookies** add memory/session support.

### How Cookies Work
1. Server sends cookie in **Set-Cookie** header.
2. Browser **stores** the cookie.
3. Browser sends cookie back with **future requests**.
4. Server identifies user (e.g., login session).

Used for:
- Login sessions
- User preferences
- Shopping carts

---

## 🧠 Revision Key Points

| Topic | Key Idea |
|-------|----------|
| **WWW** | Collection of interlinked web pages |
| **URL** | Identifies web resource |
| **HTTP** | Transfers web data (stateless) |
| **Browser** | Displays web pages |
| **Server** | Provides web content |
| **Cookies** | Maintain user session/state |

---

# **Streaming Audio and Video (Deep Notes)**

---

## ✅ **Overview**
Modern networks carry **audio, video, and interactive multimedia**.  
These media types require **high data rates**, **continuous playback**, and **low delay** → so networking and compression techniques are essential.

---

# **1) Digital Audio**

### 🎵 What is Audio Digitization?
Audio is originally **analog** (continuous sound wave).  
To store or transmit it, we convert to **digital (binary)** form.

### **Process**
1. **Microphone** converts sound → electrical signal.
2. **ADC (Analog-to-Digital Converter)** samples the signal.
3. Each sample is **quantized** into a binary number.
4. Stored / transmitted as digital audio.

### **Sampling**
- Number of samples taken per second.
- Example:
  - **44.1 kHz** (CD-quality audio)
  - **48 kHz** (Professional audio)

Higher sampling rate → more accurate sound reproduction.

### **Bit Depth**
- Number of bits per sample.
- **16-bit audio** provides 65,536 amplitude levels.
- Higher bit depth → lower quantization noise.

### **Quantization Noise**
- Difference between actual signal and recorded digital value.
- If bit depth is low → noise becomes audible.

---

## 🎧 **Audio Compression**

Audio files are **compressed** to reduce:
- Storage size
- Transmission bandwidth

### **Two Key Functions**
| Function | Meaning |
|---------|---------|
| **Encoding** | Compressing data at sender |
| **Decoding** | Decompressing at receiver |

### **Types of Compression**
| Type | Idea | Examples |
|------|------|----------|
| **Waveform Coding** | Uses frequency transforms (e.g., Fourier/DCT) | Older formats |
| **Perceptual Coding** | Uses psychoacoustics (removes inaudible sounds) | **MP3**, **AAC** |

Human ears do **not** hear all frequencies → unused frequencies are removed to reduce size.

---

# **2) Digital Video**

### 🎥 What is Video Digitization?
Video = **sequence of images (frames)** displayed rapidly (~ **25–60 fps**).

Each frame is made of **pixels**:
- **RGB** color model (3 values per pixel)
- or **YCbCr** (brightness + color difference)

### **Why Compression Is Needed**
Uncompressed HD video is **too large** for storage/transmission.

---

## 🎞 **Video Compression Workflow (JPEG / MPEG)**

### Step-by-Step (Core Pipeline)
1. **Convert RGB → YCbCr**
   - Human eye is more sensitive to brightness (Y) than color (Cb, Cr).
2. **Chrominance Subsampling**
   - Reduce resolution of Cb & Cr components.
3. **DCT (Discrete Cosine Transform)**
   - Converts 8×8 pixel blocks into frequency components.
4. **Quantization**
   - Remove small frequency components (lossy step).
5. **Run-Length Encoding + Huffman Encoding**
   - Compress repeated patterns efficiently.

---

## 🎬 MPEG Video Frame Types

| Frame Type | Meaning | Reduces Data By |
|-----------|---------|----------------|
| **I-Frame** | Full independent picture | No reference use (large) |
| **P-Frame** | Frame predicted from previous frames | Removes temporal redundancy |
| **B-Frame** | Uses both previous & next frames | Highest compression |

**Example:**I → B → B → P → B → B → P → B → B → I


---

# **3) Streaming Stored Media (Video-on-Demand)**

Used in **YouTube, Netflix, Prime Video**.

### How It Works:
- Video stored on a **media server**.
- User downloads + plays **simultaneously** (no need to wait fully).
- Uses **RTSP (Real-Time Streaming Protocol)** for controls:
  - **Play, Pause, Resume, Seek**

### Handling Network Problems:
| Strategy | Advantage | Disadvantage |
|---------|-----------|--------------|
| **TCP** | Reliable | High delay (jitter) |
| **FEC (Parity packets)** | Repairs losses | More overhead |
| **Interleaving** | Distributes losses | Complexity; delay increases |

### Buffering
Client maintains a **playback buffer** to absorb jitter:
Network → Buffer → Playback


---

# **4) Streaming Live Media**

Used in **Online TV, Live Events, Radio Broadcasts, YouTube Live**.

### Characteristics:
- Data is created and sent **in real-time**.
- Cannot download ahead → must be played as it arrives.
- Often uses **UDP** (fast but unreliable).

### Optimization:
- If multiple users watch the same stream →
  **Multicast** can send **one copy to many users** efficiently (if network supports it).

---

# **5) Real-Time Conferencing (VoIP / Video Calling)**

Used in **Zoom, Google Meet, Teams, Skype**.

### Required Protocols
| Purpose | Protocol |
|--------|----------|
| **Media Delivery (audio/video)** | **RTP (Real-time Transport Protocol)** |
| **Session Setup / Call Management** | **SIP or H.323** |

---

## 📞 SIP Signaling Methods (Call Control)

| Method | Meaning |
|--------|---------|
| **INVITE** | Start a call |
| **ACK** | Confirm call |
| **BYE** | End call |
| **CANCEL** | Cancel attempt |
| **OPTIONS** | Query server capabilities |
| **REGISTER** | Inform server of user’s address |

---

## 🆚 Comparison: **H.323 vs SIP**

| Item | **H.323** | **SIP** |
|------|-----------|---------|
| Designed By | ITU | IETF |
| Architecture | Monolithic | Modular |
| Setup Protocol | Q.931 over TCP | SIP over TCP/UDP |
| Message Format | Binary | ASCII (human-readable) |
| Multimedia Support | Yes | Yes |
| Addressing | Telephone style numbers | URLs (easy to integrate with web) |
| Complexity | Large, complex | Simple, flexible |
| Common Today? | Legacy systems | **Used in most modern apps** |

---

# 🧠 Final Revision Summary

| Topic | Key Idea |
|------|----------|
| Audio | ADC → Digital → Compression |
| Video | Frames → DCT → MPEG Frames (I,P,B) |
| Stored Streaming | RTSP + Buffering |
| Live Streaming | UDP + Multicast |
| Voice/Video Calls | SIP/H.323 for setup, RTP for media |

---

