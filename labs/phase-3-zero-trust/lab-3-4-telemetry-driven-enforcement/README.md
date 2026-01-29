# Lab 3.4 — Telemetry-Driven Trust Enforcement

## Goal
Understand how **telemetry signals** are used to dynamically **enforce, limit, or revoke trust** in a Zero Trust architecture.

This lab completes Phase 3 by turning:
> logs and signals

into:
> access decisions and enforcement actions.

---

## Why This Lab Exists

Up to now, Phase 3 has established that:

- Identity grants access (Lab 3.1)
- Network trust is explicit and minimal (Lab 3.2)
- Trust is conditional and contextual (Lab 3.3)

But Zero Trust is incomplete without this final capability:

> **Responding to signals in real time.**

Telemetry is what allows trust to be **continuously evaluated**.

---

## Architecture Intent (Read First)

- Signals do not exist for visibility alone
- Telemetry must influence enforcement
- Trust can be reduced or revoked at any time
- Detection without response is incomplete security

This lab prepares the system for **SIEM and response (Phase 4)**.

---

## What Counts as Telemetry in Zero Trust

Telemetry includes:

- Identity events (authentication, role usage)
- Session activity (SSM sessions, API calls)
- Network behavior (VPC Flow Logs)
- Behavioral anomalies
- Access frequency and patterns

Zero Trust systems **listen continuously**.

---

## Scenario Overview

You will model a system where:

- Access is identity-based
- Trust is conditional
- Telemetry influences enforcement decisions

This lab is **design-first**, not automation-heavy.

---

## Step 1 — Identify High-Value Signals

From your existing environment, identify signals such as:

- Unexpected outbound connections
- Unusual session duration or frequency
- Access outside expected workflows
- Identity usage inconsistent with role intent

Write these down as **decision inputs**.

---

## Step 2 — Define Enforcement Actions

For each signal, define an action:

Examples:
- Terminate active SSM session
- Reduce permissions on the role
- Block outbound traffic
- Flag identity for investigation

Zero Trust requires **predefined responses**.

---

## Step 3 — Map Signals to AWS Sources

Conceptually map signals to sources:

- CloudTrail → identity actions
- VPC Flow Logs → network behavior
- SSM Session logs → access behavior
- GuardDuty (future) → risk signals

You are not configuring SIEM yet — you are designing for it.

---

## Step 4 — Model a Trust Revocation Flow

Example:

1. Identity authenticates successfully
2. Access granted via SSM
3. Telemetry detects unexpected outbound behavior
4. Trust score decreases
5. Session terminated or permissions reduced

This is **adaptive enforcement**.

---

## Step 5 — Explain This in an Interview (Critical)

Be able to say:

> “Zero Trust means access is continuously evaluated.
> Telemetry drives enforcement, not just alerts.
> Trust can be revoked at any time based on signals.”

This is senior-level reasoning.

---

## Success Criteria Checklist

- ✅ You can explain telemetry as an enforcement driver
- ✅ You can model trust revocation scenarios
- ✅ You understand signal → decision → action flow
- ✅ You can explain how Phase 3 leads to SIEM

---

## Why This Completes Phase 3

- Identity grants access
- Network enforces intent
- Context shapes trust
- **Telemetry enforces decisions**

Phase 3 is now **operational Zero Trust**.

---

## What Comes Next

➡️ **Phase 4 — Detection & Response (SIEM)**

This is where:
- Signals are centralized
- Decisions are automated
- Responses are orchestrated

Phase 3 made Phase 4 possible.
