# UPV CRS 2.0

This project aims to replace the existing CRS with CRS 2.0. The following section outlines the technical details of the proposed web-based system, including its architecture, technology stack, and deployment strategy.

**Course:** CMSC 126 Activity: Unit 5-6

---

## Table of Contents
- [System Summary](#system-summary)
- [Tech Stack](#tech-stack)
- [Hosting](#hosting)
- [System Design](#system-design)
- [Mockups](#mockups)

---

## System Summary
**CRS 2.0** is a web-based student registration and information system designed to replace the existing CRS used by the University of the Philippines Visayas. The system aims to provide a modern and user-friendly experience for students, faculty, staff, and administrators by updating university processes such as access to student information. It still supports the core functionalities of the original website, with added functionalities such as document access, announcements, calendar viewing, student information management, teacher evaluation, enrollment tracking, and more.

### Team Members
- Gabrielle Sumergido
- Christie Jude Tarre
- Claire Dane Vincoy

---

## Tech Stack

- Frontend: ReactJS
- Backend: Spring Boot (Java)
- Database: PostgreSQL


### Frontend Tools

The frontend of the CRS 2.0 will be developed using React, a component-based JavaScript library suitable for building multi-functional and data-driven web applications through its efficient rendering and reusable UI components. 

**Key Advantages**
- **Component-Based Architecture**: UI elements such as login forms and student dashboards can be developed as reusable and independent components to improve maintainability and scalability.
  
- **Virtual DOM**: It updates only the necessary parts of the user interface instead of reloading the entire page, improving performance during high-traffic such as enrollment period.
  
- **Large Ecosystem**: React provides a wide range of tools and libraries for building scalable and interactive web applications.
  
- **TypeScript Support**: It enhances reliability by catching errors at compile time rather than at runtime.
  
- **Seamless API Integration**: React interacts with the Spring Boot backend framework through RESTful APIs, enabling the frontend to retrieve and use backend services for data exchange. 

### Backend Tools

The backend of the CRS 2.0 will be implemented using Java with Spring Boot, a framework which simplifies the development process by reducing manual configuration in Java-based web applications. This allows the team to focus on building core system features rather than managing infrastructure and repetitive standard code. 

**Key Advantages**
- **Auto-Configuration**: This reduces manual setup and configuration errors through auto-configuration, allowing more focus on developing core functionalities.
  
- **Embedded Server**: It uses an embedded Tomcat server, which reduces the need for separate web server installation.

- **Spring Data JPA**: It simplifies the database interactions by managing relationships between entities.

- **Spring Security**: It ensures strict access control over sensitive data by implementing authentication and authorization mechanisms.

- **Production-Ready**: Spring Boot includes features such as health checks, logging, and error handling that help monitor and maintain web applications.

### Database

The system will use **PostgreSQL** as its primary relational database. PostgreSQL is appropriate for academic data management because of its reliability and ability to handle complex queries. Moreover, it has strong ACID (Atomicity, Consistency, Isolation, and Durability) compliance, ensuring integrity and consistency of data throughout all transactions. 

**Key Advantages**
- **ACID Compliance**: It ensures that all transactions are processed reliably, preventing data corruption even during system failures.

- **Complex Query Support**: It efficiently handles advanced queries such as retrieving student records, class availability, and enrollment status across multiple tables. 

- **Cost-Free**: It is open-source and free to use, making it a practical choice for the team.

- **Security**: It provides built-in security features such as role-based access control and row-level security. It ensures that sensitive data is only accessible to authorized users.

- **Scalability**: It supports large and growing datasets without performance degradation.

### Other Tools

- **Git / GitHub** is used for version control and team collaboration.

- **Figma** is used for mockup creation and UI design. 

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

## System Design

### Sitemap

### Flowchart

---

## Mockups

### Homepage

### Student Page

### Schedule / Conflict Check Screen

### Additional Page
