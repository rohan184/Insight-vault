
# 🚀 InsightVault – Scalable Event Analytics Platform

InsightVault is a self-hosted event tracking and analytics platform, designed to help developers and product teams collect, store, and analyze custom events from their applications. Think of it as your own lightweight, private alternative to Mixpanel or PostHog.

---

## 🧩 Features

- ✅ Event ingestion via HTTP API
- ✅ Real-time or batch event processing pipeline
- ✅ Efficient storage using ClickHouse / Parquet
- ✅ Query API for reporting and insights
- ✅ Optional web dashboard for visualizing metrics
- ✅ Containerized services with full CI/CD
- ✅ Infrastructure-as-code (Terraform) support
- ✅ Prometheus + Grafana observability

---

## 🏗️ Architecture Overview

```txt
            ┌────────────┐
   Clients  │ Web / App  │
            └────┬───────┘
                 │
         ┌───────▼────────┐
         │ Event Ingestor │  ← REST API (Go/FastAPI)
         └───────┬────────┘
                 │
          Message Queue       (Kafka / Redis Streams)
                 │
         ┌───────▼────────┐
         │  ETL Processor │  ← Spark / Airflow / Prefect
         └───────┬────────┘
                 │
        ┌────────▼─────────┐
        │   Storage Layer  │ ← ClickHouse / S3 + Parquet
        └────────┬─────────┘
                 │
      ┌──────────▼──────────┐
      │ Reporting API Layer │ ← REST / GraphQL
      └──────────┬──────────┘
                 │
          ┌──────▼───────┐
          │  Dashboard   │ ← React / Svelte (optional)
          └──────────────┘
```

---

## 🧱 Tech Stack

| Layer         | Tech Options                                    |
|---------------|--------------------------------------------------|
| Backend       | Go / FastAPI / Node.js                          |
| Queue         | Kafka / RabbitMQ / Redis Streams                |
| ETL           | Spark / Airflow / Prefect / Dagster             |
| Storage       | ClickHouse / PostgreSQL / S3 + Parquet          |
| Dashboard     | React + Tailwind / Svelte                       |
| Infra & DevOps| Docker, Kubernetes, GitHub Actions, Terraform   |
| Observability | Prometheus, Grafana, Loki                       |

---

## 🚧 Getting Started

### Prerequisites

- Docker & Docker Compose
- Python/Go (for API)
- Kafka/Redis running locally or via Docker

### Setup

```bash
git clone https://github.com/rohan184/Insight-vault.git
cd insightvault
cp .env.example .env
docker-compose up --build
```

---

## ⚙️ Core Modules

### 1. **Event Ingestor**
- Accepts JSON POST requests:
```json
{
  "event": "user_signup",
  "user_id": "abc123",
  "timestamp": "2025-07-18T10:00:00Z",
  "properties": {
    "referrer": "twitter",
    "plan": "pro"
  }
}
```

### 2. **ETL Pipeline**
- Consumes from Kafka.
- Transforms & partitions events.
- Stores to ClickHouse or Parquet.

### 3. **Query API**
- REST or GraphQL endpoints for:
  - Daily Active Users
  - Funnel reports
  - Retention analysis
  - Custom aggregations

### 4. **Optional Dashboard**
- Secure login for orgs.
- Visualize events and reports.

---

## 🛡️ Authentication & Security

- JWT-based user auth (optional).
- Org-based multitenancy.
- API tokens for ingestion.

---

## 🧪 Testing

```bash
pytest tests/
# or
go test ./...
```

---

## 📊 Observability

- **Prometheus**: Metrics
- **Grafana**: Dashboards
- **Loki / Fluentd**: Centralized logging

---

## 📦 Deployment

- Pre-built Docker containers
- GitHub Actions for CI/CD
- Terraform scripts for provisioning:
  - S3 buckets
  - RDS / ClickHouse
  - Kubernetes namespace

---

## 🧠 Future Enhancements

- [ ] SDKs for web/mobile (JavaScript, Android)
- [ ] Webhooks & alerting on events
- [ ] RBAC for admin roles
- [ ] Anomaly detection using ML models

---

## 🤝 Contributing

Contributions are welcome! Open issues, suggest features, or submit PRs.

---

## 📄 License

MIT License

---

## 🧑‍💻 Maintained By

**Rohan Das**  
Backend Engineer | Data Pipeline Enthusiast | DevOps Curious  
[LinkedIn](#) | [Twitter](#) | [Portfolio](#)
