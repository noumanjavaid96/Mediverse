# Test Plan: Mediverse

## 1. Introduction
This document outlines the testing strategy for the Mediverse platform, focusing on ensuring quality for the multi-tenant architecture and the comprehensive feature set for all user roles.

## 2. Testing Scope

### 2.1 In-Scope
*   **Functional Testing:** End-to-end testing of all user stories for Patient, Doctor, Hospital Admin, and Super Admin roles.
*   **Multi-Tenancy Testing:** Specific testing to ensure data isolation between tenants.
*   **API Testing:** All API endpoints, including performance, security, and tenant data access rules.
*   **Third-Party Integration Testing:** Testing integrations with Agora, Stripe/PayPal, RxNorm, etc.
*   **Security & Compliance Testing:** Vulnerability scanning, penetration testing (post-MVP), and testing against HIPAA compliance requirements.
*   **User Acceptance Testing (UAT):** Client-led testing to validate business workflows.

## 3. Testing Levels
1.  **Unit Testing:** Developers will write unit tests for all backend and frontend components.
2.  **Integration Testing:** QA will test the interaction between microservices and with third-party APIs.
3.  **System Testing:** End-to-end testing of the complete system by QA.
4.  **UAT:** Carried out by the client (Salman's team) to ensure business requirements are met.

## 4. High-Level Test Scenarios

### 4.1 Multi-Tenancy
*   Verify that a Hospital Admin from Hospital A cannot see any data (doctors, patients, appointments) from Hospital B.
*   Verify that a Super Admin can see data across all tenants.
*   Verify that a search performed by a user in Tenant A does not return results from Tenant B.

### 4.2 Patient Portal
*   Verify the end-to-end appointment booking and payment flow.
*   Verify that a patient can successfully join a telehealth session.
*   Verify that a patient can view their own EHR data but not others'.

### 4.3 Doctor Portal
*   Verify that a doctor can create and edit an encounter note, and it is saved correctly.
*   Verify the e-prescribing workflow, including searching for a drug from RxNorm.
*   Verify that a doctor's availability changes are reflected in the patient booking portal in real-time.

### 4.4 Hospital Admin Portal
*   Verify that a Hospital Admin can successfully onboard a new doctor.
*   Verify that a custom booking link correctly filters the list of doctors for the patient.

### 4.5 Super Admin Portal
*   Verify that a Super Admin can successfully onboard a new hospital.
*   Verify that subscription management changes are correctly applied to a tenant.

## 5. Defect Management
*   **Tool:** Jira or a similar bug tracking system.
*   **Priority Levels:**
    *   **P0 - Blocker:** Prevents major functionality; no workaround. Must be fixed within 24 hours.
    *   **P1 - Critical:** Major functionality is broken, but a workaround exists.
    *   **P2 - Major:** A feature is not working as expected.
    *   **P3 - Minor:** UI issues or other minor bugs.
*   **Exit Criteria for MVP:** All P0 and P1 bugs must be resolved. Over 95% of P2 bugs must be resolved.
