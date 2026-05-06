# ADR: Record — Janarthanan Ramamoorthy on SAP BTP and related services (Golden Tax / Peppol)

## Status

Accepted (record of correspondence; not a new technical design choice by this repo alone).

## Context

ISS **Janarthanan Ramamoorthy** (Senior SAP Consultant) exchanged email on **SAP BTP** usage for **Golden Tax** and related work, including **subaccounts**, **global account roles**, **Business Application Studio (BAS)**, and (in a later thread) a **BTP subaccount** used by the **test** system. This ADR pulls **only his messages** into one place so delivery and commercial discussions can cite a single internal record.

## Record (what we are capturing)

ISS field contact **Janarthanan** described how **BTP** was being used and how access should be set up: separate concerns for **Peppol integration** vs **Golden Tax development**, who gets **admin** on the Golden Tax subaccount for **audit and handover after go-live**, and that a subaccount was understood as **not production** but still **used by test** when asking whether it could be removed.

## Evidence — messages from Janarthanan (extracted)

Sources are saved under `handover/sources/` and summarized in `handover/` notes; quotes below are plain-text extracts.

### A) Test tenant / Golden Tax BTP access — **24 Oct 2025**

**Thread:** `handover/20260420-170104-PDM-test-tenant-access-application.md`  
**Source file:** `handover/sources/20260420-170104-PDM-test-tenant-access-application/re-test-tenant-access-application.eml`

Times below are taken from **Janarthanan’s message metadata inside that `.eml`** (`Date: 2025-10-24 …` or Chinese `发送时间: 2025年10月24日 …`). They read as **local wall-clock** (same zone as the Outlook export; the top-level mail `Date` is **Fri, 24 Oct 2025 22:05:41 +0800** for Tony’s reply).

1. **2025-10-24 14:15** — Access troubleshooting (global roles):

   > Hi Coco,  
   >  
   > The Global account admin and viewer role is already included you. Can you please share the screen what do you see after login  
   >  
   > Regards,  
   > Janarthanan Ramamoorthy  

2. **2025-10-24 14:54** — BTP subaccount for Peppol vs new subaccount for development:

   > Hi Coco,  
   >  
   > This one is **BTP Sub account created by me for peppole integration**. For your development you can create the new subaccount using create button on top right corner.  
   >  
   > May I ask you what development are you going to do using the BTP?  
   >  
   > Regards,  
   > Janarthanan Ramamoorthy  

3. **2025-10-24 15:23** — Golden Tax subaccount admins (audit / handover):

   > Hi Coco,  
   >  
   > You may go ahead and create sub account for golden tax and please include **Minting**, **Rocky** and **me** as admin to control the subaccount. The admin access help to audit, handover and control the subaccount after golive.  
   >  
   > Regards,  
   > Janarthanan Ramamoorthy  

4. **2025-10-24 20:03** — Acknowledgement of Coco’s update (Chinese header: `2025年10月24日 20:03`):

   > Noted @coco.wang Thanks  
   >  
   > Regards,  
   > Janarthanan Ramamoorthy  

### B) Integration Suite / Application Studio / subaccount — **17 Apr 2026**

**Thread:** `handover/20260417-144950-PDM-integration-suite-app-studio-extra-charge.md`  
**Source file:** `handover/sources/20260417-144950-PDM-integration-suite-app-studio-extra-charge/re-urgent-integration-suite-and-application-studio-extra-charge.eml`

**How to read the dates in this file (important):**

- The **outer** message in the saved `.eml` is from **Chakriya**, not Janarthanan. Header: **`Date: Fri, 17 Apr 2026 04:40:21 +0000`** (same instant as **17 Apr 2026 12:40 +0800**).
- **Janarthanan** does **not** have his own `Date:` header in that outer part; his words appear **quoted** inside **Man Li’s** reply. That reply says **`Sent: 17 April 2026 10:07 AM`** and introduces Janarthanan with the Apple Mail line **`On 17 Apr 2026, at 09:59, Janarthanan Ramamoorthy wrote:`** — use **that** as the time of Janarthanan’s message in this thread (timezone not spelled out in the quote line; Man’s `Sent` is the next line in the same block).

5. **17 Apr 2026, 09:59** (cited in thread as above; immediately followed by Man Li **`Sent: 17 April 2026 10:07 AM`** to Janarthanan) — Test vs production and whether a subaccount can be removed:

   > Hi Man,  
   >  
   > This is subaccount is not deployed into production, It is still used by test system. So can we remove it?  
   >  
   > Regards  
   > Janarthanan Ramamoorthy  

## Consequences

- **Delivery:** Treat **BTP subaccounts** as explicitly separated in discussion: **Peppol-related** subaccount (per Janarthanan) vs **Golden Tax** work, with **BAS** called out by Acloudear in the same thread as in the handover note.
- **Governance:** Golden Tax–related subaccount **admin** expectation was stated: **Minting**, **Rocky**, **Janarthanan** for audit and handover after go-live (same thread).
- **Cost / lifecycle:** The **17 Apr 2026** thread (see evidence B) records ISS asking whether a **non-production** subaccount still used by **test** can be **removed** — relevant when reconciling **integration suite / BAS** charges and environment strategy.

## Related documents

- `handover/20260420-170104-PDM-test-tenant-access-application.md`
- `handover/20260417-144950-PDM-integration-suite-app-studio-extra-charge.md`
