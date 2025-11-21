# Lab 11 – Application Migration  
**Name:** Rohan Surti (surt0008) [041164260] 

---
## Task 1 – Set Up Tooling for Discovery  

### Do we use agent based, agentless, or a mix?  
For this migration, the best option is to use a mix of agent-based and agentless discovery.  
- **Agentless** works well for VMware because it does not require installation on the servers.  
- **Agent-based** is useful when we need detailed dependency information.  
Using both gives better accuracy.

### How many appliances are needed and why?  
Only one **Azure Migrate appliance** is needed. All servers are in the same on-premises VMware environment, so one appliance can discover everything. More appliances are only required for multiple separate networks or data centers.

### Credentials needed  
- **Software inventory:** Windows admin credentials and Linux SSH credentials  
- **SQL discovery:** SQL admin or a read-only service account  
- **Dependency mapping:** Local admin or root credentials to read processes and connections  

### Three best practices for discovery  
1. Make sure the appliance can reach all servers and required ports are open.  
2. Test all credentials first, so the discovery does not fail later.  
3. Let the discovery run for about **30 days** to collect enough performance data.

---

## Task 2 – Perform Assessment Planning  

### Assessment type  
Tailwind should use a **production assessment** because this is a real business application and requires proper sizing.

### Target region and performance history  
- The target region should be the closest Azure region used by the company.  
- Performance history should be 30 days so Azure Migrate can size the servers using real usage data.

### Performance-based sizing or on-premises sizes?  
**Performance-based sizing** is better because it uses real usage. On-premises sizes are usually oversized. Performance sizing helps reduce cost and provides accurate VM sizes.

### Comfort factor, pricing, licensing  
- **Comfort factor:** 1.2 for safety  
- **Pricing model:** Pay-as-you-go  
- **Licensing:** Azure Hybrid Benefit (if the company already owns Windows/SQL licenses)

---

## Task 3 – Dependency Analysis  

### Application components  
- WEB01  
- WEB02  
- APP01  
- SQL01  
- LB01 (internal load balancer)

### Eight dependencies  
1. Port 80 from users to the web servers  
2. Port 443 for secure traffic  
3. Web servers connecting to APP01  
4. Port 1433 from APP01 to SQL01  
5. Nightly backup processes  
6. DNS lookups  
7. Domain controller communication  
8. Firewall rules between each tier  

### Items to filter out as noise  
- Windows Update  
- Antivirus traffic  
- Public internet IPs  
- Background Microsoft system services  

These are not part of the application and should be removed.

### Business requirements  
- The application is important for the business  
- Allowed downtime: **1 hour**  
- Data is internal business data  
- SQL Server licensing must be considered  
- Monthly patching  
- Firewall rules must be recreated correctly  
- IP changes should not break the application  

---

## Task 4 – Validate Assessment Results with Application Owner  

### Recommended VM sizes  
- **WEB servers:** D2s v5  
- **APP server:** D4s v5  
- **SQL server:** D8s v5 or memory-optimized  

### Components to replace or optimize in Azure  
- Replace LB01 with Azure Load Balancer  
- SQL01 may move to SQL Managed Instance or SQL VM  
- Backups through Azure Backup
- Firewall rules recreated in NSGs

### Check if dependencies are correct  
All communication flows and ports should be confirmed with the application owner.

### Check SLA and downtime  
Azure VMs can meet uptime requirements.  
The 1-hour downtime window is achievable with planned migration.

### SQL migration options  
- Rehost SQL on an Azure VM  
- Azure SQL Managed Instance  
- Azure SQL Database (if supported)  

---

## Task 5 – Migration Plan (Runbook)  

### Pre-migration tasks  
- Review assessment results  
- Prepare VM sizes and storage  
- Create networks, subnets, NSGs  
- Set up backup and rollback plan  
- Notify teams about migration timing  

### Migration steps  
1. Migrate **WEB01** and **WEB02**  
   - Test web pages in Azure  
2. Migrate **APP01**  
   - Test API communication  
3. Migrate **SQL01**  
   - Update connection strings  
   - Test full workflow  

### DNS updates  
Update DNS records to point to new Azure IPs.

### Connection string changes  
APP01 must be updated to connect to SQL in Azure.

### Load balancer steps  
Set up Azure Load Balancer and add both web servers.

### SQL migration notes  
Choose the right SQL option and test the database after migration.

### Post-migration validation checklist  
- Web pages load correctly  
- API works  
- Database connection works  
- Backups running  
- Monitoring active  
- Firewall rules correct  

### Back-out plan  
If something goes wrong:  
- Switch DNS back to on-premises  
- Power on old servers  
- Restore the original database if required  

---

## Task 6 – Migration Waves  

| Wave | Servers         | Reason |
|------|-----------------|--------|
| Wave 1 | WEB01, WEB02 | Stateless and easy to move; rollback simple |
| Wave 2 | APP01 | Depends on web tier; move after web servers |
| Wave 3 | SQL01 | Highest risk; move last |

---

## Conclusion  
In this lab, I created a clear migration plan for Tailwind Traders based on class steps. I documented the discovery setup, assessment planning, dependency analysis, and validation process. I also prepared a simple runbook and grouped the servers into migration waves. This helped me understand how companies plan and organize real migrations to Azure in a safe and structured way.