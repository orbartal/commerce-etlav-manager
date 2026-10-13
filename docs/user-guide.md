[← Back to Main README](../README.md)

# 3. User Guide

## Table of Contents

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

The structured analytical system identifies the affected products. \
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
