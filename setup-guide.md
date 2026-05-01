# ⚙️ Setup Guide – Azure 3-Tier Architecture

## 📌 Overview

This guide provides a **high-level step-by-step approach** to setting up a secure 3-tier architecture on Microsoft Azure.

The deployment is performed **manually via Azure Portal** to understand core infrastructure concepts.

---

## 🧱 Architecture Summary

* **Entry Layer** → Application Gateway (Public)
* **Application Layer** → Virtual Machines (Private)
* **Database Layer** → Azure Database for MySQL (Private)
* **Secure Access** → Azure Bastion

---

## 🪜 Step-by-Step Setup

### 1️⃣ Create Resource Group

* Navigate to Azure Portal
* Create a new Resource Group
* Example: `airspace-rg-westus2`

---

### 2️⃣ Create Virtual Network (VNet)

* Define address space (e.g., `10.0.0.0/16`)
* Create subnets:

  * `ag-subnet` (Application Gateway)
  * `app-subnet` (Application Layer)
  * `db-subnet` (Database Layer)

---

### 3️⃣ Configure Network Security Groups (NSG)

* Allow HTTP/HTTPS to Application Gateway
* Allow internal traffic between subnets
* Restrict direct internet access to app and DB layers

---

### 4️⃣ Deploy Application Gateway

* Public IP enabled
* Associate with `ag-subnet`
* Configure:

  * Backend pool (App VMs)
  * HTTP settings
  * Listener & routing rules

---

### 5️⃣ Create Application Virtual Machines

* Deploy 2 VMs in `app-subnet`
* Install:

  * Ubuntu OS
  * .NET Runtime / API
* Disable public IP

---

### 6️⃣ Configure Internal Load Balancer

* Private frontend IP
* Backend pool → App VMs
* Health probes & load balancing rules

---

### 7️⃣ Setup Database Layer

* Create Azure Database for MySQL
* Enable private access only
* Configure firewall/private endpoint
* Create schema & tables

---

### 8️⃣ Configure Azure Bastion

* Deploy Bastion in a dedicated subnet
* Use it for secure SSH access to VMs
* No need for public IP on VMs

---

### 9️⃣ Connect Application to Database

* Update connection string in API
* Use private IP / DNS of database
* Validate connectivity

---

### 🔟 Test End-to-End Flow

* Access via Application Gateway public IP
* Hit API endpoint:

```bash
curl http://<app-gateway-ip>/api/airports/getallairports
```

✔️ Verify:

* Response is successful
* Traffic flows through all layers

---

## 🔐 Security Best Practices

* No public IP for backend resources
* Use NSGs for subnet-level control
* Enable private endpoints for database
* Use Bastion for secure access

---

## 🧪 Validation Checklist

* Application Gateway accessible
* Load balancer distributing traffic
* App VMs responding correctly
* Database connectivity working
* No direct public access to backend

---

## 🚀 Next Steps

* Implement auto scaling (VMSS)
* Add monitoring (Azure Monitor, Logs)
* Introduce CI/CD pipelines
* Convert to Infrastructure as Code

---

## 🏁 Summary

This setup demonstrates a **production-style Azure architecture** with proper **network isolation, security, and scalability principles**.

It serves as a strong foundation for real-world cloud deployments.
