# Backup & Restore Runbook

**Goal:** Prove we can recover order data (availability).  
**Scope:** Non-production dataset (`data/orders.csv`).  
**Steps:**
1. Generate a timestamped backup in `backups/`.
2. Restore the latest backup to `data/restored_orders.csv`.
3. Record both events in `logs/*.txt` (UTC).
4. Verify row counts match; attach logs as evidence.

**KPIs:** Success rate; Recovery Time Objective (RTO).  
**Frameworks:** NIST **Recover** · ISO 27001 operational controls · SOC 2 Availability.
