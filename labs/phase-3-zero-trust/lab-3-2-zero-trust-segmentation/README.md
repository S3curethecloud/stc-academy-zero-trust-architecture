# Lab 3.2 — Zero Trust Network Segmentation

**Phase:** Phase 3 — Zero Trust Architecture  
**Theme:** Removing implicit internal trust  
**Level:** Advanced  

---

## 🎯 Lab Goal

Enforce **least-privilege east-west traffic** between workloads by replacing
implicit network trust with **explicit service-to-service intent**.

This lab removes the dangerous assumption that:

> “If traffic is inside the VPC, it is trusted.”

---

## 🧠 Zero Trust Principle

- No implicit trust based on network location
- Every workload interaction is **explicitly allowed**
- Lateral movement is denied by default

---

## 🏗 Architecture Intent

- Workloads run in **private subnets**
- No flat trust zones
- Security Groups reference **other Security Groups**
- Traffic is allowed only where intent exists

---

## 🔧 What You Will Build

- Two application tiers:
  - `app-a` (producer)
  - `app-b` (consumer)
- Explicit SG → SG rules
- Denied lateral traffic by default

---

## 📋 Prerequisites

- Phase 2 Secure Compute Foundations completed
- Private subnets with routing in place
- EC2 or containerized workloads
- IAM permissions to manage Security Groups

---

## 🧪 Step-by-Step

### Step 1 — Identify Workloads

Identify two workloads:

- App A (source)
- App B (destination)

Each must have **its own Security Group**.

---

### Step 2 — Create Security Groups

Create:

- `sg-app-a`
- `sg-app-b`

Rules:

- ❌ No CIDR-based trust
- ❌ No “allow all internal”
- ✅ Only explicit references

---

### Step 3 — Enforce Explicit Intent

Allow **only** App A → App B on required port:

Example:

- Source: `sg-app-a`
- Destination: `sg-app-b`
- Port: application-specific (e.g. 443)

All other east-west traffic remains **denied**.

---

### Step 4 — Validate Denial

Attempt:

- App B → App A
- App A → unrelated workloads

These must **fail**.

---

## ✅ Success Criteria

- No CIDR-based internal allow rules
- All east-west traffic is explicit
- Lateral movement denied by default
- Architecture defensible in interviews

---

## 🧠 Why This Is Zero Trust

- Network location grants **no trust**
- Identity + intent drive access
- Compromise does not equal lateral freedom

This is the foundation of Zero Trust networking.
