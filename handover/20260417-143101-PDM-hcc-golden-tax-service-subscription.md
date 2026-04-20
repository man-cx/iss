# Handover: HCC — Golden Tax service subscription (email thread)

## Source

- **Saved thread (repo):** [re-hcc-golden-tax-service-subscription.eml](sources/20260417-143101-PDM-hcc-golden-tax-service-subscription/re-hcc-golden-tax-service-subscription.eml) (copy of the mail file that was under `/Users/manli/Downloads/Re_ HCC - Golden Tax Service Subscription.eml`)
- **Subject:** Re: HCC - Golden Tax Service Subscription  
- **Latest message:** Wed, 3 Dec 2025 14:06:24 +0800 — Man Li (Acloudear) → Alex Chua (ISS), with Chakriya and Acloudear team on Cc.

## What this thread is about

Home Control (HCC) work uses a **Golden Tax** integration. That needs an **external service subscription** (annual, prepaid). There was also a **SAP BTP** line item: about **USD 6,506** for **SAP Integration Suite**, which ISS suspected was tied to Golden Tax.

## Timeline (short)

1. **11 Nov 2025** — Man asked Alex (ISS) to handle settlement; annual subscription invoice referenced. Alex asked **ISS Accounts** (`accounts@iss-data.com`) to process invoices.
2. **18 Nov 2025** — Man asked finance for **clear cost allocation**, whether **HCC** knew about the cost; mentioned **Rocky** had not been aware; service **live from 7 Nov 2025** for setup, training, test, and go-live; asked for payment so the project is not blocked.
3. **21 Nov 2025** — Alex stated the deal is **between Acloudear and ISS**; **ISS absorbs the cost** and **does not recharge Home Control**; all mail on this topic should go **to ISS only**, not the end customer.
4. **2 Dec 2025** — Alex asked Man to confirm whether a **USD 6,506** **Integration Suite** charge on **BTP** for HCC is **correct** and linked to Golden Tax.
5. **3 Dec 2025 (latest)** — Man replied: team had created an **extra Integration Suite tenant** for Golden Tax **production**, then agreed **one environment** is enough for **both test and production**, so the **extra tenant was removed**. Man’s technical team confirmed the **USD 6,506 will not be charged**.

## Current understanding (for whoever picks this up)

- **Commercial rule from ISS:** Costs for this arrangement sit with **ISS vs Acloudear**; **not** passed to **Home Control** as a recharge (per Alex, 21 Nov).
- **Technical / billing clarification:** The **6,506** figure was tied to a **second IS tenant** that is now **de-provisioned**; Man states it **should not be billed**.  
- **Still worth doing:** On the next **BTP / invoice** cycle, **check that the charge does not appear** (or is credited), so finance and the project stay aligned.

## People and channels (from the headers)

- **ISS:** Alex Chua, Chakriya Phokintorn, ISS Accounts  
- **Acloudear:** Man Li, Criss Zhuang, Shawn Huang, Tankler Wang, Weslin Lv, Tony Yang  

## Stakeholders (team registry)

For roles, see `registry/team-registry.md`.

- **ISS:** Alex Chua (company owner / project director), Chakriya (project manager)
- **Acloudear:** Tankler (company founder / project director), Man Li (project manager), Tony (chief technical director)

## Related repo item

- Ticket **TKT-001** (CPI / Golden Tax app cost) may overlap this topic; compare notes if you work that ticket.
