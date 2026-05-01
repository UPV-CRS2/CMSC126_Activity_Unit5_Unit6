# UPV CRS 2.0

This project aims to replace the existing CRS with CRS 2.0. The following section outlines the technical details of the proposed web-based system, including its architecture, technology stack, and deployment strategy.

**Course:** CMSC 126 Activity: Unit 5-6

---

## Table of Contents
- [System Summary](#system-summary)
- [Tech Stack](#tech-stack)
- [Hosting](#hosting)
- [Mockups](#mockups)

---

## System Summary

### Team Members
- Kiano Michiko Soliva
- Gabrielle Sumergido
- Christie Jude Tarre
- Claire Dane Vincoy

---

## Tech Stack

### Frontend Tools

### Backend Tools

### Database

### Other Tools (Optional)

---

## Hosting

CRS 2.0 will be hosted using **Amazon Web Services (AWS)** to leverage specialized tools tailored to our tech stack: **AWS Amplify** (Frontend), **AWS Elastic Beanstalk** (Backend), and **Amazon RDS** (Database). Furthermore, AWS also provides more tools and services optimal for robust scalability, which opens room for future development and expansion of CRS 2.0, in the event of its approval. 

### System Flow: How AWS hosting would work (simplified):
```
Student Browser (User Entry)
      ↓ HTTPS
AWS Amplify (Global CDN + React Hosting)
      ↓ API Calls (REST)
Elastic Load Balancer (Traffic Distribution)
      ↓
┌─────────────────────────────────────┐
│    Private VPC (Virtual Network)    │
│ AWS Elastic Beanstalk (Spring Boot) │
│         ↓              ↓            │
│   Amazon RDS        AWS IAM         │
│  (PostgreSQL)    (Access Control)   │
└─────────────────────────────────────┘
      ↓
  AWS CloudWatch (Performance Monitoring & Alerts)
  Amazon S3 (Automated DB Backups)
```

### Features, Safety, Reliability

- **Frontend Delivery (AWS Amplify)**: By hosting the React frontend on a Global Content Delivery Network (CDN), the UI remains fast and accessible even if the backend is under heavy load. This prevents the "white screen" effect students often face during high-traffic periods (enrollment, pre-registration, evaluation, etc.).
  
- **Secure Traffic Management (Elastic Load Balancer)**: The ELB serves as the front door. It handles SSL/TLS termination, ensuring all data is encrypted in transit. It also automatically reroutes traffic away from unhealthy server instances, maintaining system availability by distributing traffic to avoid server bottlenecks.
  
- **Infrastructure Isolation (Private VPC)**: To ensure maximum safety, the Spring Boot backend and PostgreSQL database are hidden within a Virtual Private Cloud (VPC). This makes the database unreachable from the public internet, neutralizing the risk of external hacking attempts and avoiding information leakage.
  
- **Automated Scalability (Elastic Beanstalk)**: The system uses Auto-scaling Groups to spin up additional backend capacity instantly for high traffic periods. Otherwise, It shrinks back down to regular session periods to ensure cost-efficiency.
  
- **High Availability (Amazon RDS Multi-AZ)**: Utilizing Multi-Availability Zone deployment so that if the primary database fails, AWS automatically switches to a standby replica in seconds and ensures that enrollment records are never lost and the system stays online. This provides automatic failover and data consistency.
  
- **Audit & Recovery**: Amazon S3 stores daily encrypted snapshots of the database, together with CloudWatch to monitor system errors in real-time. This allows the university to restore the entire system to a specific point in time in the event of a critical error and faster backtracking in locating the cause of it.


---

## Mockups

### Homepage

### Student Page

### Schedule / Conflict Check Screen

### Additional Page
