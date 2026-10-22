# Via Fidei — Technical Architecture

## 1. Overview

Via Fidei is a Catholic faith and learning application for Catholics and people exploring Catholicism.

The application will provide structured learning journeys, Catholic educational content, saint biographies, documented miracle accounts, prayer and reflection resources, and a future source-grounded AI assistant.

The system will use a separated frontend and backend architecture. The frontend will provide the user interface, while the backend will manage application data, business rules, validation, and API responses.

The architecture should support incremental development, reliable content sourcing, automated testing, and future expansion without unnecessary complexity in the initial release.

## 2. Architecture Goals

- Maintain a clear separation between frontend and backend responsibilities.
- Support two learning journeys with shared educational content where appropriate.
- Organize lessons, saints, miracles, prayers, and sources into maintainable structures.
- Keep content references and recognition status available to the user.
- Support a future AI assistant grounded in approved content and trusted sources.
- Apply secure configuration, validation, and testing practices.
- Keep the initial implementation suitable for a portfolio project while allowing future growth.

## 3. Technology Stack

### Backend

- Python
- Django
- Django REST Framework for REST APIs, if included in the installed dependencies
- SQLite for initial local development

A production database will be selected when deployment requirements are defined.

### Frontend

- React
- TypeScript
- The existing frontend build tooling, to be confirmed from the repository

### Development and Version Control

- Git
- GitHub Issues
- Feature branches
- Pull requests and code review
- Automated backend and frontend tests

The application must not commit secret keys, passwords, API credentials, or local environment files.

## 4. High-Level System Design

The application will be organized into the following logical layers.

### 4.1 Frontend

The React and TypeScript frontend will be responsible for:

- Displaying the home page and learning journeys.
- Listing and displaying lessons.
- Listing and displaying saint profiles.
- Listing miracle accounts and their locations.
- Displaying prayer and reflection resources.
- Showing source references and recognition status.
- Handling navigation, loading states, empty states, and API errors.

The frontend should not independently determine official Church recognition status or contain duplicated business rules that belong in the backend.

### 4.2 Backend API

The Django backend will be responsible for:

- Exposing structured API endpoints.
- Retrieving and validating application data.
- Applying business rules.
- Returning consistent JSON responses.
- Managing relationships between educational content and its sources.
- Supporting filtering and pagination where appropriate.
- Enforcing permissions if content management or authentication is introduced.

### 4.3 Database

The database will store structured educational content and its relationships.

The initial development database will be SQLite. Database-specific behavior should be kept out of application logic wherever practical to make a future database migration easier.

### 4.4 Content Sources

Content will be prepared using reliable Catholic, historical, and scholarly references.

Each published content item should be linked to its supporting sources. The application should distinguish source material from the application's own explanation or summary.

Content must be reviewed for accuracy before publication.

## 5. Proposed Django Application Modules

The backend may be divided into Django apps as the project grows. These are proposed logical boundaries, not a requirement to create every app immediately.

### 5.1 Learning

Responsibilities:
- Learning journeys.
- Lessons and lesson sections.
- Topic organization.
- Content intended for different audience levels.

Proposed entities:
- `LearningJourney`
- `Lesson`
- `Topic`

A lesson may belong to one or more topics. Learning journeys may reference multiple lessons.

### 5.2 Saints

Responsibilities:
- Saint biographies.
- Feast days and historical details.
- Virtues, patronage, and related educational content.
- Links to relevant sources.

Proposed entity:
- `Saint`

Saint profiles should distinguish documented biographical facts from devotional traditions or disputed historical details when that distinction matters.

### 5.3 Miracles

Responsibilities:
- Miracle accounts.
- Locations and historical context.
- Investigation or recognition status.
- Links to official records and other references.

Proposed entities:
- `Miracle`
- `Location`

The recognition status must use controlled values rather than unrestricted text. The available values and their precise meanings should be defined before implementation.

A reported event must not automatically be classified as Church-recognized. The status should reflect reliable documentation from the relevant Church authority, with the source and date recorded when available.

### 5.4 Prayer and Reflection

Responsibilities:
- Traditional Catholic prayers.
- Scripture references.
- Reflection prompts.
- Related learning resources.

Proposed entities:
- `Prayer`
- `Reflection`

The exact model structure will depend on whether reflections are standalone resources or sections associated with lessons.

### 5.5 Sources

Responsibilities:
- Recording references used by published content.
- Providing source titles, publishers or issuing authorities, URLs, and relevant notes.
- Connecting a source to one or more content items.

Proposed entity:
- `Source`

A reusable source model will help avoid copying the same reference into many unrelated records.

## 6. Proposed Data Relationships

The initial data model should support the following relationships:

- A learning journey can contain multiple lessons.
- A lesson can cover multiple topics.
- A saint can have multiple supporting sources.
- A miracle account can have one or more associated locations, depending on the event.
- A miracle account can have multiple supporting sources.
- A prayer or reflection can reference related lessons and sources.
- A source can support multiple content items.

The exact Django model relationships will be finalized during implementation, based on the MVP and actual content requirements.

Content identifiers should be stable. User-facing titles and descriptions should be separate from internal identifiers wherever appropriate.

## 7. API Design

The backend will expose versioned REST endpoints when the API foundation is ready.

The proposed base path is `/api/v1/`.

Example endpoint groups:

| Resource | Proposed endpoint |
|---|---|
| Learning journeys | `/api/v1/learning-journeys/` |
| Lessons | `/api/v1/lessons/` |
| Topics | `/api/v1/topics/` |
| Saints | `/api/v1/saints/` |
| Miracles | `/api/v1/miracles/` |
| Locations | `/api/v1/locations/` |
| Prayers | `/api/v1/prayers/` |
| Reflections | `/api/v1/reflections/` |
| Sources | `/api/v1/sources/` |

These are proposed endpoints, not implemented routes.

List endpoints should support appropriate filtering and pagination as the amount of content grows. Detail endpoints should return the content and relevant source references required by the frontend.

The API should use consistent error responses and suitable HTTP status codes.

## 8. Content Integrity and Recognition Status

Content accuracy is a core architectural concern.

### 8.1 Source Attribution

Where applicable, a source record should include:
- Title.
- Author, publisher, or issuing authority.
- URL or publication reference.
- Publication date, if known.
- Access date for online references, where useful.
- Notes about which claim the source supports.

### 8.2 Miracle Status

The miracle data model must distinguish the type of claim and its documented status.

The final status vocabulary should be reviewed against the relevant Church authority and event type. Possible distinctions include formally recognized or approved, under investigation, reported without a formal determination, and uncertain or disputed.

These categories must not imply that all miracle types follow the same investigation process. The UI should explain the meaning of each status and avoid presenting a lack of formal determination as proof for or against a supernatural event.

### 8.3 Editorial Review

New content should be reviewed before publication. Editorial review may initially be a documented manual process; a dedicated content administration workflow can be added later.

## 9. Future AI Assistant

A source-grounded AI assistant is a future enhancement and is not required for the initial MVP.

When implemented, it should:
- Retrieve relevant information from approved content and trusted references.
- Provide source links or citations with its answers.
- Distinguish established Catholic teaching from disputed historical claims and personal interpretations.
- Acknowledge uncertainty when evidence is incomplete.
- Avoid inventing quotations, references, or Church decisions.
- Avoid presenting itself as a substitute for pastoral guidance.

The design should keep content retrieval and source attribution separate from language generation so that answers can be evaluated and tested.

Any external AI provider, data handling policy, costs, and security implications must be assessed before implementation.

## 10. Security and Configuration

- Keep secrets in environment variables or an appropriate secrets manager.
- Maintain a safe example environment file without real credentials.
- Configure Django's allowed hosts, debug mode, and secret key appropriately for each environment.
- Validate input using Django forms, model validation, or serializers as appropriate.
- Apply appropriate permissions to any write or administrative endpoints.
- Use Django's built-in security protections.
- Configure CORS narrowly if the frontend and backend require cross-origin requests.
- Do not expose administrative or content-editing capabilities through public endpoints without authorization.

Authentication is not required solely to read public educational content. If user-specific features are introduced, the authentication and authorization design must be reviewed first.

## 11. Testing Strategy

### Backend

- Model and validation tests.
- API endpoint tests.
- Tests for source relationships and content status.
- Permission tests for any protected functionality.
- Tests for important business rules.

### Frontend

- Component tests for important user interactions.
- API loading, empty, and error state tests.
- Navigation and accessibility checks.
- End-to-end tests for critical journeys when appropriate.

Tests should be introduced alongside each feature instead of being postponed until the end.

## 12. Development and Deployment Environments

### Local Development

- Django backend running in a local development environment.
- React frontend running using the existing frontend tooling.
- SQLite database for initial development.
- Environment-specific configuration for local settings.

### Production

Production deployment details are not yet finalized.

Before deployment, the project must define its hosting platform, production database, static asset handling, HTTPS, logging, backups, environment variables, and operational monitoring.

## 13. GitHub Workflow

All meaningful changes should follow the project's existing workflow:

1. Create or update a GitHub Issue.
2. Create a feature branch from the current `main`.
3. Implement one focused change.
4. Run relevant checks and tests.
5. Commit changes with clear messages and reference the Issue where appropriate.
6. Push the branch to GitHub.
7. Open a pull request describing the change and its verification.
8. Review and merge the pull request.

Documentation and implementation should remain aligned. Significant architecture changes should be documented through the same review process.

## 14. Incremental Implementation Plan

### Phase 1: Requirements and Architecture

- Finalize the MVP requirements.
- Review and update this architecture.
- Confirm the existing backend and frontend structure.
- Identify dependencies already installed and any missing components.

### Phase 2: Backend Foundation

- Verify Django configuration and dependency versions.
- Establish API conventions.
- Design the first data models.
- Add migrations and automated tests as required.

### Phase 3: Frontend Foundation

- Verify the existing React and TypeScript setup.
- Establish routing and reusable UI patterns.
- Add a consistent API client and error handling.

### Phase 4: Learning Content

- Implement learning journeys, lessons, and topics.
- Add source attribution.
- Connect the frontend to the backend.

### Phase 5: Saints and Miracles

- Implement saint profiles, miracle accounts, locations, and source relationships.
- Define and validate recognition status.
- Add sourced initial content.

### Phase 6: Prayer and Reflection

- Implement prayer and reflection resources.
- Connect related lessons and references.

### Phase 7: Quality and Release Preparation

- Run automated tests and quality checks.
- Review security, accessibility, and content accuracy.
- Document local setup and usage.
- Prepare the application for a portfolio demonstration.

## 15. Architecture Principles

- Build only what is needed for the current milestone.
- Prefer clear, maintainable code over unnecessary abstraction.
- Keep API contracts explicit.
- Treat content sourcing and accuracy as first-class requirements.
- Use controlled values for important classifications.
- Test critical behavior as features are introduced.
- Preserve the existing technology stack unless a documented reason justifies a change.
- Revisit architecture decisions when actual requirements demand it.