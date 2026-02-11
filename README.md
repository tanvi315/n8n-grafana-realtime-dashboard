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




✅ Setup Steps (Start → End)
1️⃣ Create PostgreSQL Database (Neon)

Create a Neon project

Copy database credentials

Run table creation query:

CREATE TABLE automation_logs (
  id SERIAL PRIMARY KEY,
  workflow_name TEXT NOT NULL,
  status TEXT NOT NULL,
  amount NUMERIC NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

2️⃣ Insert Data Using n8n

Add PostgreSQL node in n8n

Connect using Neon credentials

Use INSERT query:

INSERT INTO automation_logs (workflow_name, status, amount)
VALUES
('Invoice Process', 'Success', 3900),
('Payment Run', 'Failed', 2300),
('Bank Upload', 'Success', 4100);


Execute workflow

Verify records are added

3️⃣ Connect PostgreSQL to Grafana

Go to Connections → Add Data Source

Select PostgreSQL

Enter:

Host

Database name

Username

Password

SSL Mode: require

Click Save & Test

4️⃣ Create Grafana Dashboard

Go to Dashboards → New Dashboard

Click Add Panel

Select PostgreSQL data source

Add SQL query:

SELECT * FROM public.automation_logs
ORDER BY id DESC;


Choose visualization:

Table

Bar Chart

Stat

Click Save Dashboard

5️⃣ Enable Auto Refresh

Open Dashboard

Top right → Refresh dropdown

Select:

5s / 10s / 30s

Set Time Range:

Last 5 minutes

Now whenever n8n inserts new records →
📊 Grafana updates automatically.

🔄 Final Data Flow
n8n → PostgreSQL (Neon) → Grafana Dashboard (Live Auto Refresh)
