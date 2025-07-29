# Pterodactyl Panel – Easy Install Script

<div align="center">
  <img src="https://img.shields.io/badge/Made%20by-eDen-blueviolet?style=for-the-badge&logo=github" alt="Made by eDenGT">
</div>

Pterodactyl Panel is an open‑source, container‑based game server management panel built for speed, security, and ease of use. Unlike older, clunky panels, Pterodactyl offers a modern and lightweight approach to managing game servers.

Its active community and support for easily adding new game “eggs” make it flexible and beginner‑friendly.

This guide shows you how to install and secure Pterodactyl Panel + Wings using an automated script with free HTTPS (Nginx + Certbot).

A comprehensive, beginner-friendly guide and script to install **Pterodactyl Panel + Wings** on your own cloud server (AWS, Vultr, DigitalOcean, etc.).  

This script automates the process, reducing setup time from **~30 minutes to ~5 minutes**.

---

## 🚦 Prerequisites

-   Fresh Linux server (**Ubuntu 20.04/22.04 recommended**)
-   At least **2GB RAM** and **1 vCPU**
-   **Root access** (SSH or console login)

---

## 🛠️ Step-by-Step Installation

### 1. Set Up Your Cloud Server

-   Create an EC2 instance on AWS (**t2.small** or higher recommended), or use any other provider (Vultr, DigitalOcean, Linode, etc.).
-   Choose **Ubuntu 20.04/22.04 LTS** as the OS.
-   Open these ports in your firewall/security group: `80` (HTTP), `443` (HTTPS), `22` (SSH).

**Login to your server using SSH:**

```bash
ssh ubuntu@<your-server-ip>
```

---

### 2. Run the Pterodactyl Install Script

Once logged in, run the following command to start the automated installer:

```bash
bash <(curl -s https://pterodactyl-installer.se)
```

Press **Enter** to begin.

---

### 3. Fill Out the Installation Options

-   **Select Option 2:** Install both Panel and Wings.
-   **When prompted, provide:**
    -   Database name, username, password (press Enter for default if unsure)
    -   Timezone (e.g., `UTC` or your local timezone)
    -   **Admin email, username, and password**  
        **→ Make sure to remember these! You will use them to log in to the panel as an admin.**
    -   FQDN (domain or server IP)
    -   Firewall configuration → **Select Yes**
    -   HTTPS setup → **Select No** (unless you have a domain + SSL ready)

> Installation will take **10–15 minutes**.  
> The script will handle most configurations for you.

---

### 4. Advanced Settings

-   If asked to install **MariaDB**, choose **No** (unless you specifically need it).
-   If asked to configure **UFW firewall**, choose **Yes**.
-   If asked to configure **HTTPS**, choose **No** (unless using a domain and have SSL ready).

---

### 5. Confirm Panel Loads (HTTP)

After installation, open your browser and visit:

```
http://<your-server-ip>
```

You should see the Pterodactyl login page.  
**Do not log in yet!**  
For security, it's highly recommended to enable HTTPS before using your panel.

---

### 6. [Recommended] Secure Your Panel with HTTPS (Nginx + Certbot)

> **This is the recommended and secure way to access your panel.**  
> By default, the Pterodactyl panel runs over HTTP. To protect your login and data, enable HTTPS using a free SSL certificate from Let’s Encrypt.

#### Step 1: Point Your Domain

Create an **A record** in your DNS provider (Cloudflare, GoDaddy, etc.):

```
panel.yourdomain.com → <your-server-ip>
```

Wait a few minutes for DNS propagation.

#### Step 2: Install Certbot

Run the following commands:

```bash
sudo apt update
sudo apt install certbot python3-certbot-nginx -y
```

#### Step 3: Obtain and Apply SSL Certificate

Run:

```bash
sudo certbot --nginx -d panel.yourdomain.com
```

-   Agree to the terms.
-   Enter your email.
-   Choose to redirect HTTP to HTTPS when prompted.

#### Step 4: Enable Auto-Renewal

Certificates renew automatically every 90 days, but enable the timer to ensure this:

```bash
sudo systemctl enable certbot.timer
sudo systemctl start certbot.timer
```

---

**Done!**  
Now your panel is securely accessible via(https):

```
https://panel.yourdomain.com
```

---

### 7. Log In to Your Pterodactyl Panel

Open your browser and go to your secure panel URL:

```
https://panel.yourdomain.com
```

Log in with the **admin email/username and password you set during installation**.

> If login fails, join our [Discord](https://discord.gg/) and open a ticket with a screenshot for help.

---

## ➕ Next Step: Add a Node

Pterodactyl uses **Nodes** (your server) to host game servers.  
To add your node:

1. Log in to the Pterodactyl admin panel.
2. Go to **Nodes** in the sidebar.
3. Click **Create Node** and follow the prompts.
4. Copy the **Wings** configuration and run it on your server as instructed.

> This step is essential for hosting game servers on your panel.

---

## 📺 Video Guide: How to Add a Node

[Watch Here](#) <!-- Replace # with your actual video link if available -->

A step-by-step video showing how to add a node to your Pterodactyl Panel after installation.

---

## ❓ Why Use This Script?

-   ⏱️ **Reduces setup time** from ~30 min to ~5 min
-   🧑‍💻 **Beginner-friendly** (no complex manual configs)
-   🌐 **Works on most cloud providers**
-   🔒 **Secure** (firewall and best practices included)
-   🛠️ **Automated** (minimal manual input required)

---

## 🛟 Support

Join our **Discord** and open a ticket if you face issues.

---

## ✨ Made with ❤️ by eDenGT

> If you found this helpful, star the repo and follow me for more cool projects!

---

## 🎉 Conclusion

Your **Pterodactyl Panel** is now live!  
Next, explore custom themes and add game servers to your panel.

---
