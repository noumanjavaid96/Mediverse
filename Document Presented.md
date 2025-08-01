***

# Mediverse Platform Requirements Document

**Version 2.0 - Post August 1st Meeting Update**

> **IMPORTANT NOTICE FOR DR. USMAN**: This document has been updated following our August 1st meeting. Please review each section carefully and provide detailed feedback via Notion comments. Once development begins, major functionality changes will significantly impact timelines. Your thorough review now is critical for project success.

***

## 1. Project Overview

### 1.1 Meeting Summary (August 1, 2024)

**Key Outcomes:**

* Core functionalities and execution approach finalized

* Technical document simplified into visual, easily understandable format

* User journeys and workflows presented with flowcharts

* Notion commenting system established for detailed feedback

* Development timeline dependencies on stakeholder approval confirmed

**Critical Action Required:**

* Dr. Usman to provide comprehensive feedback via Notion comments

* All major functionalities must be approved before development starts

* Any post-development changes will cause significant timeline delays

### 1.2 Core Value Propositions

**For Doctors:**

* Complete autonomy over schedule and pricing

* Integrated practice management tools

* Direct patient communication channels

* Revenue optimization through dynamic pricing

**For Patients:**

* Transparent doctor selection with reviews and ratings

* Flexible appointment booking (in-person/virtual)

* Comprehensive health record access

* Competitive pricing through marketplace dynamics

**For Healthcare Institutions:**

* White-label solutions for hospital-specific portals

* Analytics and reporting

* Staff and resource management tools

***

## 2. User Roles & Permissions

### 2.1 Core User Roles

| Role               | Primary Functions                                    | Access Level         | Registration Method                        |
| ------------------ | ---------------------------------------------------- | -------------------- | ------------------------------------------ |
| **Patient**        | Book appointments, access records, consultations     | Standard User        | Email/Phone verification                   |
| **Doctor**         | Manage practice, conduct consultations, patient care | Professional User    | Invitation-based + credential verification |
| **Hospital Admin** | Manage hospital operations, staff oversight          | Administrative       | Hospital onboarding process                |
| **Super Admin**    | Platform management, hospital oversight              | System Administrator | Internal assignment                        |

***

## 3. User Journeys & Workflows

> **REVIEW INSTRUCTION FOR DR. USMAN**: Each flowchart node below corresponds to specific features in our development database. Please verify that these workflows align with your clinical practice expectations and comment on any missing steps or incorrect sequences.

### 3.1 Flowchart-to-Feature Mapping

**Epic Alignment with User Journeys:**

| Flowchart Section          | Corresponding Epic                          | Features Database Reference |
| -------------------------- | ------------------------------------------- | --------------------------- |
| Patient Registration/Login | Patient Authentication & Profile Management | Epic 1.1-1.4                |
| Doctor Search & Booking    | Doctor Discovery & Appointment Booking      | Epic 2.1-2.3                |
| Telehealth Sessions        | Telehealth & EHR Access                     | Epic 3.1-3.3                |
| Doctor Operations          | Doctor Portal & Patient Management          | Epic 4.1-4.8                |
| Hospital Management        | Hospital Administration & Emergency         | Epic 5.1-5.4                |

### 3.2 Patient Journey

```mermaid
flowchart TD
    A[Patient Visits Platform] --> B{Registered?}
    B -->|No| C[Registration Process]
    B -->|Yes| D[Login]
    C --> E[Email/Phone Verification]
    E --> F[Complete Medical Profile]
    F --> G[Dashboard Access]
    D --> G
    G --> H[Search Doctors]
    H --> I[Filter by Specialty/Location/Price]
    I --> J[View Doctor Profiles]
    J --> K[Check Availability]
    K --> L[Select Appointment Type]
    L --> M{Consultation Type?}
    M -->|In-Person| N[Book Physical Appointment]
    M -->|Virtual| O[Book Telehealth Session]
    N --> P[Payment Processing]
    O --> P
    P --> Q[Confirmation & Reminders]
    Q --> R[Attend Appointment]
    R --> S[Receive Prescription/Notes]
    S --> T[Access Medical Records]
    T --> U[Rate & Review Doctor]
```

### 3.3 Doctor Journey & Comprehensive Onboarding

> **CRITICAL REVIEW FOR DR. USMAN**: The doctor onboarding system below implements our doctor-centric single account model. Please verify this aligns with real-world doctor registration scenarios and hospital affiliation processes.

### 3.3.1 Enhanced Doctor Onboarding Flow (Epic 4.1-4.8)

```mermaid
flowchart TD
    A[Doctor Registration Request] --> B{Registration Source?}
    B -->|Website Direct| C[Direct Website Registration]
    B -->|Hospital Invitation| D[Hospital Registered Doctors]
    C --> E[Email/Phone Verification]
    D --> F[Hospital Admin Verification]
    E --> G[Duplicate Check System]
    F --> G
    G --> H{Existing Account Found?}
    H -->|Yes| I[Account Conflict Resolution]
    H -->|No| J[Credential Verification Process]
    I --> K[Merge/Link Account Options]
    J --> L[Medical License Verification]
    L --> M[Professional Background Check]
    M --> N[Specialization Validation]
    N --> O[Profile Creation]
    O --> P[Services & Pricing Setup]
    P --> Q[Availability Configuration]
    Q --> R[Platform Training]
    R --> S[Account Activation]
    S --> T[Dashboard Access]
```

### 3.3.2 Doctor Operational Journey (Epic 4.3-4.4)

```mermaid
flowchart TD
    A[Dashboard Access] --> B[Manage Appointments]
    B --> C{Appointment Type?}
    C -->|Scheduled| D[Prepare for Consultation]
    C -->|Walk-in Request| E[Accept/Decline]
    D --> F[Conduct Consultation]
    E --> F
    F --> G[Update Medical Records]
    G --> H[Generate Prescription]
    H --> I[Session Summary]
    I --> J[Payment Processing]
    J --> K[Patient Follow-up]
```

### 3.3.3 Doctor Onboarding Requirements & Duplicate Prevention

### A. Complete Doctor-Only Onboarding System

**Core Principle**: Mediverse implements a **Doctor-Centric Registration Model** where doctors maintain singular, verified accounts regardless of their affiliation with multiple hospitals or direct platform registration.

**Registration Channels:**

1. **Direct Website Registration**: Doctors self-register through the platform
2. **Hospital-Sponsored Registration**: Hospitals invite doctors to join their network
3. **Referral-Based Registration**: Existing doctors refer colleagues

### B. Duplicate Registration Prevention Strategy

**Primary Identification Matrix:**

```
Doctor Uniqueness Verification:
├── Medical License Number (Primary Key)
├── National ID/SSN (Secondary Key)
├── Email Address (Tertiary Key)
├── Phone Number (Quaternary Key)
└── Full Name + Date of Birth (Fallback)
```

**Duplicate Detection Algorithm:**

1. **Real-time Check**: During registration, system performs instant lookup
2. **Fuzzy Matching**: Handles variations in name spelling, formatting
3. **Cross-Reference Validation**: Checks against medical board databases
4. **Manual Review Queue**: Flagged cases require admin verification

### C. Conflict Resolution Framework

**Scenario 1: Doctor Registered via Website, Hospital Attempts Re-registration**

**System Response:**

* **Immediate Block**: Prevent duplicate account creation

* **Notification**: Alert hospital admin of existing account

* **Linking Process**: Offer to link doctor to hospital network

* **Doctor Consent**: Require doctor approval for hospital affiliation

**Pros:**
✅ Maintains data integrity and prevents confusion
✅ Preserves doctor’s existing patient relationships
✅ Reduces administrative overhead
✅ Ensures consistent patient experience
✅ Prevents revenue splitting conflicts

**Cons:**
❌ May delay hospital onboarding process
❌ Requires additional verification steps
❌ Potential friction between hospital and doctor
❌ Complex consent management

**Scenario 2: Hospital-Registered Doctor Attempts Direct Registration**

**System Response:**

* **Account Recognition**: Identify existing hospital-linked account

* **Upgrade Path**: Offer to convert to independent account

* **Hospital Notification**: Inform hospital of doctor’s independence request

* **Transition Period**: Allow gradual migration of appointments/data

**Pros:**
✅ Supports doctor autonomy and career mobility
✅ Maintains platform relationship regardless of hospital changes
✅ Enables independent practice opportunities
✅ Preserves patient continuity

**Cons:**
❌ May create tension with hospital partners
❌ Complex data migration requirements
❌ Potential revenue impact for hospitals
❌ Requires careful contract management

### Edge Cases & Solutions

**Edge Case 1: Doctor with Multiple Medical Licenses (Multi-State Practice)**

**Problem**: Doctor licensed in multiple states may appear as different practitioners

**Solution:**

* **Primary License Designation**: Doctor selects main practicing license

* **Secondary License Linking**: Additional licenses linked to primary account

* **State-Specific Profiles**: Separate practice profiles per state

* **Unified Billing**: Single payment account across all states

**Edge Case 2: Doctor Name Changes (Marriage, Legal Name Change)**

**Problem**: Legal name changes may create false duplicates or prevent account access

**Solution:**

* **Name Change Verification**: Legal document upload requirement

* **Alias Management**: Maintain record of previous names

* **Medical Board Sync**: Update with licensing authorities

* **Patient Notification**: Inform existing patients of name change

**Edge Case 6: Doctor Account Inheritance (Death/Incapacitation)**

**Problem**: Managing doctor accounts when practitioner cannot continue

**Solution:**

* **Estate Management Process**: Legal heir account transfer

* **Patient Record Transition**: Secure transfer to designated successor

* **Appointment Cancellation**: Automated patient notification system

* **Data Retention Compliance**: HIPAA-compliant record preservation

### 3.4 Hospital Admin Journey

> **REVIEW FOR DR. USMAN**: Please verify this hospital administration workflow matches your experience with hospital operations and doctor management processes.

```mermaid
flowchart TD
    A[Hospital Onboarding] --> B[Admin Account Creation]
    B --> C[Hospital Profile Setup]
    C --> D[Speciality Configuration]
    D --> E[Doctor Invitation System]
    E --> F[Doctor Acceptance/Rejection]
    F --> G[Custom Booking Links]
    G --> H[Dashboard Access]
    H --> I[Monitor Operations]
    I --> J[Appointment Oversight]
    J --> K[Generate Reports]
    K --> L[Performance Analytics]
    L --> M[Revenue Management]
```

### 3.5 Emergency Consultation System (Hospital-Exclusive)

> **EMERGENCY WORKFLOW REVIEW FOR DR. USMAN**: This emergency system is designed for critical situations. Please verify the workflow matches hospital emergency protocols and comment on response time requirements.

**Overview:**
A dedicated emergency consultation feature exclusively available to hospitals for urgent medical situations. This system provides immediate access to available doctors through a streamlined interface designed for time-critical scenarios.

**Core Requirements:**

### 3.5.1 Emergency Call Interface

* **Dedicated Emergency Screen**: Separate interface accessible only to hospital staff

* **One-Click Access**: Prominent emergency button on hospital dashboard

* **Priority Routing**: Automatic routing to available emergency-qualified doctors

* **Instant Notifications**: Real-time alerts to all available doctors

* **Emergency Code Integration**: Support for hospital emergency codes and protocols

### 3.5.2 Available Doctor Selection

* **Real-Time Availability**: Live status of doctors (available/busy/offline)

* **Specialty Filtering**: Filter doctors by emergency specialties (ER, ICU, Cardiology, etc.)

* **Response Time Display**: Show average response time for each doctor

* **Priority Ranking**: Rank doctors by emergency experience and availability

* **Backup Options**: Secondary doctor suggestions if primary choice unavailable

### 3.5.3 Emergency Video Conferencing

* **Instant Connection**: Sub-10 second connection time

* **High Priority Bandwidth**: Dedicated bandwidth allocation for emergency calls

* **Multi-Participant Support**: Include multiple doctors, nurses, and specialists

* **Screen Sharing**: Share patient monitors, X-rays, and medical data

* **Session Recording**: Automatic recording for medical records and legal purposes

* **Mobile Compatibility**: Full functionality on mobile devices for on-call doctors

**Technical Specifications:**

### 3.5.4 Emergency Workflow

```mermaid
flowchart TD
    A[Hospital Staff Emergency] --> B[Access Emergency Interface]
    B --> C[Select Emergency Type]
    C --> D[View Available Doctors]
    D --> E[Filter by Specialty]
    E --> F[Select Primary Doctor]
    F --> G[Initiate Emergency Call]
    G --> H{Doctor Response?}
    H -->|Available| I[Start Video Conference]
    H -->|Busy| J[Try Next Available Doctor]
    H -->|No Response| K[Escalate to Backup]
    I --> L[Conduct Emergency Consultation]
    J --> G
    K --> M[Notify Emergency Coordinator]
    L --> N[Document Emergency Session]
    N --> O[Generate Emergency Report]

```

## 4. Core Application Flow

***

### 4.1 System Architecture Overview

```mermaid
graph TB
    subgraph "Frontend Layer"
        A[Patient Portal]
        B[Doctor Portal]
        C[Hospital Admin Portal]
        D[Super Admin Dashboard]
    end

    subgraph "API Gateway"
        E[Authentication Service]
        F[Appointment Service]
        G[Payment Service]
        H[Notification Service]
    end

    subgraph "Core Services"
        I[User Management]
        J[EHR System]
        K[Telehealth Engine]
        L[Analytics Engine]
    end

    subgraph "External Integrations"
        M[Payment Gateways]
        N[SMS/Email Services]
        O[Video Calling SDK]
        P[Insurance APIs]
    end

    A --> E
    B --> E
    C --> E
    D --> E
    E --> I
    F --> J
    G --> M
    H --> N
    K --> O
    L --> P
```

### 4.2 Data Flow Architecture

1. **Authentication Flow**: Multi-factor authentication with role-based access control
2. **Appointment Flow**: Real-time availability checking with conflict resolution
3. **Payment Flow**: Secure payment processing with escrow for dispute resolution
4. **Communication Flow**: HIPAA-compliant messaging and video consultations
5. **Data Sync Flow**: Real-time synchronization across all user interfaces

***

## 5. Integration Points

### 5.1 Payment Gateway Integration

**Primary Requirements:**

* Multi-currency support

* Subscription management for hospital plans

* Real-time payment status updates

**Recommended Providers:**

* Stripe

**Integration Specifications:**

```
Payment Flow:
1. Patient selects appointment → 2. Payment authorization →
3. Funds held in escrow → 4. Appointment completion →
5. Automatic release to doctor → 6. Platform fee deduction
```

### 5.2 Insurance Verification APIs

**Integration Requirements:**

* Real-time eligibility verification

* Coverage details and copay calculation

* Prior authorization checking

* Claims submission capability

**API Specifications:**

* REST API with OAuth 2.0 authentication

* HIPAA-compliant data transmission

* Real-time response within 3 seconds

* Fallback mechanisms for API downtime

### 5.3 Telehealth Integration

**Video Calling SDK Requirements:**

* HD video quality with adaptive bitrate

* Screen sharing capabilities

* Session recording (with consent)

* Multi-participant support

* Mobile app compatibility

**Recommended SDK:**

* Agora.io (Primary choice based on existing implementation)

* Twilio Video (Backup option)

***

***

## 7. Technical Specifications

### 7.1 Technology Stack

**Frontend:**

* React.js with TypeScript

* Tailwind CSS for styling

* React Query for API management

**Backend:**

* Node.js with Express.js

* PostgreSQL for primary database

* Redis for caching and sessions

* AWS S3 for file storage

**Infrastructure:**

* AWS/Azure/Digital Ocean cloud hosting

* Docker containerization

* CI/CD with GitHub Actions

### 7.2 Security Requirements

* Multi-factor authentication

* Regular security audits

* Data backup and disaster recovery

***

### 8.2 Implementation Recommendations

**Recommended Approach: “Fail-Safe First”**

1. **Conservative Duplicate Detection**: Initially on the side of flagging potential duplicates for manual review rather than allowing false negatives
2. **Gradual Automation**: Start with manual verification processes, then gradually automate as confidence in the system grows
3. **Stakeholder Communication**: Proactive communication with hospitals about the duplicate prevention benefits
4. **Doctor Education**: Clear onboarding materials explaining the single-account policy and its benefits

**Why This Approach:**
✅ **Prevents Data Corruption**: Early detection prevents complex data cleanup later
✅ **Builds Trust**: Demonstrates platform reliability to both doctors and hospitals
✅ **Reduces Support Burden**: Fewer account conflicts mean fewer support tickets
✅ **Ensures Compliance**: Proper verification from day one prevents regulatory issues

### 8.3 Stakeholder Communication Strategy

**For Hospitals:**

* **Pre-Implementation**: Explain benefits of unified doctor accounts

* **During Conflicts**: Provide clear resolution paths and timelines

* **Post-Resolution**: Share success metrics and improved efficiency data

**For Doctors:**

* **Registration**: Clear explanation of verification requirements

* **Conflicts**: Transparent communication about existing accounts

* **Resolution**: Step-by-step guidance through linking/merging process

**For Patients:**

* **Transparency**: Clear indication of doctor verification status

* **Continuity**: Assurance that their medical history remains intact

* **Trust**: Visible security measures protecting their data

***

## 11. Next Steps & Action Items

> **POST-AUGUST 1ST MEETING UPDATE**: Following our comprehensive discussion, the immediate priority is Dr. Usman's detailed review and API requirements finalization. Major functionalities will be locked once development begins to avoid timeline delays.

### Critical Immediate Actions (Next 48-72 Hours)

1. **Dr. Usman's Comprehensive Review**: Complete detailed review of all sections via Notion comments
   - Focus on clinical workflow accuracy and real-world applicability
   - Verify doctor onboarding process alignment with hospital practices
   - Review emergency consultation protocols against hospital standards
   - Identify missing features or incorrect assumptions
   - Validate API integration requirements

2. **Stakeholder Feedback Integration**: Address all comments and concerns raised during August 1st meeting
3. **Final Approval**: Obtain sign-off on all major functionalities before development lock
4. **Epic-to-Flowchart Alignment**: Ensure all flowchart nodes align with Features Database epics

### API Requirements Definition (Critical Priority)

**Based on August Meeting Discussion - Required API Specifications:**

1. **Medical License Verification APIs**
   - Integration with state medical boards (multi-state support)
   - Real-time license validation and status checking
   - Automated renewal notifications and compliance tracking
   - Cross-reference with disciplinary action databases

2. **Payment Gateway APIs**
   - Stripe integration for secure payment processing
   - Escrow functionality for appointment payments
   - Multi-currency support for international patients
   - Automated refund processing for cancelled appointments

3. **Telehealth Video APIs**
   - Agora SDK integration specifications
   - WebRTC implementation requirements
   - Mobile compatibility standards (iOS/Android)
   - Emergency consultation priority routing

4. **Insurance Verification APIs**
   - Real-time eligibility checking
   - Coverage verification and benefit details
   - Claims processing integration
   - Prior authorization workflow automation

5. **Notification APIs**
   - SMS/Email service integration (Twilio/SendGrid)
   - Push notification systems for mobile apps
   - Emergency alert mechanisms for hospital staff
   - Appointment reminder automation

6. **EHR Integration APIs**
   - HIPAA-compliant data exchange protocols
   - HL7 FHIR standard implementation
   - Secure record sharing between providers
   - E-prescribing system integration

### Sprint Planning Updates (Based on Epic Alignment)

**Sprint 1-2: Foundation (Epics 1.1-1.4, 2.1-2.3)**
- Patient Authentication & Profile Management
- Doctor Discovery & Appointment Booking
- Basic platform infrastructure

**Sprint 3-4: Core Operations (Epics 4.1-4.8)**
- Doctor Portal & Patient Management
- Appointment management system
- Basic telehealth functionality

**Sprint 5-6: Advanced Features (Epics 3.1-3.3, 5.1-5.3)**
- Telehealth & EHR Access
- EHR Management & E-Prescribing
- Payment processing integration

**Sprint 7-8: Hospital Integration (Epics 6.1-6.11)**
- Hospital Administration features
- Emergency Video Conferencing System
- Multi-hospital doctor management

**Sprint 9-10: Platform Management (Epics 7.1-7.4)**
- Super Admin Platform Management
- Analytics and reporting
- System optimization

### Short-term Goals (Next 2 Weeks)

1. **API Documentation**: Complete detailed API specifications based on requirements
2. **Development Environment Setup**: Configure development, staging, and production environments
3. **Third-party Vendor Finalization**: Complete contracts with payment and telehealth providers
4. **Compliance Framework**: Establish HIPAA compliance procedures and documentation
5. **Epic Validation**: Ensure all Features Database epics are properly mapped to development sprints

### Medium-term Objectives (Next Month)

1. **MVP Development**: Begin Phase 1 development with locked requirements
2. **API Integration Testing**: Test all third-party service integrations
3. **Security Implementation**: Deploy core security measures and conduct audits
4. **Beta Testing Preparation**: Recruit and onboard beta testing participants
5. **Hospital Partnership Pilot**: Initiate pilot program with select hospital partners

### Risk Mitigation Strategies

**Development Risks:**
- Lock major functionalities after Dr. Usman's approval to prevent scope creep
- Implement fail-safe duplicate detection as discussed in August meeting
- Prioritize API integrations that are critical for MVP functionality

**Clinical Risks:**
- Ensure all workflows are validated by Dr. Usman before implementation
- Implement robust emergency consultation protocols
- Maintain HIPAA compliance throughout development process

**Business Risks:**
- Secure hospital partnerships early in development cycle
- Validate payment processing requirements with financial stakeholders
- Ensure scalability for multi-hospital operations

***

## Conclusion

This document serves as the comprehensive foundation for Mediverse development, incorporating insights from successful healthcare platforms while addressing the specific needs of our Doctor-Centric Marketplace model. Following our August 1st meeting, this document has been significantly restructured to ensure optimal alignment between flowcharts and Features Database epics, with enhanced focus on API requirements and sprint planning.

**CRITICAL NEXT STEP**: Dr. Usman's comprehensive review via Notion comments is absolutely essential before development begins. Any major functionality changes after development starts will significantly impact project timelines and budget.

**Key Updates Post-August Meeting:**
- Enhanced epic-to-flowchart alignment with priority and status tracking
- Detailed API requirements definition based on meeting discussion
- Sprint planning updates aligned with Features Database structure
- Risk mitigation strategies for development, clinical, and business concerns
- Emphasis on fail-safe duplicate detection approach

**Document Version**: 3.0 (Post-August 1st Meeting - Major Update)

**Last Updated**: August 2, 2024

**Prepared By**: Muhammad Nouman Javaid, Sr. Business Analyst

**Meeting Date**: August 1, 2024

**Pending Approval**: Dr. Usman Qadeer (Critical Review Required)

**Status**: Awaiting Comprehensive Stakeholder Feedback via Notion Comments

**Development Lock**: Pending Dr. Usman's approval to prevent scope creep

***

> **URGENT ACTION REQUIRED**: Dr. Usman, please provide comprehensive feedback on each section via Notion comments within 48-72 hours to avoid development delays. Focus particularly on:
>
> **Clinical Validation:**
> * Verify all clinical workflows match real-world hospital practices
> * Validate doctor onboarding process alignment with current hospital procedures
> * Review emergency consultation protocols against established hospital standards
> * Confirm telehealth integration meets clinical requirements
>
> **Technical Requirements:**
> * Validate API integration requirements for medical license verification
> * Confirm EHR integration specifications meet hospital standards
> * Review payment processing requirements for hospital billing
> * Verify notification systems align with hospital communication protocols
>
> **Epic Alignment:**
> * Confirm all flowchart nodes properly map to Features Database epics
> * Validate sprint planning sequence matches development priorities
> * Identify any missing features or incorrect assumptions
> * Approve priority levels assigned to each epic
>
> **Risk Assessment:**
> * Review proposed fail-safe duplicate detection approach
> * Validate risk mitigation strategies for clinical and business concerns
> * Confirm compliance requirements are adequately addressed

***

*This document is confidential and proprietary to the Mediverse project team. Distribution is restricted to authorized personnel only.*