# NBestsuNgan - Side Projects Portfolio

A collection of side projects showcasing skills in data engineering, AI/ML, and software development.

---

## 📊 Low-code Data Distributed Processing Framework On Top Apache Airflow

**Repository:** [NBestsuNgan/Low-code-Data-Distributed-Processing-Framework-On-Top-Apache-Airflow](https://github.com/NBestsuNgan/Low-code-Data-Distributed-Processing-Framework-On-Top-Apache-Airflow)

### Overview
A low-code data processing framework built on Apache Airflow that enables scalable workflow orchestration using a control table concept. This framework allows users to replicate tasks with different parameters easily without rewriting code for each new workflow.

### Key Features
- **Control Table Architecture:** 6 control tables for managing streams, process groups, processes, dependencies, schedules, and logging
- **Dynamic DAG Generation:** Apache Airflow dynamically generates tasks based on control table configurations
- **Data Tier Management:** Implements tiered data processing (staging → dimension/fact tables → aggregations)
- **Multi-Service Architecture:** Integrated with Spark-Iceberg, MinIO, Oracle, and PostgreSQL

### Tech Stack
- **Orchestration:** Apache Airflow
- **Processing:** Apache Spark with Iceberg (Open Table Format)
- **Storage:** MinIO (S3-compatible object storage), Oracle PDB (Data Warehouse)
- **Database:** PostgreSQL (Airflow metadata)
- **Containerization:** Docker & Docker Compose

### Architecture Highlights
```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Control Table │────▶│   Orchestrator  │────▶│  Processing     │
│   (PostgreSQL)  │     │   (Airflow)     │     │  (Spark-Iceberg)│
└─────────────────┘     └─────────────────┘     └─────────────────┘
                                                        │
                        ┌─────────────────┐            │
                        │   Data Lakehouse│◀───────────┘
                        │   (MinIO)       │
                        └─────────────────┘
                                │
                        ┌─────────────────┐
                        │   Data Warehouse│
                        │   (Oracle PDB)  │
                        └─────────────────┘
```

---

## 🤖 cc-mimic - Lightweight Claude Code Mimic

**Repository:** [NBestsuNgan/cc-mimic](https://github.com/NBestsuNgan/cc-mimic)

### Overview
A lightweight AI coding agent that mimics Claude Code functionality. Built from scratch to understand and replicate the core patterns of AI-powered coding assistants.

### Key Features
- **Interactive TUI:** Rich terminal user interface with streaming responses
- **Tool System:** Extensible tool registry with approval policies
- **Session Management:** Save, resume, and checkpoint conversations
- **MCP Support:** Model Context Protocol server integration
- **Configuration:** Environment-based configuration with validation

### Tech Stack
- **Language:** Python 3.12+
- **UI:** Rich (terminal UI library)
- **LLM Integration:** OpenRouter API
- **Architecture:** Async/await with Click CLI

### Project Structure
```
cc-mimic/
├── main.py              # CLI entry point
└── src/
    ├── agent/           # Agent logic and events
    ├── client/          # LLM client
    ├── config/          # Configuration management
    ├── context/         # Conversation context
    ├── hooks/           # Lifecycle hooks
    ├── prompts/         # System prompts
    ├── safety/          # Safety checks
    ├── scripts/         # Utility scripts
    ├── tools/           # Tool implementations
    ├── ui/              # Terminal UI
    └── utils/           # Utilities
```

---

## 💬 Line Bot - Google ADK Agent on Vertex AI

**Repository:** [NBestsuNgan/line-bot](https://github.com/NBestsuNgan/line-bot)

### Overview
A LINE chatbot powered by Google Agent Development Kit (ADK) and deployed on Vertex AI Agent Engine. Features enterprise search capabilities using Vertex AI Search.

### Key Features
- **Google ADK Integration:** Built with Google's Agent Development Kit
- **Vertex AI Search:** Enterprise search engine integration for knowledge retrieval
- **Cloud Deployment:** Automated deployment to Vertex AI Agent Engine
- **CI/CD Pipeline:** GitHub Actions for continuous deployment
- **Infrastructure as Code:** Terraform for GCP resource management
- **Observability:** OpenTelemetry tracing and Cloud Logging

### Tech Stack
- **Language:** Python 3.12+
- **AI/ML:** Google ADK, Gemini 2.5 Flash, Vertex AI
- **Cloud:** Google Cloud Platform (Vertex AI, GCS, Cloud Run)
- **Infrastructure:** Terraform, Docker
- **CI/CD:** GitHub Actions
- **Dependency Management:** uv

### Architecture
```
┌─────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   LINE App  │────▶│   Vertex AI     │────▶│   Vertex AI     │
│             │     │   Agent Engine  │     │   Search        │
└─────────────┘     └─────────────────┘     └─────────────────┘
                            │
                    ┌───────┴───────┐
                    │   GCS Buckets │
                    │   (Artifacts) │
                    └───────────────┘
```

---

## 🌐 Portfolio Website

**Repository:** [NBestsuNgan/NBestsuHgan.github.io](https://github.com/NBestsuNgan/NBestsuHgan.github.io)

### Overview
Personal portfolio website hosted on GitHub Pages showcasing projects and skills.

---

## 🛠️ Skills Demonstrated

### Data Engineering
- Apache Airflow workflow orchestration
- Apache Spark distributed processing
- Data lakehouse architecture (Iceberg, MinIO)
- Data warehouse design (Oracle, PostgreSQL)
- ETL/ELT pipeline development

### AI
- Google Agent Development Kit (ADK)
- Vertex AI and Gemini models
- LLM integration and prompt engineering
- AI agent architecture

### Software Development
- Python async/await patterns
- CLI application development
- Terminal UI with Rich
- API design and integration

### DevOps & Cloud
- Docker containerization
- Google Cloud Platform (Vertex AI, GCS, Cloud Run)
- Infrastructure as Code (Terraform)
- CI/CD with GitHub Actions
- Monitoring and observability (OpenTelemetry)

---

*Last updated: June 2026*
