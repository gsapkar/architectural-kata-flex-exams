## Background
In response to the evolving demands of modern professionals, FLEX EXAMS will enable candidates to conveniently undertake examinations from the comfort of their homes, tailored to their schedules. 
Candidates can opt for comprehensive training through third-party providers or pursue self-study methodologies. 
Committed to delivering a seamless and dependable examination experience, FLEX EXAMS is a solution that not only encompasses essential functionalities but also offers responsive support, minimal downtime, and expedited update deployments.

## Requirements
### Functional
#### Exam Management
-	Ability to administer and maintain questions library, exam templates and email templates
-	Create, schedule and monitor exams, define multiple settings for them such as categories, navigation rules and scoring rules
#### User Management
-	Ability to administer users, roles and permissions
#### Questions Management
-	Ability to choose predefined question types, but also be flexible for easy upgrade with new types
-	Support rich content such as pictures, audio, video
#### Audit Trail
-	Logging the actions that users perform
-	Search and filter the audit trails list
#### Proctoring
-	Ability to register participants and verify identity via ID documents
-	Ability to follow the participants actions through video and photos during the exam

### Non-Functional
#### Scalability & Elasticity
-	Support up to 1000 users at a time and handle increased load at peak times
#### Availability
-	The system should be highly available with near zero downtime
#### Security
-	Available only for authenticated and authorized users
-	Provide confidentiality and integrity of data
#### Usability
-	The system should be localized in multiple languages
-	The system should be easy to use and have intuitive UI compliant to W3C standards
-	Page load time should be up to 5 seconds, ideally under 2 seconds

## Proposed Solution
### Architecture Style

While analysing the requirements, we identified various architecture characterstics.
