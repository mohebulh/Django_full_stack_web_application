# University Cyber Clinic
A full-stack Django web application that connects local small and medium-sized enterprises (SMEs) with free cybersecurity support from a university, building a bridge between students, academics and the local business community.**

Built (October 2024 – April 2025) using Agile/Scrum, and deployed to a live domain.

---

## The Problem

Small businesses are frequent targets of ransomware, phishing and data breaches. Most cannot afford a security consultant. Universities, meanwhile, have the skills and the students who need real-world experience. University Cyber Clinic gives SMEs one place to:

- learn which cybersecurity services are available,
- book a consultation with the clinic team,
- download practical security guides, and
- manage their appointments online.

## Key Features

### For SME clients
- **Account registration with email verification.** Secure, token-based verification links, with a rate-limited "resend verification" option.
- **Login, logout and full password-reset flow.** Built on Django's authentication system with custom views and branded email templates.
- **Appointment booking.** A Flatpickr date picker that calls a **JSON API endpoint** to show only the time slots still free, which prevents double-booking.
- **Reschedule and cancel.** Clients manage their own bookings from a personal dashboard.
- **Automatic confirmation emails.** Sent over SMTP (TLS) with a **PDF receipt attached**, generated with xhtml2pdf and including a **QR code**.
- **Add to calendar.** Downloadable **.ics** files for Outlook, Google Calendar and Apple Calendar.
- **User profile.** Phone number, business name and profile picture upload.
- **Service pages.** Network security assessment, cloud security, data protection, incident response and forensics, compliance and risk management, ransomware protection, physical security integration, training and awareness, and cybersecurity consulting.
- **Resource library.** Downloadable guides such as an incident response checklist and best-practice guides.
- **Contact form.** Optionally sends the user a copy of their message.

### For clinic staff and administrators
- **Role-based access control.** Staff-only views protected with `@staff_member_required`; client views protected with `@login_required`.
- **Admin dashboard.** Overview of appointments, users and messages, with a live **unread-message counter** that updates via the Fetch API without reloading the page.
- **Appointment management.** Assign staff to appointments, mark them completed or pending, and send automatic notification emails to clients and staff.
- **CSV export** of all appointments for reporting.
- **User management.** View, edit and delete users.
- **Content management.** Create and edit announcements and upload resources without touching the code.
- **Contact inbox.** Read, mark as read and delete messages from SMEs.
- **"My assigned appointments"** view for each staff member.

## Tech Stack

| Layer | Technologies |
|---|---|
| **Back end** | Python, Django (MVT architecture), Django ORM, Django authentication, Django signals, Django admin |
| **Database** | MySQL (production), SQLite (local development), relational schema design and migrations |
| **Front end** | HTML5, Tailwind CSS (django-tailwind, PostCSS, Autoprefixer), JavaScript (ES6, Fetch API), Django templates, django-widget-tweaks, Flatpickr, responsive design |
| **APIs** | JSON endpoints for available booking slots and unread-message counts |
| **Documents and email** | xhtml2pdf (PDF generation), qrcode, SMTP email with TLS, HTML email templates, iCalendar (.ics) generation |
| **Deployment and infrastructure** | Linux shared hosting (StackCP), SSH (PuTTY), custom domain, static and media file handling, network topology design |
| **Tools and process** | Git and GitHub, Agile/Scrum, Microsoft Teams, Microsoft Forms |

## Data Model

| Model | Purpose |
|---|---|
| `Appointment` | Booking date and time, client details, status (pending or completed), assigned staff member, optional link to a registered user |
| `UserProfile` | One-to-one extension of Django's `User` (phone, business name, profile image, verification-email timestamp), created automatically by a `post_save` signal |
| `ContactMessage` | Enquiries from SMEs, with read/unread tracking |
| `Announcement` | Events and news published by the clinic |
| `Resource` | Downloadable files or external links for the resource library |

## Design and Research

User-centred design work is included in this repository:

- **User personas** (`Persona 1.docx`, `Persona 2.docx`), representing typical SME owners.
- **Use case diagram** describing what clients, staff and administrators can do.
- **User flow diagram** showing the journey from landing page to booked appointment.
- **Workflow diagram** of the clinic's internal process.
- **Network topology diagram** for the hosting infrastructure.
- **User roles document** defining permissions.
- **A survey sent to real local businesses** to collect requirements and feedback.

## How the Team Worked

The project ran as a six-phase Agile/Scrum plan with four sprints. The team held daily 15-minute stand-ups, sprint planning, reviews and retrospectives, and fortnightly stakeholder updates.

| Phase | Dates | Focus |
|---|---|---|
| Planning and setup | Oct – Nov 2024 | Requirements analysis, technology selection, proposal presentation |
| Sprint 1: Infrastructure | Nov – Dec 2024 | Repository setup, database schema, authentication, server environment |
| Sprint 2: Core development | Jan – Feb 2025 | Appointment booking, user dashboard, resource library, user management |
| Sprint 3: Features | Feb – Mar 2025 | Admin dashboard, reporting, security enhancements |
| Sprint 4: Integration and testing | Mar 2025 | Integration, UI/UX, API and security testing |
| Launch | Apr 2025 | Deployment and handover documentation |

Team roles: web developer, back-end developer, mobile developer and IT infrastructure.

**My role:** _[Describe what you personally built here, for example: "Back-end developer: designed the database schema, built the appointment booking system and JSON slot API, and implemented email verification and PDF receipts."]_

The full plan, including risk management, is in [`Project Timeline`](./Project%20Timeline).

## Running Locally

```bash
git clone https://github.com/mohebulh/Django_full_stack_web_application.git
cd Django_full_stack_web_application/src/django-project/universitycyberclinic

python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install django django-tailwind django-widget-tweaks xhtml2pdf qrcode pillow mysqlclient

# Set your own database and email settings (see settings.py), then:
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Visit `http://127.0.0.1:8000/`.

## Skills Demonstrated

Full-stack web development · Python · Django · MySQL · relational database design · REST/JSON endpoints · authentication and authorisation · role-based access control · secure email verification and password reset · JavaScript · Tailwind CSS · responsive UI · PDF and QR code generation · SMTP email integration · Linux deployment over SSH · Agile/Scrum · user-centred design · requirements gathering · technical documentation · teamwork

# Detailed Project Timeline

## Phase 1: Project Planning & Setup (Oct 28 - Nov 15, 2024)
- Duration: 3 weeks
- Key Activities:
  * Team formation and role assignment
  * Requirements analysis
  * Technology stack selection
  * Proposal Presentaion
  * Development environment setup
  * Initial project documentation

## Phase 2: Sprint 1 - Infrastructure (Nov 18 - Dec 20, 2024)
- Duration: 5 weeks
- Key Deliverables:
  ### Web Developer:
  * Project repository setup
  * Basic website structure
  * UI component library
  
  ### Mobile Developer:
  * Mobile app architecture
  * Development environment
  * Basic app structure
  
  ### IT Infrastructure:
  * Server environment setup
  * Network configuration
  * Basic security implementation
  
  ### Backend Developer:
  * Database schema design
  * Basic API structure
  * Authentication system

## Holiday Break (Dec 23, 2024 - Jan 3, 2025)
- 2 weeks break
- Team members available for emergency support only
- Documentation review and planning for next phase

## Phase 3: Sprint 2 - Core Development (Jan 6 - Feb 7, 2025)
- Duration: 5 weeks
- Key Deliverables:
  ### Web Developer:
  * Appointment booking system
  * User dashboard
  * Resource library interface
  
  ### Mobile Developer:
  * Mobile booking system
  * User profile features
  * Push notification system
  
  ### IT Infrastructure:
  * Monitoring systems
  * Backup solutions
  * Security policies
  
  ### Backend Developer:
  * Booking system API
  * Resource management
  * User management system

## Phase 4: Sprint 3 - Feature Development (Feb 10 - Mar 7, 2025)
- Duration: 4 weeks
- Key Deliverables:
  ### Web Developer:
  * Analytics dashboard
  * Reporting system
  * Advanced UI features
  
  ### Mobile Developer:
  * Offline capabilities
  * Advanced mobile features
  * Performance optimization
  
  ### IT Infrastructure:
  * Advanced security measures
  * System automation
  * Performance monitoring
  
  ### Backend Developer:
  * Advanced API features
  * Security enhancements
  * Performance optimization

## Phase 5: Sprint 4 - Integration & Testing (Mar 10 - Mar 28, 2025)
- Duration: 3 weeks
- Key Deliverables:
  ### Web Developer:
  * Integration testing
  * UI/UX testing
  * Performance optimization
  
  ### Mobile Developer:
  * App store preparation
  * Mobile testing
  * Final mobile optimizations
  
  ### IT Infrastructure:
  * Security testing
  * System integration testing
  * Final security audit
  
  ### Backend Developer:
  * API testing
  * Performance testing
  * Final security implementations

## Phase 6: Final Documentation & Launch (Mar 31 - Apr 1, 2025)
- Duration: 2 days
- Key Activities:
  * Final documentation completion
  * System deployment
  * Launch preparation
  * Handover documentation

## Key Dates and Deadlines
- Project Kickoff: October 28, 2024
- Infrastructure Complete: December 20, 2024
- Core Features Complete: February 7, 2025
- Feature Complete: March 7, 2025
- Testing Complete: March 28, 2025
- Project Launch: April 1, 2025

## Regular Meetings Schedule
- Daily Standups: Every day at 11:00 AM (15 minutes) on teams
- Sprint Planning: First Monday of each sprint (2 hours)
- Sprint Review: Last Friday of each sprint (1 hour)
- Sprint Retrospective: Last Friday of each sprint (1 hour)
- Stakeholder Updates: Bi-weekly on Wednesday (30 minutes) after 02:00PM

## Risk Management
1. Holiday Season Impact
   - Reduced availability during December
   - Critical tasks scheduled before/after break
   - Emergency support roster planned

2. Testing Buffer
   - Additional testing time allocated in March
   - Parallel testing tracks for different components

3. Launch Preparation
   - Pre-launch checklist to be completed by March 28
   - Contingency day available on March 29-31 if needed

4. Resource Availability
   - Team capacity planning accounting for holidays
   - Cross-training within team for critical functions
