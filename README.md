\# 🚀 Production-Grade 3-Tier Architecture on Azure


!\[Azure](https://github.com/ksquare2020/azure-3-tier-architecture/blob/main/three%20tier-azure.png)

!\[Azure](https://github.com/ksquare2020/azure-3-tier-architecture/blob/main/three%20tier-azure%202.png)

!\[Azure](https://github.com/ksquare2020/azure-3-tier-architecture/blob/main/three%20tier-azure%203.png)

!\[Azure](https://github.com/ksquare2020/azure-3-tier-architecture/blob/main/three%20tier-azure%204.png)

!\[Azure](https://github.com/ksquare2020/azure-3-tier-architecture/blob/main/three%20tier-azure%205.png)

!\[Architecture](https://img.shields.io/badge/Architecture-3--Tier-green?style=for-the-badge)
 
!\[Status](https://github.com/ksquare2020/azure-3-tier-architecture/blob/main/three%20tier-api.png)
 
!\[Status](https://github.com/ksquare2020/azure-3-tier-architecture/blob/main/three%20tier-web.png)


\---


\## 📌 Overview



This project demonstrates a \*\*secure, scalable, and production-ready 3-tier architecture\*\* built on Microsoft Azure.



All resources were \*\*provisioned manually using Azure Portal\*\* to gain hands-on experience in real-world cloud architecture.



\---



\## 🧱 Architecture



!\[Architecture](architecture/architecture-diagram.png)



\---



\## ⚙️ Components Used



\### 🔹 Resource Group



\* airspace-rg-westus2



\### 🔹 Virtual Network



\* Address Space: 10.0.0.0/16



\### 🔹 Subnets



\* ag-subnet → Application Gateway

\* app-subnet → Application Layer

\* db-subnet → Database Layer



\### 🔹 Compute



\* AppVm1

\* AppVm2

\* OS: Ubuntu

\* Backend: .NET API



\### 🔹 Networking



\* Application Gateway (Public Entry Point)

\* Internal Load Balancer

\* Network Security Groups (NSG)



\### 🔹 Database



\* Azure Database for MySQL (Private Access)



\### 🔹 Secure Access



\* Azure Bastion (SSH without public exposure)



\---



\## 🔁 Traffic Flow



```

User → Application Gateway → Internal Load Balancer → App VMs → MySQL Database

```



\---



\## 🔐 Security Design



\* No Public IP assigned to Virtual Machines

\* Application Gateway is the only public entry point

\* Database is accessible only via private network

\* NSG rules restrict traffic between tiers

\* Bastion enables secure access



\---



\## 🧪 Validation



Test API through Application Gateway:



```

curl http://<APPLICATION-GATEWAY-PUBLIC-IP>/api/airports/getallairports

```



✔️ Expected Result:



\* HTTP 200 OK

\* API response returned successfully



\---



\## 📸 Screenshots (Proof of Deployment)



All resources were created manually. Screenshots are added as proof:



!\[VNet](screenshots/vnet.png)

!\[Subnets](screenshots/subnets.png)

!\[App Gateway](screenshots/app-gateway.png)

!\[Load Balancer](screenshots/load-balancer.png)

!\[VM](screenshots/app-vm.png)

!\[Database](screenshots/database.png)



\---



\## 💡 Deployment Approach



This project was implemented \*\*fully manual (no Terraform/Bicep)\*\* to:



\* Understand Azure networking deeply

\* Gain real-world architecture experience

\* Improve troubleshooting skills



\---



\## 🏁 Key Highlights



\* Fully private backend architecture

\* High availability using multiple VMs

\* Layered security design

\* No direct internet exposure for application and database

\* Production-ready architecture pattern



\---



\## 📂 Project Structure



```

airspace-3tier-azure/

│

├── README.md

├── architecture/

│   └── architecture-diagram.png

│

├── screenshots/

│   ├── vnet.png

│   ├── subnets.png

│   ├── app-gateway.png

│   ├── load-balancer.png

│   ├── app-vm.png

│   └── database.png

│

└── docs/

&#x20;   └── setup-guide.md

```



\---



\## 🚀 Future Improvements



\* VM Scale Sets (Auto Scaling)

\* CI/CD Pipeline integration

\* Azure Monitor \& Alerts

\* Web Application Firewall (WAF)

\* Infrastructure as Code (Terraform/Bicep)



\---



\## 🏁 Conclusion



This project demonstrates how to design and implement a \*\*secure, scalable, real-world 3-tier architecture on Azure\*\*, following best practices used in production environments.



\---



\## 🔗 Connect



If you found this useful, feel free to connect or share feedback.



\#Azure #CloudArchitecture #DevOps #DotNet #Networking



