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
