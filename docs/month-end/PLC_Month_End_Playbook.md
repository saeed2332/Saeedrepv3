# Alliance Surgical PLC – Monthly Close Playbook (Business Central)

How Claude runs the PLC month end with Saeed every month: the order of work, how to talk Saeed
through each step, which Business Central (BC) reports to request (with click-by-click
instructions), the journal formats that BC accepts, and the lessons learned from the July,
August and September 2026 closes.

Source material this playbook is built on:
- `MONTH-END MASTER HANDOVER.docx` and `MONTH-END CONTROL TRACKER.xlsx` (company SOPs).
- `CC_SOPs__Handovers.xlsx` (original FC notes: recharges, Bupa, VAT, payroll).
- The August 2026 close conversation (ChatGPT share "PLC AUG26") and the September 2026 close
  with Claude.
- The August 2026 archive in Google Drive: `PLC > 2026-2027 > 05 August 26 > Schedules / Journals`.
- Microsoft Learn documentation for Business Central (links at the end).

Entities: **PLC** (Alliance Surgical PLC) first, then **ASCH** (Corporate Health) and **PMI**
(Alliance Health PMI). Financial year April–March. P01 = April … P06 = September.

---

## 1. How to work with Saeed (communication rules)

These come directly from Saeed's feedback. Follow them every time.

1. **One topic at a time, in the order in section 2.** Open each topic by saying in one or two
   lines what we're doing and what I need. Finish with a clear "done → next is X". Saeed moves
   on with "done, next".
2. **Assume Saeed does not know BC.** Every report request gives the exact BC page name
   (search with `Alt+Q`), every filter value in BC filter syntax, which columns must be visible,
   how to export, and a suggested file name. Never just say "export the G/L".
3. **Ask for all the reports needed for a topic up front**, not one at a time over several
   turns. Saeed found it frustrating to be asked repeatedly.
4. **Deliver journals in the exact BC format the first time** (section 5), as a spreadsheet,
   ready to paste or publish. Saeed should never have to ask "in this format" twice. Say exactly
   which cell range to copy, which BC journal or batch to paste into, and which column to start
   in.
5. **Corrections: give a corrected file, not "post the mistake and then an adjustment"**, unless
   the wrong entry is already posted. If it is posted, give only the reversing or delta lines.
   For example, the £70 TMD fix in August: Saeed wanted just the £70, not the whole journal again.
6. **Never guess or plug.** Unsupported amounts are VERIFY/HOLD, listed with the evidence
   needed. A prior month's amount is a template, not evidence.
7. **Check what was posted.** After Saeed posts, ask for a fresh G/L export and confirm the
   posting: document number, accounts, amounts, VAT, dimensions and dates.
8. **Own mistakes plainly.** If an earlier statement was wrong, say so and give the corrected
   position.
9. **Keep it concise and fast.** Short answers, one action at a time, no long explanations unless asked. Every reply ends with a short **Open items** list carrying forward unresolved topics, so nothing is dropped when we move on.
   (Previous wording: **Keep it concise.**) Use tables for amounts and short numbered steps for BC actions. Don't
   explain close mechanics unless asked.
10. **When Saeed lacks access** (Handelsbanken, Lloyds), draft a short Teams message to Jay.
11. **Archive at the end of each entity's close.** Save the final correct schedules and journals
    to the Drive month folder. Leave out corrections, undo journals and wrong versions.

12. **Batch mode (from October 2026, Saeed's instruction): all three companies at once.**
    Saeed has made me the final decision maker. Each month:
    1. Ask once for the **whole-year G/L Entries export for PLC, ASCH and PMI**
       (Posting Date 01/04/YYYY..end of next month).
    2. **Review the ledger before preparing any journal.** Run a month-by-month matrix of every
       P&L account and add my proposed journals to the current month. Every account should look
       like prior months. Any difference must be explained, or else accrued, prepaid,
       capitalised or reclassed. Check: recurring invoices missing this month, invoices posted
       next month with a VAT date in this month, one-offs posted to rent or expense, BC
       auto-deferrals spreading past-period costs, rent coded to expense instead of 35300
       (IFRS16), new fixed-asset additions, and duplicate or wrong-sign bank journals.
    3. Deliver one journal pack per company (`<CO>_<Month>_<YYYY>_Journals_TO_POST.xlsx`, with
       a "0 Post in this order" tab, BC-format tabs and a Decisions tab) plus **one request list**
       for everything still needed (reports, invoices, questions for Neil).
    4. Rule from August: if an accrual has been posted every month, keep it and review it
       later. One-offs need evidence.

Standard opening for a new month:
> "We're closing PLC <Month YY> (P0X). Step 1 is X. To start I need: [report list with BC
> steps]. While you pull those, I'll roll forward last month's schedules from Drive."

---

## 2. PLC monthly flow (order of work)

WD = working day (WD0 = first working day after month end). Each step lists what I request,
what I produce, and the checks.

### Step 0 – Set up and housekeeping (throughout / WD-1 / WD0)
- **Housekeeping (SOP Overview):**
  - Post trade invoices from the finance inbox.
  - Check the Gus posting runs and the bank postings.
  - Back up the bank statements: export all transactions across all accounts and entities to
    `Bank > Year > Month` (Handelsbanken: Transactions → Download → all companies, CSV, show
    balance; Barclays: Export Balances and Transactions → date range → CSV transactions → all
    accounts).
  - Review and approve the weekly payment run.
- **Drive:** create `NN Month YY` under `PLC > 2026-2027` with `Schedules` and `Journals`
  subfolders, matching the August layout. Download last month's archive, which is the template.
- **Request:** the PLC General Ledger Entries export (R1) for the month so far.
- **Produce:** a Close Index workbook (Status / Recharges / Issues & Decisions tabs).
- **Reversal check:** list every RV journal that reversed on the 1st (accruals, bonuses, Medven,
  interest, invoice accrual, prepayments). Each one must be replaced by a month-end journal or
  explicitly released. Until then the month's P&L is unusable: staff costs show credits,
  interest goes negative, and depreciation and non-recoverable VAT show £0.

### Step 1 – Gus backlog: unposted invoices
Gus syncs invoices into BC through the API, but some land as **unposted** Sales or Purchase
Invoices. Revenue or cost stuck there distorts the month and the invoice accrual.
- **Request:** R2 (unposted Sales Invoices and Purchase Invoices lists), plus R3 (Gus unposted
  invoice status export) if available.
- **Check:** each purchase invoice must have its matching sales invoice. **Pair them on External Document No.** (sale and purchase carry the same reference, sometimes with a trailing '.'), not on dates, because the VAT dates can differ. The company does not
  take on cost without a sale. Look for duplicates and VAT-date errors.
- **Matching workbook (SOP General 1.04):** put the four exports on four tabs and add these
  VLOOKUP columns:
  - On the sales tab: Duplicate (ext. doc. further down the list), On PI, On Customer Ledger
    Entries.
  - On the purchase tab: Duplicate, On SI, On Vendor Ledger Entries.
  - Mark each problem line "Y" when cleared; post only those.
- **Common causes:**
  - Duplicate invoice no.: check Gus treatment dates, patient and values. If the invoices are
    genuinely separate, add "." to the reference. IPRS invoices are split, so duplicates there
    are usually fine.
  - Sale without a purchase (or the reverse): ask Michelle to repost in Gus, then credit the
    orphan.
  - VAT date outside the allowed range: check the date. If it's correct, temporarily open the
    VAT period, then close it again.
- **Talk Saeed through:** **Post Batch** (B5), one posting date at a time with the Work Date set
  to that date. Leave Replace Posting/Document/VAT Date **off**. Never re-date invoices to today.

### Step 2 – Intercompany recharges (WD0)
| Customer | Copy from (latest clean posted invoice) | Lines | Notes |
|---|---|---|---|
| ACS | last month's ACS management recharge | 70100 £60,000 + Bupa (61600) for Marie Lee, Kaye Drew, Matthew Parks | No VAT. Next free ext. ref ACSnnn |
| AMI | last month's rates/Bupa invoice | 66100 rates £4,200 (VERIFY vs 11th-floor bill) + Bupa NE/JG/SD/JM | No VAT. Ext AMI188 |
| TMD | last month's Money Doctors invoice | 61600 Bupa (Christopher & Olivia Smith) | No VAT. Ext AS172 |
| ACS + AMI | last month's "50% of Mike's retainer" invoices | 65500, 50/50 of Mike Davies' (Hood Street) retainer + expenses from his latest invoice | **20% VAT**. Ext MD-ACS-nnn / MD-AMI-nnn |
| **The Money Doctors** (TMD001, raised in **ASCH**) | SI000042 (fixed) | 66500 Telephones £120 + 66175 Property Service Charges £500 | 20% VAT (£744). Ext `MON YY`. Billed to TMD, **not PLC**; TMD pays by BACS quoting the SI number. |
| PLC (raised in **ASCH**) | SI000043 (call charges) | 66500 = all CTALK purchase invoices posted in ASCH that month, less £120. One-off CTALK items go on a separate line (as in SI000039). | 20% VAT. Ext `MONYY`. PLC copies PI026791. Never accrue these: raise the SI dated the month end. |
- **Bupa first:** post the Bupa purchase invoice (deferral to 23200) or, if it hasn't arrived,
  accrue the premium (Step 3). Bupa renews in Sep/Oct, so check the Group Invoice Detail for new
  per-person prices.
- **Bupa 2026/27 renewal (from 01/10/26, invoice D23044361, issued 08/10/26):**
  - The invoice covers Oct + Nov 2026: £7,162.58 gross, collected 07/11. That's
    £3,581.29/month, up from £2,548.06 (+41%).
  - New monthly recharges (gross ÷ 2):
    - ACS: Kaye Drew £538.53, Marie Lee £462.94, Matthew Parks £75.62.
    - AMI: NE (Nathan Edwards) £183.60, JG (Josh Green) £183.60, SD (Suzanne Dunleavy)
      £132.52, JM (Jamie Mcmahon) £223.01.
    - TMD/Money Doctors: Christopher Smith £132.10 + Olivia Smith £175.08 = £307.18.
  - Bruce Braithwaite (ASCH contractor, couple, £462.94/m) is on the PLC scheme. Ask whether to
    recharge ASCH.
  - The September cover invoice is **D22935614** (issued 02/08, £2,548.06, DD 03/09). Post it
    dated 30/09 with no deferral; F1 releases the Sep accrual.
  - Bupa issues each invoice about a month ahead of its cover month (issue date in M−1). Renewal
    pattern: no invoice in September; the first renewal invoice covers Oct + Nov, then monthly
    from 01/12 at £3,581.29. The annual 2026/27 cost is £42,975.48. No DD in October.
- **BC:** Copy Document (B7) with **Include Header ON, Recalculate Lines OFF**.
- **Check:** confirm all of them in a fresh G/L export (amount, VAT, dates, ext. ref).
- **Budget check:** compare the recharges with the management-accounts budget. The Sep 26
  budget assumes PLC→ACS £61.5k plus a £1.5k ASCH charge (group net £60k); confirm whether it
  went live.
- **Known:**
  - ASCH June fixed charge to TMD: SI000037 was credited (SC000007), but TMD's 19/08 payment of
    £1,488 quotes SI000037. TMD has paid £4,464 against £3,720 of live invoices, a £744 credit.
    Re-raise June to TMD if its customer ledger shows the credit.
  - Recalculate Lines ON created £12k VAT on the £60k ACS recharge (Aug).
  - Sep SI028129 reused ext ref ACS095. No action is needed, because the invoice number is the
    unique reference.

### Step 2b – Credit card postings (WD1)
- **Check:** the credit card journals (nh crcd / kf crcd, GJ batches) for the month are posted,
  coded correctly and complete. Watch the VAT on foreign-currency/software charges and any
  intercompany items, which feed the intercompany check. Late card postings are a common
  cause of intercompany differences.

### Step 3 – General accruals (34100)
- **Roll forward:** `P0X_ACCRUALS_PREPAYS_<Month>_2026` (sheets Accruals New / Accruals JNL /
  Close Control). In Accruals New, column AH-type cells hold the month's charge, invoice columns
  hold invoices received, and the month balance = b/f + charge + invoices.
- **Invoice review:** list every overhead purchase invoice entered this month and the previous
  two. Any recurring supplier with no invoice this month gets an accrual at the latest actual.
  Items found so far: Interactive Development, Healthcode click fees, PTX/Bottomline, Mid
  Market, registration fees, Porsche storage, Stella cleaning, ASCH telephone, the £500
  retainer, TMD payroll fee and Bupa. Release accruals that have been invoiced. Static balances
  get flagged VERIFY.
- **Accrual audit (every month, all three companies, before the journal):**
  1. On the TB, the accruals account (PLC 34100, ASCH/PMI 34200) must be nil before this month's
     journal, because every line is RV. Any residue is a non-reversing journal that was never
     released.
  2. For every line, find the supplier's invoices wherever they post (e.g. Time managers
     invoices go to 66300, not the 65850 accrual line). Knock off each invoice by the **service
     month in its description**, not its posting date.
  3. A line that is the same amount every month never hits the P&L. With no invoice for 3+
     months it is a stale balance: release it unless there's a contract or invoice.
  4. Back-dated suppliers (Interactive Development, Healthcode, Medven): their invoice is dated
     the month end it covers. Check for a 30th/31st-dated posting before posting the journal.
- **Request:** R1 G/L export (latest) and R6 Purchase Invoices posted next month but dated this
  month (late invoices).
- **HOLD items:** bonuses + NI, Medven/PSP £20k/month, Class 1A. Never in the journal without
  evidence. (Aug: RGJ000208 £143,663 was posted anyway, so decide each month.)
- **Second pass (SOP 1.09):** after the variance analysis vs budget/forecast (Step 13), add
  any accruals the variances reveal (missing invoices) in a version 2 before the final TB.
- **Output:** BC journal, ACCRUALS batch, `RV Reversing Variable` / `1M`, doc `ACC<Mon><YY>`,
  balancing line 34100 (format F1).

### Step 4 – Prepayments (23100 manual vs 23200 automatic)
- **23200 = BC automatic deferrals** (Deferral Code on purchase invoices). Never also put these
  on the manual schedule.
- **Completeness check (SOP 1.08):** in `Vendor Ledger Entries`, filter Posting Date = the
  month (and the Trade posting group). Scan for annual or quarterly invoices with no deferral
  and add them to the manual schedule.
- **23100 = manual schedule.** Add new invoices that cover future periods with no deferral, and
  release expired lines.
- **Output:** PREPAYMENT batch in the **exact BC format F2** (Line No. … External Document No.).
  Saeed asked that this format always be used for PLC prepayments.

### Step 5 – Accrued fixed-deposit interest (24100 / 80100)
- Roll the `PLC_Accrued_Interest_<Month>_2026` schedule forward one column. Post the cumulative
  accrual RV/1M, doc `INT<Mon><YY>`.
- Stop accruing at maturity. The £1m and £2m 6M deposits mature **24/10/2026**, so get renewal
  terms. Make sure interest actually received isn't double counted.

### Step 6 – ROU printers (64300/14020 dep, 80250/35300 interest)
- **Lease calendar – check every month:**
  - PLC Apogee printers: 12 quarters from 23/05/2025; the final depreciation month is May 2028. Set the **Expiration Date** on the LEASE recurring-journal lines to 31/05/2028 so BC stops posting after that.
  - ASCH 10th floor Rear/Front: terminated (legal fee PI028104, period to 30/09/2026). Derecognise the ROU asset and liability at the termination date in the ASCH close.
  - ASCH new suites (304/310/312): assess as new leases.
- **Lease end checklist:** final depreciation month = asset fully depreciated; lease liability 35300 = 0 after the last rental; remove the lines from the batch; tidy any rounding.
- Take the month's column from the lease schedule, doc `LEASE<Mon><YY>`, V/1M (F1).
- **Apogee ImagePLAN printers:** £989.76/qtr rising 5% a year (£1,039.24 from 2026). The "Agreed Minimum Quarterly Charge" line on Apogee invoices is the lease rental. Post it Dr 35300 (no deferral, never 63100). Support and print charges go to 63100.

### Step 7 – Fixed assets (13030 cost / 13040 acc dep / 64200 dep)
- **Request:** R10 PLC fixed asset register (not in Drive yet), new capital invoices, and the
  capitalisation threshold.
- **Low-value IT peripherals** (keyboards, mice, headsets, cables): expense them to IT costs and don't capitalise. Decided Oct 2026 for £426 of keyboards and mice. The formal threshold is still to be confirmed from the FA register or accounting policy.
- **Output:** depreciation journal F1, doc `DEP<Mon><YY>`. Reconcile the register to 13030/13040.

### Step 8 – Payroll and pension (RGJ payroll batch) – do this early, ahead of the accruals
- **People's Partnership pension direct debit:** the bank posts it to **61500 expense**, but the
  payroll journal already expenses the employer pension and credits 33700. Each DD pays the
  previous month's 33700 liability, so reclass it Dr 33700 / Cr 61500 (General Journal) every
  month until the bank posting rule is changed to 33700. Jul GJ000492 was the first fix.
- **Request:** R11 payroll report / `Alliance Payroll Journal Template - <MON><YY>`.
- **Payroll provider file (SOP 1.02):** ignore the N/C column (legacy system) and the
  provider's directors/staff split. Some people related to Neil aren't officially directors.
  Directors' salaries are fixed and the same as last month unless the payroll payment
  approval shows a change. Staff = total wages − directors. Click into each Account No. to
  check the mapping before posting.
- **PMI:** one employee, no split. After posting, PMI staff costs for the month + the £50 TMD
  fee = the PMI→AMI recharge.
- **Template check:** in `Alliance Payroll Journal Template - <MON><YY>.xlsx`, cell A6/M6 on tab 1 drives the posting date, doc no. and description. Make sure it is the 1st of the payroll month (Sep 26 was left at 01/08).
- **Mapping:** 61100 directors, 61200 staff, 61400 er NI, 61500 er pension, 33200 net wages,
  33400 PAYE/NI/student loan, 33700 pension, 25300 loans, 33250 unpaid/sick. Doc
  `PAY<MON><YY>`, F1.

### Step 9 – Non-recoverable VAT (67100 / 32500) and VAT returns
- **VAT return calendar (SOP VAT Returns):** PLC quarters end Mar/Jun/Sep/Dec and are submitted
  Apr/Jul/Oct/Jan (VAT no. GB861242246). ASCH quarters end Feb/May/Aug/Nov and are submitted
  Mar/Jun/Sep/Dec. **PLC Q/E Sep 26 is due in October; confirm ASCH Q/E Aug 26 was submitted in
  September.**
- **Return workflow:**
  1. VAT Return Periods → Get Return Periods.
  2. VAT Statements → template VAT Return → Preview (Open entries, Before and Within Period,
     date = quarter end) → Open in Excel.
  3. VAT Entries, view "Current Return", VAT date to quarter end → Excel.
  4. Reconcile boxes 1–9 and the input/output VAT G/L (Review Entries).
  5. Calculate partial exemption (PLC only).
  6. Submit, then Calculate and Post VAT Settlement.
- **Monthly:** the approved forecast figure (ask for it). Never reuse £4,397.22.
- **Quarter end** (Jun, Sep, Dec, Mar): partial-exemption true-up from R12, then the VAT return
  workflow.

### Step 10 – Invoice accrual (accrued income 24100 / accrued cost 34300)
Purpose: pull fund income (51xxx) and cost (52xxx) that belong to the month but were posted
after it. Run it **after** the Gus posting runs (Aug was exported 14/09).
- **Request:**
  - R4 G/L Entries, saved view "Invoice Accrual (Month-end)": Posting Date `<1st next month>..`,
    VAT Date `..<month end>`. In this BC setup VAT Date stands in for Document Date.
  - R3 Gus cut-off review export.
- **Build:**
  - Replace the raw G/L tab and rebuild the unique dimension combinations (G/L account +
    5 dimensions).
  - Check = 0.
  - Check that every cost line has a sale.
  - Gus statuses: ReadyToBePosted = accrue candidate; WaitingApproval = HOLD unless the service
    is confirmed; accrue both sides, never cost only.
- **Output:** the ACCINC batch RV/1M, doc `INVACC<MON><YY>`, with **all five dimensions**
  (Department, Costcentre, Type, Treatment group, Treatment code).
- **Posting method:** paste **directly into the BC journal grid** (B9) using format F3. Edit in
  Excel only exposes two dimensions unless the Designer fields `ShortcutDimCode3-5` are added.

### Step 11 – Fund receipts and Fund Control (37050)
- **Request:** R13 fund bank statements (AWG / Mitie / Rolls-Royce on Barclays) and the open
  fund debtors.
- **Output:** Cash Receipt Journal, batch **DUMMY** (the batch name goes in the header, not in
  the lines). Paste starting at **Posting Date** (format F4). Apply each receipt to its fund
  sales invoice.
- **Then:** G/L account 37050 → Review Entries → Hide Reviewed Entries. Mark the pairs that
  net to zero as reviewed. The remaining Fund Control balance must equal and oppose open fund
  debtors.

### Step 12 – Balance-sheet reconciliations
- **Request:** R5 Customer Trial Balance + Aged AR; R7 Vendor Trial Balance + Aged AP; R8 Bank
  Account Ledger Entries + statements; R14 Detail Trial Balance; R15 the unposted-journals
  check.
- **BC bank reconciliation (SOP 1.10):**
  1. Search Bank Reconciliation → New → choose the account; set the statement date and ending
     balance.
  2. Bank → Import bank statement (Barclays CSV transactions; Handelsbanken CSV with one
     amount column, signs negated).
  3. Match: Match Automatically, then Match Manually (1-to-many is fine, many-to-many isn't);
     Remove Match fixes mistakes.
  4. Transfer to General Journal for unposted bank lines, then Post.
  - Full BC rec works for Handelsbanken current, Barclays MTA, ASCH current, PMI Handelsbanken
    and PMI Barclays premium. Not possible for HB EUR (currency), the Barclays DD account (too
    many-to-many) or the Deposit account (no statements).
  - Also update the "Monthly bank and intercompany check" workbook (balance per bank vs per
    BC; intercompany per entity).
- **Banks:** Handelsbanken current 21100, Handelsbanken EUR 21125, Lloyds 21150, Barclays MTA
  21300, Deposit 21400. Saeed has Barclays access; Handelsbanken and Lloyds come from Jay
  (draft the Teams message).
- **Intercompany:** equal and opposite by counterparty. Name every difference, no plugs. July
  open difference: ~£18,335.30.

### Step 13 – Management accounts
- **Request:** R16 Financial Reports MGMT ACS (PLC/ASCH/PMI), OVERHEADS, M-FUND P&L, and the
  "In network postings" analysis.
- **Build (SOP 2.1–2.5):** roll the prior final workbook, recolour the tabs yellow and set the
  month in Data input & checks B2. Run the Financial Reports per entity: Refresh → check the
  checks at the bottom → export using the layout → paste to the blue tab. Re-run all of an
  entity's reports after any adjustment. Paste only the current month for FUNDP&L. Analysis
  view = G/L Entries "In network postings" → analysis mode → pivot G/L Name / Department
  Code / Type Code. Enter the intercompany debtor/creditor balances from the customer/vendor
  reports. All Data input & checks cells must be OK, and each entity's net profit must equal
  its in-month TB net profit.
- **Distribution:** PDF by WD5 to Neil, Ann and Adam with an email summary, forwarded to
  Michael Davis.
- **Build:** roll the prior final workbook. Paste raw exports to the source tabs only, skipping
  the extra G/L Budget Filter row. Write CEO/CFO commentary.
- **PDF:** check every page for overflow and cut-off headings or commentary (Aug: pages 3,
  14–17 needed fixing).
- **Workbook QC before use (fix once, then check every month):**
  - Combined P&L Analysis: the CoS budget total must be `E23 = SUM(E18:E22)`, with `C23 = E23`
    and `F23 = B23 - E23`. In Aug a wrong total showed GP £93.8k favourable when it was £13.7k
    adverse.
  - Funds Overview (Rolls-Royce): each month must point at its own source column. Aug repeated
    July's data (£278.6k vs £264.1k income).
  - Overhead review: variance = Budget − Actual and Forecast − Actual (month and YTD), always as
    formulas, never hardcoded.
  - Balance sheets (PMI, PLC, ASCH): P&L Reserve B/F is the true brought-forward figure, and
    Current Year Profit is cumulative Apr–month and agrees to the FY P&L. In Aug the PLC
    balance sheet showed a £111.4k current-year loss against an Apr–Aug P&L loss of ~£49.2k.
- **Briefing for Neil (CFO) – prepare each month:**
  - **Headline vs underlying:** strip out one-offs before calling YTD "ahead of budget". The
    £75k ACS dividend sits in June Other Income, and deposit interest is ~£22k above budget YTD.
  - **Revenue variances:** split volume from margin. Did cost of sales fall with the activity?
  - **Fund margins (AWG, Mitie, Rolls-Royce):** drill into any fund below ~5% GP. In Aug,
    Rolls-Royce hospital work was ~£203.7k revenue against ~£203.2k cost.
  - **Consultancy and professional fees** vs budget (PLC consultancy £95.5k vs £36.4k YTD at Aug).
  - **Cash bridge for each entity:** profit, creditors, debtors, non-cash. For ASCH, cash falls
    as deferred income is released; for PMI, the client-fund cash isn't free cash.
  - **Known budget run-rate gaps** (ASCH admin fees £72.9k actual vs £77.9k budget each month)
    and **old one-off lines** (June Members Fees −£18.02k).
  - **PMI:** the monthly margin is distorted by run-off accrual corrections, so discuss YTD and
    net liabilities instead (−£421.2k net assets, mainly the £498.2k intercompany creditor).

### Step 14 – Archive and lock
- **Drive:** save the final schedules and journals (correct versions only) plus the Close Index
  in the month folder.
- **Lock:** after approval, set General Ledger Setup → Allow Posting From = 1st of the next
  month (B11). Check User Setup overrides.

Then repeat the relevant steps for **ASCH** and **PMI** (PMI reconciliation / BDX / STRIPE
batch, PMI payroll → AMI staff recharge).

**ASCH recurring checks:**
- **Deferred income:** RR admin fee and AWG Healthy U. The August journals reverse on the 1st, so
  post the new month's deferral from the schedules, otherwise revenue is overstated.
- **Accrual reversals:** match each one to an invoice or re-accrue only what is still
  outstanding (electricity, vehicle insurance, property insurance, Azure…).
- **Depreciation and ROU:** fixtures, office equipment, ROU, lease interest and the £6.825k MDM
  asset.
- **Bruce Braithwaite:** his monthly invoice (£2,735.33) is coded 65550 Consultancy, so reclass
  it to 61525 Contractor.
- **Rent invoices:** check for refundable deposits (e.g. Suite 304/312), which belong on the
  balance sheet, not in P&L.

**PMI:** September needs the BDX/commission journals, Stripe journal, supplier accruals,
payroll and the cyber-insurance prepayment. The August broker commission (£58,456.67) and
admin-fee (£10,100) accruals have reversed. Kindred, Rapid Quote and app-support accruals have
also reversed and need checking. Correct August items through the current month; don't reopen
an issued pack.

---

## 3. Report request cookbook (copy these instructions to Saeed)

General BC tips to include when relevant:
- **Search:** press `Alt+Q` and type the page or report name.
- **Company:** check top-left that the company is **Alliance Surgical PLC** before every export.
- **Filters:** click the funnel icon (Filter pane) → `+ Filter` → choose the field → type the
  value. Ranges: `01/09/2026..30/09/2026`; up to: `..30/09/2026`; from: `01/10/2026..`
- **Show a column:** ⚙ (Settings) → Personalise → `+ Field` → drag in → Done.
- **List pages:** export via `Share` (or `⋯`) → **Open in Excel**.
- **Reports:** on the request page choose **Send to… → Microsoft Excel Document**.

| # | What | BC page / report | Filters & settings | File name |
|---|---|---|---|---|
| R1 | G/L entries for the month | `General Ledger Entries` | Posting Date `01/MM/YYYY..` (to latest). Columns: Posting Date, VAT Date, Document Type, Document No., G/L Account No., Description, Amount, Debit, Credit, Bal. Account, External Document No., User ID, Department Code, Costcentre Code, Type Code, Treatment group Code, Treatment code Code. Open in Excel | `PLC_<Mon>_GL.xlsx` |
| R2 | Unposted Gus invoices | `Sales Invoices` and `Purchase Invoices` (unposted lists) | No filter, or Posting Date `..<month end>`. Show Posting Date, VAT Date, External Document No., Amount. Open in Excel. Also export `Customer Ledger Entries` and `Vendor Ledger Entries` for the month for matching | `PLC_<Mon>_Unposted_SI.xlsx` / `_PI.xlsx` |
| R3 | Gus cut-off status | Gus (not BC): unposted / status report | Statuses ReadyToBePosted, WaitingApproval, AwaitingBankDetails with invoice, payment and recharge totals and service dates | `Gus_<Mon>_status.xlsx` |
| R4 | Invoice accrual source | `General Ledger Entries` → saved view **Invoice Accrual (Month-end)** | Posting Date `01/<next month>..`; VAT Date `..<month end>`. Include G/L Account Name, VAT Amount and all 5 dimension columns. Export after the Gus posting runs | `PLC_<Mon>_InvoiceAccrual_GL.xlsx` |
| R5 | Debtors | `Customer Trial Balance`; `Aged Accounts Receivable` | CTB: Date Filter `..<month end>`, LCY. Aged AR: Aged as of `<month end>`, Aging by Posting Date, Period Length 1M, Print Details Yes, LCY Yes. Send to Excel | `PLC_<Mon>_Customer_TB.xlsx`, `_Aged_AR.xlsx` |
| R6 | Late purchase invoices | `Vendor Ledger Entries` | Posting Date `01/<next month>..`, Document Type Invoice. Show Document Date / VAT Date, External Document No., Description, Amount. Open in Excel | `PLC_<Mon>_Late_PI.xlsx` |
| R7 | Creditors | `Vendor Trial Balance`; `Aged Accounts Payable` | Same settings as R5 | `PLC_<Mon>_Vendor_TB.xlsx`, `_Aged_AP.xlsx` |
| R8 | Banks | `Bank Account Ledger Entries` + bank statements | Posting Date `..<month end>`, show Bank Account No. Statements to month end for every PLC account (Barclays: Saeed; Handelsbanken/Lloyds: ask Jay) | `PLC_<Mon>_Bank_Ledger.xlsx` |
| R9 | Deferrals | `Purchasing Deferral Summary` (report) | Date to `<month end>`. Send to Excel | `PLC_<Mon>_Deferral_Summary.xlsx` |
| R10 | Fixed assets | PLC fixed asset register (Excel) + capital invoices | Last month's rolled register | — |
| R11 | Payroll | Payroll report / journal template from provider | Month | `Alliance Payroll Journal Template - <MON><YY>.xlsx` |
| R12 | VAT (quarter end) | `VAT Returns` → Get Return Periods; `VAT Statement` Preview; `VAT Entries` | VAT Date in quarter; Open VAT entries; Before and Within Period | — |
| R13 | Fund receipts | Barclays fund accounts (AWG, Mitie, Rolls-Royce) statements | Month | — |
| R14 | Trial balance | `Detail Trial Balance` or `Trial Balance` | Date Filter `<month start>..<month end>` | `PLC_<Mon>_TB.xlsx` |
| R15 | Unposted journals check | `General Journals`, `Recurring General Journals`, `Payment Journals`, `Cash Receipt Journals` | Look for any line dated ≤ month end. Screenshot; don't delete or post | — |
| R16 | Management accounts | `Financial Reports` → MGMT ACS / OVERHEADS / M-FUND P&L | Date Filter `<month start>..<month end>`; G/L Budget Filter as prior final month; Refresh; export unchanged | — |

---

## 4. BC how-to reference (talk-through snippets)

- **B1 Find anything:** `Alt+Q`, type the name, open it.
- **B2 Switch company:** ⚙ → My Settings → Company (or the company name top-left).
- **B3 Work Date:** ⚙ → My Settings → Work Date. Set it temporarily for Post Batch; reset it
  afterwards.
- **B4 Filters:** Filter pane → `+ Filter`. `..` means up to, `x..` means from. Use `|` for OR
  (`21100|21300`).
- **B5 Post Batch (unposted invoices):**
  1. In `Sales Invoices` (then `Purchase Invoices`), filter to one Posting Date and select those
     invoices.
  2. Choose Posting → **Post Batch**. Leave Replace Posting Date / Replace Document Date /
     Replace VAT Date OFF.
  3. Set the Work Date to that posting date first, because BC refuses if they differ.
  4. Afterwards check the **Error Message Register** for failures.
- **B6 Preview before posting:** on a journal or document use **Preview Posting**. Check
  accounts, VAT, dimensions and balance = 0.
- **B7 Copy a recharge invoice:** `Sales Invoices` → New → enter Customer → Prepare → **Copy
  Document**:
  1. Document Type = Posted Invoice; choose the last clean invoice.
  2. Include Header **ON**, Recalculate Lines **OFF**.
  3. Update Posting/Document/VAT/Due dates, descriptions (month) and the External Document No.
  4. Preview Posting → Post.
  5. Print/Send → **Send by Email**.
- **B8 Deferral on a purchase invoice:** if the Deferral Code column is hidden, Personalise the
  lines → `+ Field` Deferral Code. Pick the code → Deferral Schedule → start = 1st of the period
  → Recalculate. Check the total = amount to defer.
- **B9 Paste a journal into BC** (preferred for large or multi-dimension journals):
  1. `Recurring General Journals` → choose the Batch (ACCRUALS, PREPAYMENT, ACCINC, payroll…).
  2. Make sure the visible column order matches the spreadsheet: Personalise if needed, and
     start at **Recurring Method**.
  3. Clear old template lines: click in the grid → `Ctrl+A` → `Ctrl+Delete`. This deletes the
     lines, not the batch.
  4. Copy the data range from the spreadsheet (no headers).
  5. Click the first blank **Recurring Method** cell → `Ctrl+V`. BC assigns line numbers itself.
  6. Check balance = 0, spot-check dimensions, Preview Posting, Post.
- **B10 Edit in Excel → Publish** (for formats with Line No.):
  1. In the journal: Share → **Edit in Excel**.
  2. Paste the rows, keeping amount cells **numeric**. `#####` or text amounts give "Cannot
     convert a value to target type Edm.Decimal".
  3. Click Publish. If some rows fail, republish **only** the failed rows.
  4. Duplicate Document No. errors: change the Document No.
  5. Extra dimension fields can be added via the Excel add-in **Design** → edit the table → add
     `ShortcutDimCode3/4/5` in blank columns at the end.
- **B11 Lock the month:** `General Ledger Setup` → Allow Posting From = 1st of the next month.
  `User Setup` can override per user, so check it.
- **B12 Recurring methods:**
  - `RV Reversing Variable` = posts and auto-reverses the next day; the amount clears after
    posting. Use it for accruals, prepayments, interest and invoice accrual.
  - `V Variable` = posts without reversal; use it for payroll, depreciation, ROU, non-rec VAT.
  - After posting, the batch's dates roll forward by the frequency (1M). Always overwrite dates,
    Document No. and month descriptions, because BC can roll a 30-day month to the 30th instead
    of the 31st.
- **B13 Fund Control review:** `Chart of Accounts` → 37050 → **Review Entries** → Hide Reviewed
  Entries → select pairs netting to 0 → Set Selected as Reviewed.

---

## 5. Journal formats that work in BC (deliver exactly these)

**F1 – Recurring General Journal paste** (accruals, payroll, depreciation, ROU, interest,
non-rec VAT). Columns A–W:
`Recurring Method | Recurring Frequency | Posting Date | VAT Date | Document Type | Document No. |
Account Type | Account No. | Description | Gen. Posting Type | Gen. Bus. Posting Group |
Gen. Prod. Posting Group | Amount | Amount (LCY) | Debit Amount | Credit Amount |
Allocated Amt. (LCY) | Expiration Date | Department Code | Costcentre Code | Type Code |
Treatment group Code | Treatment code Code`
Paste from Recurring Method. Include a Control tab with the journal balance (0), the posted
register reference and the batch name.

**F2 – PLC prepayment EXACT BC format** (Edit in Excel layout, 47 columns A–AU):
`Line No. | Journal Batch Name (PREPAYMENT) | Journal Template Name (RECURRING) | Recurring
Method | Recurring Frequency | Posting Date | VAT Date | Document Date | Document Type |
Document No. | Account Type | Account No. | Depreciation Book Code | FA Posting Type |
Description | Business Unit Code | Salespers./Purch. Code | Campaign No. | Currency Code |
Gen. Posting Type | Gen. Bus. Posting Group | Gen. Prod. Posting Group | VAT Bus. Posting Group |
VAT Prod. Posting Group | Amount | Amount (LCY) | Debit Amount | Credit Amount | VAT Amount |
VAT Difference | Payment Terms Code | Applies-to Doc. Type | Applies-to Doc. No. | Applies-to ID |
On Hold | Bank Payment Type | Reason Code | Allocated Amt. (LCY) | Bill-to/Pay-to No. |
Ship-to/Order Address Code | Expiration Date | Comment | Job Queue Status |
Shortcut Dimension 1 Code | Shortcut Dimension 2 Code | Reverse Date Calculation |
External Document No.`
Line numbers go in steps of 10000. The last line is 23100 Total prepayments.

**F3 – Invoice accrual** (ACCINC):
- Use F1 columns with all five dimensions populated, pasted directly into BC (B9). One
  24100/34300 pair plus the dimensional lines, built from the "Remove duplicates" combinations.
- If publishing via Excel instead, use the F2 layout plus `ShortcutDimCode3/4/5` columns.

**F4 – Cash receipt (fund receipts), batch DUMMY / template CASHRCPT:**
- Starts `Line No. | Journal Batch Name | Journal Template Name | Posting Date | VAT Date |
  Document Date | Document Type | Document No. | … | Account Type (Customer) | Account No. |
  Description | … | Amount (negative) | … | Bal. Account Type (G/L Account) | Bal. Account No.
  (37050) | … | Applies-to Doc. Type (Invoice) | Applies-to Doc. No. | … | Shortcut Dimension 1
  Code | Shortcut Dimension 2 Code`.
- When pasting into the BC grid, start at **Posting Date**, not Line No. or the batch.

**End of each close:** one workbook with every journal in its own tab, same format every month.

---

## 6. Lessons and pitfalls (don't repeat)

- **Recharges:** Copy Document with Recalculate Lines ON added £12k VAT to the ACS £60k
  recharge.
- **Paste alignment:** a column-shifted paste in June mis-coded 13 expense lines and the
  balancing account. Always check the BC column order matches.
- **Date roll:** recurring batches can roll to the 30th; descriptions and doc numbers don't
  update themselves.
- **HOLD items posted:** the August HOLD items were posted (RGJ000208 £143,663) despite the
  DO NOT POST control. Raise the decision explicitly each month.
- **Hood Street:** the Mike Davies recharge is 50/50 to ACS and AMI with VAT. The old £3,720
  monthly release (PI014931) is still running and is flagged VERIFY.
- **Duplicate reference:** the July ACS Hood Street invoice SI023221 was not corrected like
  the AMI one. ACS may have been overcharged £1,655.33 net.
- **Rates:** 2026/27 bills are on BC auto-deferral (PI025855–61), so no rates accrual is
  needed. The 11th floor is £3,800.25/month vs the £4,200 AMI recharge (VERIFY).
- **Printer lease:** the ROU schedule repays £990/quarter to 35300, but BC expenses the Apogee
  invoice to 63100. Possible double count.
- **Fund margin swings are mostly invoice-accrual cut-off timing.** The accrual only catches
  invoices in BC when R4 is exported, and anything posted later lands in the next month. Fund
  margins by service month (VAT date): RR Jul 2.0% / Aug 7.0% (reported 7.3% / 1.6%), AWG
  Jul 18% / Aug 18% (reported 2.5% / 17.3%), Mitie ~22%. Each month, before commenting on a fund
  margin, compare the reported margin with the service-month margin. Export R4 as late as
  possible, after the Gus backlog is posted.
- **Fund pricing:** RR hospital work is billed at about cost ÷ 0.95, so a structurally low
  margin (~5–7%) is expected. Physio uses the same mark-up, e.g. PI027016 £45.00 → SI027121
  £47.37.
- **Invoice accrual:** a big negative P&L impact can be correct: costs posted late against
  sales already recognised. Check the sale pairing before assuming an error.
- **Excel publish failures:** amounts stored as text or `#####` fail. Republish only the failed
  rows.
  - "Account No. cannot be found in G/L Account" means the sheet is linked to the wrong
    company. Open Edit in Excel from the batch in the right company.
  - "Direct Posting must be Yes" for PLC 23200: that account is BC's auto-deferral account.
    Manual journals use 23100.
- **Static accruals** (shredding, Pitney Bowes, corporate lead gen) need evidence or release.
  The 08/10 audit found invoiced months never knocked off (Time managers, ASCH property
  insurance, which BC deferral already covers) and lines with no invoice all year (lead gen,
  Shield HR, PMI Kindred advertising/Rapid Quote/app dev £18,706.80).
- **Uploads:** the Drive connector uploads small files reliably. For large workbooks (>25KB)
  ask Saeed to drag them into the folder.

---

## 7. Month status log

Update this at the end of each session.

### September 2026 (P06) – in progress (as of 08/10/2026)
- [x] Step 2 recharges: Hood Street POSTED 30/09 – SI028241 ACS / SI028242 AMI, £8,597.68 + £1,719.54 VAT each (1p over £17,195.35; ext refs reuse -002, no action). SI028129 ACS £60,753.78, SI028130 AMI £4,726.10, SI028131 TMD £221.67
  posted 30/09. **Hood Street recharge NOT yet raised** (ACS £8,597.67 / AMI £8,597.68 + 20%
  VAT).
- [ ] Step 3 accruals:
  - Draft £53,647.82, including the Bupa accrual £2,548.06.
  - To add: Healthcode £1,097.28, Stella £351.25, £500 retainer (VERIFY), ASCH telephone
    £2,915.27 (VERIFY).
  - Release the Direct IP £369.18 line (PTX invoiced).
  - Decide the HOLD items (bonuses/NI/Medven £168,234).
- [ ] Step 4 prepayments: draft £6,384.25. Add Grenke £96; franking £194.90 VERIFY.
- [ ] Step 5 interest INTSEP26 £44,694.24 cumulative and Step 6 ROU LEASESEP26: drafted.
- [ ] Steps 7–14 outstanding: FA register needed; payroll report needed; VAT Q2 true-up; invoice
  accrual after the Gus runs.
- **External review items (ChatGPT, 05/10) – the agreed order is PLC payroll/pension → PLC
  recurring journals → ASCH deferrals/accruals → ASCH depreciation/reclasses → PMI → management
  accounts workbook QC:**
  1. [ ] PLC pension DD reclass Aug £4,403.58 (GJ000501) and Sep £4,416.61 (GJ000520) to 33700.
     Journal drafted (PENSRECLAUG26/SEP26). Confirmed in the GL.
  1a. [ ] Pension reclass: Aug GJ000538 correct (31/08 £4,403.58). Sep GJ000539 short by £13.03, so post Dr 33700 / Cr 61500 £13.03 at 30/09. Detail: GJ000539 posted 30/09 for £4,403.58 (the Aug amount) with a 'Sep 26 (GJ000520)' description; the Sep DD was £4,416.61. Confirm whether the Aug-dated line was also posted (need the 33700/61500 GL from 01/08), then post the remainder (£13.03, or £4,416.61 if the Aug line wasn't posted).
  1b. [x] 05/10 17:21 GL: all 130 late-Sep Gus sales (£48,413.13) now have their purchase invoice posted in Sep (£43,178.47, 10.8% margin). Previous note: 132 Gus sales invoices posted 29–30/09 (£48.4k on 51xxx); only 17 lines matched a posted purchase. Check the unposted Purchase Invoices list and post the matching PIs (Sep dates).
  1c. [x] PI028104 £2,250 + VAT: a Shakespeare Martineau legal fee (inv 100375471, 30/09/26) for terminating the 10th floor lease, billed to PLC. 65650 Legal is correct; no correction.
      Knock-on effects to resolve:
      - Who was the tenant? The ROU schedule shows the 10th Floor Rear/Front as ASCH leases (to Dec 2026). If ASCH, decide whether to recharge the fee.
      - ASCH must derecognise the 10th-floor ROU asset and liability at the termination date.
      - The PLC 2026/27 10th-floor rates deferrals (PI024130 / PI024316) keep releasing to Mar 27, so a council rates adjustment is needed.
      - The new ASCH suites (Suite 310 £12,240; deposits for 304/312) may need a new ROU calculation.
  1d. [x] July ACS Hood Street overcharge SI023221: Saeed's decision 05/10 is to leave it; ACS can request a credit note. No action.
  1e. [ ] PLC printer lease: correction journal LEASEFIXSEP26 drafted (Dr 35300 £2,970.24 / Cr 63100 £2,310.24 / Cr 23200 £660, plus Oct/Nov offsets of £330). Ties 35300 to the schedule (£5,636.50) after LEASESEP26. The ROU schedule confirms the 10th floor Rear/Front are ASCH leases (to Dec 26).
      Also: the 33700 TB shows Apr–Jun pension DDs never reached 33700; get the 33700/61500 GL from 01/04/26. 35300 HOF £442.10 debit is a legacy hot-drinks lease balance to clear.
      Background: printer lease double count CONFIRMED. The Apogee ImagePLAN agreement (signed 23/05/25, 12 quarters, £989.76/qtr + VAT, 5% annual increase allowed) matches the ROU schedule. The "Agreed Minimum Quarterly Charge" £1,039.24 (= £989.76 × 1.05) is the lease rental, but BC defers it to 63100 expense (~£346.41/month) while the ROU also charges depreciation and interest, and 35300 is never reduced. Fix: reclass every minimum-charge posting since lease start to Dr 35300 / Cr 63100 (needs the 63100 + 35300 GL from 01/11/2025). Update the ROU schedule repayments to £1,039.24 from the increase date. Future invoices: code the minimum-charge line to 35300 with no deferral. Device Network Support (£750/qtr) stays in 63100.
  2. [x] PLC Sep payroll journal: CHECKED 05/10. The template had the date 01/08 (would have posted PAYROLLAUG26 at 31/08); corrected to 01/09. Balanced £132,804.29; net £79,163.14 agrees to the wages paid 30/09. PMI £3,478.45 → AMI recharge £3,528.45. POSTED RGJ000210 30/09, verified 05/10 (13 lines, all correct). Needs the Sep payroll report. Wages
     were paid 30/09 (£79,163.14, GJ000533).
  3. [ ] PLC recurring journals: accruals (incl. bonus/Medven decision), interest, non-rec VAT,
     depreciation, ROU, invoice accrual. Confirmed: Sep 61300 −£103,663; 80100 −£34,291; no
     64200/64300/67100 entries.
  4. [ ] ASCH RR/AWG deferred income (£83,758 RR and £59,050 AWG reversed 01/09).
  5. [ ] ASCH accrual reversals: electricity £7.7k, vehicle insurance £4.6k, property insurance
     ~£3.0k (Azure invoiced).
  6. [ ] ASCH Bruce Braithwaite PI000314 £2,735.33: Dr 61525 / Cr 65550.
  7. [ ] ASCH depreciation, ROU, lease interest and MDM asset.
  8. [ ] ASCH Suite 312 £1,848 and Suite 304 £3,696 deposits: move to balance sheet if
     refundable. Check the Suite 310 £12,240 invoice.
  9. [ ] PMI Sep journals (BDX/commission, Stripe, accruals, payroll, cyber prepayment).
  10. [ ] Management-accounts workbook formula fixes (Step 13 QC list), plus confirm whether
     the £61.5k/£1.5k recharge change is live.
- **Items from ChatGPT's first (August) review, missing from its second list:**
  11. [ ] ASCH Tax & Social Security control: £98.0k liability in Jun, £11.9k debit in Jul,
      £18.7k debit in Aug. Reconcile to the VAT, PAYE and NI controls; no balancing journal.
  12. [ ] ASCH static balances unchanged since April: £600k intercompany debtors, £300.2k Other
      Debtors, £320k Other Creditors. Need supporting schedules.
  13. [ ] ASCH AWG receivable ~£421.9k (£461,088 invoice less £39,202.80 credit), ~90% of
      ASCH trade debtors. Collection status for commentary.
  14. [ ] ASCH NH expense batch: £2.88k Pilates and AppleCare/iPhone in Other Staff Costs.
      Confirm business purpose. Mileage £6.446k was offset by a £5.216k reversal of an
      unsupported NH expense accrual.
  15. [ ] PLC trade debtors: the +£103k movement is mainly the AWG negative fund-control
      balance reducing, not customers owing more. Explain in commentary and the debtor rec.
  16. [ ] PLC reserves presentation: £111.4k current-year loss vs ~£49.2k Apr–Aug P&L (part of
      item 10). Fix the reporting rows for all three entities.
  17. [ ] Intercompany balances: ASCH creditor £814.9k, PMI creditor £498.2k. Reconcile each
      counterparty, continuing the July ~£18,335.30 difference.
  19. [x] RR 1.6% Aug margin TESTED (05/10). Invoices posted in Aug made 21.8%. The Aug
      accrual took £97.4k cost vs £46.5k income; 99.5% of costs match a sale. By service month
      RR made 7.0% in Aug and 2.0% in Jul, so £20–30k of July-dated cost landed in Aug after
      the July accrual export. A timing issue, not an error to correct. Jul+Aug combined ~4.5%.
  20. [ ] £75k ACS dividend (June Other Income) – VERIFY. Needs the June GL for the
      other-income account, the bank receipt and a dividend voucher or board minute from ACS.
      Make sure it isn't an intercompany settlement booked to income.
  21. [ ] ASCH cash vs deferred income – VERIFY. The release is normal, but check Aug: deferred
      income fell £98.7k = revenue. Confirm no new billing should have been added and that the
      schedule agrees to the G/L. Needs the ASCH GL plus the RR/AWG deferred income schedules.
  22. [ ] PMI client funds £136.9k vs client-fund creditors £85.5k – a £51.4k gap to
      reconcile. Client cash should equal client creditors plus amounts due to PMI. Needs the
      PMI Balance Reconciliation, plus the 35300/24500/35500 G/L.
  23. [ ] ASCH admin fees £72.9k/month vs £77.9k budget – VERIFY. Check whether a contract,
      price uplift or new client in the budget hasn't been invoiced or released. Needs the
      budget build for admin fees plus the admin-fee billing/deferral schedule by client.
  18. [ ] Prepare the briefing for Neil (Step 13): RR margin, the £75k one-off, AWG receivable,
      the ASCH tax debit, PMI net liabilities, the pension fix and the formula error.
- **07/10/2026 batch-mode update (all three companies, nothing for September posted yet):**
  - Reviewed the full-year G/Ls (exported 07/10).
  - Packs sent to Saeed in chat: `PLC_/ASCH_/PMI_September_2026_Journals_TO_POST.xlsx` and
    `September_2026_Requests_ALL_COMPANIES.xlsx`. The earlier Drive copies of the ASCH pack and
    request list are renamed SUPERSEDED; archive the finals after posting.
  - PLC accruals £224,813.75. Following the posted pattern, these include bonuses + NI
    £107,934, Medven £60k, Class 1A £300, Healthcode, Stella and the ASCH telephone recharge.
    Shredding and Direct IP are released.
  - PLC prepayments £6,480.25; interest £44,694.24; ROU £338.63; printer fix; pension top-up
    £13.03; depreciation £577.85.
  - ASCH findings:
    - PI000309 £17,784 is the Spaces deposit, coded to rent.
    - PI000308 £25,144 is the Mitie Sep25–Aug26 recon, being auto-deferred to Mar 27. Expense now.
    - PI000289 10th Front rent is coded to 66150, not 35300.
    - The £5,500 outreach invoice is missing for September (accrued).
    - DCA KND £403 not needed (invoice posted).
    - Laptop PI000313 capitalised.
    - MTE GB VGP income (£22.5k/m) ended in August: question for Neil.
    - The ASCH VAT return (Jun–Aug) was due 07/10.
  - ASCH projected September loss ~£16.8k.
  - PLC finding: 51300 has £9,100 of debits in September. GJ000542 (Barclays DD £5,460) may
    duplicate Medven PI028192 – bank statement needed.
  - PMI: STRIPE from the P06 recon, accruals, broker commission £64,590.76, cyber prepayment
    £359. Payroll and the AMI recharge wait for September payroll. Howden PI000107 £44,553.22
    is unpaid (payment reversed). Projected profit ~£4.2k (Aug £4.7k).
- **08/10/2026 accrual audit (all three companies):**
  - PLC 34100 is nil at 30/09 before the September journal (TB), so nothing is stuck. ASCH and
    PMI need their TBs to confirm.
  - PLC P1 is now £145,300.92 (was £161,898.48):
    - Time managers cut to £137.33 on 66300 (invoiced to August).
    - Pitney Bowes cut to £2,800 (the 01/04 DDs with no invoice).
    - Lead gen £11,000 and Shield HR £1,500 released.
    - Tab P1b is a delta if the old P1 was already posted.
  - ASCH A1 is now £26,989.19:
    - Property insurance £3,429.42 released (duplicate of the deferred landlord invoices).
    - PLC telephone accrued income removed (Saeed raising the SI copied from SI000043).
    - Vehicle insurance £5,071 kept, with a question to James.
  - PMI M3 £18,706.80 released and the tab removed. The historic 34200 £5,807 debit
    (GJ000155) is to be checked on the TB.
  - Also check on the TB: the ASCH 23200 AWG Portal prepayment, possibly released twice on
    01/04 (GJ000068 and GJ000069, £11,029.33).
  - Bonuses: the 2025/26 £65,500 + NI £11,016 is still unpaid six months on (no bonus in
    payroll). Neil to confirm.
- **Remind Saeed once everything is posted (he asked 08/10):**
  1. Medven Jul–Sep invoice is posted dated 30/09; otherwise PLC Sep shows a £40k credit.
  2. Interactive Development and Healthcode Sep invoices: none dated 30/09 on top of the
     accrual.
  3. Neil: is the 2025/26 bonus (£65.5k + NI) being paid?
  4. James: who insures the ASCH vehicles (£5,071)? Do the Pitney 01/04 DDs have invoices?
  5. ASCH and PMI TBs: PMI 34200 £5,807 debit; ASCH 23200 AWG Portal double release
     (£11,029.33).
  6. ASCH recharge invoices to PLC (copies of SI000042/43) and the PLC purchase side, dated
     30/09.
  7. Fresh G/Ls for all three to verify the postings. Then the invoice accrual, NRVAT and fund
     journals, the PMI payroll and AMI recharge, recs, and the MA.
  8. Drive: archive the final packs and schedules only.
- **08/10/2026 post-posting review (fresh G/Ls 20:43–20:47):**
  - All the original pack tabs are posted. P1, A1 and M3 went in as the pre-audit versions
    (RGJ000211, RGJ000175, RGJ000098). The deltas are in
    `September_2026_Fixes_after_posting_08Oct.xlsx`:
    - F1 PLC delta: £43,402.44, including the Medven £60k accrual (the invoice is still not
      posted).
    - F2 PLC fixes:
      - GJ000544 duplicated the ROU journal RGJ000217.
      - 35300 true-up of £442.10 to the schedule (£5,636.50).
      - Pension reclass of £8,859.10: the April and May contribution DDs had been expensed to
        61500.
    - F3 ASCH delta: property insurance plus the accrued income.
    - F4 PMI delta: £18,706.80.
  - Not yet raised: the ASCH Sep recharge SIs (copies of SI000042/43) and the PLC purchase
    side, plus the PMI→AMI recharge (copy of SI000015, £3,528.45).
  - (Corrected 09/10) The ASCH fixed £744/month invoices are billed to The Money Doctors, not
    PLC. There's no intercompany issue.
  - James changed GJ000542 into a receipt (GJ000543 credits 51300 £4,550). Ask whether the
    30/09 Barclays £5,460 was money in or out; if out, it should pay Medven PI028192.
  - ASCH PI000298 £2,303.97 is "Spaces (Northgate House, Bath)", a new cost from September.
    Ask what it is.
  - PLC 24100 carries £193.9k outside the month-end journals. Reconcile it in Step 12.
- **09/10/2026:**
  - ASCH SI000044 (Sep calls, £4,679.86) and SI000045 (Sep fixed, £744) are posted correctly.
  - PLC: Interactive Development PI028433 (INV100832, £5,460) was posted dated 30/09, so F1 now
    releases that accrual. F1 = £35,394.38, 34100 → £197,292.86.
  - Bupa D22935614 (Sep cover) is confirmed **not** in BC; the 03/09 DD is unapplied on the
    vendor.
- **Drive:** `PLC > 2026-2027 > 06 September 26`. Drafts uploaded except
  `P06_ACCRUALS_PREPAYS…` and `Right_of_Use_Assets…`, which Saeed is adding manually.

---

## 8. SOP coverage map (CC_SOPs__Handovers.xlsx → this playbook)

| SOP task (Overview tab) | SOP timing | Playbook step |
|---|---|---|
| General housekeeping (inbox invoices, Gus, bank postings, statement backup) | Throughout | Step 0, Step 1 |
| Interco recharges | WD0 | Step 2 |
| Non-recoverable VAT provision | WD0 | Step 9 |
| Fixed assets (capitalisation + depreciation) | WD1 | Step 7 |
| ROU depreciation + lease unwind | WD1 | Step 6 |
| Fund receipts | WD1 | Step 11 |
| Credit cards | WD1 | Step 2b |
| Accrued interest | WD1 | Step 5 |
| Intercompany balances | WD1 | Step 12 |
| Payroll postings | WD2 | Step 8 |
| Prepayments & accruals | WD3 | Steps 3–4 |
| Invoice accrual | WD4 | Step 10 |
| Management accounts + P&L review | WD4–WD5 | Step 13 |
| Balance-sheet reconciliations | WD6+ | Step 12 |
| Weekly payment run | Weekly | Step 0 |
| PLC / ASCH VAT returns | Quarterly | Step 9 |
| Kindred (BDX, arrears, PMI rec, broker commissions) | Monthly | PMI section |
| Audit, corporation tax, budget & forecast, fund budgets, P11Ds, ONS surveys | Annual / ad hoc | Out of the monthly flow; raise when due |

Where the SOP and the later handover disagree, the handover / latest posted BC wins. For
example, the SOP says directors' salaries are 61600, but the validated mapping is 61100.
The SOP's Logins tab holds passwords: never copy it into this repo or any output.

## Microsoft Learn references
- [Working with general journals (recurring journals, reversing methods)](https://learn.microsoft.com/en-us/dynamics365/business-central/ui-work-general-journals)
- [Post multiple documents at the same time (Post Batch)](https://learn.microsoft.com/en-us/dynamics365/business-central/ui-batch-posting)
- [Specify posting periods (Allow Posting From/To, User Setup)](https://learn.microsoft.com/en-us/dynamics365/business-central/finance-how-specify-posting-periods)
- [Viewing and editing in Excel from Business Central](https://learn.microsoft.com/en-us/dynamics365/business-central/across-work-with-excel)
- [Undo a posting using a reversing entry](https://learn.microsoft.com/en-us/dynamics365/business-central/finance-how-reverse-journal-posting)
- [Close accounting periods](https://learn.microsoft.com/en-us/dynamics365/business-central/year-close-account-periods)
