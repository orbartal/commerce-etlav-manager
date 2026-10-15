[← Back to Main README](../README.md)

# 6. Business Model

CommerceETLAV is a proof-of-concept (POC) project designed to demonstrate Big Data, AI/ML, distributed systems, and software architecture skills.

The project simulates an analytics service used by a fictional retail company.

The retail business provides the domain, entities, and events needed to demonstrate the technical capabilities of CommerceETLAV.

## Table of Contents

- [6. Business Model](#6-business-model)
  - [6.1 Purpose](#61-purpose)
  - [6.2 Business Model](#62-business-model)
  - [6.3 Actors](#63-actors)
  - [6.4 MVP Scope](#64-mvp-scope)
  - [6.5 Retail Client Lifecycle](#65-retail-client-lifecycle)
  - [6.6 Session Lifecycle](#66-session-lifecycle)
  - [6.7 Order Lifecycle](#67-order-lifecycle)
  - [6.8 Business Rules](#68-business-rules)
  - [6.9 Data Generation](#69-data-generation)
  - [6.10 Related Documents](#610-related-documents)

---

## 6.1 Purpose

CommerceETLAV simulates an analytics service for a fictional retail company.

### Design Principle

**Big Data / AI First:** The project goal is to demonstrate Big Data, AI/ML, distributed systems, and software architecture. The business exists only to support it and give context. So, keep minimal commerce business logic. Add business complexity only when needed to demonstrate Big Data, AI/ML, or architecture skills.

### Project Constraints

- Developed by one software engineer.
- Initial implementation target: approximately two weeks.
- Runs locally using Docker Compose.
- Uses synthetic, deterministic commerce data.
- Prioritizes technical demonstrations over realistic commerce operations.
- Business complexity must remain minimal.

## 6.2 Business Model

### Fictional Retailer

| Property | Description |
|---|---|
| Company Name | Prosperity Bazaar Empire |
| Abbreviation | PBE |
| Business Domain | Retail commerce |
| Business Model | Business-to-Consumer (B2C) |
| MVP Sales Channel | Online store |
| Advanced Sales Channels | Online and physical stores |
| CommerceETLAV Relationship | PBE is a customer of the CommerceETLAV analytics service |
| Data | Synthetic commerce events |

Prosperity Bazaar Empire (PBE) is a fictional retail company created for the CommerceETLAV demonstration.

PBE sells products to registered Retail Clients.

CommerceETLAV receives and processes events describing PBE's business activities.

CommerceETLAV does not implement PBE's real commerce operations.

### CommerceETLAV Service

CommerceETLAV provides:

- Event ingestion and streaming.
- Raw and processed data storage.
- Data transformation and analytics.
- SQL queries and business metrics.
- AI/ML analysis of client event comments.
- Data visualization and monitoring.

The retailer generates business events.

CommerceETLAV processes those events and exposes analytical results.

## 6.3 Actors

The system distinguishes between two types of human actors.

| Actor | Description | Identifier |
|---|---|---|
| Retail Client | A customer purchasing products from PBE | `retailClientId` |
| CommerceETLAV User | A person using the analytics service | `etlavUserId` |

### Retail Clients

Retail Clients interact with PBE.

For the MVP, each Retail Client:

- Has a predefined identity loaded from a Generator configuration file. The Generator selects existing client identifiers and does not create new client identities at runtime.
- Has one delivery destination. Advanced versions may support multiple saved destinations.
- Has at most one active session. Advanced versions may support multiple concurrent sessions.
- Creates one order per session.
- Can add multiple items to an order.
- Completes a simple purchase and delivery lifecycle without errors, failures, cancellations, or returns.

The MVP assumes all business operations succeed.

Advanced versions may support more complex business workflows, failures, cancellations, returns, and recovery.

### CommerceETLAV Users

CommerceETLAV Users explore and analyze business data through:

- Dashboards and visualizations.
- Business reports and metrics.
- AI-generated insights.
- Data-processing and monitoring information.

Examples include:

- Business analysts.
- Marketing managers.
- Operations managers.
- Executives.
- Data engineers.

Direct analytical queries may be supported as an additional capability but are not required for the MVP user experience.

### Security

Authentication, authorization, roles, and permissions are outside the MVP scope.

Retail Client sessions are simulated.

CommerceETLAV Users are conceptual business actors; the MVP does not require user-account management.

## 6.4 MVP Scope

### Supported Features

| Feature | MVP | Advanced Version |
|---|---|---|
| Retailers | One fictional retailer | Multiple retailer tenants |
| Sales Channels | Online only | Online and physical stores |
| Retail Clients | Preconfigured in Generator | Registration, updates, deletion, and client-management events |
| Active Sessions | One per client | Concurrent sessions across devices |
| Session Management | Simulated start and end | Expiration, scheduled closure, authentication methods |
| Orders | One per session | Multiple orders per session and orders spanning sessions |
| Concurrent Orders | Not supported | Multiple active orders per client |
| Order Items | Multiple items per order | Add, remove, and update quantities |
| Delivery Destinations | One predefined destination per client | Multiple saved destinations and destination changes |
| Shopping Cart | Draft order | Separate cart entity if needed |
| Order Submission | Supported | More complex submission and validation |
| Purchase / Payment | Simulated successful payment | Payment failures, retries, refunds |
| Fulfillment / Delivery | Simulated successful delivery | Shipment tracking and multiple delivery states |
| Client Event Comments | Supported on every event | Richer comments and other unstructured data |
| Returns | Not supported | Return requests and completed returns |
| Cancellations | Not supported | Order cancellation |
| Product Reviews | Not supported | Product ratings and free-text reviews |
| Physical Stores | Not supported | Store locations, POS transactions, and store-specific events |
| Authentication | Simulated | Real authentication methods |
| Authorization | Not implemented | Roles and permissions |
| Business Validation | Minimal; Generator produces valid scenarios | Full business rules and validation |
| Data Quality | Valid, complete, unique events | Invalid events, duplicates, missing data, late arrivals |
| Reliability | No simulated failures | Retries, recovery, ordering checks, and deduplication |
| Business Events | Seven MVP event types | Additional event types and lifecycle transitions |

Advanced features are planning possibilities, not implementation commitments.

They should be introduced only when they provide meaningful Big Data, AI/ML, or architecture value.

### MVP Assumptions

All generated business scenarios are valid.

The MVP assumes:

- No invalid events.
- No missing required values.
- No duplicate events.
- No business-operation failures.
- No payment failures.
- No delivery failures.
- No cancellation or return operations.
- No parallel actions within a client session.
- No concurrent sessions for the same Retail Client.

These assumptions simplify the business model.

They do not imply that real distributed systems guarantee error-free delivery or processing.

Handling failures, retries, duplicates, and invalid data can be introduced in later technical milestones.

## 6.5 Retail Client Lifecycle

### MVP Model

Retail Clients are defined in a preconfigured dataset.

The Generator selects clients from this dataset to produce deterministic business scenarios.

Each Retail Client has:

- A unique `retailClientId`.
- A retailer association identified by `tenantId`.
- One predefined delivery destination.

The Generator does not invent new Retail Client identifiers during event generation.

### Client Discovery

The Ingestor accepts events containing previously unknown `retailClientId` values.

When necessary, it creates an analytics-side reference for the Retail Client.

This does not create an account in PBE's retail system.

For the MVP, all generated client identifiers originate from the Generator's predefined configuration.

### Advanced Version

Advanced versions may support:

- Client registration.
- Client profile updates.
- Client deletion.
- Multiple delivery destinations.
- Explicit client-management events.

These features are outside the MVP scope.

## 6.6 Session Lifecycle

### Definition

A Retail Session represents one simulated login period for a Retail Client.

A session begins with `SESSION_START`.

A session ends with `SESSION_END`.

### MVP Rules

- Every session belongs to exactly one Retail Client.
- A Retail Client has at most one active session.
- A session has a unique `sessionId`.
- Every event belongs to a Retail Client and an active session, including the event that closes it.
- Sessions are sequential, not concurrent, for the same client.
- A closed session cannot be reopened.
- A new login creates a new session.
- The Generator produces complete, valid session histories.

### Session Flow

```text
SESSION_START
      |
      v
  ACTIVE SESSION
      |
      v
  ORDER LIFECYCLE
      |
      v
SESSION_END
```

### Advanced Version

Advanced versions may support:

- Concurrent sessions on different devices.
- Session expiration and scheduled closure.
- Different authentication methods.
- Session-related failures and recovery.

## 6.7 Order Lifecycle

### MVP Model

An order represents one purchase transaction.

For the MVP:

- Each session contains exactly one order.
- Each client has at most one active order.
- Each order belongs to one Retail Client.
- Each order uses the client's predefined delivery destination.
- An order may contain multiple items.
- An order follows one successful, sequential lifecycle.
- Orders cannot be cancelled or returned.

### MVP Event Flow

```text
1. SESSION_START
        |
        v
2. ORDER_CREATED
        |
        v
3. ORDER_ITEM_ADDED
        |
        +---- May repeat for multiple items
        |
        v
4. ORDER_SUBMITTED
        |
        v
5. PURCHASE
        |
        v
6. DELIVERED
        |
        v
7. SESSION_END
```

### Order States

| Event | Resulting Order State |
|---|---|
| `ORDER_CREATED` | DRAFT |
| `ORDER_ITEM_ADDED` | DRAFT |
| `ORDER_SUBMITTED` | AWAITING_PAYMENT |
| `PURCHASE` | PAID |
| `DELIVERED` | DELIVERED |

`SESSION_START` and `SESSION_END` affect the session, not the order state.

### Event Meaning

| Event Type | Business Meaning |
|---|---|
| `SESSION_START` | Retail Client starts a login session |
| `ORDER_CREATED` | Retail Client creates a new draft order |
| `ORDER_ITEM_ADDED` | Retail Client adds an item to the order |
| `ORDER_SUBMITTED` | Retail Client finishes the order and proceeds to payment |
| `PURCHASE` | Payment completes successfully |
| `DELIVERED` | Order arrives at the client's destination |
| `SESSION_END` | Retail Client ends the session |

### Advanced Version

Advanced versions may support:

- Multiple orders per session.
- Orders spanning multiple sessions.
- Multiple saved delivery destinations.
- Order-item removal.
- Destination changes.
- Order cancellation.
- Payment failures.
- Returns and refunds.
- More detailed fulfillment and delivery stages.

These features are outside the MVP scope.

## 6.8 Business Rules

The MVP follows these rules:

| ID | Rule |
|---|---|
| BR-01 | Every event belongs to one retailer tenant. |
| BR-02 | Every event belongs to one Retail Client. |
| BR-03 | Every event belongs to one Retail Session. |
| BR-04 | A Retail Client has at most one active session. |
| BR-05 | Every session contains exactly one order. |
| BR-06 | An order contains one or more items. |
| BR-07 | Each client has one predefined delivery destination. |
| BR-08 | Every order follows the defined successful lifecycle. |
| BR-09 | Events within a business scenario occur sequentially. |
| BR-10 | Every event supports a client event comment. |
| BR-11 | The Generator produces valid, deterministic scenarios. |
| BR-12 | No cancellation, return, or review operations occur in the MVP. |

## 6.9 Data Generation

### Purpose

The Generator simulates events received from PBE.

Its purpose is to provide reproducible datasets for Big Data and AI/ML demonstrations.

For the MVP, the Generator acts as the simplified event gateway.

A mature implementation may receive events from external retail systems and normalize different event formats.

### Synthetic Data

The Generator uses synthetic data for:

- Retail Clients.
- Products.
- Sessions.
- Orders.
- Order items.
- Event timestamps.
- Client event comments.

### Client Event Comments

Every event supports a free-text field named:

`clientEventComment`

The field represents a comment associated with the Retail Client's business action.

For example, a client may provide a comment when adding a product to an order.

The Generator may also create synthetic comments for other event types.

These comments provide unstructured data for AI/ML analysis.

### Event Volume

| Scenario | Average Event Rate | Purpose |
|---|---:|---|
| Local Demo | 1 event/second | Functional demonstration |
| Current Business Model | 10 events/second | Simulated normal workload |
| Future Growth | 100 events/second | Scalability planning |
| Peak Workload | 1,000 events/second | Short-duration load target |
| Stress Test | 10,000 events/second | Optional technical experiment |

These values are workload assumptions and targets, not measured performance guarantees.

### Determinism

The Generator should support reproducible event generation.

The same generation configuration and seed should produce the same logical events.

This enables repeatable integration and end-to-end testing.

## 6.10 Related Documents

| Document | Purpose |
|---|---|
| [README.md](../README.md) | Project overview and architecture |
| [docs/business.md](business.md) | Business model, actors, lifecycles, and rules |
| [docs/events.md](events.md) | Event schema, event types, identifiers, timestamps, and validation |

`docs/events.md` defines the technical representation of the business events described here.