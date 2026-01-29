# Lab 3.3 — Context & Conditional Trust Decisions

## Goal
Understand how **context and conditions** influence trust decisions after access is granted.

This lab moves Zero Trust beyond:
> “Who are you?”

to:
> “Under what conditions should access continue?”

This is the foundation of **adaptive, risk-aware access control**.

---

## Why This Lab Exists

Phase 1 proved identity.
Phase 2 secured compute placement.
Phase 3.1 removed inbound access.
Phase 3.2 removed implicit internal trust.

Yet one question remains:

> Should access always be allowed just because identity is valid?

Zero Trust answers **no**.

Trust is conditional.

---

## Architecture Intent (Read First)

- Authentication ≠ Authorization
- Trust is **dynamic**, not static
- Access decisions should respond to:
  - Identity state
  - Environment
  - Risk signals
  - Time and context

This lab is **architectural**, not UI-driven.

---

## What “Context” Means in Zero Trust

Context is any signal that influences trust:

- Identity posture (role, session type)
- Access method (SSM, API, console)
- Network behavior
- Time, frequency, or anomaly
- Telemetry from surrounding systems

Zero Trust uses context to **limit or revoke trust**, not just grant it.

---

## Scenario Overview

You will model a system where:

- Access is identity-based
- Trust is **conditionally granted**
- Context determines whether access continues

No new AWS services are required — this is about **design reasoning**.

---

## Step 1 — Define a Baseline Trust Policy

Assume:

- Access is granted via IAM + SSM
- Instance has no inbound ports
- Identity is authenticated

Baseline trust condition:
> “Allow access only for approved roles during expected conditions.”

Write this down. This is your **policy intent**.

---

## Step 2 — Introduce Contextual Constraints

Now add conditions to the policy:

Examples:
- Access allowed only via SSM (not SSH)
- Access allowed only for short-lived sessions
- Access denied if anomalous behavior occurs
- Access restricted outside normal operating windows

This is **conditional trust**.

---

## Step 3 — Map Context to AWS Signals (Conceptual)

In AWS, context comes from:
- IAM session attributes
- CloudTrail identity events
- VPC Flow Logs
- Session Manager activity
- GuardDuty / detection systems (later phase)

You are not configuring them yet — you are **designing for them**.

---

## Step 4 — Model a Trust Revocation Scenario

Example scenario:

- Identity authenticates successfully
- Session begins via SSM
- Unexpected outbound behavior appears
- Telemetry indicates risk

Decision:
> Trust should be reduced or revoked.

Zero Trust requires:
- Ability to **terminate sessions**
- Ability to **restrict permissions**
- Ability to **respond dynamically**

---

## Step 5 — Explain This in an Interview (Critical)

Be able to say:

> “Zero Trust is not just identity-based access.
> It is continuous evaluation of identity, context, and signals to decide whether access should persist.”

This lab gives you that explanation.

---

## Success Criteria Checklist

- ✅ You can explain conditional trust clearly
- ✅ You understand context as a security signal
- ✅ You can model trust revocation
- ✅ You can explain Zero Trust beyond buzzwords

---

## Why This Is Zero Trust

- Trust is not permanent
- Access is conditional
- Decisions adapt to signals
- Breach is assumed

This is what separates **senior architects** from tool operators.

---
