---
layout: page
title: "Audit Trails & Log Retention for AI in GxP: A Practical Starter Checklist"
permalink: /insights/audit-trails-log-retention-ai-gxp/
---

If an AI system impacts GxP decisions, you will eventually be asked some version of:
**“Show me what happened, who decided, what changed, and how you know it worked.”**

That is audit trails and log retention—applied to modern AI systems.

## The principle
You don’t need “more logs.” You need the **right logs**, tied to:
- system boundaries
- ownership
- decision points
- and retention rules aligned to risk

## What auditors usually want (in plain language)
- **Traceability:** what version ran, on what data, with what configuration
- **Integrity:** logs are complete, tamper-resistant, and reviewable
- **Accountability:** actions are attributable to a user/service account
- **Review:** there is a cadence that proves logs are actually used

## The starter checklist (minimum viable audit trail)
### 1) Model identity
- model name / ID
- version tag / build hash
- release date + approver
- training dataset reference (or dataset version pointer)

### 2) Data lineage
- input source(s) and transformations
- validation checks (schema, missingness, drift monitors)
- time window / cohort definition (when applicable)

### 3) Runtime record
- inference timestamp
- model version used
- key parameters/config
- output + confidence (if used)
- downstream action taken (if applicable)

### 4) Change control events
- what changed (data, model, thresholds, UI, workflow)
- why it changed (ticket / deviation / risk assessment)
- approval record
- rollback plan + actual rollback events

### 5) Monitoring + triage
- alert threshold vs action threshold
- owner and response SLA
- decision log for “accept / mitigate / freeze / rollback”
- effectiveness checks after changes

## Retention: how long is “long enough”?
A practical approach:
- align retention to **risk and business criticality**
- ensure you can reconstruct events across the relevant lifecycle (release → operation → incident → remediation)

More important than the exact number is that retention is:
- defined
- justified
- and actually implemented consistently

## The operating model that makes this real
- weekly review of key signals (drift, performance, incidents)
- monthly governance readout (decisions, changes, trends)
- quarterly control effectiveness review (are the controls working?)

If you can’t show governance and decision logging, your “audit trail” is just storage.
