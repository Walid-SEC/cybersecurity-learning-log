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
