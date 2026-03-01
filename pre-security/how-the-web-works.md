# HTTP – HyperText Transfer Protocol

## Key Topics
- Application layer protocol for web communication  
- Client-server model  
- Request methods (GET, POST, PUT, DELETE, HEAD, OPTIONS)  
- Response status codes (200, 301, 400, 401, 403, 404, 500)  
- Headers & message body  

## Takeaways
- HTTP is **stateless**, each request is independent  
- HTTPS = HTTP + TLS, encrypted traffic  
- Understanding HTTP helps in web debugging, pentesting, and analyzing web apps  

## HTTP Requests
- **GET** → Retrieve data  
- **POST** → Send data to server  
- **PUT** → Replace data  
- **DELETE** → Remove data  
- **HEAD** → Retrieve headers only  
- **OPTIONS** → Check allowed methods  

## HTTP Responses
- **Status codes** indicate success, client errors, or server errors  
- **Headers** provide metadata (Content-Type, Cookies, Cache-Control)  
- **Body** contains actual content (HTML, JSON, etc.)  

---

# DNS – Domain Name System

## Key Topics
- Resolves domain names to IP addresses  
- Hierarchical & distributed system  
- Record types (A, AAAA, CNAME, MX, NS, TXT)  
- Recursive and iterative queries  

## Takeaways
- DNS is **essential for networking and security**  
- Misconfigurations can leak internal info  
- DNS knowledge is critical for recon in pentesting  

## DNS Records
- **A** → Maps domain to IPv4  
- **AAAA** → Maps domain to IPv6  
- **CNAME** → Alias for another domain  
- **MX** → Mail servers  
- **NS** → Name servers  
- **TXT** → Arbitrary text (SPF, verification, etc.)  

## DNS Query Process
- Client asks resolver (ISP or local)  
- Resolver checks cache  
- Resolver queries root → TLD → Authoritative server  
- Response returned to client 
- TTL controls caching 

# How a Website Works — Step by Step

When you type a URL into your browser, a lot happens behind the scenes:

1. You request a website e.g. `google.com`
2. Your PC checks its **local cache** for the IP address
3. If not cached, it asks your **recursive DNS server**
4. Recursive DNS queries a **root server** to find the authoritative DNS server
5. The **authoritative DNS server** returns the IP address
6. Request passes through a **Web Application Firewall (WAF)**
7. Request passes through a **load balancer**
8. Connects to the **web server** on port `80` (HTTP) or `443` (HTTPS)
9. Web server receives the **GET request**
11. Web application talks to the **database** if needed
12. Browser receives HTML/CSS/JS and **renders the webpage**


## Web Infrastructure

### CDN (Content Delivery Network)
- Hosts static files (JS, CSS, images, videos) across servers worldwide
- When a user requests a file, the CDN serves it from the **nearest server**
- Reduces load on the origin server and improves load times globally

### Databases
Web servers communicate with databases to store and retrieve data.

| Database   | Type           |
|------------|----------------|
| MySQL      | Relational (SQL)|
| MSSQL      | Relational (SQL)|
| PostgreSQL | Relational (SQL)|
| MongoDB    | Non-relational (NoSQL) |

### WAF (Web Application Firewall)
- Sits **between the user and the web server**
- Analyses requests for known attack patterns
- Checks if requests are coming from real browsers or bots
- Uses **rate limiting** to block excessive requests from a single IP
- If a request looks malicious → it gets **dropped** before reaching the server

### Load Balancer
- Distributes incoming traffic across multiple web servers
- Prevents any single server from being overwhelmed
- Improves availability and uptime

---


## Web Security Basics

### Exposed Credentials in Source Code
- Developers sometimes accidentally leave credentials in frontend code
- Use `Ctrl+U` to view page source or right-click → **Inspect Element**
- Look in HTML comments, JavaScript files, or config files loaded by the page
- Example of what to look for:
```html
<!-- dev login: admin / password123 -->
```
```javascript
const apiKey = "supersecretkey123"; // hardcoded — bad practice
```

### HTML Injection
- Occurs when user input is not sanitised and gets rendered as HTML
- Attackers inject HTML tags directly into input fields
- The server/browser reads it as part of the page

**Example payload:**
```html
Click here to claim your prize!
```

**Why it's dangerous:**
- Can redirect users to malicious sites (phishing)
- Can deface or modify what other users see on the page
- Gateway to more serious attacks like XSS (Cross-Site Scripting)

**Prevention:**
- Sanitise and escape all user input server-side
- Never trust data coming from the client

---

## Putting It All Together

> When you request a website, your computer uses **DNS** to find the server's IP address. Your browser then communicates with the web server using **HTTP/HTTPS**. The server may query a **database**, and the response passes back through the infrastructure (WAF, load balancer) before your browser receives **HTML, CSS, JS** and renders the page.

---

## Takeaways
- DNS translates domain names to IPs — know the record types and resolution flow
- HTTP is the language of the web — understand methods, status codes, and headers
- WAFs, CDNs, and load balancers are part of real-world web infrastructure
- Source code can leak sensitive info — always check it during recon
- Unsanitised input = HTML injection risk — never trust user input
