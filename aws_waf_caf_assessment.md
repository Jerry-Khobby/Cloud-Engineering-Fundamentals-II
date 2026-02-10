# **AWS Well-Architected & Cloud Adoption Framework Lab Solution**

---

## **Task 1 – Review the Existing Architecture**

**Workload Components:**

* **Frontend:** Web application hosted on a single on-premises server.
* **Backend:** Relational database (e.g., MySQL) on on-premises server.
* **Networking:** Single network, public IP, basic firewall rules.
* **Storage:** Local disk storage for database and static content.

**Potential Risks / Weaknesses:**

1. **No backup strategy:** Database and application data at risk.
2. **Single-AZ deployment:** No high availability, single point of failure.
3. **Open security groups/firewall:** Vulnerable to attacks.
4. **Manual scaling:** Unable to handle traffic spikes efficiently.
5. **No monitoring or logging:** Hard to detect failures or performance issues.

---

## **Task 2 – WAF Assessment Table**
| Pillar                 | Observation (Strength)        | Improvement Needed                         | Recommendation                                            | Supporting AWS Service                               |
| ---------------------- | ----------------------------- | ------------------------------------------ | --------------------------------------------------------- | ---------------------------------------------------- |
| Operational Excellence | Basic processes in place      | Limited monitoring and automation          | Implement automated deployment and monitoring             | AWS CloudWatch, AWS CloudTrail, AWS CodePipeline     |
| Security               | Existing firewall rules       | Open ports and no IAM enforcement          | Implement least-privilege access, secure endpoints        | AWS IAM, Security Groups, AWS WAF                    |
| Reliability            | Single server works currently | No redundancy; single AZ                   | Deploy multi-AZ architecture with failover                | Amazon RDS Multi-AZ, Elastic Load Balancer           |
| Performance Efficiency | Application works at low load | Cannot auto-scale with traffic             | Implement auto-scaling and optimized resource types       | Auto Scaling Groups, Amazon EC2, Amazon Aurora       |
| Cost Optimization      | Minimal on-prem costs         | Inefficient resource use; no cost tracking | Use right-sized instances, leverage reserved/spot pricing | AWS Cost Explorer, AWS Savings Plans, Spot Instances |


-	 

---

## **Task 3 – AWS Cloud Adoption Framework (CAF) Readiness Summary**

### **1. Business Perspective**

The organization aims to migrate its two-tier web application to AWS to increase scalability and reliability. Business readiness shows a clear ROI objective but lacks formal KPIs for cloud adoption success. **Key actions:** Define metrics for uptime, customer satisfaction, and operational cost reduction. Ensure executive sponsorship and alignment with strategic goals.

### **2. People Perspective**

Staff have some experience managing on-premises servers but limited cloud knowledge. Training and skill-building are required. **Key enablers:** Cloud certification programs, hands-on labs, and creation of a cloud center of excellence (CoE) to provide expertise and governance.

### **3. Governance Perspective**

Current governance is ad-hoc with no cloud policies. Compliance and change management processes are weak. **Key actions:** Establish cloud governance policies, define budget controls, enforce tagging standards, and implement monitoring and audit processes via AWS Organizations and Config.

### **4. Platform Perspective**

Existing application architecture is monolithic and single-AZ. **Key actions:** Re-architect for scalability, leveraging managed services (Amazon RDS, S3, ELB, Auto Scaling) to increase reliability and performance while reducing operational overhead.

### **5. Security Perspective**

Security practices are basic with open firewall rules and no IAM enforcement. **Key enablers:** Implement least-privilege IAM roles, enable encryption in transit and at rest, use AWS WAF for web protection, and monitor using AWS Security Hub and GuardDuty.

### **6. Operations Perspective**

Current operations rely on manual tasks with no centralized monitoring or alerting. **Key actions:** Implement centralized logging and monitoring with CloudWatch, automate operational workflows with AWS Systems Manager, and set up automated backups and recovery procedures.

---

## **Task 4 – Improved Architecture Description**

**Proposed Architecture:**

* **Frontend (Web Tier):**

  * Amazon EC2 instances in an **Auto Scaling Group** across **multiple AZs**
  * **Elastic Load Balancer** to distribute traffic

* **Backend (Database Tier):**

  * Amazon RDS (MySQL or Aurora) **Multi-AZ deployment** for high availability
  * Automated **backups and snapshots** enabled

* **Storage & Static Content:**

  * Amazon S3 for static assets
  * Optional CloudFront CDN for global delivery

* **Security:**

  * IAM roles and policies for least-privilege access
  * Security Groups and NACLs to restrict traffic
  * AWS WAF to protect against common web exploits

* **Monitoring & Operations:**

  * AWS CloudWatch for metrics and alarms
  * AWS CloudTrail for audit logs
  * AWS Systems Manager for operational automation

* **Cost Optimization:**

  * Use right-sized EC2 instances, RDS reserved instances
  * Enable auto-scaling to reduce idle resources
  * Monitor with AWS Cost Explorer

**Architecture Diagram:**
[Architecture](./architecture_diagram.png)

---

## **Reflection**

This lab reinforced the importance of **structured evaluation using AWS frameworks**. Applying the Well-Architected Framework helped identify both strengths and weaknesses across operational, security, reliability, performance, and cost pillars. I learned how specific AWS services—like RDS Multi-AZ, Auto Scaling, and CloudWatch—directly address these weaknesses. The CAF analysis highlighted organizational readiness, showing that technical solutions alone are insufficient without addressing people, governance, and operational processes. Designing the improved architecture taught me to integrate **best practices with practical constraints**, ensuring high availability, security, and cost efficiency. Overall, I gained hands-on insight into how cloud architects **critically evaluate workloads**, recommend improvements, and communicate solutions effectively, bridging technical architecture and organizational readiness. This exercise will guide real-world cloud migrations by emphasizing the holistic approach needed for successful AWS adoption.


