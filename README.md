# 🚀 Real-Time Automation Dashboard  
### n8n → PostgreSQL (Neon) → Grafana (Live Auto Refresh)

---

## 📌 Project Overview

This project demonstrates how to build a real-time automation monitoring system where:

✅ n8n inserts workflow execution data  
✅ PostgreSQL (Neon Cloud) stores the data  
✅ Grafana automatically refreshes and displays live updates  

The dashboard updates automatically whenever new data is inserted from n8n.

---

## 🏗️ System Architecture

        n8n (Workflow Automation)
                    ↓
        PostgreSQL (Neon Cloud DB)
                    ↓
        Grafana Dashboard (Auto Refresh Enabled)

### 🔄 How It Works

1. n8n executes a workflow
2. n8n inserts data into PostgreSQL using SQL query
3. PostgreSQL stores the log entry
4. Grafana queries the database every few seconds
5. Dashboard updates automatically (Live View)

This creates a **real-time monitoring system**.

---

## 🗄️ Database Schema

Table: `automation_logs`

```sql
CREATE TABLE automation_logs (
  id SERIAL PRIMARY KEY,
  workflow_name TEXT NOT NULL,
  status TEXT NOT NULL,
  amount NUMERIC NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);
