# JobFlow — MVP Requirements

## 1. Project Overview

JobFlow is a full-stack job application management platform that helps job seekers organize job opportunities, track application progress, and prepare for interviews.

## 2. Target Users

People actively searching for jobs who need a central place to manage their applications.

## 3. Core MVP Features

### 3.1 User Authentication
- Users can register for an account.
- Users can log in and log out.
- Each user can access only their own private job application data.

### 3.2 Job Application Management
- Add a job application.
- View all saved applications.
- Edit application details.
- Delete an application.
- Store company name, job title, job posting URL, application date, status, and notes.

### 3.3 Application Status Tracking
- Track applications through statuses:
  - Wishlist
  - Applied
  - Interview
  - Offer
  - Rejected

### 3.4 Dashboard
- Display the total number of applications.
- Show application counts by status.
- Display recent applications.

### 3.5 Search and Filtering
- Search by company or job title.
- Filter applications by status.

## 4. Technology Stack

- Backend: Python, Django, Django REST Framework
- Frontend: React, TypeScript, Bootstrap
- Database: PostgreSQL
- Version control: Git and GitHub

## 5. Non-Functional Requirements

- Protect private user data.
- Validate user input on the backend.
- Provide clear error messages.
- Use a responsive interface for desktop and mobile.
- Keep the code organized and maintainable.

## 6. Out of Scope for the MVP

- Automatic job scraping
- AI-generated resume tailoring
- Automated job applications
- Paid subscriptions
- Third-party job board integrations

## 7. MVP Success Criteria

A registered user can securely create an account, manage job applications, update their statuses, and view application statistics from a dashboard.
