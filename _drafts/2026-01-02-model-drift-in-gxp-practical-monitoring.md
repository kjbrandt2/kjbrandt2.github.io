---
layout: post
title: "Model Drift in GxP: What It Is (and Isn’t) + A Practical Monitoring Playbook"
date: 2026-01-02
categories: [gxp, ai, quality]
tags: [Model Drift, GxP, AI Validation, Monitoring, Data Integrity, Audit Trails]
excerpt: "A practical, audit-friendly approach to defining drift from a validated baseline, setting triggers, assigning owners, and documenting decisions."
---

“Model drift” in GxP isn’t a vibe. It’s a **controlled, measurable change from a validated baseline**.

This matters because the moment a model touches a GxP decision, monitoring becomes part of the **validated state**, not a nice-to-have.

## What drift is (and isn’t)
**Drift is:** model behavior changing over time relative to a validated baseline.

**Drift is not:**
- a single bad prediction
- random noise
- “the model auto-updating” unless you actually deploy changes

The point is defensibility: can you explain what changed, how you detected it, and what you did about it?

---

## The three drifts to monitor (separately)
Most programs fail because they blend signals and can’t interpret the cause.

1) **Data drift**  
Inputs shift (sensor calibration, upstream process changes, new suppliers, different operators, etc.)

2) **Concept drift**  
The relationship between inputs and outcomes changes (process physics/biology changes, new failure modes)

3) **Performance drift**  
Model metrics degrade (AUROC, precision/recall, MAE, calibration, false positives/negatives)

**Practical rule:** treat these as three dashboards, not one number.

---

## Step 1: Define the validated baseline
You need a frozen reference point:
- training dataset version + lineage
- model version + configuration
- decision thresholds
- intended use statement
- validation summary metrics (what “acceptable” means)

If you can’t anchor to baseline, you can’t prove drift.

---

## Step 2: Set acceptance metrics + limits (alert vs action)
Borrow the mindset from process validation:
- **Alert limit:** investigate trend/signal
- **Action limit:** formal response (change control, model rollback, CAPA, etc.)

Limits should map to risk:
- higher patient-impact decisions → tighter limits and faster response SLAs
- low-risk supportive tools → wider limits and scheduled review

---

## Step 3: Define triggers, owners, and response SLAs
A drift program fails when “someone should look at it” is the plan.

Minimum:
- **Trigger:** metric threshold, scheduled review, or change-control event
- **Owner:** accountable for review + decision
- **SLA:** how fast you review/escalate when triggered
- **Approvals:** who signs off on major actions (QA, Validation, etc.)

---

## Step 4: Evidence that survives an audit
Auditors don’t want your dashboard screenshot. They want the story and the record.

Keep:
- monitoring logs + reports (with timestamps)
- review minutes (signals discussed, decisions made)
- investigations when signals cross thresholds
- change control records for updates/retraining/threshold changes
- traceability from signal → decision → action

If it isn’t documented, it didn’t happen.

---

## Step 5: Change control events that should trigger review
At minimum, consider drift review when:
- upstream process parameters or ranges change
- supplier/material changes occur
- instrument or software updates occur
- labeling/method changes affect outcomes
- complaint/deviation trends shift

This is how monitoring stays connected to the validated state.

---

## A simple audit question to pre-answer
**“How do you know the model is still performing as validated, and what happens when it isn’t?”**

If you can show:
- baseline definition
- monitoring plan + thresholds
- owner/SLA
- decision records
- change control linkage

…you’re in good shape.

---

## Question for you
What’s your current drift trigger: **metric thresholds, periodic review, or change-control events**?
