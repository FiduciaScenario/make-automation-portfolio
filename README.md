# 🚀 Enterprise Make.com Automation Portfolio

A collection of production-ready business process automations, API integrations, and fault-tolerant workflows built on **Make.com**.

---

## 📂 System Architecture Overview

| # | Scenario | Core Technologies | Primary Focus | Architecture Type |
|---|----------|-------------------|---------------|-------------------|
| 1 | **B2B Lead Ingestion & Scoring** | Webhooks, Custom Variables, Google Sheets | Instant Lead Processing | Synchronous Single-Record |
| 2 | **Resilient Batch Enrichment & Triaging** | HTTP API, Error Handlers (Resume), Iterators, Router | Mass Processing & High Availability | Asynchronous Batch Loop |

---

## 🟢 Scenario 1: B2B Lead Ingestion & Scoring

### 🎯 Business Problem
Sales teams often lose hot leads due to delayed response times and manual copy-pasting from web forms into databases.

### 🛠️ Technical Solution & Stack
* **Webhook Trigger:** Instantaneous real-time ingestion of inbound web form leads.
* **Tools (Set Variable):** Calculates lead priority scoring on the fly.
* **Google Sheets Integration:** Appends sanitized record data directly into the central sales spreadsheet.

### 📈 Business Impact
* **Zero Manual Data Entry:** Fully automates row logging.
* **Instant Processing:** Reduces lead contact time from hours to seconds.

---

## 🔵 Scenario 2: Resilient Batch Lead Enrichment & Triaging

### 🎯 Business Problem
High-volume B2B lead pipelines require fetching external API data in bulk. Standard scenarios crash when third-party APIs experience downtime or rate limits.

### 🛠️ Technical Solution & Stack
* **HTTP Module:** Fetches bulk lead payloads from external REST APIs.
* **Fault Tolerance (Resume Handler):** Implements an automatic error-handling fallback. If the target API fails, mock/cached data is injected, ensuring 100% workflow uptime.
* **Iterator (Loop Engine):** Unpacks complex data arrays into individual processing bundles.
* **Conditional Router:** Routes high-scoring "Hot Leads" to Outlook email alerts and standard records to Google Sheets.

### 📈 Business Impact
* **99.9% System Availability:** Error handlers prevent workflow crashes during external outages.
* **Scalable Batching:** Processes hundreds of records per execution cycle with zero manual intervention.

---

## 📥 How to Import These Scenarios

1. Download the desired `.json` Blueprint file from the repository root.
2. Open your **Make.com** dashboard and create a new scenario.
3. Click the **`...` (More)** menu at the bottom toolbar and select **Import Blueprint**.
4. Upload the `.json` file and re-bind your service credentials (Google, Microsoft 365, Webhooks).

---
*Maintained by **FiduciaScenario** | Professional Automation Portfolio*
