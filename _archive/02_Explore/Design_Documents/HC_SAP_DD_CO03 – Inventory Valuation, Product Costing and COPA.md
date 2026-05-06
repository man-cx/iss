**FICO Inventory Valuation, Product Costing and COPA**

**FICO 存货计价，产品成本核算与成本效益分析**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: CO_DD_003 Inventory Valuation, Product Costing and COPA**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

       Frey Zheng               FICO Lead               08/20/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Jane Chen           Finance - Costing       

     Minting Wang              Finance            

      Sally Jin                Finance            

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [5](#design-document-approval-options)](#design-document-approval-options)

[2. Inventory Valuation, Product Costing and COPA [5](#inventory-valuation-product-costing-and-copa)](#inventory-valuation-product-costing-and-copa)

[2.1 Purpose [5](#purpose)](#purpose)

[2.2 Business Reason [5](#business-reason)](#business-reason)

[2.3 Business Benefits [6](#business-benefits)](#business-benefits)

[3. Process Scope Design [6](#process-scope-design)](#process-scope-design)

[3.1 Master Data [6](#master-data)](#master-data)

[3.1.1 Cost component structure [6](#cost-component-structure)](#cost-component-structure)

[3.1.2 Costing variance [6](#costing-variance)](#costing-variance)

[3.1.3 Costing sheet [7](#costing-sheet)](#costing-sheet)

[3.1.4 List of COPA characteristic [7](#list-of-copa-characteristic)](#list-of-copa-characteristic)

[3.1.5 List of COPA value field [9](#list-of-copa-value-field)](#list-of-copa-value-field)

[3.2 Inventory Valuation [10](#inventory-valuation)](#inventory-valuation)

[3.3 Product Costing [10](#product-costing)](#product-costing)

[3.3.1 Business Process Steps [11](#business-process-steps)](#business-process-steps)

[3.4 Profitability Analysis [11](#profitability-analysis)](#profitability-analysis)

[3.5 HC Functional Requirements [12](#hc-functional-requirements)](#hc-functional-requirements)

[3.6 HC Delegation Of Authority [13](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.7 Standard Documents / Settings [13](#standard-documents-settings)](#standard-documents-settings)

[3.8 Design Considerations / Key Assumptions [13](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.9 Cross Functional Integration Dependencies [13](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[3.10 Support / Closing Considerations [13](#support-closing-considerations)](#support-closing-considerations)

[4. Authorization Roles [13](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [13](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [14](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [14](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [14](#reports)](#reports)

[6.1.1 Standard Reports [14](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [14](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [14](#interfaces)](#interfaces)

[6.3 Conversions [15](#conversions)](#conversions)

[6.4 Enhancements [15](#enhancements)](#enhancements)

[6.5 Forms [15](#forms)](#forms)

[6.6 Workflows [16](#workflows)](#workflows)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       08/11/2025

                                                              

                                                              
  ------------- --------------------------------------------- --------------------

# Guidelines {#guidelines .LS_Heading-1}

## Design Document Approval Overview {#design-document-approval-overview .LS_Heading-3}

The SAP Implementation Project Design Documents are the result of the Fit / Gap workshops.  All Project Design Documents must be reviewed and approved by the Home Control team to confirm we have captured the appropriate requirements as well as gaps, proposed solutions, and RICEFW objects​ from the workshops.

SAP Design Documents are living, breathing documents. As the SAP system is configured, tested, modified, and approved, the design documents may be updated to reflect the final design​.

Answerthink Team Leads create the original design documents​. Should Home Control decide to update the Design Documents, it is up to Home Control to perform the updates.

As we leave the Explore stage and enter the Realize stage, we ask for approval but understand that there may be open decisions or uncertainty in some areas.  Therefore, we provide the following approval options.

## Design Document Approval Options​ {#design-document-approval-options .LS_Heading-3}

> [Sign-Off Without Reservation​]{.underline}

- No issues or concerns​ at this point

> [Sign-Off with Reservation​]{.underline}

- Minor issues or concerns (3-5) that need to be finalized during Realize stage.

- Place Reservation(s) on the Issues Log, assign owner and due date, manage​ issue/concern.

> [Withhold Sign-Off - Major Decisions Unresolved​]{.underline}

- Major design issues that need to be resolved in order to move forward in Realize stage (e.g., Iprojects vs. Project Systems​)

- Place on the Issues Log, assign owner and due date, manage​ issue

- Complete Key Design Decision document and escalate (PMO then Executive Sponsor)

If you have any items that may withhold signature it is your responsibility to escalate as soon as possible

#  Inventory Valuation, Product Costing and COPA {#inventory-valuation-product-costing-and-copa .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

Product Cost Planning refers to the creation of standard cost estimates for materials with standard price control. The standard cost is used for inventory valuation, to calculate the costs of goods manufactured for each product. Home Control use the standard costing method for all materials include component and finished goods.

CO-PA (Profitability Analysis) provides a powerful tool for on-line analysis of the profitability of various segments of the business. CO-PA enables to evaluate market segments, which can be classified according to products, customers or any combination of these, with respect to company\'s profit or contribution margin. The aim of CO-PA in SAP is to provide the sales, marketing, and product management / corporate planning departments with information that will support their decision-making and to assess the business performance in a chosen market segment and to compare results.

## Business Reason {#business-reason .LS_Heading-3}

- Update standard costs for products as part of annual operations planning.

- Manage material valuations

- View and analyze the material inventory values from various perspectives

- Analyze profit for different dimensions such as products, sales divisions

## Business Benefits {#business-benefits .LS_Heading-3}

- Calculate standard costs annually to reflect the changes in prices of purchased parts, labor and overhead costs, and bills of materials and operations needed to manufacture semi-finished and finished goods

- Gain more insight into the profitability of market segments (product, customer, customer orders, projects) or strategic business units (sales organizations, business areas) with respect to your company\'s profit or contribution margin

# Process Scope Design {#process-scope-design .LS_Heading-1}

## Master Data {#master-data .LS_Heading-3}

## Cost component structure {#cost-component-structure .LS_Heading-3}

The Cost Component Structure defines how the various primary and secondary cost elements are grouped

The following structure will be used for Home Control Group

+----------------+---------------------+----------------------------------+
| Cost Component | Description         | GL accounts                      |
+================+=====================+==================================+
| 1              | Material            | 7700000 - 7709999                |
|                |                     |                                  |
|                |                     | 7820000 - 7829999                |
|                |                     |                                  |
|                |                     | 7889200 - 7889900                |
+----------------+---------------------+----------------------------------+
| 2              | Labor               | 7732100                          |
+----------------+---------------------+----------------------------------+
| 3              | Overhead            | 5706000 - 5706000                |
+----------------+---------------------+----------------------------------+

## Costing variance {#costing-variance .LS_Heading-3}

The Costing Variant is the main structure in Controlling- Product Costing that controls the way a product is costed in the system e.g. the way BOM are selected; valuation strategy etc.

Home Control will use costing variance SG2 with the following detail set up

+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Costing type & Costing date | Costing run will update standard price of component/ finished goods.                                                                                        |
|                             |                                                                                                                                                             |
|                             | Default costing date from will be first date of next month.                                                                                                 |
|                             |                                                                                                                                                             |
|                             | Default costing date to will be last date of next month                                                                                                     |
|                             |                                                                                                                                                             |
|                             | *For example*: If users execute costing on 20.11.2015, default costing valid from will be 01.12.2015                                                        |
|                             |                                                                                                                                                             |
|                             | Default costing date to will be 31.12.2015                                                                                                                  |
+=============================+=============================================================================================================================================================+
| Valuation variant           | [Component (Material):]{.underline}                                                                                                                         |
|                             |                                                                                                                                                             |
|                             | Standard price of materials will use effective price from purchase Infor record.                                                                            |
|                             |                                                                                                                                                             |
|                             | Note that in purchasing process, price in PIR is updated price from vendor. This price will be updated to purchase order and schedule line agreement (VSA). |
|                             |                                                                                                                                                             |
|                             | [Labor:]{.underline}                                                                                                                                        |
|                             |                                                                                                                                                             |
|                             | Labor cost is subcontract services fee.                                                                                                                     |
|                             |                                                                                                                                                             |
|                             | [Overhead:]{.underline}                                                                                                                                     |
|                             |                                                                                                                                                             |
|                             | Factory overhead is defined for each finished good. A fixed percentage will be assigned for each FG. Home Control will use the following overhead rate.     |
|                             |                                                                                                                                                             |
|                             |   ----------------------------------------------------------------                                                                                          |
|                             |   **Overhead Group**   **Description**            **Rate**                                                                                                  |
|                             |   -------------------- -------------------------- ----------------                                                                                          |
|                             |   SG21D                SG21 HC OEM Remote         2.71%                                                                                                     |
|                             |                                                                                                                                                             |
|                             |   SG21N                SG21 HC Touch Screen       19.47%                                                                                                    |
|                             |                                                                                                                                                             |
|                             |   SG21X                SG21 HC Universal Remote   19.39%                                                                                                    |
|                             |   ----------------------------------------------------------------                                                                                          |
+-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

## Costing sheet {#costing-sheet .LS_Heading-3}

Overhead costs are costs which can only indirectly be attributed to the product. At Home Control, we will allocate these overhead cost by using costing sheet.

Costing sheet of Home Control will be ZHCSG -- Home Control Singapore. It includes:

- Calculation base for overhead:

> The calculation base determines which cost elements should have overhead applied.
>
> At Home Control, overhead will be calculated based on:
>
> 7700111: Materials consumed materials sub.contr
>
> 7732100: Subcontr.work thirds items

- Overhead rate

  -------------------------------------------------------------------------------------
  **Valid from**   **Valid To**       **Controlling Area**   **OVH group**     **Rate**
  ---------------- ------------------ ---------------------- --------------- ----------
  01.01.2010       31.12.9999         HC01                   SG21N               19.47%

  01.01.2010       31.12.9999         HC01                   SG21X               19.39%

  31.08.2024       31.12.9999         HC01                   SG21D                2.71%
  -------------------------------------------------------------------------------------

## List of COPA characteristic {#list-of-copa-characteristic .LS_Heading-3}

+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| **Characteristics** | **Description**         | **Data Element**  | **Check Table**   | **Remark**                               |
+=====================+=========================+===================+===================+==========================================+
| **FIXED CHARACTERISTICS**                                                             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| ARTNR               | Product                 | ARTNR             | MARA              |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| BUKRS               | Company Code            | BUKRS             |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| FKART               | Billing type            | FKART             |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| GSBER               | Business area           | GSBER             |                   | Not applicable for HC                    |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| KAUFN               | Sales order             | KDAUF             |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| KDPOS               | Sales ord. item         | KDPOS             |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| KNDNR               | Customer                | KUNDE_PA          | KNA1              |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| KOKRS               | CO area                 | KOKRS             |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| KSTRG               | Cost object             | KSTRG             |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| PPRCTR              | Partner pr.ctr          | PPRCTR            |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| PRCTR               | Profit center           | PRCTR             | MARC              | D53 -- Remote control                    |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| PSPNR               | WBS element             | PS_PSP_PNR        |                   | Not applicable for HC                    |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| RKAUFNR             | Order                   | AUFNR             |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| SPART               | Division                | SPART             | MARA              | CE Consumer Electronics                  |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | HA Home Automation                       |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | SB Set-top Box                           |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | PC Personal Computer                     |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | RT Retail                                |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | OT Others                                |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| VERSI               | Version                 | RKEVERSI          |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| VKORG               | Sales org.              | VKORG             | MVKE              | SG28 Home Control Singapore Pte Ltd      |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN17 Home Control Solutions Limited      |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | US10 Premium Home Control Solutions LLC  |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | BE10 Home Control Europe NV              |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| VRGAR               | Record type             | RKE_VRGAR         |                   |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| VTWEG               | Distr. channel          | VTWEG             | MVKE              | DC Direct Customer Sales                 |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | IC Inter-Company Sales                   |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | KS Kit Sales                             |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CS Component Sales                       |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| WERKS               | Plant                   | WERKS_D           |                   | CN13 CN6A HC (Suzhou) Limited            |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN17 CN7A Sub-contract                   |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN7B CMS/ ODM                            |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN7C Kitting                             |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN7F HIMIT                               |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | SG21 CN8A Sub-contract                   |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN8B CMS/ ODM                            |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN8C Kitting                             |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN8E Kit Subcon                          |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | CN8F HIMIT                               |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | SG28 Sub-contract                        |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | BE10 BE10 Home Control Europe NV         |
|                     |                         |                   |                   |                                          |
|                     |                         |                   |                   | US10 US10 Premium Home Control Solutions |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| **REFERENCED CHARACTERISTICS**                                                        |                                          |
+---------------------------------------------------------------------------------------+------------------------------------------+
| **Customer**                                                                                                                     |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| LAND1               | Country                 | KNA1              | LAND1             | Customer country                         |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| LAND2               | Ship to Country         | KNA1              | LAND1             | Ship To country                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| VBUND               | Trading partner         | KNA1              | VBUND             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| **Material**                                                                                                                     |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| MATKL               | Material group          | MARA              | MATKL             | Commodity Item                           |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| MVGR1               | Material group 1        | MVKE              | MVGR1             | [End- customer]{.mark}                   |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| MVGR2               | Material group 2        | MVKE              | MVGR2             | [Sales Region]{.mark}                    |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| MVGR3               | Material group 3        | MVKE              | MVGR3             | [IC DB]{.mark}                           |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| MVGR4               | Material group 4        | MVKE              | MVGR4             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| MVGR5               | Material group 5        | MVKE              | MVGR5             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| MTART               | Material Type           | MARA              | MTART             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| EXTWG               | External Material Group | MARA              | EXTWG             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| KONDM               | Material pricing group  | MVKE              | KONDM             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| KTGRM               | Acct asgnmt grp         | MVKE              | KTGRM             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| HERKL               | Country of origin       | MARC              | HERKL             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| PSTYV               | Item Category           | VBAP              | PSTYV             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+
| PRODH               | Prod. Hierarchy         | MARA              | PRDHA             |                                          |
+---------------------+-------------------------+-------------------+-------------------+------------------------------------------+

## List of COPA value field {#list-of-copa-value-field .LS_Heading-3}

+--------------+-----------------+----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
| **Category** | **Value Field** | **Description**      | **Remark**                                                                                                                            |
+:=============+:================+:=====================+:======================================================================================================================================+
| Quantity     | ABSMG           | Billed Quantity      | Data from SD                                                                                                                          |
+--------------+-----------------+----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
| Sales        | VV032           | Intercompany Sales   | SD condition:                                                                                                                         |
|              |                 |                      |                                                                                                                                       |
|              |                 |                      | ZIIP Mkt Price-IIP Basis                                                                                                              |
+--------------+-----------------+----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
|              | VV003           | List price to dealer | SD condition:                                                                                                                         |
|              |                 |                      |                                                                                                                                       |
|              |                 |                      | ~~ZPR3 Price No Man.Proc~~.                                                                                                           |
|              |                 |                      |                                                                                                                                       |
|              |                 |                      | PR00 gross price                                                                                                                      |
+--------------+-----------------+----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
|              | VV030           | Miscellaneous Sales  | SD condition:                                                                                                                         |
|              |                 |                      |                                                                                                                                       |
|              |                 |                      | ZSS1 Manual price                                                                                                                     |
+--------------+-----------------+----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
| COGS         | VV032           | Cost                 | SD condition:                                                                                                                         |
|              |                 |                      |                                                                                                                                       |
|              |                 |                      | VPRS Cost                                                                                                                             |
+--------------+-----------------+----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
| Rebate       | [VV100]{.mark}  | Customer rebate      | FI posting                                                                                                                            |
|              |                 |                      |                                                                                                                                       |
|              |                 |                      | Finance users will enter manually in FI module rebate value for each customer. Users will directly maintain COPA segment during FI JV |
+--------------+-----------------+----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
| Freight      | VV110           | Customer freight     | FI posting                                                                                                                            |
|              |                 |                      |                                                                                                                                       |
|              |                 |                      | Finance users will enter manually in FI module rebate value for each customer. Users will directly maintain COPA segment during FI JV |
+--------------+-----------------+----------------------+---------------------------------------------------------------------------------------------------------------------------------------+

##  Inventory Valuation {#inventory-valuation .LS_Heading-3}

(1) Material Valuation

> Material valuation in SAP is not an independent application area, since most Material Valuation functions take place automatically in the background in SAP System. Material Valuation represents a link between Materials Management and Financial Accounting, since it updates the G/L accounts in Financial Accounting.

(2) Valuation level

> Plant has been kept the lowest level of valuation, i.e. the same material (having same material code) can have different valuation price in different plants.

(3) Price Control

> In the SAP System, there are two types of price control:
>
> 1\. Standard price (S)
>
> 2\. Moving average price (V)
>
> Materials can be subjected to different price controls (S or V) in different plants.

At Home Control, all materials will use standard price.

(4) Refer below for material setup strategy for Home Control

  --------------------------------------------------------------------------
  Valuation class   Description      GL account
  ----------------- ---------------- ---------------------------------------
  1006              Prod inv SEMI    1000100- Prod. Inv. Stores raw mat.

  1106              Comm.Inv. FERT   1100100-Comm. Inv.Stores Fin. Goods\`
  --------------------------------------------------------------------------

## Product Costing {#product-costing .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+------------------------------------------------------------------------------------------------------------------------------------+----------------------------+---------------------------------------+--------------------------------------------+
| Process Step                                                                                                                       | Business Role              | Transaction/App                       | Expected Results                           |
+====================================================================================================================================+============================+=======================================+============================================+
| 1.  Run Standard Cost Estimate\                                                                                                    | CO PC Period end Executive | Manage Costing Runs - Estimated Costs | Standard Cost Estimate run                 |
|     Execute costing run to process mass data.                                                                                      |                            |                                       |                                            |
|                                                                                                                                    |                            |                                       |                                            |
| Users will create different costing runs for different companies.                                                                  |                            |                                       |                                            |
|                                                                                                                                    |                            |                                       |                                            |
| In this step, system will cost for selected materials after exploring BOM.                                                         |                            |                                       |                                            |
|                                                                                                                                    |                            |                                       |                                            |
| Suzhou accountants will execute costing run for all companies of Home Control.                                                     |                            |                                       |                                            |
+------------------------------------------------------------------------------------------------------------------------------------+----------------------------+---------------------------------------+--------------------------------------------+
| 2.  Analyze Cost\                                                                                                                  | CO PC Period end Executive | Manage Costing Runs - Estimated Costs | Analyze report is created                  |
|     System will generate reports to analyze current standard price and new standard price. Users can extract report to excel also. |                            |                                       |                                            |
+------------------------------------------------------------------------------------------------------------------------------------+----------------------------+---------------------------------------+--------------------------------------------+
| 3.  Update price current month                                                                                                     | CO PC Period end Executive | Change Material Costs                 | The month price of the material is updated |
|                                                                                                                                    |                            |                                       |                                            |
| Users will change this month price if the current standard price is very big different from new standard price.                    |                            |                                       |                                            |
+------------------------------------------------------------------------------------------------------------------------------------+----------------------------+---------------------------------------+--------------------------------------------+
| 4.  Mark Cost Estimate\                                                                                                            | CO PC Period end Executive | Manage Costing Runs - Estimated Costs | Mark Cost Estimate                         |
|     After new price is accepted, users will mark this price for next month use.                                                    |                            |                                       |                                            |
+------------------------------------------------------------------------------------------------------------------------------------+----------------------------+---------------------------------------+--------------------------------------------+
| 5.  Release Cost Estimate\                                                                                                         | CO PC Period end Executive |                                       | Standard price is released                 |
|     On the first day of next month, standard price will be released. Accounting document is posted                                 |                            |                                       |                                            |
|                                                                                                                                    |                            |                                       |                                            |
| Dr/ Cr Inventory                                                                                                                   |                            |                                       |                                            |
|                                                                                                                                    |                            |                                       |                                            |
| Cr/ Dr Price revaluation account (P&L)                                                                                             |                            |                                       |                                            |
+------------------------------------------------------------------------------------------------------------------------------------+----------------------------+---------------------------------------+--------------------------------------------+

## Profitability Analysis {#profitability-analysis .LS_Heading-3}

(1) Profitability Analysis is the business process of planning and actual accounting of revenues, deductions, cost of goods sold, rebates, etc. and generating gross margin and marketing contribution and plan/actual analysis of Profit and Loss.

> Profitability Analysis process would depend on few key concepts and master data in Profitability Analysis:
>
> a\. Characteristics
>
> b\. Characteristic Values
>
> c\. Value Fields

(2) Characteristic

> The characteristics in Profitability Analysis represent those criteria according to which analysis can be performed on operating results and sales and profit plan. Characteristics are parameters based on which analysis done in CO-PA.
>
> Characteristics capture the dimension information which will be required for analysis and reporting.

(3) Value Field

> Value Fields are referred as reporting lines in CO-PA. Value Fields captures the lowest level information on which CO-PA reporting will be done. These are the fields that contain the currency amounts and quantities to analyse in CO‑PA. They represent the structure of costs and revenues.
>
> There are two types of value fields:
>
> \- Value fields that contain amounts in currencies are also referred to as \"amount fields\". All amount fields in a single line item use the same currency.
>
> \- Value fields that contain quantities are referred to as \"quantity fields\".

(4) COPA Actual Posting

> **Transfer of Sales Revenue and Sales Deductions from SD Module**
>
> When Billing Documents are released to accounting from SD Module, the Sales Revenue are also transferred on-line to the Profitability Analysis based on the SD Condition Type and PA Value Fields mapping. When the values are transferred from SD the lowest level characteristics like product and customer is also transferred which helps derive most of the characteristics.
>
> **Direct FI Postings**
>
> Revenue posting in Financial Accounting will get updated in COPA through Profitability Segment(s). Whenever a posting takes place in Financial Accounting, in case of revenue/ sales expense accounts, users can enter Profitability Segments to post directly to COPA.
>
> At Home Control, Sales Rebate and Freight outward will be entered in FI and post directly to COPA.
>
> **Assessment of Cost Centers**
>
> CO-PA provides a reporting environment in which all costs can be measured against revenues. In order to achieve this, costs in certain Cost Centers that are not fully credited in Cost Center Accounting need to be transferred to CO-PA (for example, HO overheads, Marketing Overheads, sales force etc.). Assessment is performed to transfer the following costs to CO-PA
>
> The bases on which these costs will stand transferred to COPA depend upon the assessment cycles defined. Such costs get assessed to the defined profitability segments based on the tracing factor defined viz. Sales quantity, sales revenue etc.

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- System should be able to calculate standard cost for materials based on BOM purchased price.

- System should be able to calculate overhead cost for finished product

- System should be able to analyze profit for different dimensions such as products, sales divisions

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- At Home Control, all materials will use standard price.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- Inventory valuation requires real-time inventory data provided by the supply chain department, which serves as the basis for cost accounting.

- The results of product cost accounting provide core data support for cost-benefit analysis.

- Cost-benefit analysis needs information such as capacity utilization provided by the operations department and market prices provided by the sales department, and such information depends on the accuracy of previous inventory valuation and cost accounting.

- The optimal production batch decision derived from cost-benefit analysis will, in turn, affect inventory management strategies (such as safety stock levels), forming a closed-loop linkage.

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

# Authorization Roles {#authorization-roles .LS_Heading-1}

1.  

2.  

3.  

<!-- -->

1.  
2.  
3.  
4.  

## Authorization Roles {#authorization-roles-1 .LS_Heading-3}

+----------------------------+----------------------------------------------------------+--------------------------------+--------------------------+
| **Business Role**          | **Role Description**                                     | **Authorization Restrictions** | **Baseline ZRS Role(s)** |
+============================+==========================================================+================================+==========================+
| CO PC Period end Executive | - Responsible to execute standard cost estimate monthly. | Std Roles                      | - BR_OVERHEAD_ACCOUNTANT |
+----------------------------+----------------------------------------------------------+--------------------------------+--------------------------+
| COPA executive             | - Responsible to execute COPA report                     |                                | - BR_OVERHEAD_ACCOUNTANT |
+----------------------------+----------------------------------------------------------+--------------------------------+--------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

  -----------------------------------------------------------------------
  **Document Type**       **Document Flow**
  ----------------------- -----------------------------------------------
  N/A                     

                          

                          

                          

                          
  -----------------------------------------------------------------------

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

4.  

5.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **SAP App**                               **Description / Usage**
  ----------------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Display Material Price Change Documents   Query and display all change records of material prices.

  Market Segments - Plan/Actual             Compare the planned and actual performance of each market segment by product, customer and other dimensions, so as to optimize resource allocation and marketing strategies.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+--------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                  |
+-----------------+-----------------+----------------+------------------+----------------+---------------------+
| **Report Name** | **Description** | **Key Files**  | **Std.**         | **Complexity** | **Comment**         |
|                 |                 |                |                  |                |                     |
|                 |                 |                | **SAP App/Rprt** |                |                     |
+:================+=================+:===============+:=================+:===============+:====================+
| N/A             |                 |                |                  |                |                     |
+-----------------+-----------------+----------------+------------------+----------------+---------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                 |
+------------------+------------------+------------------+------------------+--------------------+
| **Interface**    | **Description**  | **In Scope**     | **Complexity**   | **Comments**       |
+:=================+:=================+:=================+:=================+:===================+
| N/A              |                  |                  |                  |                    |
+------------------+------------------+------------------+------------------+--------------------+

## Conversions {#conversions .LS_Heading-3}

The following data conversions have been identified as in scope:

范围内需要切换的数据如下

+-----------------------------------------------------------------------------------------------------------------------------+
| **Conversions**                                                                                                             |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| **Data**      | **Source System** | **Import Complexity**[^1] | **Extract Complexity**[^2] | **Volume\     | **Complexity** |
|               |                   |                           |                            | (# items)**   |                |
+===============+===================+===========================+============================+===============+================+
| N/A           |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|               |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified as in scope:

+-----------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                    |
+------------------+------------------+------------------+------------------+-------------------------+
| **Enhancement**  | **Description**  | **Complexity**   | **In Scope**     | **Comments**            |
+==================+==================+==================+==================+:========================+
| N/A              |                  |                  |                  |                         |
+------------------+------------------+------------------+------------------+-------------------------+
|                  |                  |                  |                  |                         |
+------------------+------------------+------------------+------------------+-------------------------+
|                  |                  |                  |                  |                         |
+------------------+------------------+------------------+------------------+-------------------------+

## Forms {#forms .LS_Heading-3}

The following forms have been identified as in scope:

+---------------------------------------------------------------------------------------------------+
| **Forms**                                                                                         |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Form**          | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **表单​​**          | **​​描述​​**          | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

## Workflows {#workflows .LS_Heading-3}

The following workflows have been identified as in scope:

以下工作流被纳入范围：

+---------------------------------------------------------------------------------------------------+
| **Flexible Workflow**                                                                             |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Workflow**      | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **​​灵活工作流​​**    | **​​描述​​**          | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
