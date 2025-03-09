## Checklist of Software Architecture Patterns to Find Appropriate Design

| Criteria                 | Monolithic | Modular Monolith | Microservices | Serverless | Event-Driven |
|--------------------------|------------|------------------|---------------|------------|--------------|
| **When to Choose?** | MVP, small teams, simple domains | Teams that need modularity but don’t want full microservices complexity | Large teams, complex domains, scalability needs | Variable/sporadic traffic, rapid prototyping | Real-time processing, async workflows |
| **Traffic (Users/Day)** | < 10K (steady) | 10K–100K (moderate growth) | 10K - 1M (predictable growth) | 1M+ (variable: 1K–1M+ spikes) | 1M+ (high concurrency, e.g., IoT, trading) |
| **Data Growth** | < 10GB (structured, SQL) | 10GB–500GB (structured with some modular separation) | 10GB - 1TB (distributed, mixed SQL/NoSQL) | 1TB+ (unpredictable: auto-scaling databases) | 1TB+ (high velocity: streaming data, logs, events) |
| **Complexity** | Simple (single codebase) | Medium (modularized, single deployment) | Medium-High (distributed systems) | Medium (focus on business logic) | High (event choreography, message brokers) |
| **Scalability** | Low (vertical scaling only) | Medium (horizontal scaling within a monolithic deployment) | High (horizontal scaling - per service) | Auto-Scales (managed by cloud provider) | High (async, decoupled services) |
| **DevOps Overhead** | Low (single deploy) | Moderate (versioned modules, testing) | High (CI/CD pipelines, monitoring) | Low (no server management) | Medium-High (message brokers, event sourcing) |
| **Deployment Speed** | Fast (single artifact) | Moderate (module coordination) | Slower (orchestrating multiple services) | Fast (per-function deployment) | Moderate (event schema management) |
| **Cost Efficiency** | Low upfront cost | Moderate (some modular infra but shared deployment) | Moderate-High (infra + DevOps) | Pay-per-use (ideal for spiky workloads) | Moderate-High (event broker costs) |
| **Team Size Estimates** | Small: 1–3 developers (MVP/simple apps like blogs). Medium: 3–5 developers (small e-commerce, CMS). | Medium: 5–10 developers (small-scale microservices, e.g., a SaaS startup). Large: 10–20+ developers (enterprise systems like Amazon, Netflix). | Small: 2–4 developers (prototypes, APIs, or event-triggered tasks). Medium: 4–8 developers (larger serverless workflows, e.g., image processing pipelines). | Medium: 5–8 developers (real-time apps like chat or notifications). Large: 8–15+ developers (IoT platforms, stock trading systems). |
| **Example** | Local store, blog, CMS, small e-commerce | SaaS apps, enterprise software with internal modularity | Large e-commerce (Amazon), SaaS (Slack) | Flash sales, Traffic spikes, Image processing, Cron jobs, API gateways | Real-time stock updates, Real-time analytics (Uber), IoT (Smart Homes) |
| **Real-World Examples** | WordPress, Shopify (basic) | - | Netflix, Spotify, Airbnb | Netflix (image resizing), Coca-Cola (campaigns) | LinkedIn (notifications), Robinhood (trading) |

### Frontend Technologies

| Architecture | Technologies |
|-------------|-------------|
| Server-Side Rendering or Simple SPA | React, Vue |
| Micro Frontends or SPA aggregating Microservices | React, Angular, Vue, Micro Frontend Frameworks, API Composition (BFF) |
| SPA or Static Site (Cloud Storage) | React, Vue, Angular, Cloud Storage (S3, Blob Storage) |
| SPA consuming event streams or APIs | React, Vue, Angular, WebSockets, Server Sent Events (SSE) |

### Backend Technologies

| Architecture | Technologies |
|-------------|-------------|
| Single Application | Django, Ruby on Rails, Laravel, Spring Boot |
| Independent Services | Docker, Kubernetes, API Gateway, Kafka, RabbitMQ, gRPC, REST, NoSQL (MongoDB, Cassandra) |
| Function-as-a-Service (FaaS) | AWS Lambda, Azure Functions, Google Cloud Functions, DynamoDB, Firestore, API Gateway |
| Event-Driven Microservices | Kafka, RabbitMQ, AWS SQS, Event Streams, Microservices |

### Database

| Architecture | Technologies |
|-------------|-------------|
| Monolithic | MySQL, PostgreSQL, SQLite |
| Modular Monolith | PostgreSQL, Redis, Cassandra, NoSQL (MongoDB, Cassandra) |
| Microservices | DynamoDB, Firebase Firestore, Cosmos DB |
| Event-Driven | PostgreSQL, Event Store DB, Apache Kafka Streams |

### Containerization & Orchestration

| Architecture | Technologies |
|-------------|-------------|
| Monolithic | Not required |
| Modular Monolith | Docker, Kubernetes, Istio |
| Serverless | AWS Lambda, Google Cloud Functions |
| Event-Driven | Docker, Kubernetes, Kafka Streams |

## Architecture Patterns & Suitability

### Use Case vs Recommended Patterns

| Use Case | Recommended Patterns | Why? |
|----------|----------------------|------|
| **Enterprise CRUD Apps** | Layered, Monolithic, Hexagonal | Simple, modular, and easy to maintain for small to medium apps. |
| **High-Traffic Systems** | Microservices, Event-Driven, CQRS, Space-Based | Scalability, fault isolation, and parallel processing. |
| **Real-Time Systems (e.g., IoT)** | Event-Driven, Pub/Sub, P2P | Low latency, async communication, and event processing. |
| **Data-Intensive Apps** | Event Sourcing, CQRS, Pipeline-Filter | Efficient data transformation, audit trails, and read/write optimization. |
| **Decentralized Apps** | Blockchain, Peer-to-Peer (P2P) | Trustless transactions, tamper-proof data. |
| **Rapid Prototyping** | Monolithic, Serverless | Fast development, minimal upfront infrastructure costs. |
| **High Security/Compliance** | Layered, Hexagonal, Zero-Trust Architecture | Strict separation of concerns, auditability, and secure dependencies. |
