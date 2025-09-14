# Backup & Restore — Report

**Period tested:** 2025-09-11  
**System/Scope:** POS orders CSV (non-prod, isolated)  
**Objective:** Demonstrate recoverability within SLAs (Availability)

## KPIs / SLAs (Targets)
- Success rate: 100% per scheduled test
- **RTO:** ≤ 30 min
- **RPO:** ≤ 1 hour
- Backup age at test start: ≤ 24 hours
- Data integrity: 100% row count match (pre vs post)

## Plan & Approvals
- Change ticket: CAB-2025-0911-01 (approved by App Owner/DBA/ISMS)
- Environment: Non-production, read-only
- Dataset: Latest CSV backup (synthetic, no PII)

## Execution Summary (UTC)
- Start: 16:00:10  • End: 16:00:42  • **Elapsed (RTO):** 00:00:32
- Backup used: `backups/orders_20250911_1600Z.csv`  (age: 12 min)
- Restore target: `data/restored_orders.csv`
- Validation: row count pre=4, post=4  • Constraints: N/A (CSV)

## Results vs KPIs
| KPI               | Target     | Actual       | Status |
|-------------------|------------|--------------|--------|
| Success rate      | 100%       | 100%         | PASS   |
| RTO               | ≤ 30 min   | **0.53 min** | PASS   |
| RPO               | ≤ 1 h      | **12 min**   | PASS   |
| Backup age        | ≤ 24 h     | **12 min**   | PASS   |
| Data integrity    | 100% match | **Match**    | PASS   |

## Findings & Actions
- F-01: Integrity check limited to row count.  
  **Action:** add checksum/hash of file and schema validation for DB restores. **Owner:** DBA. **Due:** 2025-10-01.
- F-02: Backups currently stored locally in demo.  
  **Action:** document retention/rotation + encryption at rest in real env. **Owner:** ISMS/Infra. **Due:** 2025-10-15.

## Evidence Map
- Logs: `logs/backup_log.txt`, `logs/restore_log.txt`
- Restored data: `data/restored_orders.csv`
- Evidence integrity (SHA-256 examples):  
  - `2025-09-11T15-27-08Z  backup_log.txt  SHA256=<...>`  
  - `2025-09-11T15-27-08Z  restore_log.txt  SHA256=<...>`

## Framework Mapping
- **NIST CSF:** Recover (RC)  
- **ISO/IEC 27001:** Annex A 8.13 (Information backup), A.5.30 (ICT readiness for BC)  
- **SOC 2:** Availability

**Sign-off**  
DBA/App Owner: __________________  • ISMS/GRC: __________________  • Date: __________

