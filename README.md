# CommerceETLAV

**Extract → Transform → Load → Analyze → Visualize**

CommerceETLAV is a local, open-source commerce data platform designed to demonstrate an end-to-end Big Data, ETL, data warehouse/lakehouse, analytics, and AI/ML architecture.

The project follows commerce data from generation through streaming, ingestion, storage, transformation, structured analysis, AI/ML analysis, APIs, and visualization.

> **Project Status:** Planning / Initial Development

---

## Executive Summary

CommerceETLAV is designed for three main audiences:

- **Reviewer / Interviewer** — An employer who wants to learn about my software engineering abilities from the project.
- **Demo User** — Anyone who wants to see a small project using Big Data, ETL, data warehouse/lakehouse concepts, analytics, and AI/ML.
- **Developer** — Anyone who wants to build a similar project using Big Data, ETL, data warehouse/lakehouse concepts, analytics, and AI/ML.

### Reviewer / Interviewer

CommerceETLAV demonstrates:

- Big Data and data engineering.
- Distributed data processing.
- Structured analytics.
- AI/ML analysis.
- Microservice architecture.
- APIs and visualization.
- Automated testing.
- Observability.
- Incremental software development.
- Architecture and design decisions.

Recommended reading:

- [1. Project Goals](#1-project-goals)
- [2. Project Architecture](#2-project-architecture)
- [4. Development Process](#4-development-process)
- Project principles.
- Technology stack.
- Project roadmap.

### Demo User

CommerceETLAV is designed to run locally with minimal setup.

A user should be able to install and start the complete platform with one simple command and minimal active interaction.

Recommended reading:

- [3. User Guide](#3-user-guide)
- Quick start.
- Generate data.
- Structured analytics.
- AI/ML analysis.
- Website.
- Running tests.

### Developer

CommerceETLAV demonstrates how multiple application and infrastructure services can be combined into one testable data platform.

Recommended reading:

- [2. Project Architecture](#2-project-architecture)
- Components and repositories.
- Data model.
- [4. Development Process](#4-development-process)
- Testing strategy.
- Project roadmap.
- [5. Additional Documents](#5-additional-documents)

---

## Contents

1. [Project Goals](#1-project-goals)
2. [Project Architecture](#2-project-architecture)
3. [User Guide](#3-user-guide)
4. [Development Process](#4-development-process)
5. [Additional Documents](#5-additional-documents)

---

## Diagram Index

| Diagram | Title | Section |
|---|---|---|
| 2.1 | Data Flow | [2.1 Data Flow](#21-data-flow) |
| 2.2 | Analysis Flow | [2.2 Analysis Flow](#22-analysis-flow) |
| 2.3 | Complete System | [2.3 Complete System](#23-complete-system) |
| 2.4 | Security Extension | [2.9 Security Boundary](#29-security-boundary) |
| 3.1 | Test Flow | [3.9 Running Tests](#39-running-tests) |
| 4.1 | Development Lifecycle | [4.2 Development Lifecycle](#42-development-lifecycle) |
| 4.2 | Tenant Test Flow | [4.4 Testing Strategy](#44-testing-strategy) |
| 5.1 | Documentation Evolution | [5.2 Documentation Evolution](#52-documentation-evolution) |

---

## Table Index

| Table | Title | Section |
|---|---|---|
| 2.1 | Application Services | [2.4 Application Services](#24-application-services) |
| 2.2 | Infrastructure Services | [2.5 Infrastructure Services](#25-infrastructure-services) |
| 2.3 | Technology Stack | [2.7 Technology Stack](#27-technology-stack) |
| 2.4 | Running Services | [2.8 Running Services](#28-running-services) |
| 4.1 | Project Status | [4.5 Project Status](#45-project-status) |
| 4.2 | Project Roadmap | [4.6 Project Roadmap](#46-project-roadmap) |
| 4.3 | Repository Responsibilities | [4.7 Repository Responsibilities](#47-repository-responsibilities) |

---

# 1. Project Goals

## 1.1 Project Description

CommerceETLAV demonstrates a complete commerce data flow:

**Extract → Transform → Load → Analyze → Visualize**

The system generates understandable commerce data and processes it through a modern Big Data architecture.

The same data can be analyzed using both traditional structured-data technologies and AI/ML technologies.

The project is intentionally small enough to run locally and understand, while demonstrating architecture and technologies that are relevant to much larger data systems.

## 1.2 Project Goals

The project demonstrates:

- Data generation and ingestion.
- Event streaming.
- Big Data storage and processing.
- ETL pipelines.
- Data warehouse and lakehouse concepts.
- Structured data analytics.
- SQL analytics.
- AI/ML analysis of unstructured data.
- Combined structured and AI/ML analysis.
- REST APIs.
- Web visualization.
- Workflow orchestration.
- Monitoring and observability.
- Microservice architecture.
- Docker-based local deployment.
- Automated end-to-end testing.

## 1.3 Project Scope

CommerceETLAV is an engineering demonstration.

Its primary purpose is to demonstrate Big Data and AI/ML technologies, architecture patterns, development practices, and engineering decisions.

It is not intended to be a production commerce platform.

Features that introduce significant production complexity without contributing directly to the project's Big Data and AI/ML goals may be intentionally excluded.

The architecture should still make it possible to add such features later without unnecessarily redesigning unrelated components.

## 1.4 Security Scope

Production security is intentionally excluded from the initial implementation.

This is a conscious scope decision rather than an architectural omission.

Authentication, authorization, user management, and advanced security policies would add significant complexity without contributing directly to the primary Big Data and AI/ML goals of the project.

A production system could introduce security incrementally at several levels:

1. **UI access** — control which functionality is presented to a user.
2. **API access** — control which Gateway API operations a user may execute.
3. **Data access** — control which entities and data a user may access through an allowed operation.
4. **Contextual access** — make authorization depend on authentication method, time, previous actions, risk, or other context.

UI restrictions alone are not a security boundary because a client can bypass the UI and access an API directly.

A first security extension could implement authentication and API authorization in the public Gateway without redesigning the internal Big Data platform.

UI-level permissions could later be added to the Website independently.

More advanced data-level and contextual authorization is outside the scope of the initial demonstration.

## 1.5 Structured Analytics

Structured fields use narrow, well-defined types that can be processed using SQL and traditional analytical tools.

Example questions include:

- What is the total revenue per day?
- Which products have the highest conversion rate?
- Which countries generate the most orders?
- Where do customers leave the purchase funnel?
- Which products experienced an increase in returns?

## 1.6 AI/ML Analysis

Commerce data also contains free-text information such as customer reviews.

This allows AI/ML components to answer semantic questions that cannot be answered effectively using ordinary SQL aggregation alone.

Example questions include:

- What problems are customers reporting about a product?
- Why are customers unhappy with a product?
- What new complaint started appearing recently?
- What are the main reasons customers return a product?

## 1.7 Combined Analysis

The strongest use cases combine structured Big Data analytics with semantic AI/ML analysis.

For example:

> Which products experienced a significant increase in returns, and what reasons are customers giving in their reviews?

Traditional analytics can identify **what changed**.

AI/ML can analyze free text to help explain **what customers are describing**.

Together they provide richer business insight.

---

# 2. Project Architecture

## 2.1 Data Flow

CommerceETLAV is composed of independently containerized application services and established open-source infrastructure products.

The complete environment is managed by `commerce-etlav-manager` and runs locally using Docker Compose.

**Diagram 2.1 — Data Flow**

```text
Generator
    ↓
  Kafka
    ↓
Ingestor
    ↓
  MinIO
    ↓
Analyzer / Spark
    ↓
 Iceberg
    ↓
  Trino
    ↓
Presenter
    ↓
 Website
```

The main flow follows commerce data from its creation to its final presentation.

## 2.2 Analysis Flow

Structured analytics and AI/ML analysis operate on the same commerce data but solve different types of problems.

**Diagram 2.2 — Analysis Flow**

```text
                Curated Data
                     │
            ┌────────┴────────┐
            ▼                 ▼
          Trino             Thinker
     SQL Analytics         AI / ML
            │                 │
            └────────┬────────┘
                     ▼
                 Presenter
                     ▼
                  Website
```

Trino handles structured analytical queries.

Thinker handles AI/ML and semantic analysis.

Presenter combines their results behind the public application API.

## 2.3 Complete System

The complete system contains CommerceETLAV microservices, third-party infrastructure services, data components, monitoring, UI, and external testing.

**Diagram 2.3 — Complete System**

```text
                           CommerceETLAV
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│  DATA GENERATION AND INGESTION                                              │
│                                                                             │
│  ┌───────────┐      ┌─────────┐      ┌──────────┐                           │
│  │ Generator │ ───► │  Kafka  │ ───► │ Ingestor │                           │
│  └───────────┘      └─────────┘      └────┬─────┘                           │
│                                           │                                 │
│                                           ▼                                 │
│                                      ┌─────────┐                            │
│                                      │  MinIO  │                            │
│                                      │Data Lake│                            │
│                                      └────┬────┘                            │
│                                           │                                 │
│  PROCESSING AND STORAGE                   ▼                                 │
│                                                                             │
│                                  ┌──────────────────┐                       │
│                                  │ Analyzer / Spark │                       │
│                                  └────────┬─────────┘                       │
│                                           │                                 │
│                                           ▼                                 │
│                                  ┌──────────────────┐                       │
│                                  │ Iceberg / Parquet│                       │
│                                  └────────┬─────────┘                       │
│                                           │                                 │
│                         ┌─────────────────┴─────────────────┐               │
│                         ▼                                   ▼               │
│                  ┌────────────┐                       ┌───────────┐          │
│                  │   Trino    │                       │  Thinker  │          │
│                  │ SQL Query  │                       │  AI / ML  │          │
│                  └─────┬──────┘                       └─────┬─────┘          │
│                        │                                    │                │
│                        └────────────────┬───────────────────┘                │
│                                         ▼                                   │
│                                  ┌─────────────┐                            │
│                                  │  Presenter  │                            │
│                                  │ Public API  │                            │
│                                  └──────┬──────┘                            │
│                                         │                                   │
│                              ┌──────────┴──────────┐                        │
│                              ▼                     ▼                        │
│                       ┌────────────┐         ┌────────────┐                 │
│                       │  Website   │         │  Superset  │                 │
│                       │ Demo UI    │         │ BI / Charts│                 │
│                       └────────────┘         └────────────┘                 │
│                                                                             │
│  ORCHESTRATION                       OBSERVABILITY                           │
│                                                                             │
│  ┌────────────┐                      ┌────────────┐   ┌────────────┐         │
│  │  Airflow   │                      │ Prometheus │──►│  Grafana   │         │
│  │ Workflows  │                      │  Metrics   │   │ Dashboard  │         │
│  └────────────┘                      └────────────┘   └────────────┘         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
                    ▲                                  ▲
                    │                                  │
                    └──────────┐            ┌──────────┘
                               │            │
                         ┌─────┴────────────┴─────┐
                         │      E2E Tester        │
                         │ REST / Selenium Tests  │
                         └────────────────────────┘
```

The Tester remains outside the system boundary and validates the system as an external client.

## 2.4 Application Services

**Table 2.1 — Application Services**

| #  | Repository | Service Role | Responsibility |
|---:|---|---|---|---|
| 1 | `commerce-etlav-manager` | Management | Integrates the complete project, infrastructure, configuration, scripts, Docker Compose, and documentation |
| 2 | `commerce-etlav-generator` | Generation | Generates deterministic commerce data and events |
| 3 | `commerce-etlav-ingestor` | Ingestion | Consumes events and persists incoming commerce data |
| 4 | `commerce-etlav-analyzer` | Analytics | Performs structured ETL and analytical processing |
| 5 | `commerce-etlav-thinker` | AI/ML | Performs AI/ML and semantic analysis |
| 6 | `commerce-etlav-presenter` | Gateway | Provides the public backend API and application Gateway |
| 7 | `commerce-etlav-website` | Visualization | Provides the user-facing web application |
| 8 | `commerce-etlav-tester` | Testing | Performs external black-box E2E testing |

Each application repository owns its application source code and Dockerfile.

## 2.5 Infrastructure Services

**Table 2.2 — Infrastructure Services**

| # | Product | Role | Responsibility |
|---:|---|---|---|
| 1 | Apache Kafka | Streaming | Provides the event stream between producers and consumers |
| 2 | MinIO | Data Lake | Provides local S3-compatible object storage |
| 3 | Apache Spark | Processing | Performs distributed data transformation and processing |
| 4 | Trino | SQL Query | Executes distributed SQL queries over curated data |
| 5 | Apache Airflow | Orchestration | Schedules and coordinates data workflows |
| 6 | Apache Superset | BI | Provides analytical dashboards and business visualization |
| 7 | Prometheus | Metrics | Collects system and application metrics |
| 8 | Grafana | Monitoring | Visualizes operational metrics and system health |

Infrastructure configuration and required infrastructure Dockerfiles are owned by `commerce-etlav-manager`.

## 2.6 Data Components

The main data components are:

- **Parquet** — column-oriented physical data format optimized for analytical workloads.
- **Apache Iceberg** — table format providing schemas, metadata, snapshots, and table management over data files.
- **MinIO objects** — physical storage for raw and processed data.

Parquet and Iceberg are data technologies rather than independent running microservices.

The intended storage relationship is:

```text
MinIO
  │
  ├── Raw Data
  │
  └── Curated Data
        │
        └── Iceberg Tables
              │
              └── Parquet Files
```

## 2.7 Technology Stack

**Table 2.3 — Technology Stack**

| # | Area | Technology | Purpose |
|---:|---|---|---|
| 1 | Application Backend | Java / Spring Boot | Generator, Ingestor, Presenter, and related backend services |
| 2 | AI/ML Backend | Python / FastAPI | Thinker AI/ML service |
| 3 | Frontend | React / TypeScript | CommerceETLAV Website |
| 4 | Streaming | Apache Kafka | Commerce event streaming |
| 5 | Object Storage | MinIO | Local data lake |
| 6 | Data Format | Parquet | Analytical file storage |
| 7 | Table Format | Apache Iceberg | Lakehouse table management |
| 8 | Data Processing | Apache Spark | Distributed ETL and processing |
| 9 | SQL Analytics | Trino | Distributed analytical SQL |
| 10 | Orchestration | Apache Airflow | Pipeline scheduling and coordination |
| 11 | BI | Apache Superset | Business dashboards |
| 12 | Metrics | Prometheus | Metrics collection |
| 13 | Monitoring | Grafana | Operational dashboards |
| 14 | Containers | Docker | Service packaging |
| 15 | Integration | Docker Compose | Complete local system execution |
| 16 | API Testing | Java / Python | Black-box REST E2E testing |
| 17 | UI Testing | Selenium | Black-box Website E2E testing |

The project prefers technologies that are:

- Open source.
- Popular and recognizable.
- Appropriate for their architectural role.
- Locally runnable.
- Simple enough to demonstrate and explain.

## 2.8 Running Services

The exact ports will be finalized during implementation.

**Table 2.4 — Running Services**

| # | Service | Role | Type | Protocol / Address | Description |
|---:|---|---|---|---|---|
| 1 | Generator | Generate | Microservice — Java / Spring Boot | HTTP / `localhost:<port>` | Generates commerce data and events |
| 2 | Kafka | Stream | Infrastructure — Apache Kafka | Kafka / `localhost:<port>` | Provides the commerce event stream |
| 3 | Ingestor | Ingest | Microservice — Java / Spring Boot | HTTP / `localhost:<port>` | Consumes and persists incoming events |
| 4 | MinIO | Store | Infrastructure — MinIO | HTTP / `localhost:<port>` | Stores raw and processed data |
| 5 | Spark | Transform | Infrastructure — Apache Spark | HTTP UI / `localhost:<port>` | Executes distributed ETL processing |
| 6 | Analyzer | Analyze | Microservice | HTTP / `localhost:<port>` | Coordinates structured analytical processing |
| 7 | Trino | Query | Infrastructure — Trino | HTTP / `localhost:<port>` | Executes SQL analytics |
| 8 | Thinker | AI/ML | Microservice — Python / FastAPI | HTTP / `localhost:<port>` | Performs semantic and AI/ML analysis |
| 9 | Presenter | Gateway | Microservice — Java / Spring Boot | HTTP / `localhost:<port>` | Provides the public backend API |
| 10 | Website | Visualize | Microservice — React / TypeScript | HTTP / `localhost:<port>` | Provides the main user interface |
| 11 | Superset | BI | Infrastructure — Apache Superset | HTTP / `localhost:<port>` | Provides analytical dashboards |
| 12 | Airflow | Orchestrate | Infrastructure — Apache Airflow | HTTP / `localhost:<port>` | Coordinates data workflows |
| 13 | Prometheus | Metrics | Infrastructure — Prometheus | HTTP / `localhost:<port>` | Collects operational metrics |
| 14 | Grafana | Monitor | Infrastructure — Grafana | HTTP / `localhost:<port>` | Displays operational dashboards |
| 15 | Tester | Test | External test application | CLI / optional HTTP | Executes black-box E2E scenarios |

## 2.9 Security Boundary

The Tester and normal clients should interact with CommerceETLAV through documented public interfaces.

Tests should not depend on internal Kafka topics, MinIO files, Iceberg metadata, or other implementation details to determine whether a scenario succeeded.

API authentication and authorization can later be added at the Presenter / Gateway boundary.

**Diagram 2.4 — Security Extension**

```text
Website
    │
    ▼
Presenter / Gateway
    │
    ├── Authentication
    ├── API Authorization
    │
    ▼
Internal Services
```

This allows basic API security to be added without redesigning the Big Data pipeline.

## 2.10 Commerce Data Model

The data model represents understandable commerce concepts such as:

- Customers.
- Products.
- Sessions.
- Searches.
- Product views.
- Shopping carts.
- Orders.
- Purchases.
- Returns.
- Reviews.

Events contain mostly structured fields and at least one optional free-text field.

Example:

```json
{
  "eventId": "e-10042",
  "timestamp": "2026-09-20T18:42:10Z",
  "customerId": "c-104",
  "productId": "p-42",
  "sessionId": "s-992",
  "eventType": "PRODUCT_REVIEW",
  "country": "CA",
  "price": 129.99,
  "rating": 2,
  "text": "Battery stopped charging after one week."
}
```

Structured fields support SQL and traditional analytics.

Free-text fields support semantic AI/ML analysis.


## 2.11 Docker Topology

CommerceETLAV uses Docker Compose to run the complete platform locally.

The proposed final architecture contains **19 Docker containers**:

- **7 application containers** — CommerceETLAV microservices, Website, and Tester.
- **12 infrastructure containers** — third-party services, metadata storage, and initialization utilities.

Of these, **16 containers run continuously**, while **3 containers run only during initialization or testing**.

The architecture is designed for a single-machine, non-production demonstration.

The goals are:

- Run the complete platform using one Docker Compose configuration.
- Keep application services independently containerized.
- Use established open-source infrastructure products.
- Minimize unnecessary containers and operational complexity.
- Make service dependencies and communication explicit.
- Allow incremental development and integration.
- Avoid production-specific complexity such as clustering, replication, and high availability.

### Docker and Roles

**Table — Docker and Roles**

| # | Container | Application / Service | Role |
|---:|---|---|---|
| 1 | `generator` | Java / Spring Boot | Generate deterministic commerce events |
| 2 | `ingestor` | Java / Spring Boot | Consume Kafka events and store raw data |
| 3 | `analyzer` | Spark-based processing application | Transform, clean, aggregate, and write curated data |
| 4 | `thinker` | Python / FastAPI | Perform AI/ML semantic analysis |
| 5 | `presenter` | Java / Spring Boot | Provide the public REST API and application Gateway |
| 6 | `website` | React / Web Server | Provide the user-facing interface |
| 7 | `tester` | Java / Python + Selenium | Execute external black-box E2E tests |
| 8 | `kafka` | Apache Kafka / KRaft | Provide the event streaming broker |
| 9 | `minio` | MinIO | Provide S3-compatible object storage |
| 10 | `spark` | Apache Spark | Execute distributed ETL jobs in local mode |
| 11 | `iceberg-catalog` | Iceberg REST Catalog | Manage Iceberg table metadata |
| 12 | `trino` | Trino | Query Iceberg tables using SQL |
| 13 | `airflow` | Apache Airflow | Schedule and coordinate data workflows |
| 14 | `superset` | Apache Superset | Provide BI dashboards and SQL visualization |
| 15 | `prometheus` | Prometheus | Collect and store application and infrastructure metrics |
| 16 | `grafana` | Grafana | Provide operational monitoring dashboards |
| 17 | `postgres` | PostgreSQL | Store metadata for Airflow and Superset |
| 18 | `airflow-init` | Airflow Initialization | Initialize and migrate the Airflow metadata database |
| 19 | `minio-init` | MinIO Client | Initialize buckets and storage configuration |

**Container Notes**

1. **Manager Repository**
   - `commerce-etlav-manager` is a GitHub repository, not a running container.
   - It owns the main `docker-compose.yml`, infrastructure configuration, and maintenance scripts.

2. **Application Containers**
   - Each CommerceETLAV application repository owns its application code and Dockerfile.
   - Application containers can be built and updated independently.

3. **Tester Container**
   - `tester` is an external black-box testing application.
   - It runs on demand and exits when testing is complete.
   - It validates the platform through documented public APIs and the Website.

4. **Initialization Containers**
   - `airflow-init` and `minio-init` execute during environment initialization.
   - They exit after their initialization tasks finish successfully.

5. **Data Components**
   - Parquet is a physical file format.
   - Apache Iceberg is a table format.
   - Neither requires a dedicated processing container.
   - The Iceberg REST Catalog is a separate service that manages table metadata.

6. **Kafka**
   - Kafka uses KRaft mode.
   - A separate ZooKeeper container is not required.

7. **Spark**
   - Spark initially runs in local mode.
   - Separate Spark worker containers are not required.
   - The relationship between `analyzer` and `spark` will be finalized during implementation.

8. **PostgreSQL**
   - One PostgreSQL container supports both Airflow and Superset.
   - Each application uses a separate database or schema.

9. **Deployment Scope**
   - The topology does not include production clustering, replication, or high availability.
   - Additional exporters or supporting services may be introduced if required.

10. **Container Count**
    - The 19-container architecture is a proposed final topology.
    - The actual count may change as implementation decisions are finalized.

### Docker Communications

Containers communicate through Docker Compose networking.

Internal services should use Docker Compose service names rather than fixed container IP addresses.

For example:

```text
kafka:9092
minio:9000
trino:8080
thinker:8000
presenter:8080
```

Only services that require access from a browser, developer machine, or external client should publish ports to the host.

**Table — Docker Communications**

| # | Source | Destination | Protocol | Purpose |
|---:|---|---|---|---|
| 1 | Generator | Kafka | Kafka TCP | Publish commerce events |
| 2 | Ingestor | Kafka | Kafka TCP | Consume commerce events |
| 3 | Ingestor | MinIO | S3 API / HTTP | Store raw commerce data |
| 4 | Analyzer | Spark | Spark Job Submission | Execute ETL processing |
| 5 | Spark | MinIO | S3 API / HTTP | Read raw data and write Parquet files |
| 6 | Spark | Iceberg Catalog | REST / HTTP | Resolve and update Iceberg table metadata |
| 7 | Iceberg Catalog | MinIO | S3 API / HTTP | Access table metadata and storage |
| 8 | Trino | Iceberg Catalog | REST / HTTP | Discover Iceberg tables and metadata |
| 9 | Trino | MinIO | S3 API / HTTP | Read curated Parquet data |
| 10 | Thinker | Trino | SQL / HTTP | Retrieve structured data for AI/ML analysis |
| 11 | Presenter | Trino | SQL / HTTP | Execute structured analytical queries |
| 12 | Presenter | Thinker | REST / HTTP | Request AI/ML insights |
| 13 | Website | Presenter | REST / HTTP | Request application data |
| 14 | Presenter | Generator | REST / HTTP | Trigger commerce data generation |
| 15 | Presenter | Analyzer | REST / HTTP | Trigger or inspect analytical processing |
| 16 | Airflow | Analyzer | REST / HTTP | Trigger processing workflows |
| 17 | Airflow | PostgreSQL | PostgreSQL TCP | Store orchestration metadata |
| 18 | Superset | Trino | SQL / HTTP | Execute analytical queries |
| 19 | Superset | PostgreSQL | PostgreSQL TCP | Store BI dashboard metadata |
| 20 | Prometheus | Application Services | HTTP `/actuator/prometheus` or `/metrics` | Collect application metrics |
| 21 | Prometheus | Infrastructure Exporters | HTTP `/metrics` | Collect supported infrastructure metrics |
| 22 | Grafana | Prometheus | HTTP API | Query operational metrics |
| 23 | Tester | Presenter | REST / HTTP | Execute public API E2E tests |
| 24 | Tester | Generator | REST / HTTP | Test Generator before Presenter is implemented |
| 25 | Tester | Website | HTTP / WebDriver | Execute browser-based E2E tests |
| 26 | `airflow-init` | PostgreSQL | PostgreSQL TCP | Initialize the Airflow metadata database |
| 27 | `minio-init` | MinIO | S3 API / HTTP | Create required storage buckets |

**Communication Notes**

1. **Internal Networking**
   - Containers use Docker Compose DNS and service names.
   - Internal communication does not require publishing ports to the host.

2. **Public Gateway**
   - Presenter is the primary public backend API.
   - Website communicates with Presenter to retrieve data and execute supported operations.
   - Browser-based requests require a browser-accessible address or reverse proxy.

3. **Event Streaming**
   - Generator publishes commerce events to Kafka.
   - Ingestor consumes those events and persists raw data in MinIO.

4. **Data Processing**
   - Analyzer coordinates structured ETL processing.
   - Spark reads raw data from MinIO and writes curated data using Parquet and Iceberg.
   - The exact Analyzer-to-Spark job execution mechanism will be selected during implementation.

5. **Lakehouse Metadata**
   - Spark and Trino communicate with the Iceberg REST Catalog.
   - Both access the underlying data stored in MinIO.
   - The Catalog implementation and its metadata persistence configuration will be finalized during implementation.

6. **Structured Analytics**
   - Trino executes SQL queries against curated Iceberg tables.
   - Presenter uses Trino for application-level structured analytics.
   - Superset can query Trino directly for BI dashboards.

7. **AI/ML Analysis**
   - Thinker can retrieve structured analytical data from Trino.
   - Presenter invokes Thinker through its REST API.
   - Combined analysis connects structured analytical results with semantic AI/ML insights.

8. **Workflow Orchestration**
   - Airflow coordinates data-processing workflows.
   - It can trigger Analyzer operations and track workflow execution.
   - Airflow stores its orchestration metadata in PostgreSQL.

9. **Observability**
   - Prometheus collects metrics from supported application and infrastructure endpoints.
   - Grafana queries Prometheus to display operational dashboards.
   - Infrastructure services without native Prometheus endpoints may require exporters.

10. **External Testing**
    - Tester interacts with documented public APIs and the Website.
    - It should not directly inspect Kafka, MinIO, Iceberg, or other internal data stores to determine test success.
    - During early milestones, Tester may access Generator directly before Presenter exists.

11. **Initialization**
    - `airflow-init` prepares the Airflow metadata database.
    - `minio-init` creates required storage buckets and configuration.
    - These containers are not continuously running services.

12. **Security Scope**
    - Production authentication and authorization are intentionally excluded from the initial demo.
    - API authentication and authorization can later be added at the Presenter / Gateway boundary.
    - UI permissions can be added independently to the Website.
    - Data-level and contextual authorization require additional design and are outside the initial scope.

### Architecture Decisions

The following decisions should be finalized during implementation:

- **Analyzer and Spark** — whether Analyzer remains a separate service or executes directly inside the Spark container.
- **Iceberg Catalog** — which REST Catalog implementation and metadata persistence approach to use.
- **Airflow Deployment** — whether a single Airflow container is sufficient or separate scheduler/API components are required.
- **AI/ML Runtime** — which local AI/ML libraries or models Thinker will use and whether additional model-serving infrastructure is necessary.
- **Metrics Exporters** — which infrastructure components require separate exporters.
- **Public Ports** — which services expose localhost ports and which remain internal.
- **Resource Limits** — memory and CPU allocation for a practical single-machine demonstration.

The objective is to preserve a simple, understandable, and runnable Docker Compose environment while demonstrating the complete Big Data and AI/ML architecture.

---

# 3. User Guide

## 3.1 Quick Start

The final project should require minimal active setup.

The intended workflow is approximately:

```bash
git clone <commerce-etlav-manager-url>
cd commerce-etlav-manager
python scripts/install.py
```

The installation script will:

1. Validate prerequisites.
2. Download or clone required CommerceETLAV repositories.
3. Prepare infrastructure configuration.
4. Build application Docker images.
5. Start the Docker Compose environment.
6. Wait for service health checks.
7. Initialize required data.
8. Display public service addresses.

A reviewer should require approximately one minute or less of active interaction.

Downloads and Docker image builds may continue automatically for several minutes.

## 3.2 Expected Startup

Expected final output will be similar to:

```text
CommerceETLAV started successfully.

Website:       http://localhost:<port>
API:           http://localhost:<port>
Superset:      http://localhost:<port>
Grafana:       http://localhost:<port>

System status: HEALTHY
```

## 3.3 System Operations

The Manager will provide simple commands or scripts for:

- Start.
- Stop.
- Restart.
- Health check.
- Reset all data.
- Clean the local environment.
- Maintenance operations.

> **TODO:** Add exact commands after implementation.

## 3.4 Generate Data

The Generator will support deterministic commerce scenarios.

Generated data will include structured commerce activity and free-text customer information.

> **TODO:** Add Generator API and examples.

## 3.5 Structured Queries

Users will be able to query structured analytics such as:

- Revenue.
- Orders.
- Conversion rates.
- Product performance.
- Customer journeys.
- Funnel behavior.
- Returns.
- Geographic trends.

Example questions include:

- What was today's revenue?
- Which product has the highest conversion rate?
- Which products have rapidly increasing return rates?
- Which countries generate the most purchases?

> **TODO:** Add API and SQL examples.

## 3.6 AI/ML Queries

Users will be able to query semantic information such as:

- Common customer complaints.
- Emerging product problems.
- Reasons for returns.
- Changes in customer sentiment or reported issues.

Example questions include:

- What problems are customers describing?
- Why are customers unhappy with Product X?
- What new complaint appeared this week?
- What are the main reasons customers return Product X?

> **TODO:** Add AI/ML API examples.

## 3.7 Combined Queries

Combined analysis connects structured trends with semantic information.

Example:

> Which products have rapidly increasing return rates, and what problems are customers describing for those products?

The structured analytical system identifies the affected products.

The AI/ML system analyzes related free text to identify and summarize customer-reported problems.

> **TODO:** Add complete combined-analysis examples.

## 3.8 Website and APIs

The Website will provide a simple demonstration interface for:

- Pipeline state.
- Generated commerce data.
- Structured analytics.
- AI/ML insights.
- Combined insights.
- System status.

Planned public API groups include:

- Generator API.
- Presenter API.
- Administration API.
- AI/ML API exposed through the Presenter.

> **TODO:** Add API documentation, screenshots, and UI usage instructions after implementation.

## 3.9 Running Tests

Tests run against an already running and healthy CommerceETLAV environment.

The initial testing strategy resets all system data before each scenario.

**Diagram 3.1 — Test Flow**

```text
Reset System
      ↓
Generate Deterministic Data
      ↓
Run Data Pipeline
      ↓
Query Public APIs
      ↓
Validate Structured Results
      ↓
Validate AI/ML Results
      ↓
Validate Website
      ↓
PASS / FAIL
```

The project will eventually support two E2E testing methods:

1. REST API testing using a Java or Python black-box tester.
2. Website testing using Selenium.

Future versions may introduce tenants so each test can operate in an isolated data world without resetting the complete system.

---

# 4. Development Process

## 4.1 Project Principles

The project follows these engineering principles:

- **End-to-End First** — Always maintain a functioning vertical path through the system.
- **Incremental Development** — Add one meaningful capability at a time.
- **Always Testable** — Every completed milestone must have automated black-box E2E validation.
- **Simple Reviewer Experience** — A reviewer should require minimal effort to install, start, understand, and demonstrate the project.
- **Explicit Boundaries** — Services communicate through defined contracts rather than knowledge of another service's internal implementation.
- **Deterministic Tests** — Test scenarios create controlled input with predictable expected results.
- **Standard Technologies** — Prefer established and recognizable technologies over unnecessary novelty.
- **Scope Discipline** — Features that add substantial complexity without contributing to the project's Big Data and AI/ML goals are deliberately excluded.
- **Document Decisions** — Important architecture decisions should describe both the selected approach and its rationale.
- **Keep It Runnable** — The main branch should represent a complete runnable and testable system after every completed milestone.

## 4.2 Development Lifecycle

Every milestone follows the same development lifecycle.

**Diagram 4.1 — Development Lifecycle**

```text
Implementation
      ↓
Dockerfile
      ↓
Docker Compose Integration
      ↓
E2E Tester
      ↓
Manual Demonstration
      ↓
User Documentation
      ↓
Developer Documentation
      ↓
Milestone Complete
```

CommerceETLAV must remain runnable and testable after every completed milestone.

## 4.3 Definition of Done

A milestone is complete only when:

1. Its implementation is complete.
2. Required Docker images can be built.
3. It is integrated into the complete Docker Compose environment.
4. Automated E2E tests pass.
5. The functionality has been manually demonstrated.
6. User documentation has been updated.
7. Developer documentation has been updated.

## 4.4 Testing Strategy

The E2E Tester is an external client.

It validates CommerceETLAV through its documented public interfaces.

The first implementation resets all system data before each test.

A future version may introduce tenants.

**Diagram 4.2 — Tenant Test Flow**

```text
Create Tenant
      ↓
Inject Scenario
      ↓
Process Data
      ↓
Query Tenant
      ↓
Validate Results
      ↓
Delete Tenant
```

Tenant isolation would allow tests to execute without affecting unrelated or production-like data.

The two planned E2E test methods are:

- **REST API tests** — fast black-box functional testing against public APIs.
- **Selenium tests** — browser-based validation of important Website user journeys.

REST API tests should provide most functional E2E coverage.

Selenium should cover a smaller set of important user-facing scenarios.

## 4.5 Project Status

**Table 4.1 — Project Status**

| Component | Status |
|---|---|
| Project Architecture | 🟡 Planning |
| Manager | 🟡 Planning |
| Generator | ⚪ Not Started |
| Kafka | ⚪ Not Started |
| Ingestor | ⚪ Not Started |
| MinIO | ⚪ Not Started |
| Analyzer | ⚪ Not Started |
| Spark / Iceberg | ⚪ Not Started |
| Trino | ⚪ Not Started |
| Presenter | ⚪ Not Started |
| Website | ⚪ Not Started |
| Airflow | ⚪ Not Started |
| Prometheus / Grafana | ⚪ Not Started |
| Thinker | ⚪ Not Started |
| Tester | 🟡 Planning |

Status values:

- ⚪ Not Started
- 🟡 In Progress / Planning
- 🟢 Complete

## 4.6 Project Roadmap

**Table 4.2 — Project Roadmap**

| # | Milestone | Result | Affected Components |
|---:|---|---|---|
| 1 | Generator | Generate deterministic commerce data | Generator |
| 2 | Streaming | Stream commerce events | Generator, Kafka |
| 3 | Ingestion | Persist raw events | Ingestor, MinIO |
| 4 | ETL | Clean and transform data | Analyzer, Spark, Iceberg |
| 5 | Analytics | Query structured data | Analyzer, Trino |
| 6 | API | Expose public data APIs | Presenter |
| 7 | Visualization | Provide user-facing demo | Website |
| 8 | Orchestration | Automate pipeline workflows | Airflow |
| 9 | Observability | Monitor system behavior | Prometheus, Grafana |
| 10 | AI/ML | Analyze semantic data | Thinker |

> **Note:** `commerce-etlav-manager` and `commerce-etlav-tester` are omitted from the affected-components column because every milestone updates both repositories.

Detailed milestone requirements and acceptance criteria will be maintained in `roadmap.md`.

## 4.7 Repository Responsibilities

**Table 4.3 — Repository Responsibilities**

| # | Repository | Service Role | Responsibility |
|---:|---|---|---|
| 1 | `commerce-etlav-manager` | Management | Complete system integration, infrastructure, Docker Compose, scripts, and documentation |
| 2 | `commerce-etlav-generator` | Generation | Generate deterministic commerce data and events |
| 3 | `commerce-etlav-ingestor` | Ingestion | Consume events and persist raw commerce data |
| 4 | `commerce-etlav-analyzer` | Analytics | Perform structured ETL and analytical processing |
| 5 | `commerce-etlav-thinker` | AI/ML | Perform semantic and AI/ML analysis |
| 6 | `commerce-etlav-presenter` | Gateway | Provide the public backend API |
| 7 | `commerce-etlav-website` | Visualization | Provide the user-facing web application |
| 8 | `commerce-etlav-tester` | Testing | Execute external black-box E2E scenarios |

Each CommerceETLAV application repository owns:

- Application source code.
- Unit tests.
- Service-specific configuration.
- Its Dockerfile.
- Service-specific documentation where appropriate.

`commerce-etlav-manager` additionally owns:

- Complete system integration.
- Docker Compose.
- Third-party infrastructure configuration.
- Infrastructure Dockerfiles where required.
- Installation scripts.
- Start, stop, reset, health, and maintenance scripts.
- System-level documentation.

`commerce-etlav-tester` additionally owns:

- Black-box E2E scenarios.
- REST API system tests.
- Future Selenium UI tests.
- Test validation and reporting.

Every milestone modifies at least:

- `commerce-etlav-manager`.
- `commerce-etlav-tester`.

Milestones also modify or introduce the application and infrastructure components required by that milestone.

---

# 5. Additional Documents

## 5.1 Documentation Strategy

CommerceETLAV starts with this single `README.md` as its primary project document.

As the project grows, detailed material will move into dedicated Markdown documents.

The README will remain the primary project entry point.

When detailed information is moved into another document, the README should retain the core ideas and provide a link to the detailed document.

## 5.2 Documentation Evolution

**Diagram 5.1 — Documentation Evolution**

```text
Initial Stage

README.md
    └── Complete project plan and documentation


Growing Project

README.md
    ├── Core concepts
    ├── Important summaries
    └── Links
           ↓
        docs/*.md


Mature Project

README.md
    └── Permanent project entry point

docs/
    ├── user-guide/
    └── developer-guide/
```

## 5.3 Planned Documents

The project may eventually contain:

```text
docs/
├── user-guide/
│   ├── installation.md
│   ├── api.md
│   ├── website.md
│   └── demo.md
│
└── developer-guide/
    ├── architecture.md
    ├── roadmap.md
    ├── data-model.md
    ├── services.md
    ├── testing.md
    ├── ai-architecture.md
    ├── observability.md
    └── maintenance.md
```

User documentation explains how to:

- Install CommerceETLAV.
- Run and stop the system.
- Generate data.
- Use the public APIs.
- Use the Website.
- Run analytics.
- Use AI/ML analysis.
- Run tests.
- Demonstrate the project.

Developer documentation explains:

- Internal architecture.
- Service responsibilities.
- Data flow.
- Design decisions.
- Technology choices.
- Data models.
- Testing architecture.
- AI/ML architecture.
- Infrastructure configuration.
- Maintenance scripts.
- Development roadmap.

Detailed documents will be added only as the project grows enough to justify separating them from this README.