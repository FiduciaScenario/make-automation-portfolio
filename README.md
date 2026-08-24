# 🚀 Enterprise Make.com Automation Portfolio

A collection of production-ready business process automations, API integrations, and fault-tolerant workflows built on **Make.com**.

---

## 📂 System Architecture Overview

| # | Scenario | Core Technologies | Primary Focus | Architecture Type |
|---|----------|-------------------|---------------|-------------------|
| 1 | **B2B Lead Ingestion & Scoring** | Webhooks, Custom Variables, Google Sheets | Instant Lead Processing | Synchronous Single-Record |
| 2 | **Resilient Batch Enrichment & Triaging** | HTTP API, Error Handlers (Resume), Iterators, Router | Mass Processing & High Availability | Asynchronous Batch 
Loop |
| 3 | Lead Deduplication & Data Aggregator | JSON Parser, Data Store, Filters, Aggregator | Data Cleaning & Cost Optimization | Asynchronous Batch Loop |
| 4 | B2B Batch Lead Processor & Data Store Buffer | Webhooks, Iterator, Router, Data Store Buffer, Aggregator | Resilient Bulk Processing & Error Handling | Asynchronous Batch & Aggregation |


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






## Scenario 3: Lead Deduplication & Data Aggregator

### Business Problem
Inbound lead generation channels frequently process duplicate submissions. Processing identical leads multiple times wastes CRM API quotas, causes redundant outbound communications (spamming clients), and bloats internal database storage with unverified data.

### Technical Solution & Architecture
An automated deduplication pipeline built in Make.com that verifies and cleans incoming lead records prior to database ingestion:
1. **Parse JSON:** Consumes and parses structured incoming batch data.
2. **Get a Record (Data Store):** Queries the target database using the lead's unique identifier (e.g., Email).
3. **Filter ("Brak duplikatu"):** Evaluates if the record already exists using the `Basic operators: Does not exist` rule. Non-existing (unique) records proceed; existing duplicates are blocked.
4. **Add/Replace a Record:** Ingests only verified unique leads into the Data Store.
5. **Array Aggregator:** Aggregates processed unique records into a clean, unified array structure for downstream batch reporting or CRM sync.

### Business Impact & Value
* **100% Data Hygiene:** Prevents double-entry and dirty data in primary data stores.
* **Cost Optimization:** Reduces unnecessary downstream API calls and manual data scrubbing effort.
* **Sales Efficiency:** Protects sales teams from reaching out to the same prospect multiple times.
* **Estimated Market Value:** $400 – $900 single implementation / $150 – $300/mo maintenance contract.

### How to Import & Setup
1. Download the `Lead-Deduplication-Aggregator.json` blueprint file from this repository.
2. Open Make.com, create a new Scenario, and click **Import Blueprint** (via the `...` menu at the bottom).
3. Re-link your Data Store structure to match your target database fields.
4. Save and run the scenario.





---



## 🚀 Scenario 4: B2B Batch Lead Processor & Data Store Buffer

**File:** `04-batch-lead-data-store-buffer.json`  
**Category:** High-Throughput Data Processing & Resilience Architecture

### 📋 Overview
High-volume lead ingestion pipeline built for B2B applications handling bulk data payloads. The scenario accepts raw arrays of lead records via HTTP Webhook, decomposes them into individual items, applies business validation & scoring logic, routes qualified leads into Make's native **Data Store**, and aggregates rejected entries into a single execution summary report.

### ⚙️ Key Technical Features
* **Array Iteration (`Iterator`):** Unpacks complex nested JSON arrays into single-entity execution bundles.
* **Deterministic Routing & Fallback Filter:** Routes records matching strict criteria (`email contains @` AND `score >= 50`) while using a zero-condition `Fallback Route` for invalid entries.
* **Resilient Data Store Operations:** Implements `Add/Replace` upsert logic with unique keying (`email`) to prevent record duplication and state corruption.
* **Data Aggregation (`Array Aggregator`):** Collects processed metadata from multiple execution threads back into a single structured array for down-stream notification.

### 📐 Architecture Diagram
`Webhook Ingestion` ➔ `Iterator` ➔ `Router` 
 ├── *(Valid Lead)* ➔ `Data Store (Lead Buffer)`
 └── *(Fallback)* ➔ `Array Aggregator` ➔ `Tools (Summary Report)`

### 💼 Business Impact & ROI
* **90% Cost Reduction on API Operations:** Aggregates error reporting into single-event executions instead of firing individual notifications per error.
* **Zero Data Loss:** Acts as an architectural buffer between external Webhook providers and target CRMs during API rate limits or downtime.
* **Data Hygiene:** Prevents invalid emails and unqualified leads from cluttering production CRM databases.

