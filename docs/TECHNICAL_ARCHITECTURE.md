# JobFlow — Technical Architecture

## 1. Overview

JobFlow is a full-stack web application that helps job seekers organize job opportunities and track their application progress.

The application uses a separate frontend and backend that communicate through a REST API.

## 2. Technology Stack

### Frontend
- React
- TypeScript
- Bootstrap
- Vite for development and building

### Backend
- Python
- Django
- Django REST Framework

### Database
- PostgreSQL

### Development Tools
- Git and GitHub
- Visual Studio Code
- Python virtual environment

## 3. System Components

### Frontend
Responsible for displaying the user interface, collecting user input, communicating with the backend API, and presenting application data.

### Backend
Responsible for processing requests, validating data, enforcing authentication and authorization, implementing business logic, and communicating with the database.

### Database
Stores user accounts and job application records. Each user's private application data must be protected from access by other users.

## 4. API Communication

The frontend communicates with the backend using HTTP requests.

The API returns JSON responses for supported operations.

Initial API resources will include:
- Authentication
- Job applications
- Dashboard statistics

## 5. Data Model

### User
Represents a registered JobFlow user.

### JobApplication
Stores:
- Job title
- Company name
- Job posting URL
- Application date
- Application status
- Notes
- Owner (user relationship)

Each job application belongs to one user.

## 6. Security

- Authenticate users before allowing access to private application data.
- Enforce ownership checks on every protected job application operation.
- Validate incoming data on the backend.
- Store secrets and environment-specific configuration outside committed source code.
- Configure appropriate frontend and backend origins for local development.

## 7. Development Structure

The repository will contain:
- `backend/` for Django and API development
- `frontend/` for React and TypeScript
- `docs/` for project documentation
- `README.md` for project overview and setup instructions

## 8. Development Approach

Development will proceed incrementally:
1. Complete project documentation.
2. Configure the backend and database.
3. Implement authentication and job application APIs.
4. Build the frontend.
5. Integrate the frontend and backend.
6. Test functionality and improve the application.

## 9. Initial Local Development Plan

- Run the Django development server locally.
- Run the React development server locally.
- Use PostgreSQL as the intended application database.
- Configure frontend-to-backend communication through environment-specific settings.