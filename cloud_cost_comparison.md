# Cloud Cost Estimate Comparison

## Overview
This document provides a comparison of the three provided cloud infrastructure estimates: two from Microsoft Azure and one from Amazon Web Services (AWS).

## Estimates Summary

| Estimate | Cloud Provider | VM OS | Core Compute Spec | Monthly Cost |
| :--- | :--- | :--- | :--- | :--- |
| **Azure Estimate 2** | Microsoft Azure | Linux | 1 B2s (2 Cores, 4 GB RAM) | $42.86 |
| **Azure Estimate 1** | Microsoft Azure | Windows (AHB) | 1 B2s (2 Cores, 4 GB RAM) | $42.86 |
| **AWS Estimate** | AWS | Linux | t3.small (Typically 2 vCPU, 2 GB RAM) | $18.13 |

## Detailed Comparison

### 1. Compute & Instances
* **Azure (Both Estimates):** Both utilize a `B2s` instance which provides 2 Cores and 4 GB RAM, running continuously (730 hours). The only difference is the OS: Estimate 2 uses Linux, while Estimate 1 uses Windows with Azure Hybrid Benefit (AHB). Because of AHB, the OS costs are neutralized, resulting in an identical compute cost of **$40.58/month** for both.
* **AWS:** Utilizes a `t3.small` instance on Linux, which generally offers 2 vCPUs and 2 GB RAM. Combined with 20 GB of EBS storage, the compute setup costs **$16.98/month**.

### 2. Storage
* **Azure:** Both estimates provision a 50 GB Block Blob Storage account (Hot Access Tier) with a series of defined operations (write, list, read) and 1 managed P6 disk. Cost: **$2.08/month**.
* **AWS:** Provisions 50 GB of S3 Standard storage. Cost: **$1.15/month**.

### 3. Networking
* **Azure:** Configured with 10 GB total Outbound Data Transfer across two Virtual Networks. Cost: **$0.20/month**.
* **AWS:** Configured with 10 GB of Intra-Region Data Transfer. This is bundled in the EC2 costs but factored into the usage.

## Key Takeaways
1.  **Overall Cost:** The AWS configuration is significantly cheaper ($18.13/month) compared to the Azure configurations ($42.86/month).
2.  **Resource Differences:** The price discrepancy is largely driven by the compute tier. The Azure B2s instance has double the RAM (4 GB) compared to the AWS t3.small instance (2 GB), which explains a significant portion of the cost difference.
3.  **OS Licensing:** In the Azure estimates, running Windows normally incurs a premium over Linux. However, Estimate 1 applies the **Azure Hybrid Benefit (AHB)**, which allows the user to bring their own on-premises Windows Server license to Azure, making the hourly rate identical to the Linux equivalent.
