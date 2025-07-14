# Requirements Document: Mediverse (Version 1)

## 1. Introduction
This document outlines the requirements for the Mediverse multi-tenant SaaS platform. It is based on the initial requirements document (Version 1) and is subject to refinement during the Discovery Phase and upon receipt of the second version of requirements (expected July 16, 2025).

## 2. User Roles
The platform will support the following user roles:
*   **Super Admin (Platform Owner)**
*   **Hospital Admin (Tenant Super User)**
*   **Doctor (Healthcare Provider)**
*   **Patient (Service Recipient)**

---

## 3. Patient Modules

### 3.1 Authentication
*   **REQ-P-001:** Patients can sign up using an email address or phone number.
*   **REQ-P-002:** Secure sign-in with password. Optional two-factor authentication.
*   **REQ-P-003:** Forgot password functionality using OTP via email or SMS.

### 3.2 Profile Management
*   **REQ-P-004:** Patients can enter and edit demographic information (age, gender, contact).
*   **REQ-P-005:** Patients can enter and edit medical history, allergies, and current medications.
*   **REQ-P-006:** Optional fields for insurance information and emergency contact.

### 3.3 Doctor & Appointment Management
*   **REQ-P-007:** Patients can search for doctors and filter by hospital, specialty, availability, language, and gender.
*   **REQ-P-008:** Patients can view doctor profiles, including reviews and consultation fees.
*   **REQ-P-009:** Patients can book appointments by selecting an available date/time slot.
*   **REQ-P-010:** Patients can upload relevant documents prior to an appointment.
*   **REQ-P-011:** Patients can choose the consultation type (telehealth or in-person).
*   **REQ-P-012:** The system will integrate with a payment gateway (Stripe/PayPal) for consultation payments.
*   **REQ-P-013:** Patients will receive booking confirmation and reminders.
*   **REQ-P-014:** The system will support booking via custom, hospital-specific links that pre-filter doctors/services.

### 3.4 Telehealth & EHR
*   **REQ-P-015:** The system will provide a secure video/audio session for telehealth using Agora.
*   **REQ-P-016:** Patients will have read-only access to their EHR, including past clinical notes, prescriptions, and follow-up recommendations.

### 3.5 History & Notifications
*   **REQ-P-017:** Patients can view their complete appointment history and track prescriptions.
*   **REQ-P-018:** The system will send notifications for appointment reminders, messages, and record updates.

---

## 4. Doctor Modules

### 4.1 Onboarding & Profile
*   **REQ-D-001:** Doctors are onboarded via an invitation from a Hospital Admin.
*   **REQ-D-002:** Doctors can set up their profile, including certifications, specialties, languages, and biography.
*   **REQ-D-003:** Doctors can define their availability, including slot durations and vacation dates.

### 4.2 Dashboard & Patient Management
*   **REQ-D-004:** A dashboard will display upcoming appointments and shortcuts to recent patients.
*   **REQ-D-005:** Doctors can search their assigned patient list and access clinical histories.

### 4.3 EHR & E-prescribing
*   **REQ-D-006:** Doctors can create and edit encounter notes, including diagnoses, vitals, and symptoms.
*   **REQ-D-007:** Doctors can generate and digitally sign e-prescriptions.
*   **REQ-D-008:** The e-prescribing system will use the RxNorm database for a standardized drug list.

### 4.4 Telehealth
*   **REQ-D-009:** Doctors can launch secure telehealth sessions and access the patient's profile during the call.
*   **REQ-D-010:** The telehealth interface will include in-session note-taking and a timer.

---

## 5. Hospital Admin Modules (Web App Only)

### 5.1 Onboarding & Management
*   **REQ-HA-001:** Hospital Admins will have access to a dedicated, secure portal.
*   **REQ-HA-002:** Admins can onboard their hospital by entering details, setting up departments, and configuring policies.
*   **REQ-HA-003:** Admins can add, assign, and manage doctors and support staff, including role-based permissions.

### 5.2 Booking Link Management
*   **REQ-HA-004:** Admins can generate and customize unique, hospital-specific booking links (by department, doctor, or service type).
*   **REQ-HA-005:** Admins can track clicks and bookings from each link.

### 5.3 Operations & Reporting
*   **REQ-HA-006:** Admins can view and manage all appointments for their hospital.
*   **REQ-HA-007:** Admins can view a directory of all patients registered with their hospital.
*   **REQ-HA-008:** The system will provide basic reports on hospital performance and department-wise analytics.

---

## 6. Super Admin Modules

### 6.1 Platform Management
*   **REQ-SA-001:** Super Admins will have a secure, internal-only portal with 2FA.
*   **REQ-SA-002:** A dashboard will provide a high-level overview of all onboarded hospitals, users, revenue, and system health.
*   **REQ-SA-003:** Super Admins can add, edit, and remove hospitals and assign subscription plans.

### 6.2 Subscription & Auditing
*   **REQ-SA-004:** Super Admins can create and manage pricing plans, billing cycles, and trials.
*   **REQ-SA-005:** The system will provide detailed audit logs of all critical actions, searchable by user, hospital, or time range.

---

## 7. Additional Requirements (To be scoped during Discovery)

### 7.1 Call Center / PBX Integration
*   **REQ-ADD-001:** Integration with RingCentral or GetWeave.
*   **REQ-ADD-002:** Incoming call pop-ups with patient records.
*   **REQ-ADD-003:** Call queue management and call recording.

### 7.2 Review Management System
*   **REQ-ADD-004:** Automated review collection post-consultation.
*   **REQ-ADD-005:** Integration with Google and Facebook.

### 7.3 AI Use Cases
*   **REQ-ADD-006:** AI-powered appointment scheduling and reminders.
*   **REQ-ADD-007:** Predictive analytics for optimal appointment times.

### 7.4 Eligibility Verification
*   **REQ-ADD-008:** Real-time insurance eligibility checks.
