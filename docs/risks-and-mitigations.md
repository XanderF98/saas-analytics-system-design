# Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation | Owner |
|------|------------|--------|------------|-------|
| Tenant data leakage | Low | High | RLS + scoped queries + automated isolation tests; quarterly audits | Security |
| Scaling bottlenecks in processing | Medium | Medium | Load testing pre-GA; autoscaling; backpressure handling | Platform Eng |
| Quota abuse / noisy neighbor | Medium | Medium | Rate limiting; per-tenant quotas; adaptive throttling | API Team |
| Complex cross-team dependencies | Medium | Medium | Clear RACI; integration milestones; weekly dependency review | TPM |
| Incident response delays | Medium | High | On-call rotation; runbooks; alert tuning; rehearsal drills | SRE |
| Vendor lock-in (managed OLAP/pub-sub) | Medium | Medium | Abstraction layer; export paths; periodic re-evaluation | TPM + Eng |
| Compliance gaps (SOC 2) | Low | High | Control mapping; evidence collection; internal audits | Compliance |
