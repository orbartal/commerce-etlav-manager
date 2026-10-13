[← Back to Main README](../README.md)

# 5. Additional Documents

## Table of Contents

- [5. Additional Documents](#5-additional-documents)
  - [5.1 Documentation Strategy](#51-documentation-strategy)
  - [5.2 Documentation Evolution](#52-documentation-evolution)
  - [5.3 Planned Documents](#53-planned-documents)


## 5.1 Documentation Strategy

CommerceETLAV initially used a single `README.md` as its primary project document.
As the project grows, detailed material is moved into dedicated Markdown documents in the `docs/` folder. The README remains the primary project entry point.
When detailed information is moved into another document, the README should retain the core ideas and provide a link to the detailed document.

## 5.2 Documentation Evolution

**Diagram 5.1 — Documentation Evolution**

```text
Initial Stage

README.md
    └── Complete project plan and documentation


Growing Project

README.md
docs/
├── goals.md
├── architecture.md
├── user-guide.md
├── development-process.md
├── additional-documents.md
└── images/
    └── commerce_etlav_microservices_architecture_150kb.jpg


Mature Project

README.md
    └── Permanent project entry point

docs/
    ├── user-guide/
    └── developer-guide/
```

## 5.3 Planned Documents

The project may eventually contain many files in each subject folder:

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

Additional detailed documents will be created as the project grows and the documentation becomes large enough to justify further separation.
