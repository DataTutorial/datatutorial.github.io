---
title: "Tableau Server Processes"
description: ""
summary: ""
date: 2025-02-17T16:06:35Z
lastmod: 2025-02-17T16:06:35Z
draft: false
toc: true
seo:
  title: "Tableau Server - Processes" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

## Architecture

![diagram-working-across-data-sources](images/bi-platform/tableau-server-cloud/ts-architecture.png)

## Processes to Know

Tableau Server is built with multiple components that interact with each other to serve and manage visualizations. Below are the key components of Tableau Server:

### 1. **VizPortal (Application Server)**

- Manages the web application.
- Handles REST API calls.
- Supports navigation and search.
- Redirects requests to port 443 when SSL is enabled.

### 2. **Backgrounder**

- Executes server tasks like extract refreshes, subscriptions, flow executions, and alerts.

### 3. **Cache Server**

- Provides a shared external query cache.
- Stores key-value pairs from previous queries to speed up future requests.

### 4. **Data Server**

- Manages connections to data sources.

### 5. **Data Engine (Hyper)**

- Creates data extracts.
- Processes queries to data extracts.

### 6. **File Store (Filestore)**

- Stores data extract files.
- Replicates extracts to data engine nodes.

### 7. **Gateway**

- A web server (Apache) that handles requests from browsers, Tableau Desktop, tabcmd, and other clients.
- **Port**: 80.

### 8. **Index and Search Server**

- Based on OpenSearch.
- Handles the fast retrieval and display of content metadata on Tableau Server.

### 9. **Repository (PostgreSQL)**

- Main database of Tableau Server.
- Stores workbook and user metadata.
- When Tableau Catalog or Metadata API is enabled, stores content metadata and external resource metadata.
- **Ports**: 8060 – 8061.

### 10. **VizQL Server**

- Loads and displays views.
- Calculates and runs queries.

### 11. **Cluster Controller**

- Monitors components, detects failures, and handles failover if necessary.

### 12. **Advanced Management**

- This is an optional set of tools for monitoring and optimization.

### 13. **VizData (2024.2)**

- Handles connections and queries of the published data sources instead of Data Server

## Tableau Process Scenario

[![ts-architecture-scenario](images/bi-platform/tableau-server-cloud/ts-architecture-scenario.png)](https://public.tableau.com/app/profile/technical.product.marketing/viz/TableauServerProcessScenarios/ServerArchitectureFlow)
