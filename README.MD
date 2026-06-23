# Cloud Cost Comparison: AWS vs Azure

## 📘 Overview
This project compares the monthly cost of hosting a **small web application** on **Amazon Web Services (AWS)** and **Microsoft Azure**.  
It was completed as part of a hands‑on cloud economics assignment, using each provider's native pricing calculator and including compute, storage, data transfer, and discount options.

**Goals:**
- Understand pay‑as‑you‑go pricing models  
- Map equivalent services (EC2 vs. Azure VM, S3 vs. Blob Storage)  
- Evaluate the impact of licensing (Azure Hybrid Benefit)  
- Compare inter‑zone data transfer fees  
- Learn about commitment‑based discounts (Savings Plans vs. Reserved Instances)  
- Produce a clear, beginner‑friendly cost breakdown  

---

## 🧪 Application Specifications
| Resource | Details |
|----------|---------|
| **Compute** | 2 vCPU, 2 GB RAM & 2vCPU, 4GB RAM (AWS t3.small / Azure B2s) |
| **OS (Linux)** | Ubuntu (used for both clouds) |
| **OS (Windows)** | Windows Server (Azure only, with Hybrid Benefit) |
| **Managed Disk** | 20 GB SSD (AWS gp3 / Azure P6 – 64 GB minimum) |
| **Object Storage** | 50 GB/month (AWS S3 Standard / Azure Blob Hot LRS) |
| **Data Transfer Out** | 10 GB/month to internet |
| **Inter‑Zone Transfer** | 5 GB/month between two Availability Zones |

---

## 💰 Monthly Cost Comparison (On‑Demand)

| Scenario | AWS Cost (USD) | Azure Cost (USD) |
|----------|----------------|------------------|
| Linux VM + Storage + Transfer | **$217.56** | **$42.86** |
| Windows VM (with Hybrid Benefit) | Not available | **$42.86** |

## AWS Calculator link

- https://calculator.aws/#/estimate?id=b67ab9de36ace6b87067340168ed259775b39f14

## BY ADEPEGBA ISAIAH
