# AWS Well-Architected & Cloud Adoption Framework Lab

## Overview

This project demonstrates the evaluation and redesign of a two-tier web application migration to AWS using the **AWS Well-Architected Framework (WAF)** and the **AWS Cloud Adoption Framework (CAF)**. The goal is to ensure the application is **scalable, reliable, secure, cost-efficient, and operationally sound** from day one.

The lab includes:

* A **review of the existing architecture**
* A **WAF assessment table** showing strengths, weaknesses, and improvement recommendations
* A **CAF readiness summary** highlighting organizational readiness across six perspectives
* An **improved AWS architecture design** aligned with best practices
* A **reflection** on lessons learned

---

## Repository Contents

| File                           | Description                                                                                                       |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------- |
| `aws_waf_caf_assessment.md`    | Detailed lab report with Tasks 1–4, including WAF table, CAF summary, architecture description, and reflection.   |
| `architecture_diagram.png`     | Initial architecture diagram (optional reference).                                                                |
| `architecture_diagram_two.png` | Final improved AWS architecture diagram showing multi-AZ deployment, security, monitoring, and cost optimization. |

---

## How to Use

1. Review `aws_waf_caf_assessment.md` for a complete explanation of the project.
2. Open `architecture_diagram_two.png` in an image viewer or in Draw.io/Lucidchart to visualize the improved AWS architecture.
3. Use the diagrams and report as a reference for **AWS Well-Architected and CAF best practices**.

---

## Key AWS Services Used

* **Compute & Load Balancing:** EC2, Auto Scaling, Elastic Load Balancer
* **Database:** Amazon RDS (Multi-AZ)
* **Storage & Content Delivery:** S3, CloudFront
* **Security & Compliance:** IAM, Security Groups, WAF, GuardDuty, Security Hub
* **Monitoring & Operations:** CloudWatch, CloudTrail, Systems Manager
* **Cost Management:** Cost Explorer, Reserved & Spot Instances

---

## Reflection

This lab helped me understand how to **analyze cloud workloads**, identify strengths and weaknesses, and recommend improvements using AWS frameworks. It also highlighted the importance of combining **technical architecture with organizational readiness** to ensure successful cloud adoption.

