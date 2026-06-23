# Step‑by‑Step Guide for AWS vs Azure Cost Comparison

## 🗺️ Your Simple Roadmap

1. Decide your app’s specs (compute, storage, traffic)
2. Use the **AWS Pricing Calculator** → get a monthly cost (Linux)
3. Use the **Azure Pricing Calculator** → get monthly costs (Linux, then Windows with Hybrid Benefit)
4. Compare networking (inter‑zone data transfer) costs
5. Write the comparison report
6. Assemble everything in a public GitHub repository

---

## 1. 🖥️ Application Specifications

| Resource | Value |
|----------|-------|
| Virtual machine | 2 vCPU, 2 GB RAM | AWS | 2vCPU, 4GB RAM | AZURE
| Operating system | Linux (Ubuntu) for all tests; also Windows Server for the Azure Windows test |
| Attached disk (SSD) | 20 GB |
| Object storage (S3/Blob) | 50 GB per month |
| Data out to internet | 10 GB per month |
| Data between two zones | 5 GB per month |

---

## 2. ☁️ AWS Estimate (Linux Only)

We will use the **AWS Pricing Calculator**.

1. Go to [https://calculator.aws/](https://calculator.aws/)
2. Click **“Create estimate”**
3. Click **“Add service”** → **Amazon EC2**
   - **Region:** US East (N. Virginia)
   - **Instance type:** t3.small
   - **Operating system:** Linux
   - **Pricing model:** On‑Demand (no upfront)
   - **Storage:** 20 GB, General Purpose SSD (gp3)
   - **Usage:** 730 hours/month
   - Click **Save**
4. Click **“Add service”** → **Amazon S3**
   - **S3 Standard storage:** 50 GB
   - **Data transfer OUT:** 10 GB
   - Click **Save**
5. Click **“Add service”** → **Data Transfer**
   - Add **“Same region transfer”** (between Availability Zones): 5 GB
   - Click **Save**
6. At the bottom you’ll see the **monthly total**. Write it down.
7. **Screenshot** the whole calculator (showing all three services) → save as `aws-calculator.png`
8. **Export** the estimate (top right) → save the PDF or copy the **public link**.

---

## 3. ☁️ Azure Estimate – Linux & Windows

Use the **Azure Pricing Calculator**: [https://azure.microsoft.com/en-us/pricing/calculator/](https://azure.microsoft.com/en-us/pricing/calculator/)

### A. Linux Scenario

1. Open the calculator and add **“Virtual Machines”**
   - **Region:** East US
   - **Instance series:** Bs‑Series → **B2s** (2 vCPU, 4 GB RAM)
   - **OS:** Linux (Ubuntu)
   - **Managed disk:** P6 (64 GB – the smallest available SSD)
   - **Usage:** 730 hours/month
2. Add **“Storage Accounts”**
   - **Service:** Block Blob Storage, **Hot** tier, **LRS** redundancy
   - **Capacity:** 50 GB
3. Add **“Bandwidth”**
   - **Outbound data transfer:** 10 GB
   - Add another **5 GB** for “Intra‑region” (zone‑to‑zone)
4. Note the **monthly total**. Approximate cost: **$9.74**
5. **Screenshot** the calculator → save as `azure-linux.png`
6. **Export/Share** the estimate and copy the public link.

### B. Windows + Hybrid Benefit Scenario

1. Duplicate the Linux estimate (or edit it).
2. On the **Virtual Machines** card:
   - Change OS to **Windows Server**
   - Tick the box **“Azure Hybrid Benefit”**
   - Keep everything else the same.

---

## 4. 🌐 Networking Cost Comparison

Create a file called `networking-costs.md` with this table:

| Cloud | Price per GB (between AZs) | Cost for 5 GB |
|-------|----------------------------|---------------|
| AWS   | $0.2                       | $0.1          |
| Azure | $0.2                      | $2.40          |

For our example (5 GB), the difference is minimal but good to document.

---

## 6. 📝 Write the Comparison Report

Create `comparison-report.md` with the following sections:

### Cost Table
| Scenario | AWS (per month) | Azure (per month) |
|----------|-----------------|-------------------|
| Linux, on‑demand | ~$16.98 | ~$30.37 |
| Windows (with Hybrid Benefit) | Not available | ~$22.87 |

### Which Provider is Cheaper?
- **Windows apps:** Only Azure offers a cost‑effective Windows option with Hybrid Benefit.
- **AWS linux** is cheaper

### Two Cost‑Saving Tips
- **Right‑size** – Use the smallest instance that works; don’t over‑provision.
