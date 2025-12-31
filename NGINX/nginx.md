# NGINX Server

NGINX is open-source web server software used for reverse proxy, load balancing, and caching.

## Install NGINX ?

Here’s a clear, step-by-step guide on installing **Nginx** and some useful commands to manage it. I’ll cover both **Ubuntu/Debian** and **CentOS/RHEL** systems.

---

## **1. Installing Nginx**

### **On Ubuntu/Debian**

1. Update your package lists:

```bash
sudo apt update
```

2. Install Nginx:

```bash
sudo apt install nginx -y
```

3. Start and enable Nginx to run on boot:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

### **On CentOS/RHEL**

1. Install the EPEL repository (if not already installed):

```bash
sudo yum install epel-release -y
```

2. Install Nginx:

```bash
sudo yum install nginx -y
```

3. Start and enable Nginx:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## **2. Basic Nginx Commands**

### **Service Management**

```bash
sudo systemctl start nginx      # Start Nginx
sudo systemctl stop nginx       # Stop Nginx
sudo systemctl restart nginx    # Restart Nginx
sudo systemctl reload nginx     # Reload config without downtime
sudo systemctl status nginx     # Check Nginx status
```

### **Enable/Disable at Boot**

```bash
sudo systemctl enable nginx     # Enable Nginx on boot
sudo systemctl disable nginx    # Disable Nginx on boot
```

### **Check Configuration**

```bash
sudo nginx -t                   # Test Nginx configuration for errors
```

---

## **3. Useful Nginx File Locations**

| Purpose                | Location (default)            |
| ---------------------- | ----------------------------- |
| Main config file       | `/etc/nginx/nginx.conf`       |
| Site configs (Ubuntu)  | `/etc/nginx/sites-available/` |
| Enabled sites (Ubuntu) | `/etc/nginx/sites-enabled/`   |
| Logs                   | `/var/log/nginx/`             |
| Default web root       | `/var/www/html/`              |

---

## **4. Common Nginx Commands for Websites**

* Restart after config changes:

```bash
sudo systemctl reload nginx
```

* Test if Nginx is serving:

```bash
curl -I http://localhost
```

* Check active connections:

```bash
sudo netstat -tulpn | grep nginx
```

---

If you want, I can also make a **handy cheat sheet of 20+ essential Nginx commands** that’s perfect for daily use. It’s super handy to have.

Do you want me to make that cheat sheet?


Perfect! Here’s a **compact Nginx cheat sheet** with 25+ essential commands and tips for daily use:

---

# **Nginx Cheat Sheet**

## **1. Installation**

**Ubuntu/Debian:**

```bash
sudo apt update
sudo apt install nginx -y
```

**CentOS/RHEL:**

```bash
sudo yum install epel-release -y
sudo yum install nginx -y
```

---

## **2. Service Management**

```bash
sudo systemctl start nginx        # Start Nginx
sudo systemctl stop nginx         # Stop Nginx
sudo systemctl restart nginx      # Restart Nginx
sudo systemctl reload nginx       # Reload config without downtime
sudo systemctl status nginx       # Check service status
sudo systemctl enable nginx       # Enable Nginx at boot
sudo systemctl disable nginx      # Disable Nginx at boot
```

---

## **3. Configuration Management**

```bash
sudo nginx -t                     # Test configuration for errors
sudo nginx -s reload               # Reload config (alternative)
sudo nginx -s stop                 # Stop Nginx gracefully
sudo nginx -s quit                 # Stop Nginx immediately
sudo nginx -v                      # Show Nginx version
sudo nginx -V                      # Show version + compile options
```

---

## **4. File Locations**

| Purpose                  | Path                          |
| ------------------------ | ----------------------------- |
| Main config              | `/etc/nginx/nginx.conf`       |
| Sites available (Ubuntu) | `/etc/nginx/sites-available/` |
| Sites enabled (Ubuntu)   | `/etc/nginx/sites-enabled/`   |
| Default web root         | `/var/www/html/`              |
| Logs                     | `/var/log/nginx/`             |

---

## **5. Website & Server Management**

```bash
sudo mkdir -p /var/www/example.com/html    # Create website root
sudo chown -R $USER:$USER /var/www/example.com/html
sudo chmod -R 755 /var/www/example.com
```

**Create a new server block (Ubuntu example):**

```bash
sudo nano /etc/nginx/sites-available/example.com
```

Basic server block example:

```nginx
server {
    listen 80;
    server_name example.com www.example.com;

    root /var/www/example.com/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Enable site:

```bash
sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

---

## **6. Logs & Debugging**

```bash
tail -f /var/log/nginx/access.log    # View live access log
tail -f /var/log/nginx/error.log     # View live error log
```

---

## **7. Network & Connections**

```bash
sudo netstat -tulpn | grep nginx      # Check active Nginx ports
sudo ss -tulpn | grep nginx           # Alternative for netstat
curl -I http://localhost              # Test server response headers
```

---

## **8. Security & Optimization**

```bash
sudo ufw allow 'Nginx Full'          # Open HTTP/HTTPS ports (Ubuntu)
sudo ufw status                        # Check firewall rules
```

* Configure SSL with **Let’s Encrypt**:

```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx
```

---

## **9. Common Maintenance**

```bash
sudo systemctl reload nginx           # Apply config changes
sudo systemctl restart nginx          # Restart after major updates
sudo nginx -t                          # Always test config first
sudo du -sh /var/log/nginx/*          # Check log sizes
```

---

✅ **Pro Tips:**

* Always run `nginx -t` before reloading or restarting.
* Use `systemctl reload nginx` to avoid downtime.
* Keep server blocks organized in `sites-available` & `sites-enabled`.
* Monitor logs with `tail -f` during troubleshooting.

---

If you want, I can also make a **super condensed one-page version** with just commands, no explanations—perfect to print or keep in your terminal as a quick reference.

Do you want me to make that?

