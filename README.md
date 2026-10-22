# grc-security-lab1
# GRC Practical Lab: Access Review & CIS Policy Mapping

This repository contains practical Governance, Risk, and Compliance (GRC) deliverables demonstrating identity audits, Segregation of Duties (SoD) verification, and system hardening policy mapping[cite: 1].

---

## 1. GRC 1: Access Review Checklist

An Excel-based quarterly Identity & Access Management (IAM) audit spreadsheet reviewing sample user accounts to enforce the **Principle of Least Privilege** and identify **SoD violations**[cite: 1].

### Audit Sample Data

| User | Role | Groups | Last Login | Still Required? | Least Privilege? | SoD Violation? | Action | Mgr Sign-off |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `jdoe` | SOC Analyst | `Security, SOC-Level1` | 2026-10-21 | Yes | Yes | No | **Keep** | Approved (A. Smith) |
| `asmith` | SOC Lead | `Security, SOC-Level2, Domain Admins` | 2026-10-22 | Yes | No | No | **Revoke Admin** | Approved (M. Taylor) |
| `mkwame` | HR Specialist | `HR-Team, Payroll-Approvers` | 2026-05-14 | No | No | Yes | **Disable Account** | Pending Sign-off |
| `cdevin` | Software Engineer | `Dev-Team, Prod-Deployers, DB-Admins` | 2026-10-20 | Yes | No | Yes | **Remove DB-Admins** | Approved (K. Vance) |
| `ebrown` | Finance Analyst | `Finance-Read, Billing` | 2026-06-01 | No | Yes | No | **Disable Account** | Approved (R. Patel) |
| `rpatel` | Finance Manager | `Finance-Approvers, Vendor-Creation` | 2026-10-22 | Yes | No | Yes | **Remove Vendor-Creation** | Pending Sign-off |
| `srogers` | IT Support Tech | `Helpdesk, Domain Admins` | 2026-10-22 | Yes | No | No | **Downgrade Access** | Approved (M. Taylor) |
| `tnguyen` | QA Tester | `QA-Team, Staging-Users` | 2026-10-19 | Yes | Yes | No | **Keep** | Approved (K. Vance) |
| `lchen` | Compliance Officer | `GRC-Auditors, ReadOnly-All` | 2026-10-22 | Yes | Yes | No | **Keep** | Approved (J. Davis) |
| `jdavis` | CISO | `Exec-Team, Security-Admins` | 2026-10-21 | Yes | Yes | No | **Keep** | Approved (Board Chair) |

---

## 2. GRC 2: Map CIS Benchmarks to Internal Policy

Bridging technical system hardening controls with regulatory and corporate compliance frameworks[cite: 1].

### Control Mapping Table

| CIS Control Benchmark | Internal Policy Reference | Framework Cross-walk |
| :--- | :--- | :--- |
| **1.1.1.1** — Disable unused file systems (`cramfs`) | Internal Hardening Policy § 3.2 | ISO 27001 A.5.17, SOC 2 CC6.1[cite: 1] |
| **5.4.1** — Enforce maximum password age (`PASS_MAX_DAYS 365`)[cite: 1] | Internal Access Control Policy § 4.2[cite: 1] | ISO 27001 A.9.4.3, NIST AC-2 |
| **6.2.6** — Prevent world-writable files | System Integrity Standard § 5.1 | SOC 2 CC6.3, PCI-DSS 2.2.2 |

### Evidence Collection (CLI Commands)[cite: 1]
To verify compliance and capture evidence for auditors:
```bash
# Check maximum password age configuration
grep PASS_MAX_DAYS /etc/login.defs

# Run automated system compliance audit
lynis audit system
