# “Don Control Pizzas”
**Frameworks:** ISO/IEC 27001 · SOC 2 · NIST CSF  
**Focus:** Access control, availability (backup/restore), data retention  
**Data:** 100% synthetic (no real PII)

A tangible, audit-friendly portfolio applying GRC controls to a simple, relatable business (a pizza shop with online orders and delivery partners). The repo shows **end-to-end control execution**: policy → procedure/runbook → scripts/notebooks → evidence → one-page reports → crosswalk to frameworks.

---

## 🔎 What to look at first
- `01_case/` — three mini-projects with code, data, logs and reports  
  - **A_access_review/** (Who has the keys?)  
  - **B_Backup_Restore_test/** (Proof of life)  
  - **C_Data_Retention/** (Data diet)  
- `02_Frameworks/` — **Crosswalk_ISO_NIST_SOC2**, **SoA**, **RCM**, **CSF_Assessment**  
- `03_Evidence/hashes/ledger.csv` — integrity index (SHA-256) of key artifacts

> Each mini-project includes **policy**, **procedure/runbook**, **notebook/script**, **evidence**, **KPIs**, and **framework mapping** (ISO 27001 · NIST CSF · SOC 2).

---

## 🧭 Business processes & assets (scenario)
- **POS / Online ordering** (orders, payments)  
- **CRM** (customers: names, addresses, phones, loyalty)  
- **Payment gateway** (third-party)  
- **Delivery platform** (third-party)  
- **Shared spreadsheets** (operations)

---

## 🧩 Mini-projects (overview)

### A) Access Review — “Who has the keys?”
**Goal:** Ensure only authorized users hold access; recertify high-privilege roles.  
**Inputs:** `data/users.csv`, `data/roles.csv`, `data/assignment.csv`  
**Output:** `outputs/findings.csv` (orphans/inactive + high-privilege)  
**Docs/Code:** `scripts/Access_control_policy.md`, `scripts/Access_review.ipynb`, `scripts/Report_Access_review.md`  
**KPIs (targets):** 100% critical apps reviewed monthly · orphans=0 post-review · findings closed ≤30 days  
**Frameworks:** ISO 27001 A.5.16 / A.8.3 · NIST CSF **PR.AC** · SOC 2 **CC6.x**

### B) Backup & Restore Test — “Proof of life”
**Goal:** Demonstrate recoverability (Availability) with real evidence (RTO/RPO).  
**Inputs:** `data/orders.csv`  
**Outputs:** `backups/orders_YYYY-MM-DD.csv`, `data/restored_orders.csv`, `logs/backup_log.txt`, `logs/restore_log.txt`  
**Docs/Code:** `scripts/runbook_backup_restore.md`, `scripts/backup_restore.ipynb`, `scripts/report_availability.md`  
**KPIs (targets):** Success rate 100% · **RTO ≤ 30 min** · **RPO ≤ 1 h** · backup age ≤ 24 h · data integrity 100%  
**Frameworks:** ISO 27001 A.8.13 / A.5.30 · NIST CSF **Recover (RC)** · SOC 2 **Availability**

### C) Data Classification & Retention — “Data diet”
**Goal:** Label PII and enforce deletion when no longer necessary (storage limitation).  
**Inputs:** `data/customers.csv`  
**Outputs:** `data/customers_labels.csv`, `data/customers_after_purge.csv`, `logs/purge_log.txt`  
**Docs/Code:** `scripts/Data_retention_policy.md`, `scripts/Data_retention.ipynb`, `scripts/Report_Data_Retention.md`  
**KPIs (targets):** 100% datasets labeled · purge job on schedule · exceptions documented w/ end date · evidence signed  
**Frameworks:** ISO 27001 **A.8.10** · NIST CSF **PR.DS** · SOC 2 **Confidentiality/Privacy**

---

## 🗂️ Repository layout (as shipped)
Don Control Pizzas 1/
├─ 01_case/
│ ├─ A_access_review/
│ │ ├─ data/ # assignment.csv, roles.csv, users.csv
│ │ ├─ outputs/ # findings.csv (results)
│ │ └─ scripts/ # Access_control_policy.md, Access_review.ipynb, Report_Access_review.md
│ ├─ B_Backup_Restore_test/
│ │ ├─ backups/ # orders_YYYY-MM-DD.csv (point-in-time backup)
│ │ ├─ data/ # orders.csv, restored_orders.csv
│ │ ├─ logs/ # backup_log.txt, restore_log.txt
│ │ └─ scripts/ # backup_restore.ipynb, report_availability.md, runbook_backup_restore.md
│ └─ C_Data_Retention/
│ ├─ data/ # customers.csv, customers_labels.csv, customers_after_purge.csv
│ ├─ logs/ # purge_log.txt
│ └─ scripts/ # Data_retention_policy.md, Data_retention.ipynb, Report_Data_Retention.md
├─ 02_Frameworks/
│ ├─ Crosswalk_ISO_NIST_SOC2.csv
│ ├─ CSF_Assessment.xlsx
│ ├─ RCM.xlsx
│ └─ SoA.xlsx
└─ 03_Evidence/
└─ hashes/ # evidence_ledger_builder.ipynb, ledger.csv