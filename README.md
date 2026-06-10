<div align="center">

# ✦ NBestsuNgan — Side Projects

**Data Engineering · Software Development · DevOps**

[![Projects](https://img.shields.io/badge/Projects-4-6366f1?style=flat-square)](https://github.com/NBestsuNgan)
[![GitHub](https://img.shields.io/badge/GitHub-NBestsuNgan-181717?style=flat-square&logo=github)](https://github.com/NBestsuNgan)

</div>

---

## 📊 Low-Code Data Distributed Processing Framework

<div align="center">

[![Airflow](https://img.shields.io/badge/Apache_Airflow-017CEE?style=flat-square&logo=apacheairflow&logoColor=white)](https://airflow.apache.org/)
[![Spark](https://img.shields.io/badge/Apache_Spark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)](https://spark.apache.org/)
[![Iceberg](https://img.shields.io/badge/Apache_Iceberg-2972D1?style=flat-square)](https://iceberg.apache.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)](https://www.docker.com/)
[![Oracle](https://img.shields.io/badge/Oracle-F80000?style=flat-square&logo=oracle&logoColor=white)](https://www.oracle.com/)

</div>

> A low-code framework that enables **scalable workflow orchestration** without rewriting code for each new process. Define your workflow in configuration — the framework handles the rest.

### ❖ What It Does

Traditional data pipelines require copy-pasting boilerplate code for every new workflow. This project flips that pattern: register your **streams → process groups → processes → dependencies** in control tables, and Airflow dynamically generates the DAGs.

### ❖ Architecture

```
┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐
│                  │       │                  │       │                  │
│  Control Tables  │──────▶│    Airflow       │──────▶│  Spark + Iceberg │
│  (PostgreSQL)    │       │    (Orchestrator)│       │  (Processing)    │
│                  │       │                  │       │                  │
└──────────────────┘       └──────────────────┘       └────────┬─────────┘
                                                               │
                          ┌──────────────────┐                 │
                          │                  │◀────────────────┘
                          │  Data Lakehouse  │
                          │  (MinIO / S3)    │
                          │                  │
                          └────────┬─────────┘
                                   │
                          ┌────────┴─────────┐
                          │                  │
                          │  Data Warehouse  │
                          │  (Oracle PDB)    │
                          │                  │
                          └──────────────────┘
```

### ❖ Key Details

| Component | Purpose |
|-----------|---------|
| **6 Control Tables** | Streams, process groups, processes, dependencies, schedules, logging |
| **Dynamic DAGs** | Generated at runtime from control table configs |
| **Data Tiers** | Raw staging → Dimension/Fact tables → Aggregations |
| **Multi-service** | 5 Docker containers orchestrated via `docker-compose` |

[View Repository →](https://github.com/NBestsuNgan/Low-code-Data-Distributed-Processing-Framework-On-Top-Apache-Airflow)

---

## 🤖 cc-mimic — Build Your Own AI Coding Agent

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.12+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Rich](https://img.shields.io/badge/Rich_Terminal-000000?style=flat-square&logo=python&logoColor=white)](https://github.com/Textualize/rich)
[![Async](https://img.shields.io/badge/Async-await-3776AB?style=flat-square)](https://docs.python.org/3/library/asyncio.html)
[![Click](https://img.shields.io/badge/Click_CLI-4EAA25?style=flat-square)](https://click.palletsprojects.com/)

</div>

> A **lightweight Claude Code mimic** — built from scratch to understand how AI coding assistants work under the hood. Forge your own agent.

### ❖ Why I Built It

Understanding how coding agents reason, call tools, and manage context is essential for building better developer tools. This project is a deep dive into agent architecture — no frameworks, just clean Python.

### ❖ Features at a Glance

```
⌁ Streaming responses        ──▶  Real-time token streaming with Rich
⌁ Tool approval policies     ──▶  auto-ask / allowlist / deny / full-auto
⌁ Session persistence        ──▶  Save, resume, and checkpoint conversations
⌁ MCP server support         ──▶  Model Context Protocol integration
⌁ Interactive TUI            ──▶  Commands: /config /approval /stats /tools
```

### ❖ Code Architecture

```
cc-mimic/
├── main.py              ──▶ CLI entry (Click)
└── src/
    ├── agent/           ──▶  Agent loop · events · session
    ├── client/          ──▶  LLM client abstraction
    ├── tools/           ──▶  Tool registry · execution
    ├── context/         ──▶  Message history · context management
    ├── config/          ──▶  Env-based config · validation
    ├── safety/          ──▶  Approval gates
    └── ui/              ──▶  Terminal UI (Rich)
```

[View Repository →](https://github.com/NBestsuNgan/cc-mimic)

---

## 💬 Line Bot — Conversational Agent on GCP

<div align="center">

[![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white)](https://cloud.google.com/)
[![Vertex AI](https://img.shields.io/badge/Vertex_AI-4285F4?style=flat-square&logo=googlecloud&logoColor=white)](https://cloud.google.com/vertex-ai)
[![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)](https://www.terraform.io/)
[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)](https://github.com/features/actions)

</div>

> A **LINE chatbot** backed by enterprise search and deployed on Google Cloud. Conversational, observable, and production-ready.

### ❖ How It Works

```
LINE App
    │
    ▼
┌──────────────────┐
│  Vertex AI       │
│  Agent Engine    │──── Gemini 2.5 Flash
│                  │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│  Vertex AI       │
│  Search          │──── Enterprise knowledge base
│                  │
└──────────────────┘
```

### ❖ Production Setup

- **Infrastructure as Code** — Terraform provisions all GCP resources
- **CI/CD Pipeline** — GitHub Actions for automated cloud deployment
- **Observability** — OpenTelemetry tracing + Cloud Logging
- **Artifact Storage** — GCS buckets for session data and logs

### ❖ Deploy in One Command

```bash
uv run app/agent_engine_app.py \
  --project my-gcp-project \
  --agent-name linebot-agent \
  --requirements-file .requirements.txt
```

[View Repository →](https://github.com/NBestsuNgan/line-bot)

---

## 🛠️ Technical Toolkit

<div align="center">

### Data Engineering
Apache Airflow · Apache Spark · Apache Iceberg · MinIO · Oracle · PostgreSQL

### Software
Python (async/await) · Click CLI · Rich Terminal UI · REST APIs

### DevOps & Cloud
Docker · GCP (Vertex AI, GCS) · Terraform · GitHub Actions · OpenTelemetry

</div>

---

<div align="center">

✦ [github.com/NBestsuNgan](https://github.com/NBestsuNgan) ✦

</div>
