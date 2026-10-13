[← Back to Main README](../README.md)

# 1. Project Goals

## Table of content

**Note:** `goals.md` is the first part of a multi-file README for this project.

- [1. Project Goals](#1-project-goals)
  - [1.1 Project Description](#11-project-description)
  - [1.2 Project Demonstrates](#12-project-demonstrates)
  - [1.3 Project Scope](#13-project-scope)
  - [1.4 Security Scope](#14-security-scope)
  - [1.5 Structured Analytics](#15-structured-analytics)
  - [1.6 AI/ML Analysis](#16-aiml-analysis)
  - [1.7 Combined Analysis](#17-combined-analysis)

---

## 1.1 Project Description

CommerceETLAV demonstrates a complete commerce data flow:

**Extract → Transform → Load → Analyze → Visualize**

The system generates understandable commerce data and processes it through a modern Big Data architecture.

The same data can be analyzed using both traditional structured-data technologies and AI/ML technologies.

The project is intentionally small enough to run locally and understand, while demonstrating architecture and technologies that are relevant to much larger data systems.

## 1.2 Project Demonstrates

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