# Phase 3 — Zero Trust Architecture (STC Academy)
**Theme:** How trust is continuously enforced

You have now completed **Phase 2 — Secure Compute Foundations**:
- Compute is private by default
- Network intent is explicit
- Access paths are controlled
- Telemetry exists (Flow Logs)

Phase 3 answers the hardest question:

> After access is granted, how do we continuously verify and enforce trust?

Zero Trust is **not a product**.  
It is an architecture of **continuous evaluation** across identity, context, policy, network boundaries, and telemetry.

---

## Phase Definition (Locked)

**Zero Trust in STC Academy means:**

An architecture where identity, context, and signals are continuously evaluated to grant, limit, or revoke access — regardless of network location.

---

## Learning Objectives (Locked)

By the end of this phase, you can:

- Explain Zero Trust as architecture, not buzzwords
- Enforce identity-aware access to workloads
- Remove static trust paths (VPNs, bastions, flat networks)
- Apply conditional trust controls (context, risk, signal)
- Connect telemetry to enforcement decisions
- Design Zero Trust patterns suitable for interviews + consulting

---

## Canonical Lab Path (Phase 3)

### ✅ Lab 3.1 — Identity-Aware Access to Compute (No Inbound Ports)
Access private compute using identity-native sessions (SSM). No SSH, no bastions, no VPN.

### ✅ Lab 3.2 — Zero Trust Network Segmentation
Enforce least-privilege east-west traffic using explicit service-to-service intent.

### ✅ Lab 3.3 — Context & Conditional Trust Decisions
Model trust as conditional based on identity state, environment, and risk signals.

### ✅ Lab 3.4 — Telemetry-Driven Trust Enforcement & Revocation
Use telemetry (identity + flow logs) to justify restriction or revocation of access.

---

## Repo Structure

```
labs/phase-3-zero-trust/
  lab-3-1-identity-aware-access/
  lab-3-2-zero-trust-segmentation/
  lab-3-3-conditional-trust/
  lab-3-4-telemetry-driven-enforcement/
---
stc-academy-zero-trust-architecture/
```plaintree
├── README.md
├── .mgf/
│   ├── mgf.yaml
│   ├── mgf-metadata.yaml
│   └── mgf-decisions.md
├── diagrams/
│   └── phase-3-zero-trust/
│       ├── academy/
│       └── interview/
├── labs/
│   └── phase-3-zero-trust/
│       ├── lab-3-1-identity-aware-access/
│       │   ├── README.md
│       │   ├── metadata.json
│       │   └── diagrams/README.md
│       ├── lab-3-2-zero-trust-segmentation/
│       │   ├── README.md
│       │   ├── metadata.json
│       │   └── diagrams/README.md
│       ├── lab-3-3-conditional-trust/
│       │   ├── README.md
│       │   ├── metadata.json
│       │   └── diagrams/README.md
│       └── lab-3-4-telemetry-driven-enforcement/
│           ├── README.md
│           ├── metadata.json
│           └── diagrams/README.md
└── terraform/
    └── phase-3-zero-trust/
        ├── README.md
        └── placeholders.md
```
