# 🚀 Real-Time Dashboard with n8n + PostgreSQL (Neon) + Grafana

## 📌 Project Overview

This project demonstrates how to build a real-time dashboard using:

- 🔄 n8n (Workflow Automation)
- 🐘 PostgreSQL (Neon Cloud)
- 📊 Grafana (Data Visualization)

The system logs workflow data into PostgreSQL and visualizes it live in Grafana with auto-refresh.

---

## 🏗️ Architecture

n8n → PostgreSQL (Neon) → Grafana Dashboard

1. n8n inserts workflow execution data
2. PostgreSQL stores structured records
3. Grafana queries database and displays real-time charts

---

## 🗄️ Database Schema

Table: `automation_logs`

| Column         | Type      |
|---------------|----------|
| id            | Serial (PK) |
| workflow_name | Text     |
| status        | Text     |
| amount        | Numeric  |
| created_at    | Timestamp |

Example Create Table:

```sql
CREATE TABLE automation_logs (
  id SERIAL PRIMARY KEY,
  workflow_name TEXT,
  status TEXT,
  amount NUMERIC,
  created_at TIMESTAMP DEFAULT NOW()
);
