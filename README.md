# Highly Available NGINX Web Infrastructure on Azure

## 🚀 Project Overview
This project demonstrates a production-grade, fault-tolerant web architecture deployed manually via the Azure Console. It utilizes Infrastructure-as-a-Service (IaaS) principles to host static web content across multiple redundant Linux virtual machines managed by an Azure Standard Load Balancer and mapped to a custom domain using Azure DNS.

---

## 🏗️ Architecture & Component Breakdown


<img width="1198" height="412" alt="Screenshot 2026-10-14 113244" src="https://github.com/user-attachments/assets/6049b6bf-4eea-45aa-bcf4-93643c9fdace" />


* **Azure Resource Group:** Logical container holding all related cloud resources.
* **Linux Virtual Machines (`Standard_B2ats_v2`):** Ubuntu 22.04 LTS compute instances providing full root control.
* **NGINX Web Server:** High-performance open-source server delivering static web files.
* **Azure Standard Load Balancer:** Layer 4 load balancer distributing incoming web traffic across backend VMs to ensure high availability.
* **Azure Public DNS & GoDaddy:** Authoritative DNS zone management linking a custom domain name to the load balancer's frontend IP.

---

## 🛠️ Step-by-Step Deployment Guide

1. **Resource Group:** Created a shared resource group (`rg-devops-lab`) in Azure.
2. **Virtual Machines:** Provisioned two Ubuntu Linux VMs (`vm-devops-01` and `vm-devops-02`) with open SSH and HTTP ports.
3. **Web Server Setup:** Installed NGINX on both VMs via SSH and configured distinct landing page messages (`Hello from Web VM 1` / `Hello from Web VM 2`).
4. **Load Balancer:** Configured a Public Standard Load Balancer, a backend pool using NIC attachments, an HTTP health probe (`/`), and a forwarding load-balancing rule on port 80.
5. **DNS Configuration:** Created an Azure Public DNS Zone and updated GoDaddy nameservers to point domain traffic to the Azure infrastructure.

---

## 📌 Key Takeaways & Learnings
* **Redundancy & Fault Tolerance:** If one virtual machine fails, the load balancer automatically reroutes 100% of traffic to the healthy instance.
