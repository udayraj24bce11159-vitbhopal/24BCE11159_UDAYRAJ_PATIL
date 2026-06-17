# Citizen Complaint Management System (CCMS)

##  Project Objective

The objective of this project is to develop a centralized Citizen Complaint Management System using Java 25, Spring Boot, and MongoDB. The system enables citizens to register and track complaints while allowing government departments and officers to manage, assign, and resolve them efficiently.

The application implements CRUD operations, RESTful APIs, and relationship mapping between Citizens, Complaints, Departments, Officers, and Complaint History. It also provides dashboard reports and complaint tracking to improve transparency, accountability, and service delivery.

---

## Problem Statement

Traditional complaint management systems often rely on manual records and disconnected processes, making it difficult to track complaints, monitor department performance, and maintain transparency.

The Citizen Complaint Management System addresses these challenges by providing a centralized platform for complaint registration, status tracking, officer assignment, and complaint resolution using Spring Boot and MongoDB.

##  Project Overview

The Citizen Complaint Management System (CCMS) is a backend application developed using **Java 25**, **Spring Boot 3.5.x**, and **MongoDB 8.3**. The system provides a centralized platform for citizens to register complaints related to public services such as water supply, electricity, road maintenance, garbage collection, and street lighting.
Government departments and officers can manage complaints, assign responsibilities, update complaint status, and monitor complaint resolution through REST APIs tested using Postman.

---

## Technology Stack

| Component            | Technology             |
| -------------------- | ---------------------- |
| Programming Language | Java 25                |
| Framework            | Spring Boot 3.5.x      |
| Database             | MongoDB 8.3            |
| Build Tool           | Maven                  |
| IDE                  | IntelliJ IDEA 2026.1.2 |
| API Testing          | Postman                |
| Database Tool        | MongoDB Compass        |
| Server Port          | 8081                   |

---

##  System Architecture

```text
Postman Client
      │
      ▼
Controller Layer
      │
      ▼
Service Layer
      │
      ▼
Repository Layer
      │
      ▼
MongoDB Database
```

### Architecture Flow

* Controller Layer handles HTTP requests and responses.
* Service Layer contains business logic.
* Repository Layer performs MongoDB operations.
* MongoDB stores all application data as documents.

---

##  Project Structure

```text
src/main/java
└── com
    └── cms
        ├── CitizenComplaintApplication.java
        │
        ├── config
        │
        ├── controller
        │   ├── AuthController.java
        │   ├── CitizenController.java
        │   ├── ComplaintController.java
        │   ├── DepartmentController.java
        │   ├── DashboardController.java
        │   └── OfficerController.java
        │
        ├── dto
        │
        ├── exception
        │
        ├── model
        │   ├── Citizen.java
        │   ├── Complaint.java
        │   ├── ComplaintHistory.java
        │   ├── Department.java
        │   └── Officer.java
        │
        ├── repository
        │   ├── CitizenRepository.java
        │   ├── ComplaintHistoryRepository.java
        │   ├── ComplaintRepository.java
        │   ├── DepartmentRepository.java
        │   └── OfficerRepository.java
        │
        └── service
            ├── CitizenService.java
            ├── ComplaintService.java
            ├── DepartmentService.java
            ├── DashboardService.java
            └── OfficerService.java
```

## Database Design

### Collection: Citizen

```json
{
  "_id": "6a2e336ccbaad8f7486e33ee",
  "name": "Uday Patil",
  "email": "uday@gmail.com",
  "mobile": "9876543210"
}
```

### Collection: Department

```json
{
  "_id": "6a2ee2f1002da6b42b742efb",
  "departmentName": "Water Supply"
}
```

### Collection: Officer

```json
{
  "_id": "6a2ee512002da6b42b742f01",
  "officerName": "Rajesh Kumar",
  "departmentId": "6a2ee2f1002da6b42b742efb"
}
```

### Collection: Complaint

```json
{
  "_id": "6a2e33d8cbaad8f7486e33ef",
  "title": "Water Leakage",
  "description": "Water leakage near Main Road",
  "status": "Pending",
  "citizenId": "6a2e336ccbaad8f7486e33ee",
  "departmentId": "WATER_DEPT_01"
}
```

---

## Relationship Mapping

### One Citizen → Many Complaints

```text
Citizen (1) ───────► Complaint (M)
```

### One Department → Many Complaints

```text
Department (1) ───────► Complaint (M)
```

### One Department → Many Officers

```text
Department (1) ───────► Officer (M)
```

---

##  Application Configuration

### application.properties

```properties
server.port=8081

spring.data.mongodb.uri=mongodb://localhost:27017/citizen_complaint_db
```

---

##  REST API Endpoints

### Citizen APIs

| Method | Endpoint           |
| ------ | ------------------ |
| POST   | /api/citizens      |
| GET    | /api/citizens      |
| GET    | /api/citizens/{id} |
| PUT    | /api/citizens/{id} |
| DELETE | /api/citizens/{id} |

### Department APIs

| Method | Endpoint              |
| ------ | --------------------- |
| POST   | /api/departments      |
| GET    | /api/departments      |
| PUT    | /api/departments/{id} |
| DELETE | /api/departments/{id} |

### Officer APIs

| Method | Endpoint           |
| ------ | ------------------ |
| POST   | /api/officers      |
| GET    | /api/officers      |
| PUT    | /api/officers/{id} |
| DELETE | /api/officers/{id} |

### Complaint APIs

| Method | Endpoint                                  |
| ------ | ----------------------------------------- |
| POST   | /api/complaints                           |
| GET    | /api/complaints                           |
| GET    | /api/complaints/{id}                      |
| PUT    | /api/complaints/{id}                      |
| DELETE | /api/complaints/{id}                      |
| PUT    | /api/complaints/{id}/assign/{officerId}   |
| PUT    | /api/complaints/{id}/status/{status}      |
| GET    | /api/complaints/status/{status}           |
| GET    | /api/complaints/citizen/{citizenId}       |
| GET    | /api/complaints/department/{departmentId} |

### Dashboard APIs

| Method | Endpoint                              |
| ------ | ------------------------------------- |
| GET    | /api/dashboard/total-complaints       |
| GET    | /api/dashboard/pending-complaints     |
| GET    | /api/dashboard/assigned-complaints    |
| GET    | /api/dashboard/resolved-complaints    |
| GET    | /api/dashboard/department-wise-report |

### Base URL

```text
http://localhost:8081
```

---

##  Setup & Installation

### Step 1: Clone Project

```bash
git clone <repository-url>
```

### Step 2: Navigate to Project

```bash
cd cms
```

### Step 3: Configure MongoDB

Ensure MongoDB 8.3 is running locally:

```text
mongodb://localhost:27017
```

### Step 4: Build Project

```bash
mvn clean install
```

### Step 5: Run Application

```bash
mvn spring-boot:run
```

Application starts on:

```text
http://localhost:8081
```

---

##  API Testing

All APIs are tested using Postman.

Testing includes:

* Create Operations
* Read Operations
* Update Operations
* Delete Operations
* MongoDB Data Verification
* Endpoint Validation

---

##  Expected Outcomes

* Centralized Complaint Management
* Easy Complaint Registration
* Complaint Status Tracking
* Efficient Department Management
* Improved Public Service Transparency
* Faster Complaint Resolution

---

##  Future Enhancements

* Authentication & Authorization
* Complaint Priority Levels
* Email Notifications
* SMS Notifications
* Image Upload Support
* Analytics Dashboard
* MongoDB Replication
* MongoDB Sharding

---

##  Developer Information

**Project Title:** Citizen Complaint Management System (CCMS)

**Developer:** Udayraj Patil

**Roll Number:** 24BCE11159

**Course:** B.Tech CSE Core

**Institution:** VIT Bhopal University

**Academic Year:** 2024–2028


