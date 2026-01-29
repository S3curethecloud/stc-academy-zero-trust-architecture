# Lab 3.1 — Identity-Aware Access to Compute (No Inbound Ports)

## Goal
Access private compute **without opening inbound ports** (no SSH, no bastion, no VPN) using **identity-native sessions**.

This lab establishes the Zero Trust baseline:
> Access is tied to identity and policy, not network location.

---

## Prerequisites
- Phase 2 VPC exists (private subnets + NAT recommended)
- You can launch EC2 in the private app subnet
- IAM permissions to use Systems Manager (SSM)

---

## Architecture Intent (Read First)
- Instance in **private subnet**
- **No public IP**
- Security Group: **no inbound rules**
- Access via **SSM Session Manager**
- Outbound **HTTPS 443** allowed for SSM

---

## Step 1 — Confirm Private Subnet
VPC → Subnets → select your private app subnet  
Confirm:
- Auto-assign public IPv4: **Disabled**
- Route table includes: `0.0.0.0/0 → NAT` (recommended)

---

## Step 2 — Create IAM Role for SSM
IAM → Roles → Create role  
- Trusted entity: AWS service
- Use case: EC2
Attach policy:
- ✅ `AmazonSSMManagedInstanceCore`

Role name:
- `stc-ec2-ssm-role`

---

## Step 3 — Create Security Group (No Inbound)
EC2 → Security Groups → Create  
Name:
- `stc-zt-sg-private-ssm`

Inbound:
- **None**

Outbound (minimum):
- HTTPS 443 → `0.0.0.0/0`

Why:
- SSM uses outbound HTTPS.

---

## Step 4 — Launch Private EC2 (No Public IP)
EC2 → Launch instance  
- Name: `stc-zt-private-app-1`
- Subnet: private app subnet
- Auto-assign public IP: **Disabled**
- SG: `stc-zt-sg-private-ssm`
- IAM instance profile: `stc-ec2-ssm-role`

Launch.

---

## Step 5 — Verify Instance is Managed by SSM
Systems Manager → Fleet Manager (Managed nodes)  
Expected:
- Instance appears as **Managed** and **Online**

If missing:
- Confirm NAT egress exists
- Confirm outbound 443 allowed
- Confirm IAM role attached

---

## Step 6 — Start Identity-Native Session
Systems Manager → Session Manager → Start session  
Select `stc-zt-private-app-1`

✅ You now have shell access without:
- public IP
- inbound SSH
- bastion host
- VPN

---

## Step 7 — Evidence Capture (Required)
Capture screenshots:
1) EC2 instance showing **no public IP**
2) Security Group showing **no inbound**
3) Session Manager active session

Store in:
`diagrams/evidence/` (or your preferred evidence path)

---

## Success Criteria
- ✅ No public IP
- ✅ No inbound rules
- ✅ Access works via SSM Session Manager
- ✅ Access is identity-based and auditable

---

## Why This Is Zero Trust
- Access is granted by identity + permission
- Network location provides no implicit trust
- Sessions are short-lived and controllable

---

## Next Lab
➡️ **Lab 3.2 — Zero Trust Network Segmentation**
