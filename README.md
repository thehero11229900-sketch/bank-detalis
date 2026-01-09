# bank-detalis

# Software Requirements Specification (SRS)
## Project: Bank Customer Management System

---

## 1. Introduction
### 1.1 Purpose
This document provides a detailed description of the software requirements for the **Customer Module** of the Banking System. It is intended for developers, project managers, and QA testers.

### 1.2 Scope
The system handles the digital lifecycle of a bank customer, including:
* Identity Verification (KYC)
* Profile Management
* Account Relationship Mapping
* Data Security and Compliance
* 

---

## 2. Functional Requirements

### 2.1 Customer Registration (UC-01)
* **Requirement:** The system shall allow bank employees to create a new customer profile.
* **Validation:** The system must validate that the customer is at least 18 years old.
* **Unique Identifier:** A unique **Customer ID (CIF)** must be generated automatically upon successful registration.

### 2.2 KYC Documentation (UC-02)
* **Requirement:** The system must support the upload of Identity Proof (Passport/ID) and Address Proof.
* **Format:** Supported formats include PDF, PNG, and JPG (Max size: 5MB).

### 2.3 Search and Retrieval (UC-03)
* **Requirement:** Staff must be able to search for customers using:
    * Customer ID
    * National ID / SSN
    * Phone Number
    * Full Name

---

## 3. Data Dictionary (Schema)

| Field Name | Data Type | Constraint | Description |
| :--- | :--- | :--- | :--- |
| `cust_id` | UUID | Primary Key | Unique internal system ID |
| `first_name` | VARCHAR(50) | Not Null | Customer's legal first name |
| `last_name` | VARCHAR(50) | Not Null | Customer's legal last name |
| `email` | VARCHAR(100) | Unique | Primary contact email |
| `tax_id` | VARCHAR(20) | Unique | SSN, PAN, or National Tax ID |
| `account_type` | ENUM | Savings, Current | Type of primary account |
| `created_at` | Timestamp | Default: Now | Date of onboarding |

---

## 4. Non-Functional Requirements

### 4.1 Security
* **Encryption:** Sensitive fields like `tax_id` must be encrypted using **AES-256**.
* **Authentication:** Multi-factor authentication (MFA) is required for staff accessing the database.

### 4.2 Performance
* **Response Time:** Customer search results must be returned within **< 2 seconds**.
* **Availability:** The system shall maintain **99.9% uptime**.

### 4.3 Scalability
* The database must support up to **1 million** concurrent customer records without performance degradation.

---

## 5. System Design (UML)



---

## 6. Compliance & Auditing
* **Audit Trail:** Every modification to a customer record must be logged with the User ID of the editor and a timestamp.
* **GDPR/Data Privacy:** The system must allow for "Data Portability" and "The Right to be Forgotten" (logical deletion).
