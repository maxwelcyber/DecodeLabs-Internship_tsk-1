# Serverless Static Website Hosting & Global Content Delivery (Azure)

## 📌 Project Overview
This project demonstrates a fully serverless, highly durable, and cost-effective cloud architecture built to host a static personal portfolio website globally. By transitioning away from traditional virtual machines (IaaS) and adopting an **Object Storage** strategy, this implementation completely eliminates server management, operating system overhead, and compute costs while ensuring instantaneous global load times.

This project was completed as part of the Cloud Computing (AWS/Azure) Internship at **DecodeLabs**.

---

## 🏗️ Architecture Design & Pure Cloud Logic
Traditional server architectures rely on maintaining single Virtual Machines (like Azure VMs or AWS EC2 instances) which act as single points of failure, require manual OS patching, and incur high fixed costs regardless of traffic. 

This architecture embraces a modern cloud design philosophy:
1. **Object Storage Over Compute:** The frontend assets (`index.html`, `CSS`, `JS`, images) are hosted directly within an decoupled Azure Storage Account Blob container optimized for static hosting. This shifts availability metrics to **99.9%** and durability metrics to an incredible **99.999999999% (11 Nines)** via automated cross-region replication.
2. **Cattle vs. Pets Mindset:** Instead of treating servers like "Pets" (giving them unique names, manually nurturing them, and paying fixed costs), the infrastructure treats cloud resources like "Cattle." Resources are disposable, provisioned instantly, scaled automatically, and completely defined by cloud logic.
3. **Enterprise Identity Integration:** Security is handled strictly using modern IAM guidelines. Rather than using legacy master account Access Keys—which pose severe security exposure risks if leaked—this architecture integrates **Microsoft Entra ID (Active Directory)** alongside **Role-Based Access Control (RBAC)**. Permissions like `Storage Blob Data Contributor` are explicitly delegated to specific identities at precise scopes.

---

## 🛠️ Key Technical Implementations
* **Azure Blob Storage Static Hosting:** Configured dedicated object storage containers (`$web`) to parse default entry points (`index.html`) and error boundaries (`404.html`) without a compute engine layer.
* **Granular Identity & Access Management (IAM):** Implemented enterprise-grade RBAC policies, mapping Entra ID security principals directly to storage access scopes to enforce the principle of least privilege.
* **Serverless Global Scale:** Achieved zero-maintenance infrastructure capable of scaling infinitely from one visitor to millions seamlessly.

---

## 📂 Repository Structure
```text
├── index.html          # Main Portfolio Entry Point
├── 404.html            # Custom Serverless Error Document
├── css/                # Application Styling Assets
├── js/                 # Client-side Logic
└── README.md           # Technical Documentation
