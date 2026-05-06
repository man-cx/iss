# Plan: AMS Contract Review — Acloudear AMS for ISS V1.0

**Date:** 2026-05-06  
**Topic:** Legal & Commercial Review of Draft AMS Contract  
**Source:** `docs/draft/Acloudear AMS for ISS V1.0.docx`

---

## Objective

Review the draft Application Management Services (AMS) contract from Acloudear to ISS, identify legal/commercial risks, and propose amendments before sharing with ISS.

---

## Document Summary

| Item | Detail |
|------|--------|
| **Service** | Level-1 (1st line) + Level-2 (2nd line) SAP S4HC support |
| **Duration** | June 1, 2026 – May 31, 2027 (12 months) |
| **Volume** | 3 man-days/month = 36 man-days total |
| **Price** | $19,800 + 6% tax = $20,988 USD |
| **Overrun Rate** | $550/man-day |
| **Payment** | Quarterly in advance, $5,247/quarter |
| **Payment Term** | 10 days net from invoice date |

---

## 1. Critical Issues — Must Fix Before Signing

### 1.1 Section 8.1 — Unlimited Indemnification (NEW CLAUSE)

> "SAP Cloud Service Provider shall indemnify, defend and hold harmless Customer, its officers, employees, agents, representatives, consultants, and contractors from and against any and all loss, costs, penalties, fines, damages, claims, expenses or liabilities arising out of..."

**Risk:** This clause is **not present in the signed SOW** (SOW V2.4 FINAL has no indemnification section at all). It creates **unlimited, uncapped liability** for Acloudear covering ISS's officers, employees, agents, etc. This is commercially unacceptable and contradicts Section 8.2's cap.

**Recommendation:** **Strike Section 8.1 in its entirety.** The AMS contract should mirror the liability structure of the original SOW, which contains only a mutual liability cap (Section 8 of SOW).

---

### 1.2 Section 8.2 — Liability Cap Is Undermined

> "If the Customer proves that the loss of the Customer exceeds the above expenses due to the actions of the SAP CLOUD service provider, the customer reserves the right to claim."

**Risk:** While the first part of 8.2 raises the cap from **1x** (original SOW) to **3x** fees paid, this final sentence effectively **removes the cap entirely** by allowing the customer to "reserve the right to claim" beyond the cap. This contradicts the purpose of a limitation of liability clause.

**Recommendation:**  
- Negotiate whether to keep 1x (aligned with SOW) or agree to 3x.  
- **Strike the final sentence** ("If the Customer proves that the loss...reserves the right to claim").

---

### 1.3 Term "Customer" Is Ambiguous Throughout

The draft uses "Customer" inconsistently. Per the header: **"CUSTOMER"** is defined as Home Control Singapore Pte. Ltd. But many clauses appear to address ISS (the contracting party), not Home Control.

Specific examples:
- Section 6.1: "not use subcontractors without prior written approval from **CUSTOMER**" — approval should come from **ISS**, not Home Control.
- Section 8.2: "If the **Customer** proves that the loss..." — which customer?
- Payment terms: "monthly service sheet signed by the **customer**" — ISS or Home Control?

**Recommendation:** Insert a clear definition at the top:
- **"Client"** = ISS DATA PTE. LTD. (the contracting party)
- **"End Customer"** = Home Control Singapore Pte. Ltd.
Replace all ambiguous "Customer" references accordingly.

---

### 1.4 Currency Inconsistency in Pricing Table

The pricing table header says **"Service Price (in EUR)"** but all amounts show **USD**. This creates ambiguity about the payment currency.

**Recommendation:** Change header to **"Service Price (in USD)"**.

---

## 2. High Severity Issues

### 2.1 Termination for Convenience (Section 2.2)

> "Consulting Services may be terminated by either party in writing, with 2 weeks notice."

**Issue:** The original SOW states termination is "by mutual agreement" only. This draft allows unilateral termination. Two weeks is very short — Acloudear would need to demobilize resources with almost no transition time.

**Recommendation:**  
- Require **4 weeks notice** minimum.  
- Add a transition assistance clause (Acloudear will provide reasonable transition support during the notice period, billable at the daily rate).

---

### 2.2 Overrun Rate ($550/man-day) Not Aligned with SOW

The SOW rates are $650 (PM) and $550 (consultants). The AMS draft proposes **$550/man-day flat** for overrun. This is the consultant rate but does not account for PM-level work.

**Recommendation:** Either (a) align with SOW tiered rates, or (b) explicitly state AMS rate is a blended rate of $550 applicable to all roles.

---

### 2.3 Payment Term: 10 Days Net Is Aggressive

The original SOW did not specify a payment term. 10 days from invoice is tight, especially for international wire transfers to China (BANK OF CHINA).

**Recommendation:** Propose **30 days net** as industry standard for international contracts.

---

### 2.4 Quarterly Period Typo

> "1 Dec **2027** -- 28 Feb 2027"

Year is wrong — should be **2026**.

**Recommendation:** Correct to "1 Dec 2026 -- 28 Feb 2027".

---

### 2.5 Monthly Service Sheet — Who Signs?

> "The consulting services will be provided based on a monthly service sheet signed by the customer."

**Issue:** If "customer" means Home Control, this introduces a dependency on the end customer for payment verification. If ISS, it's fine.

**Recommendation:** Clarify: ISS signs the monthly service sheet. Home Control approval is not a prerequisite for Acloudear's invoice to ISS.

---

## 3. Medium Severity Issues

### 3.1 Warranty Period Extended (Section 3.2)

Extended from **30 days** (original SOW) to **40 days**. Claims period similarly extended (Section 3.3).

**Recommendation:** Minor change only. Either accept 40 days or push back to 30 days to align with SOW. Accepting 40 days is reasonable since AMS is longer-term engagement.

### 3.2 SLA "Deemed Acceptance" — Ambiguous and One-Sided

> "If the proposal is proposed for full 7 days and the client does not give verification conclusion to the proposal, it is deemed that the client has accepted the proposal and the status will be changed to be closed."

**Issue:** This is favorable to Acloudear but may be unacceptable to ISS. Also, the SLA table mixes "time to respond," "time suggested in first proposal," and "close time" — the terminology is confusing.

**Recommendation:** Clarify SLA terminology (Response Time, Resolution Target, Closure) using standard ITIL definitions. The 7-day deemed acceptance may be retained as a negotiation point but should be flagged to ISS.

### 3.3 Key Contact Person Fields Blank

Multiple placeholders empty: Contact Person 1, Contact Person 2, Maintenance Service Delivery Manager, Customer Account Manager.

**Recommendation:** Fill before sending to ISS.

### 3.4 Support Email

Uses `support@acloudear.com`. Ensure this mailbox is set up and monitored before contract starts.

**Recommendation:** Verify operational readiness.

### 3.5 No Reference to Existing SOW or CRs

The draft does not reference the existing SOW (V2.4 FINAL) or the signed P005/P006 Change Request ($28,514). The AMS contract should clarify:
- What is covered under AMS vs. what is covered under SOW warranty (SOW Section 3.2: 30-day warranty).
- P005/P006 have their own warranty obligations under the signed CR.

**Recommendation:** Add a "Relationship to Existing Agreements" clause stating this AMS supplements but does not replace the SOW or signed CRs.

---

## 4. Deemed Acceptance (Section 4.3) — Alignment Check

Section 4.3 mirrors the original SOW (10 business days, 10 days live operation). No issues — this is consistent.

---

## 5. Recommended Next Steps

1. **Discuss** the above issues. Confirm which amendments Acloudear is willing to make.
2. **Red-line** the contract with agreed amendments.
3. **Internal review** of red-lined version.
4. **Share with ISS** for their review.
5. **Negotiate and sign** before June 1, 2026.

---

## 6. Quick Reference: Changes from Original SOW

| Clause | Original SOW (V2.4) | AMS Draft V1.0 | Severity |
|--------|---------------------|----------------|----------|
| Indemnification | Not present | **Unlimited** (Section 8.1) | Critical |
| Liability Cap | 1x fees paid | 3x fees paid + **uncapped tail** | Critical |
| Termination | Mutual agreement only | Unilateral, 2 weeks notice | High |
| Warranty Period | 30 days | 40 days | Medium |
| Payment Term | Not specified | 10 days net | High |
| Overrun Rate | N/A (not in SOW) | $550 flat | High |
| Non-Solicitation | 2 years, 3x penalty | Same | OK |
| Dispute Resolution | HKIAC | HKIAC | OK |

---

*This review is for internal Acloudear purposes. Legal counsel should confirm all interpretations before finalizing.*
