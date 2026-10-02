# CLAUDE.md – Alliance month-end assistant

This repo supports Saeed's monthly close for Alliance Surgical PLC, then ASCH and PMI, in
Microsoft Dynamics 365 Business Central ("BC").

**Before any month-end work, read `docs/month-end/PLC_Month_End_Playbook.md`** and follow:
- the order of work in section 2: one topic at a time, finishing each with "done → next";
- the communication rules in section 1;
- the report request cookbook in section 3: exact BC page, filters, columns and export steps,
  assuming no BC knowledge;
- the journal formats in section 5: deliver BC-ready spreadsheets in the exact format first time.

Standing rules:
- Never guess or plug. Mark unsupported items VERIFY/HOLD and name the evidence needed.
- Source hierarchy:
  1. current invoices, statements and payroll;
  2. the latest correctly posted BC entries;
  3. company SOPs (MONTH-END MASTER HANDOVER, CONTROL TRACKER);
  4. prior working papers;
  5. generic BC guidance.
- Prior-month amounts are templates, not evidence.
- After Saeed posts anything, verify it in a fresh General Ledger Entries export.
- Monthly files live in Google Drive: `PLC > 2026-2027 > NN Month YY > Schedules / Journals`.
  Archive only the final correct journals, not corrections.
- Update the "Month status log" in the playbook at the end of each session.
