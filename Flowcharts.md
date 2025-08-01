# Mediverse Telehealth Platform - Flowcharts

## 1. Appointment Booking Flow

```mermaid
graph TD
    A[Patient initiates appointment booking] --> B{Is it an urgent/same-day appointment?};
    B -- Yes --> C[Book appointment without insurance verification];
    B -- No --> D{Does the patient have insurance?};
    D -- Yes --> E[Enter insurance information];
    E --> F{Is the insurance verified in real-time?};
    F -- Yes --> G[Book appointment];
    F -- No --> H[Flag for follow-up and book appointment];
    D -- No --> G;
    C --> I[System automatically initiates insurance verification within 24 hours];
    H --> I;
    I --> J{Is the insurance verified?};
    J -- Yes --> K[Update appointment status];
    J -- No --> L[Alert staff to follow-up with patient];
```

## 2. Emergency Telehealth Flow

```mermaid
graph TD
    A[Nurse initiates emergency virtual visit] --> B[System creates a new virtual visit and notifies the provider];
    B --> C[Provider joins the call];
    C --> D[Provider adds/edits patient name and MRN];
    D --> E[Provider takes notes during the call];
    E --> F[Provider ends the call];
    F --> G[System automatically logs the notes in the patient's chart];
```

## 3. Hospital Onboarding Flow

```mermaid
graph TD
    A[Super Admin creates a new hospital profile] --> B[Super Admin assigns features and pricing to the hospital];
    B --> C[System generates an invoice for the hospital];
    C --> D[Hospital pays the invoice];
    D --> E[Hospital is onboarded and can start using the platform];
```

## 4. Call Center/PBX Integration Flow

```mermaid
graph TD
    A[Call received on RingCentral/GetWeave number] --> B[Webhook sent to Mediverse backend];
    B --> C{Is the caller's number in the patient database?};
    C -- Yes --> D[Send real-time push to Hospital Admin/Doctor];
    D --> E[Popup appears in web portal with patient info];
    C -- No --> F[Log call without patient info];
    subgraph After Call
    G[Call ends] --> H[Log call with duration, agent name, and notes];
    H --> I[Store call recording link (HIPAA compliant)];
    end
```
