# CommerceETLAV

**Extract → Transform → Load → Analyze → Visualize**

CommerceETLAV is a local, open-source commerce data POC application. \
It demonstrates Big Data, ETL, data warehousing/lakehouse, analytics and AI/ML. \
The project follows commerce data from generation to visualization, query and end-to-end tests. \
It covers streaming, ingestion, storage, transformation, structured analysis, AI/ML analysis and APIs.


> **Project Status:** Planning / Initial Development

## Main Readme Overview
- [Project Architecture](#project-architecture)
- [Project Documentation](#project-documentation)
- [Executive Summary](#executive-summary)
- [Table of Contents](#table-of-contents)
- [Diagram Index](#diagram-index)
- [Table Index](#table-index)

## Project Architecture

![Commerce ETLAV Architecture](docs/images/commerce_etlav_microservices_architecture_150kb.jpg)

## Project Documentation

- [Project Goals](docs/goals.md) — Purpose, scope, and objectives.
- [Project Architecture](docs/architecture.md) — Services, data flows, and technologies.
- [User Guide](docs/user-guide.md) — Installation, operations, analytics, and testing.
- [Development Process](docs/development-process.md) — Principles, lifecycle, testing, and roadmap.
- [Additional Documents](docs/additional-documents.md) — Documentation strategy and future plans.

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

## Table of Contents 

Table of Contents for the entire documentation, including `README.md` and all documents in the `docs` folder. 

**Summary and Contents**

- [Executive Summary](#executive-summary)
  - [Reviewer / Interviewer](#reviewer--interviewer)
  - [Demo User](#demo-user)
  - [Developer](#developer)
- [Contents](#table-of-content)
- [Diagram Index](#diagram-index)
- [Table Index](#table-index)

**1. Project Goals**
- [1. Project Goals](#1-project-goals)
  - [1.1 Project Description](#11-project-description)
  - [1.2 Project Demonstrates](#12-project-demonstrates)
  - [1.3 Project Scope](#13-project-scope)
  - [1.4 Security Scope](#14-security-scope)
  - [1.5 Structured Analytics](#15-structured-analytics)
  - [1.6 AI/ML Analysis](#16-aiml-analysis)
  - [1.7 Combined Analysis](#17-combined-analysis)

**2. Project Architecture**
- [2. Project Architecture](#2-project-architecture)
  - [2.1 Data Flow](#21-data-flow)
  - [2.2 Analysis Flow](#22-analysis-flow)
  - [2.3 Complete System](#23-complete-system)
  - [2.4 Application Services](#24-application-services)
  - [2.5 Infrastructure Services](#25-infrastructure-services)
  - [2.6 Data Components](#26-data-components)
  - [2.7 Technology Stack](#27-technology-stack)
  - [2.8 Running Services](#28-running-services)
  - [2.9 Security Boundary](#29-security-boundary)
  - [2.10 Commerce Data Model](#210-commerce-data-model)
  - [2.11 Docker Topology](#211-docker-topology)
    - [Docker and Roles](#docker-and-roles)
    - [Docker Communications](#docker-communications)
    - [Architecture Decisions](#architecture-decisions)
  - [2.12 Docker Architecture](#212-docker-architecture)
    - [Diagram 2.5 Color Legend](#diagram-25-color-legend)
  - [2.13 Docker Communication by Trigger](#213-docker-communication-by-trigger)
    - [Diagram 2.6 Color Legend](#diagram-26-color-legend)
    - [Diagram Notes](#diagram-notes)
    - [Implementation Note](#implementation-note)
  - [2.14 Docker Communication by Protocol](#214-docker-communication-by-protocol)
    - [Diagram 2.7 — Docker Communication by Protocol](#diagram-27--docker-communication-by-protocol)
    - [Diagram 2.7 Color Legend](#diagram-27-color-legend)
    - [Communication Notes](#communication-notes)
 - [2.15 Microservices Architecture](#215-microservices-architecture)
    - [Diagram 2.8 — Microservices Architecture](#diagram-28--microservices-architecture)
    - [Diagram 2.8 Color Legend](#diagram-28-color-legend)

**3. User Guide**
- [3. User Guide](#3-user-guide)
  - [3.1 Quick Start](#31-quick-start)
  - [3.2 Expected Startup](#32-expected-startup)
  - [3.3 System Operations](#33-system-operations)
  - [3.4 Generate Data](#34-generate-data)
  - [3.5 Structured Queries](#35-structured-queries)
  - [3.6 AI/ML Queries](#36-aiml-queries)
  - [3.7 Combined Queries](#37-combined-queries)
  - [3.8 Website and APIs](#38-website-and-apis)
  - [3.9 Running Tests](#39-running-tests)

**4. Development Process**
- [4. Development Process](#4-development-process)
  - [4.1 Project Principles](#41-project-principles)
  - [4.2 Development Lifecycle](#42-development-lifecycle)
  - [4.3 Definition of Done](#43-definition-of-done)
  - [4.4 Testing Strategy](#44-testing-strategy)
  - [4.5 Project Status](#45-project-status)
  - [4.6 Project Roadmap](#46-project-roadmap)
  - [4.7 Repository Responsibilities](#47-repository-responsibilities)

**5. Additional Documents**
- [5. Additional Documents](#5-additional-documents)
  - [5.1 Documentation Strategy](#51-documentation-strategy)
  - [5.2 Documentation Evolution](#52-documentation-evolution)
  - [5.3 Planned Documents](#53-planned-documents)

## Diagram Index

| Diagram | Title | Section |
|---|---|---|
| 2.1 | Data Flow | [2.1 Data Flow](#21-data-flow) |
| 2.2 | Analysis Flow | [2.2 Analysis Flow](#22-analysis-flow) |
| 2.3 | Complete System | [2.3 Complete System](#23-complete-system) |
| 2.4 | Security Extension | [2.9 Security Boundary](#29-security-boundary) |
| 2.5 | Docker Architecture | [2.12 Docker Architecture](#212-docker-architecture) |
| 2.6 | Docker Communication by Trigger | [2.13 Docker Communication Trigger](#213-docker-communication-by-trigger) |
| 2.7 | Docker Communication by protocol | [2.14 Docker Communication Protocol](#214-docker-communication-by-protocol) |
| 3.1 | Test Flow | [3.9 Running Tests](#39-running-tests) |
| 4.1 | Development Lifecycle | [4.2 Development Lifecycle](#42-development-lifecycle) |
| 4.2 | Tenant Test Flow | [4.4 Testing Strategy](#44-testing-strategy) |
| 5.1 | Documentation Evolution | [5.2 Documentation Evolution](#52-documentation-evolution) |

## Table Index

| Table | Title | Section |
|---|---|---|
| 2.1 | Application Services | [2.4 Application Services](#24-application-services) |
| 2.2 | Infrastructure Services | [2.5 Infrastructure Services](#25-infrastructure-services) |
| 2.3 | Technology Stack | [2.7 Technology Stack](#27-technology-stack) |
| 2.4 | Running Services | [2.8 Running Services](#28-running-services) |
| 2.5 | Docker Architecture | [2.12 Docker Architecture](#212-docker-architecture) |
| 2.6 | Docker Communication by trigger | [2.13 Docker Communication by trigger](#213-docker-communication-by-trigger) |
| 2.7 | Docker Communication by protocol | [2.14 Docker Communication by protocol](#214-docker-communication-by-protocol) |
| 4.1 | Project Status | [4.5 Project Status](#45-project-status) |
| 4.2 | Project Roadmap | [4.6 Project Roadmap](#46-project-roadmap) |
| 4.3 | Repository Responsibilities | [4.7 Repository Responsibilities](#47-repository-responsibilities) |