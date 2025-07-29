# Pterodactyl Panel – Easy Install Script

![Made by eDenGT](https://img.shields.io/badge/Made%20by-eDenGT-blueviolet?style=for-the-badge&logo=github)

A simple guide and script to install **Pterodactyl Panel + Wings** on your own cloud server (AWS, Vultr, DigitalOcean, etc.).  
This reduces the manual setup from **~30 minutes to ~5 minutes** with an automated script.

---

## 🚦 Prerequisites

- A fresh Linux server (**Ubuntu 20.04/22.04 recommended**)
- At least **2GB RAM** and **1 vCPU**
- **Root access** (SSH or console login)

---

## 🛠️ Step-by-Step Installation

### 1. Set Up Your Cloud Server

- Create an EC2 instance on AWS (**t2.small** or higher recommended).
- Use **Ubuntu 20.04/22.04 LTS** as the OS.
- Open necessary ports: `80`, `443`, `22`.

**Login to the server using SSH:**

```bash
ssh ubuntu@<your-server-ip>
```
> You can use any other cloud provider like Vultr, DigitalOcean, Linode, etc.

---

### 2. Run the Pterodactyl Install Script

Once logged into your server, run:

```bash
bash <(curl -s https://pterodactyl-installer.se)
```
Press **Enter** to begin.

---

### 3. Fill Out the Installation Options

- **Select Option 2:** Install both Panel and Wings.
- **Provide the following details when prompted:**
  - Database name, username, password (press Enter for default if unsure)
  - Timezone
  - Admin email, username, and password
  - FQDN (domain or server IP)
  - Firewall configuration → **Select Yes**
  - HTTPS setup → **Select No** (unless you have domain + SSL ready)

> Installation will take **10–15 minutes**.

---

### 4. Advanced Settings

- If asked to install **MariaDB**, choose **No** (unless needed).
- If asked to configure **UFW firewall**, choose **Yes**.
- If asked to configure **HTTPS**, choose **No** (unless using a domain).

---

### 5. Access Pterodactyl Panel

Open your browser and go to:

```
http://<your-server-ip>
```

Log in with the admin credentials you created.

> If login fails, raise a ticket in our Discord and send a screenshot.

---

## ➕ Next Step: Add a Node

Pterodactyl uses **Nodes** (your server) to host game servers.  
Add your node via the admin panel.

---

## 📺 Video Guide

[Watch Here](#) <!-- Replace # with your actual video link if available -->

---

## ❓ Why Use This Script?

- ⏱️ **Reduces setup time** from ~30 min to ~5 min
- 🧑‍💻 **Beginner-friendly** (no complex manual configs)
- 🌐 **Works on most cloud providers**

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