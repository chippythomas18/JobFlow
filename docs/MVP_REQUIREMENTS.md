# Via Fidei — MVP Requirements

## 1. Project Overview

**Via Fidei** is a Catholic faith and learning application designed to help Catholics deepen their understanding of the Catholic faith and help people exploring Catholicism learn at their own pace.

The application will provide structured learning journeys, reliable educational content, stories of saints, documented miracle accounts, prayer and reflection resources, and eventually a source-grounded AI assistant.

The name *Via Fidei* means “Way of Faith.”

## 2. Problem Statement

People who want to learn about Catholicism may struggle to find information that is organized, easy to understand, trustworthy, and suitable for their level of familiarity with the faith.

Information about Catholic teachings, saints, miracles, Scripture, and prayer is spread across many websites and publications. Users may also find it difficult to distinguish official Church teachings and recognized findings from personal interpretations, traditions, or unverified claims.

Via Fidei aims to make Catholic learning more accessible through organized content, clear explanations, and references to reliable sources.

## 3. Target Audiences

### 3.1 Catholics

Users who want to deepen their understanding of Catholic teaching, Scripture, prayer, the sacraments, saints, and Catholic traditions.

### 3.2 People Exploring Catholicism

Users who are curious about Catholic beliefs, considering becoming Catholic, or preparing to enter the Catholic Church.

Content for this audience should explain unfamiliar terms clearly and avoid assuming prior knowledge of Catholic teaching.

## 4. Product Goals

- Provide accessible, structured Catholic learning.
- Offer separate learning journeys for Catholics and people exploring the faith.
- Present Catholic teachings with references to reliable sources.
- Share biographies and spiritual lessons from saints around the world.
- Present documented miracle accounts with their locations, historical context, sources, and recognition status.
- Encourage prayer, Scripture reading, and personal reflection.
- Plan for a reliable AI assistant that answers questions using trusted Catholic sources.
- Demonstrate professional full-stack software development practices through a maintainable, testable application.

## 5. MVP Scope

The MVP will focus on building a functional foundation and a small, well-sourced set of content rather than attempting to cover every topic immediately.

### 5.1 Learning Journeys

Users should be able to explore learning content organized for the two target audiences.

**For Catholics:**
- Catholic beliefs and teachings.
- Scripture and its place in Catholic life.
- Sacraments and the liturgical year.
- Saints and examples of Christian virtue.
- Prayer and spiritual reflection.

**For people exploring Catholicism:**
- Introduction to Catholicism.
- Core Catholic beliefs.
- The Bible and Catholic understanding of Scripture.
- Jesus Christ and the Church.
- Prayer, worship, and the sacraments.
- Understanding the process of becoming Catholic.

The initial release should provide a limited set of introductory lessons. More advanced topics can be added incrementally.

### 5.2 Catholic Learning Content

Each lesson should support:
- A clear title and topic.
- An accessible explanation.
- Organized sections where appropriate.
- References to relevant and reliable sources.
- Links to related lessons when useful.

Content should distinguish official Catholic teaching from theological opinions, devotional practices, and historical interpretations.

### 5.3 Saints

The application should provide a dedicated section for saints from different countries and historical periods.

Each saint profile may include:
- Name and commonly used titles.
- Country or region and historical period.
- Feast day, where applicable.
- Biography and significant life events.
- Challenges, conversion, vocation, or acts of service.
- Virtues and lessons relevant to daily life.
- Patronage, where officially or reliably documented.
- Reliable references and further reading.

The initial release should contain a small number of researched saint profiles. Additional profiles can be added over time.

### 5.4 Miracles and Places

The application should provide a section exploring documented miracle accounts associated with different locations.

Each account should include, where information is available:
- Name or description of the event.
- Location and country.
- Approximate date or historical period.
- Historical and religious context.
- The account of what reportedly occurred.
- The source of the account.
- The Church's recognition or investigation status.
- Links to official Church documentation or reputable historical and scholarly sources.

Miracle accounts must be described accurately. The application must distinguish between:
- Events formally recognized or approved by the relevant Church authority.
- Events under investigation or awaiting a determination.
- Reported or traditional accounts whose status is uncertain.

The application must not describe every reported miracle as proven. The wording should reflect the available evidence and the precise status of the event.

### 5.5 Prayer and Reflection

The initial release should provide a small collection of Catholic prayers and Scripture-based reflection resources.

Content may include:
- Traditional Catholic prayers.
- Short Scripture passages with references.
- Reflection questions.
- Suggestions for personal prayer.

Prayer and reflection content should include appropriate references where available.

### 5.6 Source and Content Management

Educational content must be traceable to reliable sources.

Preferred sources include:
- The Catechism of the Catholic Church.
- The Bible and official Catholic Scripture resources.
- Vatican publications and documents.
- Official diocesan or Church documentation.
- Reputable historical and scholarly publications.

The application should record the source, title, URL where available, and relevant notes for each content item.

Content should be reviewed for accuracy before publication.

### 5.7 Future AI Assistant

A source-grounded AI assistant is a planned enhancement, not a requirement for the first working release.

Future capabilities may include:
- Answering questions about Catholicism in accessible language.
- Using approved educational content and trusted references.
- Providing source links with answers.
- Acknowledging uncertainty when sources are incomplete or disputed.
- Avoiding unsupported claims about Church teaching or miracle recognition.

The assistant should not invent sources, present speculation as fact, or replace appropriate pastoral guidance.

## 6. Functional Requirements

The initial application should progressively support the following capabilities:

1. Display a home page explaining Via Fidei and its purpose.
2. Let users discover the two learning journeys.
3. Browse and read published lessons.
4. Browse a list of saints and view individual saint profiles.
5. Browse miracle accounts and view their locations and documented status.
6. Browse prayer and reflection resources.
7. Display references and source links for educational content.
8. Provide navigation between related content sections.

Authentication, user profiles, bookmarks, progress tracking, personalized recommendations, and the AI assistant may be introduced in later iterations unless they become necessary after the initial scope is reviewed.

## 7. Non-Functional Requirements

### 7.1 Maintainability

Use a modular architecture with clear separation between the backend, frontend, content data, and application interfaces.

### 7.2 Security

Follow Django security practices, validate input, protect sensitive configuration, and never commit credentials or secret keys to version control.

### 7.3 Accessibility

Use semantic HTML, keyboard-accessible navigation, readable text, meaningful image alternative text, and sufficient color contrast.

### 7.4 Performance

Keep pages responsive and avoid unnecessary database queries or excessive frontend assets.

### 7.5 Reliability and Accuracy

Provide source references for educational claims and represent disputed or uncertain information transparently.

### 7.6 Testing

Add automated tests for important backend functionality and frontend behavior as those features are implemented.

## 8. Technical Stack

The project will retain its existing technology choices.

**Backend**
- Python
- Django
- Django REST Framework, subject to confirmation in the technical architecture
- SQLite for initial local development, with production database decisions documented separately

**Frontend**
- React
- TypeScript
- A suitable frontend build tool already selected for the project

**Development Workflow**
- Git and GitHub.
- GitHub Issues for planning and tracking work.
- Feature branches for individual tasks.
- Pull requests for code review.
- Automated tests and appropriate quality checks.

The technical architecture document will define the detailed responsibilities of each component.

## 9. Out of Scope for the Initial Release

The following are not required for the first working release:

- A comprehensive library of every Catholic teaching, saint, or miracle.
- User accounts and social networking.
- Community discussions or user-generated miracle submissions.
- Donations, purchases, or subscriptions.
- A production-ready AI assistant.
- Mobile applications for iOS or Android.
- Personalized spiritual or theological advice.
- Claims of supernatural certainty where the available evidence does not justify them.

These features may be evaluated for future releases.

## 10. Initial Delivery Milestones

### Milestone 1: Product Definition
- Finalize MVP requirements.
- Update the technical architecture.
- Establish content sourcing and accuracy guidelines.

### Milestone 2: Application Foundation
- Confirm the Django backend structure.
- Establish the React and TypeScript frontend structure.
- Configure environment settings and development instructions.
- Add basic automated checks.

### Milestone 3: Core Learning Experience
- Implement the home page and learning journeys.
- Create the lesson content structure.
- Display a small set of introductory lessons.

### Milestone 4: Saints and Miracles
- Implement saint and miracle content structures.
- Display researched profiles and accounts.
- Include locations, references, and recognition status.

### Milestone 5: Prayer and Reflection
- Add prayer and reflection content.
- Connect relevant resources to learning journeys.

### Milestone 6: Quality and Demonstration
- Test core features.
- Review accessibility, security, content accuracy, and responsive behavior.
- Prepare project documentation and a portfolio demonstration.

## 11. Success Criteria

The MVP will be considered successful when:

- Both audiences can discover an appropriate learning journey.
- Users can browse and read introductory Catholic lessons.
- Users can explore saint profiles and miracle accounts.
- Miracle descriptions clearly identify their documented recognition status.
- Educational content includes meaningful source references.
- Prayer and reflection resources are accessible.
- The application runs using documented setup instructions.
- Core functionality has automated tests.
- Changes follow the project's Issue, branch, and pull request workflow.

## 12. Guiding Principles

Via Fidei will prioritize:
- Faithful and responsible representation of Catholic teaching.
- Clear explanations for beginners and established Catholics alike.
- Reliable sourcing and transparency about uncertainty.
- Respectful presentation of saints, miracles, and devotional traditions.
- Incremental development, maintainable code, and professional engineering practices.