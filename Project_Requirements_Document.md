# Mediverse Telehealth Platform - Project Requirements Document

## 1. Introduction

This document outlines the project requirements for the Mediverse Telehealth Platform. The platform is designed to provide a comprehensive and user-friendly solution for telehealth consultations, including insurance verification, prescription management, and video calling.

## 2. Key Features

### 2.1. Insurance Verification

*   **API Integration:** The platform will be integrated with the pVerify API for real-time insurance eligibility verification.
*   **Conditional Booking:**
    *   Patients will be allowed to book urgent/same-day appointments without insurance verification.
    *   Insurance confirmation will be required for non-urgent appointments booked >24 hours in advance.
    *   Unverified bookings will be flagged for follow-up.
*   **Post-Booking Verification:**
    *   The system will automatically initiate insurance verification for unverified bookings within 24 hours.
    *   Staff will be alerted of failed verifications via the dashboard and webhooks.

### 2.2. Prescription Management

*   **API Integration:** The platform will be integrated with the DoseSpot API for e-prescribing, including drug database access and submission to pharmacies.
*   **E-Prescribing Workflow:** Providers will be able to electronically prescribe medications to patients during or after a virtual consultation.

### 2.3. Video Calling Service

*   **API Integration:** The platform will be integrated with the Agora API for high-quality, HIPAA-compliant video calling.
*   **Customizable UI:** The video calling interface will be customizable to match the Mediverse brand and to include features such as screen sharing, chat, and recording.

### 2.4. Emergency Telehealth Use Case

*   **Nurse-Initiated Visits:** Nurses will be able to initiate emergency virtual visits for patients.
*   **Real-Time Data Entry:** During the call, providers will be able to add/edit the patient's name, MRN, and notes, which will be automatically logged in the patient's chart.

### 2.5. Hospital Onboarding Use Case

*   **Super Admin Role:** A Super Admin will be able to create and manage hospital profiles.
*   **Feature & Pricing Assignment:** The Super Admin will be able to assign specific features and pricing plans to each hospital.
*   **Invoice-Based Billing:** The system will be able to generate invoices for large hospitals.
*   **Stripe Integration:** The platform will be integrated with Stripe to process patient co-pays.

### 2.6. Post-MVP Features

*   **Role-Based Access Control (RBAC):** The platform will have a robust RBAC system to ensure that users only have access to the features and data that are relevant to their role.
*   **Multiple Delegation Levels:** Users will be able to delegate their responsibilities to other users.

### 2.7. Call Center/PBX Integration

*   **Phase 1 Use Cases:** Call Logging & Contextual Notes.
*   **Real-Time Popups:** Doctors and Hospital Admins will receive real-time popups.
*   **Call Logging:** All calls will be logged automatically, in compliance with HIPAA.
*   **Call Recording:** Call recording will be included in the MVP, in compliance with HIPAA.

### 2.8. Review Management System

*   **Review Collection:** Reviews will be collected per doctor and per hospital.
*   **External Publication:** The possibility of publishing reviews externally will be considered for a future release.
*   **Prompt Channels:** Patients will be prompted to leave a review via in-app notifications and SMS.

## 3. Flowcharts

*Flowcharts for key processes will be created and attached to this document.*

## 4. Use Cases

*Detailed use cases for all features will be created and attached to this document.*
