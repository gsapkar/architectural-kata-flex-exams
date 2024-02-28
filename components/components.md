| Component                      | Description               |
|--------------------------------|---------------------------|
| BackOffice Web app             | This will be the container of micro-frontend applications in which will load the: - User Management module - Exams Management module |
| Exam Conduction Web app        | This will be the container of micro-frontend applications in which will load the: - Proctoring module - Testing module The modules will be presented depending on the user role: Proctor or Student The Students must use Lockdown Browser.|
| Mobile Proctoring App          | Android and iOS app for streaming the candidate's videos and taking photos during the exam|
| API Gateway                    | Centralized Entry Point: An API Gateway serves as a single entry point for clients to access the microservices ecosystem. It simplifies the client-side interaction by providing a unified interface for all backend services. It Offers: - Aggregation of Services - Security and Authentication - Rate Limiting and Throttling - Caching - Monitoring and Analytics - Versioning and Lifecycle Management - Cross-Cutting Concerns    |
| Exams & Questions Management API | This API will be used for defining the exams and the questions in it. The exam domain entity will be strictly defined, but the questions can have variable structures. That's why we will use the benefits of PostgreSQL as our database because it offers a very powerful engine for manipulating with JSON fields. After configuring the exam and publishing, it will fire an event in the Event grid, and will write the exam information in the Exam conducting API database, so the Exam conducting API can calculate the results without dependency of the Exams management API. |
| Proctoring API                 | This API will serve both: Proctoring Mobile App, and the Proctoring microfrontend. It will have endpoints for uploading video and documents from the mobile app, and monitoring ongoing exam. The videos and documents will be saved on Azure blob storage and the other data will be saved in PostgreSQL database. |
| Exam Conducting API            | The Exam conducting API will provide the exam questions and will produce the exam results. It can implement caching for faster browsing. After the student finishes the exam, it will send an event to the Event grid which will trigger the Email sender function for sending the exam results to the student.  |
| Audit Trail API                | The Audit Trail API will trail all the actions happened in the whole system in a single database Elasticsearch. When action happens in the bounded context of each API, a domain event will be sent to the Event grid which will trigger the Audit trail Azure function which will write the message to the Elasticsearch DB. This API will have endpoints for various reporting and it will cache paged data for faster performance. |
| User Management API            | The User Management API will manage the roles, permissions, and the user profiles. |
| Chat API                       | The Chat API will be responsible for the chat functionality. It will keep all conversations and chat history between the students and the proctor in a no-SQL database such as Azure Cosmos DB.|
| Integration API                | This API will contain proxies and adapters to various third party integrations: Internal management system, JIRA, Salesforce|
| Third party Exam API           | This API will contain the integration with Pearson VUE Exams, and other exam providers if needed.|