# ShopPro International – Azure Cloud Cost Report

---

## **1. Migration Cost**

For the migration part, I checked the **Azure Pricing Calculator** to find the one-time costs for moving data and applications to Azure. Since **ShopPro International** has data and servers in different regions, the main cost comes from data transfer, database replication, and some temporary migration tools we will use.

### **1.1 Azure Database Migration Service**
- Helps in moving databases like **SQL and NoSQL** to Azure with minimal downtime.  
- Supports replication and testing before the actual switch.  
- For **5 TB of SQL** and **10 TB of NoSQL** databases, the total estimated cost comes to around **$300–$400**, depending on how long the migration takes.

### **1.2 Azure Data Box or Azure Storage Transfer**
- Used for transferring large amounts of data securely.  
- A physical device sent by Microsoft that helps avoid slow internet transfer.  
- Costs about **$250 per device**, ideal for the **15 TB data warehouse migration**.

### **1.3 Temporary Migration VMs**
- Temporary virtual machines are required for testing, backups, and compatibility checks.  
- These short-term resources usually run for a few days or weeks, costing around **$200–$300** in total.

### **1.4 Data Egress (Network Transfer)**
- Sending data from on-premises to Azure adds cost based on the data size.  
- Transferring **30 TB of data** at **$0.05 per GB** would cost roughly **$1,500**.

**Estimated one-time migration cost:** around **$2,000–$2,500 USD** in total.  

---

## **2. Operational Cost (Monthly)**

After migration, the monthly costs will come from running the main services such as VMs, databases, storage, and networking.  
**ShopPro** operates in **North America, Europe, and Asia-Pacific**, so resources will be deployed in all three regions for performance and reliability.

### **2.1 Web Front-End Cluster**
- **10 VMs per region × 3 regions = 30 VMs total**  
- Handles user traffic and website operations.  
- Using **B2s or D2s_v3** VMs costs around **$50–$60 each per month**, totaling about **$1,800/month**.  
- **Azure Load Balancer** and **Azure CDN** add about **$100/month** for traffic distribution and faster content delivery.

### **2.2 API Back-End Services**
- Microservices hosted across **20 VMs** to handle background processing.  
- Each VM costs around **$70/month**, adding up to **$1,400/month**.  
- With **auto-scaling**, costs will decrease during low traffic and slightly increase during high load.

### **2.3 Payment Processing**
- High-security VMs are used for handling customer payments and require **PCI compliance**.  
- Each secure VM (**D4s_v4**) costs about **$200/month**.  
- **5 VMs** total around **$1,000/month**, including encryption and security tools.

### **2.4 Database Layer**
- **Primary SQL Database (5 TB):** $800/month  
- **NoSQL Analytics DB (10 TB):** $1,200/month  
- **Data Warehouse (15 TB):** $1,500/month  
- **Total:** approximately **$3,500/month**

### **2.5 Data Analytics & ML (GPU VMs)**
- For machine learning training and data processing.  
- **2–3 GPU VMs** at **$400/month** each = **$1,200/month**.  
- These can be turned off when idle to save cost.

### **2.6 Storage & Backup**
- **Geo-redundant storage (GRS)** used for backups and disaster recovery.  
- Costs around **$200–$300/month**.  
- Ensures data safety across multiple regions.

### **2.7 Networking**
- Covers data transfers between regions and services.  
- Estimated at **$150–$200/month**.  
- Maintains connectivity between front-end, back-end, and databases.

**Total Monthly Operational Cost:** around **$8,000–$9,000 USD**, depending on workload and scaling.

---

## **3. Cost Optimization Strategy**

### **3.1 Cost Optimization Choices**
Azure offers two main pricing models **Pay-as-you-go** and **Reserved Instances**.  
- **Pay-as-you-go:** Ideal for short-term or unpredictable workloads.  
- **Reserved Instances:** Better for systems running 24/7 (e.g., databases, backend services).  

For example, a **D2s_v3 VM** costing **$70/month** can go down to **$40/month** when reserved for one year a **40% savings**.

**Auto-scaling** further reduces costs by adding or removing VMs automatically based on demand.  During high-traffic periods (e.g., holiday sales), extra VMs are added; when demand decreases, unused VMs are stopped.

**Right-sizing** ensures optimal resource use e.g., replacing a **D4s VM** (using only 30% capacity) with a **D2s VM**, saving **$50–$100/month**.  
**Azure Monitor** helps identify underused VMs for resizing.

**Storage tiering** also cuts costs:
- **Hot Tier:** For frequently accessed data  
- **Cool Tier:** For less-used data  
- **Archive Tier:** For rarely accessed data  

Moving old data to the **Archive tier** can save hundreds of dollars monthly without losing access.

---

### **3.2 Discounts and Hybrid Benefits**

**Azure Hybrid Benefit:**  
Allows reuse of **Windows Server** or **SQL Server licenses** to save up to **40%** on Windows VMs.

**Multi-Year Reservations:**  
- Reserve resources for **1 or 3 years** for bigger discounts.  
- Example: A **$800/month SQL Database** can cost **$480/month** with a 3-year reservation.  
- Best for databases, microservices, and payment servers.

**Capacity Reservations:**  
Lock in discounted rates for predictable workloads like **50 TB of Blob Storage**, reducing cost per GB.

**Enterprise Agreements and Savings Plans:**  
Automatically apply discounts to frequently used services, reducing long-term operational costs.

---

### **3.3 Future Projections**

As ShopPro grows, cloud costs may rise by **10–15% per year** due to increased data and traffic.  
**Azure Cost Analysis** will help track spending and identify services driving growth.

**Adopting newer VM generations** (Dv5 or Ev6) will improve performance and reduce costs.  
**Serverless services** like **Azure Functions**, **Logic Apps**, and **Container Apps** will further cut costs by charging only when code runs.

Regular cost reviews every quarter will ensure resources are optimized and budgets remain balanced.

---

## **4. Future Growth and Budget Plan (3-Year Projection)**

### **4.1 Expected Growth and Budget Tracking**
In the next three years, **ShopPro International** expects growth in both customers and data.  
As more transactions occur, demand for **VMs, databases, and storage** will rise by **10–15% annually**.  
Using **Azure Cost Management** and **Budget Alerts**, we’ll monitor usage and expenses to stay within budget while supporting expansion.

---

### **4.2 Scaling Compute Resources**
As user traffic grows, compute power must scale efficiently:  
- Use **auto-scaling** during high-traffic periods (e.g., sales events).  
- Stop extra servers when demand drops to avoid paying for idle time.  

For always-on services (like payment systems), continue using **Reserved Instances** to save **30–40%** and maintain cost stability.

---

### **4.3 Managing Data Growth**
To handle growing data volumes:
- Use **Hot, Cool, and Archive** storage tiers to save up to **50%** on storage.  
- Set **data lifecycle policies** to move old data automatically to cheaper tiers.  
- Use **Geo-Redundant Storage (GRS)** for reliable disaster recovery and high availability.

---

### **4.4 Modernizing Infrastructure**
ShopPro plans to modernize its setup by:
- Upgrading to **newer VM generations** (Dv5, Ev6) for better performance and energy efficiency.  
- Adopting **serverless computing** (Azure Functions, Logic Apps) for small background jobs, paying only when code runs.  
- Migrating analytics workloads to **Azure Synapse** or **Power BI Embedded**, which automatically scale with demand.


---

### **4.5 Continuous Monitoring and Adjustments**
Every **6 months**, the cloud setup will be reviewed using **Azure Advisor** and **Azure Monitor** to:
- Identify underused or oversized resources  
- Apply new discounts or cost-saving recommendations  
- Ensure the best balance of performance and affordability  



---
### **Conclusion**  
In conclusion, **ShopPro International’s 3-year cloud strategy** focuses on smart scaling, cost efficiency, and modernization. By using **Azure’s cost management tools**, **storage tiering**, and **newer VM generations**, the company can handle growth without overspending. Regular reviews and automation will ensure resources stay optimized, keeping performance high and costs under control as the business expands.
