# Univent - University Event & Workshop Management System 🎓✨


**Univent** is a centralized, web-based platform designed to simplify and automate university event and workshop management. It bridges the gap between students, event organizers, and university administrators by streamlining event creation, approvals, registration, and attendance tracking.

---

## 📋 Project Overview

Universities host numerous events, but managing them manually can be highly inefficient. **Univent** solves this by providing a unified ecosystem where:
*   **Students:** Can easily browse active events, filter categories, and securely register for seats.
*   **Organizers:** Can fill out functional event proposals, submit them for admin verification, and download automated attendance reports.
*   **Administrators:** Supervise the platform quality control through structured dashboards to either approve or reject incoming proposals.

---

## ⚙️ System Requirements

### 1. Functional Requirements (FR)
The system satisfies specific requirements partitioned by user roles and core system processes:

#### A. User Authentication & Profile Management
*   **FR-1.1:** The system shall allow users to log in securely using their official university Single Sign-On (SSO) or verified university credentials.
*   **FR-1.2:** The system shall validate email structures using a dedicated verification routine to ensure inputs match standard university patterns (`@*.edu.sa`).
*   **FR-1.3:** The system shall provide role-based access control, routing authenticated users to their specific interface (Student, Organizer, or Administrator).

#### B. Student Capabilities
*   **FR-2.1:** The system shall allow students to browse all published and active events and workshops.
*   **FR-2.2:** The system shall provide advanced search and filtering mechanisms (by date, category, status, and department).
*   **FR-2.3:** The system shall allow students to register for an event if seats are available, automatically decrementing the available capacity.
*   **FR-2.4:** The system shall generate a unique digital ticket with a transaction ID upon successful registration.
*   **FR-2.5:** The system shall allow students to cancel an active registration, which immediately re-opens the seat for other users.

#### C. Organizer Capabilities
*   **FR-3.1:** The system shall allow organizers to create and fill out a comprehensive "Event Proposal Form" containing the title, description, targeted audience, execution date, physical/virtual venue, and max capacity.
*   **FR-3.2:** The system shall allow organizers to submit proposals to the administration panel, transitioning the event state to `Pending`.
*   **FR-3.3:** The system shall enable organizers to view the status tracking history of all their submitted proposals.
*   **FR-3.4:** The system shall provide organizers with an option to download automated attendance lists and registration metrics once an event concludes.

#### D. Administrator Capabilities
*   **FR-4.1:** The system shall provide administrators with a centralized control dashboard listing all incoming `Pending` proposals.
*   **FR-4.2:** The system shall allow administrators to either **Approve** a proposal (publishing it to the student directory) or **Reject** it.
*   **FR-4.3:** The system shall enforce administrators to provide a mandatory justification comment when rejecting a proposal.

---

### 2. Non-Functional Requirements (NFR)
The system operates within strict engineering constraints to ensure optimal operational quality:

*   **NFR-1 (Performance):** The system shall load search queries and filter data configurations within less than 3 seconds under normal load conditions.
*   **NFR-2 (Scalability):** The system database and application layer shall support at least 300 concurrent active users without performance degradation.
*   **NFR-3 (Availability):** The system shall maintain a 99% uptime benchmark during active academic semesters, excluding scheduled maintenance windows.
*   **NFR-4 (Reliability):** In the event of an unexpected runtime crash, the system shall recover and restore full functionality within a maximum time-to-recover (MTTR) window of 2 minutes.
*   **NFR-5 (Security):** The system shall encrypt all sensitive database tables (passwords, user records, credentials) using industry-standard hashing algorithms.
*   **NFR-6 (Usability/Compatibility):** The interface frontend optimization shall render fully responsive views across desktop screens, tablets, and iOS/Android smartphone browsers (Safari, Chrome, Edge).

---

## 🛠️ Software Development Lifecycle (SDLC)

Project development is driven by the **Incremental Process Model**. 
This model was selected because it allows the system to be built and delivered in independent, manageable segments (increments). 

---

## 🏗️ System Architecture (MVC)

The system adheres to the **Model-View-Controller (MVC)** architectural pattern to decouple data logic from user interfaces:

*   **Model (`EventModel`, `Proposal`, `User`):** Manages data structures, state tracking (e.g., *Pending, Approved, Rejected*), and database interactions.
*   **View (`ProposalView`):** Renders role-based interfaces dynamically customized for Students, Organizers, and Admins.
*   **Controller (`ProposalController`):** Interprets input events from views, processes rules, modifies model states, and triggers UI updates.


---

## 🗺️ Architectural Diagrams & Design Models

### 1. High-Level System Scope
*   **Class Diagram:** Maps the static structure of the platform, defining essential entities such as Users, Profiles, and Accommodation Listings.
   <img width="423" height="466" alt="image" src="https://github.com/user-attachments/assets/aefd5b43-fe71-493e-8b2f-7c3afe7c8d9e" />


*   **Use-Case Model:** Full scenario paths covering core capabilities like *Login, Registration, Event Viewing, Submitting Proposals, and Reject/Approve Workflows*.

   <img width="447" height="447" alt="image" src="https://github.com/user-attachments/assets/66851ba2-ab93-40b7-a29b-bbaf6adc7cae" />


### 2.	Design Pattern
We selected the Facade Design Pattern to simplify the interaction between the user and the system’s core functionalities. This pattern provides a single unified interface that hides the complexity of multiple subsystems.

The Facade pattern is appropriate for this system because:
- 	It hides internal complexity by combining multiple operations into a single interface 
- 	It reduces coupling between the user and subsystem classes 
- 	It simplifies system interaction by providing clear and high-level operations 

<img width="440" height="296" alt="image" src="https://github.com/user-attachments/assets/646e5f02-35ef-4820-aff8-b6a03cdef065" />


