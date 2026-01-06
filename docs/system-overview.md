
# System Overview

The platform provides real-time and batch analytics for customer data across multiple tenants.
Each tenant represents a distinct customer with isolated data and configurable access controls.

## Business Goals
- Deliver actionable analytics to customers within minutes of data arrival
- Support mid-market and enterprise tenants with varying data volumes
- Provide secure data isolation and enterprise-readiness (audit, RBAC, SLAs)

## Core Capabilities
- **Data ingestion** via REST APIs and batch uploads (CSV/Parquet)
- **Event processing** in near-real time (streaming pipeline)
- **Analytics & reporting** through dashboards and exports
- **Multitenant isolation** at application and data layers
- **Observability** (metrics, logs, traces) and incident response

## Assumptions
- Initial target: 50–200 tenants, each generating 1k–100k events/day
- Growth target: 10× data volume in 18–24 months
- Availability expectation: 99.9% (monthly downtime ≤ 43 minutes)
- Latency SLO: 95% of events visible in dashboards within 5 minutes
- Compliance focus: SOC 2 Type II readiness; HIPAA not in scope initially

## High-Level Component Map
- Client Apps → API Gateway → Auth Service → Ingestion Service → Event Bus → Processing → Analytics Store → Dashboard Service
- Control Plane for tenant provisioning, configuration, and quotas
- Observability stack for monitoring, logging, and alerting

## Data Isolation Model
- Logical isolation: tenant_id propagated through request → auth token → service layer → storage layer
- Row-level security in the shared database and scoped queries
- Periodic audits and automated tests to validate isolation
