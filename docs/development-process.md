[← Back to Main README](../README.md)

## Table of contents

**4. Development Process**
- [4. Development Process](#4-development-process)
  - [4.1 Project Principles](#41-project-principles)
  - [4.2 Development Lifecycle](#42-development-lifecycle)
  - [4.3 Definition of Done](#43-definition-of-done)
  - [4.4 Testing Strategy](#44-testing-strategy)
  - [4.5 Project Status](#45-project-status)
  - [4.6 Project Roadmap](#46-project-roadmap)
  - [4.7 Repository Responsibilities](#47-repository-responsibilities)

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