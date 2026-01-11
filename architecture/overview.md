# Architecture Overview

The diagram provides a high-level view of an Azure data platform, emphasizing clear
separation between ingestion, processing, storage, and analytics, with security and
operational controls applied across the platform.

```mermaid
flowchart TB
  %% MAIN DATA FLOW (STRAIGHT, TOP-DOWN)
  Sources[Data Sources]
  Ingest[Ingestion Layer]
  Process[Processing Layer]
  Storage[Lakehouse Storage]
  Serve[Analytics & BI]
  GenAI[GenAI / Analytics Assistants]

  Sources --> Ingest
  Ingest --> Process
  Process --> Storage
  Storage --> Serve
  Serve --> GenAI

  %% CONTROL PLANE (SIDE, NO CROSSING)
  subgraph Controls[Platform Controls]
    IAM[Identity & Access]
    Monitor[Monitoring & Audit]
    Govern[Governance & Quality]
  end

  IAM -.-> Ingest
  IAM -.-> Storage
  IAM -.-> Serve

  Monitor -.-> Ingest
  Monitor -.-> Process
  Monitor -.-> Serve

  Govern -.-> Storage
  Govern -.-> Serve

