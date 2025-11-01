# Computer Networking siu tốc

Một "cuốn sách" cho web dev học cực nhanh về mạng máy tính. Cho những ai muốn khởi động nhanh và bắt đầu làm luôn các sản phẩm *rất là ra gì* liên quan đến mạng máy tính.

> Lưu ý: Rất nhiều bài hướng dẫn về mạng máy tính được mình lấy từ Viblo và đăng lại trên trang này. Nguồn của từng bài viết sẽ được để ở đầu bài vậy nên nếu bạn là tác giả của bài viết và muốn gỡ bài ra khỏi trang này thì có thể [gửi Issue](https://github.com/thu-tram/cnst/issues) nha.

As a **web developer**, you don’t need to be a networking expert, but understanding **core networking concepts** will help you **debug faster**, **design better APIs**, **optimize performance**, and **collaborate with DevOps/SRE teams**.

Here’s a **practical, developer-focused** breakdown of the essentials:

## 1. **The OSI Model (Simplified)**

Think in layers — helps you locate where things go wrong.

Thực ra bạn chỉ cần đọc cái bảng ngắn gọn này là đủ, nếu muốn tìm hiểu thêm về OSI Model thì đọc [OSI Model in computer network - Mô hình OSI trong mạng máy tính](huong-dan/osi-model.md)

| Layer | Name | What You Care About |
|-------|------|---------------------|
| 7 | Application | HTTP, WebSockets, GraphQL |
| 6 | Presentation | SSL/TLS (encryption), data formats (JSON, XML) |
| 5 | Session | Managing connections (e.g. cookies, sessions) |
| 4 | Transport | **TCP vs UDP**, ports, reliability |
| 3 | Network | **IP addresses**, routing, subnets |
| 2 | Data Link | MAC addresses, local network (LAN) |
| 1 | Physical | Cables, Wi-Fi, switches |

Tập trung vào Layers 4–7.

## 2. **IP Addresses & DNS (Layer 3 + App)**

| Concept | Why It Matters |
|--------|----------------|
| **[IPv4 vs IPv6](huong-dan/ipv4-ipv6.md)** | `192.168.1.1` vs `2001:db8::1` — IPv6 is the future |
| **Public vs Private IP** | Your local dev machine: `192.168.x.x` (not reachable from internet) |
| **[DNS](huong-dan/dns.md)** | `google.com` → `142.250.190.14`. Use `nslookup` or `dig` to debug |
| **localhost / 127.0.0.1** | Your machine talking to itself |

**Tip**: Use `/etc/hosts` or `hosts` file to mock DNS locally.


## 3. **Ports & Protocols (Layer 4)**

| Port | Protocol | Use |
|------|----------|-----|
| 80 | HTTP | Unencrypted web |
| **443** | **HTTPS** | **Encrypted web (TLS)** (Đọc thêm: [HTTPS là gì? Giải thích chi tiết SSL/TLS bằng chuyện tình Chó và Mèo](huong-dan/https-ssl-tls.md))|
| 3000, 8080, 5000 | Custom | Your dev server |
| 22 | SSH | Remote server access |
| 3306 | MySQL | DB connections |
| 5432 | PostgreSQL | DB |

> **Firewall rule**: "Allow port 443" = allow HTTPS traffic

**Pro tip**: Never expose DB ports (3306) to the internet.

## 4. **HTTP(S) – The Web Developer’s Protocol (Layer 7)**

### Key Concepts:
- **[HTTP Request Và HTTP Response](huong-dan/http-request-response.md)**
- **[Các phương thức HTTP (Methods)](huong-dan/http-methods.md)**: `GET`, `POST`, `PUT`, `PATCH`, `DELETE`
- **Status Codes**:
  - `200` OK
  - `201` Created
  - `301` Moved Permanently
  - `400` Bad Request
  - `401` Unauthorized
  - `404` Not Found
  - `500` Server Error
  - `502` Bad Gateway (reverse proxy issue)
  - `504` Gateway Timeout
- **Headers**:
  - `Content-Type: application/json`
  - `Authorization: Bearer <token>`
  - `Cache-Control`, `ETag`, `CORS` headers

### HTTPS = HTTP + TLS
- Encrypts data in transit
- Required for secure cookies, modern APIs, browser trust

## 5. **TCP vs UDP**

Đọc [bài viết về TCP và UDP](huong-dan/tcp-udp.md)

| | TCP | UDP |
|---|-----|-----|
| Connection | Yes (3-way handshake) | No |
| Reliable | Yes (retransmits lost packets) | No |
| Order | Guaranteed | Not guaranteed |
| Use | HTTP, email, file transfer | Video streaming, DNS, gaming |

> **Web dev**: You’re 99% on **TCP** (HTTP/HTTPS)


## 6. **Client → Server Communication Flow**

```
Browser (Client)
     ↓ DNS lookup → IP
     ↓ TCP handshake (port 443)
     ↓ TLS handshake
     ↓ HTTP Request
     ↓ Server processes (Node.js, Django, etc.)
     ↓ HTTP Response
     ↓ Browser renders
```


## 7. **CORS (Cross-Origin Resource Sharing)**

**Problem**: Browser blocks `app.com` from fetching `api.com/data`

**Solution**: Server sends headers:

```http
Access-Control-Allow-Origin: https://app.com
Access-Control-Allow-Credentials: true
```

**Dev workaround**: Use proxy in `vite`, `webpack`, or `create-react-app`:

```js
// vite.config.js
server: { proxy: { '/api': 'http://localhost:5000' } }
```


## 8. **Load Balancers, Proxies & CDNs**

| Tool | Job |
|------|-----|
| **Reverse Proxy** (Nginx) | Routes traffic, terminates TLS |
| **Load Balancer** | Distributes traffic across servers |
| **CDN** (Cloudflare, Akamai) | Caches static assets globally |

> Your JS/CSS often served from `cdn.example.com`


## 9. **APIs & WebSockets**

| | REST | GraphQL | WebSocket |
|---|------|---------|----------|
| Protocol | HTTP | HTTP | WS/WSS |
| State | Stateless | Stateless | Stateful |
| Use | CRUD | Flexible queries | Real-time (chat, live updates) |


## 10. **Common Tools You Should Know**

```bash
# Check if server is up
ping google.com

# See IP of domain
nslookup api.example.com

# Test HTTP
curl -I https://api.example.com/users

# Test port connectivity
telnet localhost 3000
# or
nc -zv localhost 3000

# View full request/response
curl -v https://httpbin.org/get
```


## Quick Checklist for Web Devs

- Read HTTP status codes
- Understand CORS errors
- Use `curl` to test APIs
- Know why HTTPS is mandatory
- Debug DNS issues (`nslookup`)
- Set up local dev proxy
- Read network tab in DevTools
- Understand cookies & sessions
- Know when to use WebSockets


## Bonus: Real-World Debugging Example

> **Problem**: API works in Postman, fails in browser

**Likely cause**: CORS

**Fix**:

```js
// Express.js
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', 'http://localhost:3000');
  next();
});
```


## Summary: What to Master

| Topic | Priority |
|------|----------|
| HTTP/HTTPS & Status Codes | ⭐⭐⭐⭐⭐ |
| DNS & IP | ⭐⭐⭐⭐ |
| Ports & TCP | ⭐⭐⭐⭐ |
| CORS | ⭐⭐⭐⭐ |
| Proxies & CDNs | ⭐⭐⭐ |
| WebSockets | ⭐⭐ |


**Next Step**: Open DevTools → Network tab → reload your app → **understand every request**. You’ll learn more in 10 minutes there than hours of theory.