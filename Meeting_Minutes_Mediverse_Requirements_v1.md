# Meeting Minutes & Consolidated Requirements: Mediverse
**Date:** July 15, 2025
**Topic:** Review of Mediverse Requirements Version 1

## 1. Executive Summary
The purpose of this document is to consolidate the comprehensive requirements for the Mediverse platform, as provided on July 15, 2025. The project's goal is to develop a multi-tenant SaaS platform with a fully functional MVP delivered by September 1st, focusing on built-in EHR, telehealth, and e-prescribing capabilities.

This document serves as the single source of truth for the project's scope and will be the basis for the discovery phase, technical design, and project planning. A second version of requirements is expected from the client by July 16, 2025.

## 2. Core Platform Vision
*   **Platform:** Multi-tenant SaaS platform for hospital systems.
*   **Core Features:** EHR, telehealth, e-prescribing.
*   **Target Audience:** Hospitals, Physicians, and Patients.
*   **Key Goal:** Deliver a functional MVP by September 1st.

## 3. User Roles
The platform will be built to serve the following key user roles:
*   **Super Admin (Platform Owner)**
*   **Hospital Admin (Super User for each Hospital/Tenant)**
*   **Doctor (Healthcare Provider)**
*   **Patient (Service Recipient)**

---
## 4. Consolidated Feature Requirements

### A. Patient Modules
| Feature | Description |
| :--- | :--- |
| **Sign Up / Sign In / Forgot Password** | Self-registration via email/phone; secure authentication with optional 2FA; password reset via OTP/email. |
| **Complete Profile** | Enter demographics, medical history, allergies, medications, and optional insurance/emergency contact info. |
| **Find a Doctor** | Filter doctors by hospital, specialty, availability, language, gender; view profiles and reviews. |
| **Book Appointment** | Select date/time; upload documents; choose consultation type (telehealth/in-person); make payments via Stripe/PayPal. |
| **Booking via Custom Hospital Link** | Patients can arrive via hospital-specific URLs that pre-filter the booking flow. |
| **Join Telehealth Session** | Secure video/audio call via Agora; includes a waiting room and access to doctor info. |
| **EHR Access (Read-Only)** | View clinical notes; download prescriptions; review follow-up recommendations. |
| **History & Records** | View complete appointment history and track prescriptions. |
| **Notifications** | Reminders for appointments, new messages, and updates on records. |
| **Settings & Logout** | Update profile, manage password, set communication preferences, and log out. |

### B. Doctor Modules
| Feature | Description |
| :--- | :--- |
| **Invitation-Based Sign In** | Doctors are onboarded via email invitation from a Hospital Admin. |
| **Profile Setup** | Upload certifications, add specialties, languages, availability, and biography. |
| **Dashboard** | View upcoming appointments and shortcuts to recent patients and messages. |
| **Patient List** | Searchable list of assigned patients with access to their clinical history. |
| **EHR Access** | Create and edit encounter notes (diagnoses, vitals, symptoms); upload reports. |
| **Telehealth** | Launch secure video consultations; access patient profile and take notes during the call. |
| **E--prescribing** | Generate and digitally sign prescriptions; use RxNorm for a standardized drug list. |
| **Availability Settings** | Define availability by day and slot duration; manage vacation dates. |
| **Notifications** | Reminders about appointments and system-wide alerts. |

### C. Hospital Admin Modules (Web App Only)
| Feature | Description |
| :--- | :--- |
| **Sign Up / Sign In / Forgot Password** | Secure access to a dedicated hospital portal. |
| **Onboarding Workflow** | Enter hospital details, set up departments, and configure policies. |
| **Doctor & Staff Management** | Add/assign doctors; manage credentials and availability; add support staff with role-based permissions. |
| **Booking Link Management** | Generate and customize unique hospital-specific booking URLs; track clicks and conversions. |
| **Appointment Oversight** | View and manage all appointments; reassign or cancel on behalf of doctors. |
| **Patient Directory** | View all registered patients under the hospital. |
| **Reports** | Track hospital performance metrics and department-wise analytics; download reports (CSV/PDF). |

### D. Super Admin Modules
| Feature | Description |
| :--- | :--- |
| **Sign Up / Sign In / Forgot Password** | Secure, internal-only access with enhanced security (2FA). |
| **Dashboard Overview** | High-level summary of all onboarded hospitals, users, revenue, and system health. |
| **Hospital Management** | Add, edit, and remove hospitals; assign subscription plans and monitor tenant activity. |
| **Subscription Management** | Create and manage pricing plans, billing cycles, and trials via Stripe/PayPal. |
| **User Activity Logs** | Audit logs of all critical actions, searchable by user, hospital, or time range. |
| **Reports & Analytics** | Aggregate performance data and usage metrics across all tenants. |

---
## 5. Additional Requirements (Received July 12, 2025)
These items will be further discussed and scoped during the Discovery Phase.

| Module | Functionality |
| :--- | :--- |
| **Call Center / PBX Integration** | Integration with RingCentral/GetWeave; incoming call pop-ups; call queue management; call recording. |
| **Review Management System** | Automated review collection post-consultation; integration with Google/Facebook; analytics dashboard. |
| **AI Use Cases** | AI-powered appointment scheduling; predictive analytics for optimal times; workflow automation. |
| **Eligibility Verification** | Real-time insurance eligibility checks; integration with payer databases. |

---
## 6. Documentation Expectations
The following documents will be produced as part of the project deliverables:
1.  **Project Charter**
2.  **Requirements Document**
3.  **Project Plan**
4.  **Wireframes/Prototypes**
5.  **Technical Architecture Diagram**
6.  **Test Plan**

---
## 7. Next Steps
*   Await the second version of requirements, expected by July 16, 2025.
*   Schedule a meeting to discuss these consolidated requirements at 2:30 PM today.
*   Begin the formal Discovery Phase to refine scope, effort, and integration impact.
