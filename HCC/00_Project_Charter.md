# Project Charter: Home Control SAP S/4HANA Implementation

**Status:** Closed / Transition to Support  
**Date:** January 9, 2026  
**Project Manager (Acloudear):** Man Li (Acloudear)  
**Project Manager (ISS Data):** Chakriya Phokintorn (assigned after kickoff meeting)  
**Project Code:** 1556

---

## Project Information

**Project Name:** Home Control (HC) SAP S/4HANA Public Cloud Implementation  
**Client:** Home Control (HC) / OmniDevices  
**Vendor:** Acloudear (Delivery) / ISS-Data (Prime Contractor)  
**System:** SAP S/4HANA Public Cloud  
**Project Status:** Closed / Transition to Support

---

## Project Scope

### Geographic Scope

**Overall Project Scope (ISS Data Implementation):**
- **Countries:** Singapore, China (2 entities), USA, Brazil, Belgium, Cayman Islands
- **Companies:**
  - Home Control Singapore Pte Ltd (Singapore)
  - HC (Suzhou) Limited (China) - **Acloudear scope**
  - Home Control Solutions (Suzhou) Limited (China) - **Acloudear scope**
  - Premium Home Control Solutions LLC (US) - **ISS scope**
  - Home Control Europe NV (Belgium) - **ISS scope**
  - Home Control International Limited (Cayman Island) - **ISS scope**
  - Omni Remote Do Brasil Ltda (Brazil) - **ISS scope**

**Acloudear's Limited Scope:**
- Implementation responsibilities limited to the **two China entities** only
- All other companies (Singapore, USA, Brazil, Belgium, Cayman Islands) are implemented by ISS Data

### Functional Modules Implemented

**Modules Implemented:**
- Finance (FICO)
- Sales (SD)
- Procurement (MM)
- Production (PP)

---

## Project Team

### Client Team (Home Control / OmniDevices)

**Executive Leadership:**
- **Rick Siu** - CEO / Executive Sponsor
- **Eunice Ng** - Group Financial Controller
- **Barry Cheng** - Global Operations Director
  - Focus: High-level deadlines and costs
  - Note: Frustrated by delays

**Project Management:**
- **Rocky Cai** - Project Manager (Operations)
  - Focus: Detail-oriented operations
  - Responsibility: Negotiated the "PPCA" scope and pricing logic
  - Responsibility: China operations

- **Minting Wang** - Project Manager (FICO & SEC)
  - Focus: Hands-on finance operations
  - Responsibility: Global sales and finance operations

**Function Managers / Key Users:**
- **Sally Jin** - Finance/Cash Management
- **Jianwei Shi** - FICO
- **Jelly Ding** - Purchasing / Key User / Module Lead
- **Nancy Zhang** - Supply Chain Management / Key User / Module Lead
- **Jane Chen** - Costing
- **Steyn Vantieghem** - BE10 External Accountant/PEPPOL
- **Rebecca Chan** - Group Reporting

**Key Users - Planner:**
- Sara Wang
- Irene Liu

**Key Users - Purchasing / Procurement:**
- Xiaodong Yu
- Cherry Qu
- Xiaoqin Zhuo
- Zhang Lin
- Deng Li

**Key Users - Supply Chain / Logistics / SIOP:**
- Ochoa Edith (US SCM)
- Enly Teng (Logistics)
- Jean Ong (SIOP)

### Vendor Team

**ISS-Data (Prime Contractor):**
- **Pohlim Koo** - Executive Sponsor
- **Alex Chua** - Consulting Director / Account Director / Vendor Lead
  - Focus: Contract adherence and client relationship
  - Note: Was Project Manager at kickoff; Chakriya Phokintorn assigned as PM after kickoff

- **Chakriya Phokintorn** - Project Manager (Prime)
  - Responsibility: Issue logs and user communication
  - Note: Assigned after kickoff meeting

**Acloudear (Delivery):**
- **Man Li** - Project Manager (Delivery)
  - Responsibility: Consultant team and technical execution

- **Tony Yang** - Development Lead
  - Responsibility: Development team leadership and technical development oversight

**Consultant Team (Acloudear):**
- **Frey Zheng** - FICO Consultant
- **Joe Wu** - PP Consultant
- **Moes Xu** - MM Consultant
- **Warner Yu** - SD Consultant

### Project Steering Committee

**Home Control:**
- Rick Siu (CEO)
- Eunice Ng (Group Financial Controller)
- Barry Cheng (Global Operations Director)
- Rocky Cai (Project Manager)
- Minting Wang (Project Manager)

**ISS Data:**
- Pohlim Koo (Executive Sponsor)
- Alex Chua (Project Manager at kickoff)

---

## High-Level Timeline & Milestones

### Project Phases

| Phase | Start Date | End Date | Duration |
|-------|-----------|----------|----------|
| **Discover** | - | - | Planning phase (no specific dates) |
| **Prepare** | June 6, 2025 | June 27, 2025 | ~3 weeks |
| **Explore** | June 30, 2025 | August 8, 2025 | ~6 weeks |
| **Realize** | August 11, 2025 | October 17, 2025 | ~10 weeks |
| **Deploy** | October 20, 2025 | November 30, 2025 | ~6 weeks |
| **Run** | December 1, 2025 | Ongoing | Support & operations |

**Total Implementation Duration:** June 6, 2025 - November 30, 2025 (approximately 5.5 months)

### Key Activities by Phase

- **Prepare**: Project Kickoff, Self-Enablement, Data Migration Plan
- **Explore**: Fit-to-Standard Workshops, Configuration Definition, Data Load Prep
- **Realize**: Solution Configuration, Data Migration, Testing (Unit, Integration, UAT), End User Learning
- **Deploy**: Production Cutover, System Go-Live, Hypercare

**Source:** Project Kickoff (`01_Prepare/1.4_Project Kickoff_HomeControl ver1.0.md`)

---

## Project Objectives

### Omni Devices Key Objectives

1. **Fit to standard** based on best practices
2. **Complete the project** with minimal impact to business operations
3. **Leverage new S/4 HANA functionalities** which will drive business efficiencies
4. **Leverage Fiori Apps** which will improve user experience
5. **Train the users** and manage change effectively

### Implementation Objectives

1. Implement SAP S/4HANA Public Cloud for Home Control
2. Cover core business processes: Finance, Sales, Procurement, and Production
3. Ensure successful go-live and transition to support

### Business Process Improvement Requirements

Potential changes & improvements to make with S/4 HANA (within current implemented modules):
- Monitoring Supplier inventory status
- Real time information for sales planning
- Improve forecast planning
- Automatic SO based on sales contract
- A tracked workflow for purchasing info record
- Scrap monitoring during the production process
- BoM comparison for R&D Purpose
- Freight cost allocation by product/region/customer
- Automate invoice validation and data capture
- Master data creation process
- Integration with third party system

---

## Key Deliverables

- SAP S/4HANA Public Cloud system configured and live
- Organization structure setup in S4HC Solution
- User training materials and documentation
- Data migration completed
- Test plan and standard test scenarios
- Cutover schedule
- Acceptance Protocol
- System stabilized and transitioned to support

## Integration Points

- **SAP DRC <-> Peppol Service Provider**: Bi-directional (Invoice data/E-Invoice details)
- **Product <-> Smart Operations Systems (SOS)**: Unidirectional (SOS queries new products from SAP)
- **SAP SAC <-> SAC**: Unidirectional (Standard Live connection)

## Critical Success Factors

- **Stay within the agreed scope**: Scope changes impact timeline and costs
- **Have a pragmatic mindset**: Adjust processes to fit standard functionality; it doesn't have to be perfect initially
- **Make quick decisions**: Enables the project to proceed in the right direction
- **Involve stakeholders early**: Executives, employees, key customers
- **As a key user, actively contribute**: Represent your business area well and secure availability
- **Start preparing data early**: Prevent project issues and delays
- **Never cut corners on testing**: Essential for a successful go-live and stable system

---

**Document Version:** 2.0  
**Last Updated:** January 9, 2026  
**Prepared By:** Project Management Office  
**Source Documents:**
- Project Kickoff: `01_Prepare/1.4_Project Kickoff_HomeControl ver1.0.md`
- Project Plan: `01_Prepare/1.3_Project_Plan_Simplified.md`
