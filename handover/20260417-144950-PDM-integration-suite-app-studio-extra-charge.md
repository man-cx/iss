# Handover: Urgent — Integration Suite + Application Studio causing extra charge

## Source

- **Saved thread (repo):** [re-urgent-integration-suite-and-application-studio-extra-charge.eml](sources/20260417-144950-PDM-integration-suite-app-studio-extra-charge/re-urgent-integration-suite-and-application-studio-extra-charge.eml)
- **Subject:** Re: Urgent: integration suite and application stuido causing extra charge
- **From:** Chakriya Phokintorn (ISS)
- **Date:** Fri, 17 Apr 2026 (email header shows 04:40 UTC / 12:40 +0800)

## What happened (plain English)

Chakriya reported that **Home Control is already under BTPEA**, and the project is seeing **extra monthly charges** for:

- **SAP Integration Suite**
- **SAP Business Application Studio**

Chakriya asked why the services **cannot be deactivated now** and still **incur monthly charges**, when it was previously said the **USD 6,506** would not be charged (see attached prior email inside the thread).

Chakriya also said the charges have built up for about **5 months**, totaling **over SGD 30,000**, and asked to discuss:

- How to **stop** the recurring charges
- How the already-incurred costs should be **stopped or allocated**

## Key technical constraint (from Man Li’s reply inside the thread)

Man Li replied that, to optimize BTP licensing costs, the architecture was consolidated into **one subaccount** hosting:

- **Integration Suite (CPI)**
- **Business Application Studio**

for **both Test and Production**. If that subaccount is deactivated/removed, it would **bring down the live Production Golden Tax integration**.

## Stakeholders (team registry)

For roles, see `registry/team-registry.md`.

- **ISS:** Alex Chua, Chakriya
- **Acloudear:** Tankler, Man Li, Tony

## Suggested next steps

- Confirm exactly which BTP subaccount(s) are generating the monthly charges (thread mentions “Home Control TEST”).
- Confirm whether there is a safe way to reduce cost without impacting production Golden Tax.
- Align on who pays for the accumulated cost (mentioned: **SGD 30,000+**).

