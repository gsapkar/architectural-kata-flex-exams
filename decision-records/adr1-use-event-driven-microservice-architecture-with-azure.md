
# Architecture Decision Record (ADR1)

## Title: Event-Driven Microservice Architecture with Microsoft Azure

### Status: Accepted

## Context:
Since the main characteristics of the SSS Exam management and Proctoring system are responsivenes, availability and scalability we have decided to adopt an event-driven approach of communication between microservices to decouple them and enable asynchronous communication. As part of this transition, we are evaluating cloud platforms, and Azure has been chosen as our cloud provider due to its rich set of services and seamless integration capabilities.

## Decision:
We will implement an event-driven microservice architecture using Azure services as follows:

1. **Event Hub:** We will use Azure Event Hubs as the central event ingestion and processing service. Event Hubs can handle millions of events per second and provide features such as partitioning, scaling, and built-in monitoring. Each microservice will publish events to specific Event Hubs, and other microservices can subscribe to these events for processing.

2. **Azure Functions:** We will leverage Azure Functions for event-driven serverless computing. Azure Functions allow us to execute code in response to events without managing infrastructure. We will create functions to subscribe to events from Event Hubs and perform specific business logic or trigger downstream processes. Azure Functions provide scalability, auto-scaling, and cost-efficiency, aligning with our microservices architecture principles.

3. **Azure Database for PostgreSQL:** This will be explained in a separate ADR.

4. **Azure Cosmos DB:** For event sourcing and storing event data, we will utilize Azure Cosmos DB. Cosmos DB is a globally distributed, multi-model database service that offers low-latency, scalable storage for JSON documents. We will store events as documents in Cosmos DB containers, enabling flexible querying, indexing, and analytics on event data. Cosmos DB's multi-region replication ensures high availability and disaster recovery for event data.

5. **Azure Application Insights:** To monitor and troubleshoot our event-driven microservices architecture, we will integrate Azure Application Insights. Application Insights provides real-time telemetry data, performance metrics, and logs for Azure services and applications. We will instrument our microservices with Application Insights SDK to track event processing latency, error rates, and service dependencies.

## Consequences:

**Positive:**
- **Scalability:** Azure services such as Event Hubs, Azure Functions, and Cosmos DB offer scalability and elasticity, allowing our architecture to handle growing event volumes and workloads.
- **Resilience:** Decoupling microservices through asynchronous event-driven communication enhances resilience and fault tolerance, as services can operate independently and handle failures gracefully.
- **Flexibility:** Azure's cloud-native services provide flexibility and agility in building, deploying, and managing event-driven microservices, enabling rapid innovation and iteration.
- **Learning Curve:** The team has skills for development and operations with Azure cloud-native technologies and practices.

**Negative:**

- **Cost Management:** While Azure offers pay-as-you-go pricing, managing costs for cloud services, especially when scaling, requires careful monitoring and optimization to avoid unexpected expenses.

**Risks:**
- **Vendor Lock-in:** Depending heavily on Azure services may increase dependency on the Azure ecosystem, posing risks of vendor lock-in. We will mitigate this risk by designing our microservices with abstraction layers and adhering to industry standards where possible.
- **Performance Bottlenecks:** Inadequate design or configuration of Azure services could lead to performance bottlenecks or scalability limitations. We will conduct thorough testing and performance tuning to ensure optimal performance and scalability of our event-driven architecture.

## References:
- [Azure Event Hubs Documentation](https://docs.microsoft.com/en-us/azure/event-hubs/)
- [Azure Functions Documentation](https://docs.microsoft.com/en-us/azure/azure-functions/)
- [Azure Service Bus Documentation](https://docs.microsoft.com/en-us/azure/service-bus-messaging/)
- [Azure Cosmos DB Documentation](https://docs.microsoft.com/en-us/azure/cosmos-db/)
- [Azure Application Insights Documentation](https://docs.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)
