
# Deployment of 2-Tier Application Using Single Ansible Script

This repository demonstrates the deployment of a **2-tier application architecture** using **Ansible**. Both **App Server** and **DB Server** are configured with a single playbook.

---

## Architecture

```
        ┌─────────────┐
        │   App Tier  │
        │  (Nginx +   │
        │   PHP)      │
        └─────┬───────┘
              │
       ┌──────┴───────┐
       │ DB Tier      │
       │ (MariaDB)    │
       └──────────────┘
```

* **App Server:** Hosts web application (PHP on Nginx)
* **DB Server:** Hosts MariaDB database

---

## Inventory Example

```ini
[App_server]
app1 ansible_host=192.168.1.10

[DB_server]
db1 ansible_host=192.168.1.20
```

---

## Playbook Overview

### **1. App Server Tasks**

* Install Nginx, PHP, PHP-FPM
* Start & enable services
* Deploy `index.php` page with `phpinfo()`

### **2. DB Server Tasks**

* Install MariaDB (`mariadb105-server`)
* Start & enable MariaDB service
* Create database `FCT`

---

## Usage

1. Clone the repository:

```bash
git clone <repo_url>
cd <repo_folder>
```

2. Update inventory file with your server IPs
3. Run the playbook:

```bash
ansible-playbook -i inventory.ini 2tier-deploy.yml
```

4. Access App Server via browser:

```
http://<app_server_ip>/index.php
```

You should see the PHP info page confirming PHP is running.

---

## File Structure

```
2-Tier_Architecture_using_Ansible
├─ images
├── 2tier.yml       
└── README.md              
```

---

## Author

**Ankita Pansare**
