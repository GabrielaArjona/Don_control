# Data Retention — Report

**Period reviewed:** 2025-09-11  
**Scope:** CRM customers dataset (non-prod, masked/synthetic)  
**Objective:** Reduce exposure by retaining personal data only as long as needed and proving secure deletion.

## KPIs / SLAs - Targets
- Coverage: 100% of in-scope datasets labeled with sensitivity & retention
- Retention policy: documented periods per dataset with legal/business justification
- Purge cadence: job runs on schedule (quarterly) with logs
- Exceptions: 100% documented with risk acceptance & end date
- Evidence integrity: all artifacts signed (timestamp + SHA-256)

## Legal & Policy Basis - Summary
- Storage limitation principle (keep data **no longer than necessary** for stated purposes)
- Documented retention periods per dataset; secure deletion with verifiable logs
- References: ISO/IEC 27001 A.8.10 (Information deletion); NIST CSF PR.DS; GDPR Art. 5(1)(e).


## Method & Controls
1) Heuristic column labeling → `data/customers_labels.csv`  
2) Purge by last activity (e.g., >18 months) → `logs/purge_log.txt` + `data/customers_purged.csv`  
3) Exceptions register (if any) with owner, reason, end date  


## Execution Summary (UTC)
- Run ID: <RET-2025-09-11-01> • Start: <HH:MM:SS> • End: <HH:MM:SS>
- Policy parameter: inactivity cutoff = **18 months**
- Source rows: <4> • Purged: <3> • Kept: <1>
- Labels file: `data/customers_labels.csv` • Purge output: `data/customers_purged.csv`
- Job status: **SUCCESS**

## Results vs KPIs
| KPI                    | Target                   | Actual              | Status |
|------------------------|--------------------------|---------------------|--------|
| Dataset coverage       | 100%                     | 100% (1/1)          | PASS   |
| Policy documented      | Yes                      | Yes (Policy.md)     | PASS   |
| Purge cadence on time  | On schedule              | On schedule         | PASS   |
| Exceptions documented  | 100%                     | 0 exceptions        | PASS   |
| Evidence integrity     | All signed               | Hashes recorded     | PASS   |

## Findings & Actions
- F-01: Retention period for **orders.csv** not validated against tax/contract rules.  
  **Action:** confirm with Legal/Tax; update table; adjust purge job. **Owner:** Data Owner. **Due:** 2025-09-30.
- F-02: Labeling heuristic only by column name.  
  **Action:** add data profiling & approved classification list. **Owner:** ISMS. **Due:** 2025-09-30..

## Evidence Map
- Labels: `data/customers_labels.csv`  
- Purge log: `logs/purge_log.txt`  
- Output: `data/customers_purged.csv`  


## Framework Mapping
- **ISO/IEC 27001:** Annex A 8.10 (Information deletion)  
- **NIST CSF 2.0:** PR.DS (Data Security) — retention/deletion & backups govern data lifecycle  
- **SOC 2:** Confidentiality/Privacy (criteria) — retention & disposal as per policy  
- **Local law:** storage limitation (keep only as necessary), documented periods & deletion procedures

**Sign-off**  
Data Owner: ________ • Legal/Privacy: ________ • ISMS/GRC: ________ • Date: ________
