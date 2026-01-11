# Architecture Overview

The diagram provides a high-level view of an Azure data platform, emphasizing clear
separation between ingestion, processing, storage, and analytics, with security and
operational controls applied across the platform.

```mermaid
flowchart LR
    Sources[Data Sources]
    Ingest[Ingestion Layer]
    Stream[Streaming Processing]
    Batch[Batch Processing]
    Storage[Data Lake / Lakehouse]
    Serve[Analytics & BI]
    GenAI[GenAI / Analytics Assistants]
    Monitor[Monitoring & Audit Logs]
    IAM[Identity & Access Management]

    Sources --> Ingest
    Ingest --> Stream
    Ingest --> Batch
    Stream --> Storage
    Batch --> Storage
    Storage --> Serve
    Serve --> GenAI

    IAM --- Ingest
    IAM --- Storage
    IAM --- Serve

    Monitor --- Ingest
    Monitor --- Stream
    Monitor --- Batch
    Monitor --- Serve
