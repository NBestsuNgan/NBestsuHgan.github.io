<div align="center">

# ✦ NBestsuNgan — Side Projects

**Data Engineering · Software Development · DevOps**

<p>
  <a href="https://github.com/NBestsuNgan"><img src="https://img.shields.io/badge/Projects-4-6366f1?style=flat-square" alt="Projects"></a>
  <a href="https://github.com/NBestsuNgan"><img src="https://img.shields.io/badge/GitHub-NBestsuNgan-181717?style=flat-square&logo=github" alt="GitHub"></a>
</p>

</div>

---

## 📊 Low-Code Data Distributed Processing Framework

<div align="center">

<p>
  <a href="https://airflow.apache.org/"><img src="https://img.shields.io/badge/Apache_Airflow-017CEE?style=flat-square&logo=apacheairflow&logoColor=white" alt="Airflow"></a>
  <a href="https://spark.apache.org/"><img src="https://img.shields.io/badge/Apache_Spark-E25A1C?style=flat-square&logo=apachespark&logoColor=white" alt="Spark"></a>
  <a href="https://iceberg.apache.org/"><img src="https://img.shields.io/badge/Apache_Iceberg-2972D1?style=flat-square" alt="Iceberg"></a>
  <a href="https://www.docker.com/"><img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker"></a>
  <a href="https://www.oracle.com/"><img src="https://img.shields.io/badge/Oracle-F80000?style=flat-square&logo=oracle&logoColor=white" alt="Oracle"></a>
</p>

</div>

> A configuration-driven framework that eliminates boilerplate in data pipeline development. Define workflows as data — the system generates and orchestrates them automatically.

### ❖ Technical Highlights

- **Dynamic DAG Generation** — Apache Airflow DAGs are generated at runtime from database configurations, removing the need to write new Python code for each workflow
- **Control Table Architecture** — 6 relational tables (streams, process groups, processes, dependencies, schedules, logging) serve as the single source of truth for all pipeline metadata
- **Data Lakehouse Pattern** — Apache Spark processes data on top of Apache Iceberg open table format, stored on MinIO (S3-compatible), enabling ACID transactions and schema evolution on object storage
- **Multi-tier Data Flow** — Raw staging → Dimension/Fact tables → Aggregations, with Oracle PDB as the downstream data warehouse
- **Containerized Stack** — 5 services (Airflow, Spark, Iceberg, MinIO, PostgreSQL) orchestrated via Docker Compose

### ❖ Architecture

```
┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐
│  Control Tables  │──────▶│    Airflow       │──────▶│  Spark + Iceberg │
│  (PostgreSQL)    │       │    (Orchestrator)│       │  (Processing)    │
└──────────────────┘       └──────────────────┘       └────────┬─────────┘
                                                               │
                          ┌──────────────────┐                 │
                          │  Data Lakehouse  │◀────────────────┘
                          │  (MinIO / S3)    │
                          └────────┬─────────┘
                                   │
                          ┌────────┴─────────┐
                          │  Data Warehouse  │
                          │  (Oracle PDB)    │
                          └──────────────────┘
```

[View Repository →](https://github.com/NBestsuNgan/Low-code-Data-Distributed-Processing-Framework-On-Top-Apache-Airflow)

---

## 🤖 cc-mimic — AI Coding Agent from Scratch

<div align="center">

<p>
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3.12+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"></a>
  <a href="https://github.com/Textualize/rich"><img src="https://img.shields.io/badge/Rich_Terminal-000000?style=flat-square&logo=python&logoColor=white" alt="Rich"></a>
  <a href="https://docs.python.org/3/library/asyncio.html"><img src="https://img.shields.io/badge/Async-await-3776AB?style=flat-square" alt="Async"></a>
  <a href="https://click.palletsprojects.com/"><img src="https://img.shields.io/badge/Click_CLI-4EAA25?style=flat-square" alt="Click"></a>
</p>

</div>

> A terminal-based AI coding agent built from scratch — featuring tool execution, streaming responses, and session management. No agent frameworks, just clean async Python.

### ❖ Technical Highlights

- **Agent Loop Architecture** — Implements the core reasoning-action-observation cycle: the agent receives a prompt, decides which tools to call, executes them, and feeds results back into context iteratively
- **Tool Registry with Approval Policies** — Extensible tool system with 4 safety levels (auto-ask, allowlist, deny, full-auto) controlling which tools can execute without user confirmation
- **Streaming LLM Responses** — Real-time token streaming via Rich terminal UI, providing responsive feedback during long-running operations
- **Session Persistence** — Conversations are checkpointed and resumable, with full message history preserved across sessions
- **MCP Server Integration** — Supports Model Context Protocol for connecting external tool servers, following the open standard for agent-tool communication
- **Async/Await Throughout** — Built on Python asyncio for non-blocking I/O when calling LLM APIs and executing tools concurrently

[View Repository →](https://github.com/NBestsuNgan/cc-mimic)

---

## 💬 Line Bot — Conversational Agent on GCP

<div align="center">

<p>
  <a href="https://cloud.google.com/"><img src="https://img.shields.io/badge/Google_Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white" alt="GCP"></a>
  <a href="https://cloud.google.com/vertex-ai"><img src="https://img.shields.io/badge/Vertex_AI-4285F4?style=flat-square&logo=googlecloud&logoColor=white" alt="Vertex AI"></a>
  <a href="https://www.terraform.io/"><img src="https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white" alt="Terraform"></a>
  <a href="https://github.com/features/actions"><img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" alt="GitHub Actions"></a>
</p>

</div>

> A LINE chatbot powered by enterprise search on Google Cloud. Built with Google ADK and deployed as a managed service on Vertex AI Agent Engine.

### ❖ Technical Highlights

- **Google Agent Development Kit (ADK)** — Built using Google's official framework for developing conversational agents with structured tool calling and state management
- **Vertex AI Search Integration** — Connects to enterprise knowledge base for retrieval-augmented responses, grounding answers in real documents
- **Infrastructure as Code** — All GCP resources (Agent Engine, GCS buckets, IAM) provisioned via Terraform for reproducible deployments
- **CI/CD Pipeline** — GitHub Actions workflow automates build, test, and deployment to Vertex AI on every push
- **Observability** — OpenTelemetry tracing integrated for end-to-end request visibility, with Cloud Logging for structured log aggregation
- **Managed Deployment** — Runs on Vertex AI Agent Engine (fully managed), handling scaling, health monitoring, and versioning

[View Repository →](https://github.com/NBestsuNgan/line-bot)

---

## 🛠️ Technical Toolkit

<div align="center">

<p><strong>Data Engineering</strong> · Apache Airflow · Apache Spark · Apache Iceberg · MinIO · Oracle · PostgreSQL</p>

<p><strong>Software</strong> · Python (async/await) · Click CLI · Rich Terminal UI · REST APIs</p>

<p><strong>DevOps &amp; Cloud</strong> · Docker · GCP (Vertex AI, GCS) · Terraform · GitHub Actions · OpenTelemetry</p>

</div>

---

<div align="center">

✦ [github.com/NBestsuNgan](https://github.com/NBestsuNgan) ✦

</div>
