# Lab 6: Cloud Resource Comparison Across AWS, Azure, and Google Cloud 
Name: Rohan Surti (surt0008) [041164260] 
---
For this assignment, I compared 30 common cloud services across the three main cloud providers- **Amazon Web Services (AWS)**, **Microsoft Azure**, and **Google Cloud Platform (GCP)**.  

---
| # | Description | AWS (Service Name) | Azure (Service Name) | Google Cloud (Service Name) |
|----|-------------|--------------------|----------------------|----------------------------|
| 1 | Scalable virtual machines for running applications | Amazon EC2 | Azure Virtual Machines | Compute Engine |
| 2 | Object storage for backups / static website content | Amazon S3 | Azure Blob Storage | Cloud Storage |
| 3 | Managed relational DB (MySQL/Postgres/SQL Server) | Amazon RDS | Azure Database for MySQL / PostgreSQL / SQL Database | Cloud SQL |
| 4 | Serverless compute (run code on events) | AWS Lambda | Azure Functions | Cloud Functions |
| 5 | Isolated virtual networks | Amazon VPC | Azure Virtual Network (VNet) | Virtual Private Cloud (VPC) |
| 6 | Content Delivery Network (CDN) | Amazon CloudFront | Azure CDN / Azure Front Door | Cloud CDN |
| 7 | Managed NoSQL, low-latency, high-scale | Amazon DynamoDB | Azure Cosmos DB | Cloud Bigtable |
| 8 | Block storage (persistent disks for VMs) | Amazon Elastic Block Store | Azure Managed Disks | Persistent Disk |
| 9 | Managed Kubernetes orchestration | Amazon EKS | Azure Kubernetes Service (AKS) | Google Kubernetes Engine (GKE) |
| 10 | User access + encryption key management | AWS IAM + AWS KMS | Azure Active Directory + Azure Key Vault | Cloud IAM + Cloud KMS |
| 11 | Platform that automates app deployment & scaling (PaaS) | AWS Elastic Beanstalk  | Azure App Service | App Engine / Cloud Run |
| 12 | Monitoring & logging for apps + infra | Amazon CloudWatch | Azure Monitor / Log Analytics | Cloud Monitoring + Cloud Logging |
| 13 | Domain name system (DNS) | Amazon Route 53 | Azure DNS | Cloud DNS |
| 14 | Load balancing across targets | Elastic Load Balancing  | Azure Load Balancer / Application Gateway | Cloud Load Balancing |
| 15 | Automatic scaling of infrastructure | EC2 Auto Scaling | Virtual Machine Scale Sets + Autoscale | Autoscaler (Instance Groups) |
| 16 | Message queuing between app components | Amazon SQS | Azure Service Bus / Storage Queues | Cloud Pub/Sub / Cloud Tasks |
| 17 | Managed real-time data streaming | Amazon Kinesis | Azure Event Hubs | Cloud Pub/Sub / Dataflow |
| 18 | Managed, scalable data warehouse for analytics | Amazon Redshift | Azure Synapse Analytics | BigQuery |
| 19 | Orchestrate workflows / step-based automation | AWS Step Functions | Azure Logic Apps / Durable Functions | Cloud Workflows |
| 20 | Integrate/migrate/transform/move data across systems | AWS DMS / AWS Glue | Azure Data Factory | Dataflow / Datastream / Data Fusion |
| 21 | Data catalog & governance (metadata) | AWS Glue Data Catalog / Lake Formation | Microsoft Purview | Data Catalog |
| 22 | ML & AI platform + pre-built APIs | Amazon SageMaker + AI Services | Azure Machine Learning | Vertex AI + AI APIs |
| 23 | Define/deploy infra as code | AWS CloudFormation | Azure Resource Manager (ARM) | Deployment Manager / Terraform |
| 24 | Fully managed CI/CD pipelines | AWS CodePipeline + CodeBuild | Azure DevOps Pipelines / GitHub Actions | Cloud Build + Cloud Deploy |
| 25 | Desktop-as-a-Service (virtual desktops) | Amazon WorkSpaces | Azure Virtual Desktop | Cloud Workstations |
| 26 | Backup & disaster recovery (backups, replicas) | AWS Backup + Elastic Disaster Recovery | Azure Backup + Azure Site Recovery | Backup and DR (Google Cloud) |
| 27 | Big-data analytics (store/process/analyze large/real-time datasets) | Amazon EMR | Azure HDInsight / Databricks / Synapse | Dataproc / Dataflow / BigQuery |
| 28 | Shared file storage (file systems) | Amazon EFS / FSx | Azure Files / NetApp Files | Filestore |
| 29 | Media transcoding / streaming / processing | AWS Elemental Media Services | Azure Media Services | Transcoder API / Media Solutions |
| 30 | Real-time notifications, emails, or SMS | Amazon SNS / SES | Azure Communication Services / Notification Hubs | Firebase Cloud Messaging + partners (SendGrid, Twilio) |

---

### 1. Key Similarities  

Nearly all services on one cloud have **equivalents** on the other two.

Examples include: - 
- **Virtual Machines:** You can create and manage virtual servers using AWS EC2, Azure Virtual Machines, and Google Compute Engine.  
- **Object Storage:** Files, backups, and website data are stored on AWS S3, Azure Blob Storage, and Google Cloud Storage.  
- **Serverless Computing:** You can run code without having to worry about managing servers with AWS Lambda, Azure Functions, and Google Cloud Functions.  
- **Kubernetes Services:** EKS, AKS, and GKE are the three managed Kubernetes platforms.  

The basic purpose of the services is the same despite the differences in names and dashboards. Understanding one cloud makes understanding the others easier because the fundamental concepts remain the same.   

---

### 2. Key Differences  

Even though they offer similar things, each cloud provider has its own strengths and style.  

- **AWS** is the most mature and offers the most services. Users have a great deal of control and customization options. For instance, AWS offers numerous deployment tools and a variety of storage types, including S3, EFS, and Glacier. 

- Active Directory, Office 365, Windows, and other Microsoft products are all excellent partners for **Azure**. Businesses that already use Microsoft software frequently use it.  

- **Google Cloud** is more focused on AI and data analytics. For analyzing big datasets or creating machine learning models, BigQuery and Vertex AI are incredibly effective and user-friendly tools.  

- Another difference is how each cloud handles things like pricing and automation.  
AWS gives very detailed pricing options, Azure offers strong hybrid cloud support, and Google focuses on automation and simplicity.  

---

### 3. Unique Features  

Each provider has something special  
- **AWS** is great for enterprises that need many different services and advanced configurations.  
- **Azure** is strong for companies using Windows Server or Microsoft 365 — it easily connects with on-premises systems.  
- **Google Cloud** stands out for **BigQuery**, which is one of the fastest data analytics tools, and for **AI/ML integration** through Vertex AI.  

These unique features make each platform better for different use cases.  
For example, a company focusing on AI might prefer Google Cloud, while a big enterprise might choose AWS for flexibility, and an organization using Microsoft products might stick with Azure.  

---

### 4. Naming Conventions  

One big takeaway from this comparison is how **naming conventions differ**:  
- **AWS** usually uses technical names like “Amazon S3” or “Elastic Compute Cloud (EC2)”.  
- **Azure** uses clear, descriptive names that start with “Azure,” like “Azure Virtual Machines” or “Azure Blob Storage.”  
- **Google Cloud** uses short and simple names like “Compute Engine,” “Cloud Storage,” or “BigQuery.”  

So basically, AWS names sound more technical, Azure names sound like Microsoft products, and Google Cloud names sound clean and modern.  

---

### 5. Conclusion  

In short, all three cloud providers offer similar building blocks -compute, storage, databases, networking, AI, and DevOps.  
The main differences are in integration, user experience, and naming.  

