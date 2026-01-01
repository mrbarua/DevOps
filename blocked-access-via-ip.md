Perfect — this is a **very common and good security requirement** 👍
You want:

> ✅ Your website works via **domain name**
> 🚫 Access via **public IP** is **blocked**

Below is the **correct and clean way** to do this in **nginx**.

---

## ✅ BEST SOLUTION: Block IP access in Nginx (not firewall)

This keeps your site public **only via domain**, while blocking raw IP access.

---

## 🔧 Step-by-Step

### 1️⃣ Create a “deny IP access” server block

Create a new config file:

```bash
sudo nano /etc/nginx/conf.d/block-ip.conf
```

Paste this **exact config**:

```nginx
server {
    listen 80 default_server;
    server_name _;
    return 444;
}
```

🔒 What this does:

* Catches requests **by IP**
* Closes the connection (no response)
* Prevents showing Nginx welcome page

---

### 2️⃣ Make sure your real site uses your domain

Example:

```nginx
server {
    listen 80;
    server_name example.com www.example.com;

    root /var/www/example;
    index index.html index.php;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

📌 Nginx picks the **domain match first**, then falls back to the IP block.

---

### 3️⃣ Disable the default config (VERY IMPORTANT)

```bash
sudo mv /etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf.bak
```

---

### 4️⃣ Test and reload

```bash
sudo nginx -t
sudo systemctl reload nginx
```

---

## 🧪 Test results

| URL                     | Result          |
| ----------------------- | --------------- |
| `http://YOUR_PUBLIC_IP` | ❌ Blocked       |
| `http://example.com`    | ✅ Website loads |

---

## 🔐 Optional: HTTPS version (recommended)

If you use HTTPS, also block IP on 443:

```nginx
server {
    listen 443 ssl default_server;
    server_name _;
    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;
    return 444;
}
```

---

## 🚫 ❌ DO NOT do this

* ❌ Firewall blocking port 80/443 (breaks site)
* ❌ Using `deny all` globally
* ❌ Blocking IP at OS level

---

## 🏁 Final Summary

✔ Website accessible via domain
✔ Public IP access blocked
✔ No Nginx welcome page
✔ Production-safe configuration

---

If you want, tell me:

* Do you use **HTTPS (Let’s Encrypt)**?
* What is your **domain name**?
* Rocky Linux **8 or 9**?

I’ll generate the **exact full Nginx config** for your server (copy-paste ready).
