**FICO Fixed Assets**

**FICO固定资产**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: FI_DD_004 Fixed Assets**

**Version 1.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

       Frey Zheng               FICO Lead               08/11/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

      Jane Chen           Finance - Costing       

     Minting Wang              Finance            

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [4](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [4](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [5](#design-document-approval-options)](#design-document-approval-options)

[2. J59 Account Receivables [5](#j62-fixed-assets)](#j62-fixed-assets)

[2.1 Purpose [5](#purpose)](#purpose)

[2.2 Business Reason [6](#business-reason)](#business-reason)

[2.3 Business Benefits [6](#business-benefits)](#business-benefits)

[3. Process Scope Design [6](#process-scope-design)](#process-scope-design)

[3.1 Master dater [6](#master-dater)](#master-dater)

[3.1.1 Depreciation Areas [6](#depreciation-areas)](#depreciation-areas)

[3.1.2 Asset Class [7](#asset-class)](#asset-class)

[3.1.3 Depreciation Key [8](#depreciation-key)](#depreciation-key)

[3.1.4 Asset GL Account Determination [9](#asset-gl-account-determination)](#asset-gl-account-determination)

[3.2 Manage Asset Master Data [11](#manage-asset-master-data)](#manage-asset-master-data)

[3.2.1 Business Process Steps [11](#business-process-steps)](#business-process-steps)

[3.3 Manage Capitalization of Assets [12](#manage-capitalization-of-assets)](#manage-capitalization-of-assets)

[3.3.1 Business Process Steps [12](#business-process-steps-1)](#business-process-steps-1)

[3.4 Manage Sale of Asset [13](#manage-sale-of-asset)](#manage-sale-of-asset)

[3.4.1 Business Process Steps [13](#business-process-steps-2)](#business-process-steps-2)

[3.5 Manage Transfer of Asset [14](#manage-transfer-of-asset)](#manage-transfer-of-asset)

[3.5.1 Business Process Steps [14](#business-process-steps-3)](#business-process-steps-3)

[3.6 Manage Scrapping of Asset [15](#manage-scrapping-of-asset)](#manage-scrapping-of-asset)

[3.6.1 Business Process Steps [15](#business-process-steps-4)](#business-process-steps-4)

[3.7 Manage Asset Impairments [16](#manage-asset-impairments)](#manage-asset-impairments)

[3.7.1 Business Process Steps [16](#business-process-steps-5)](#business-process-steps-5)

[3.8 HC Functional Requirements [17](#manage-assets-under-construction)](#manage-assets-under-construction)

[3.9 HC Delegation Of Authority [17](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[3.10 Standard Documents / Settings [17](#standard-documents-settings)](#standard-documents-settings)

[3.11 Design Considerations / Key Assumptions [17](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[3.12 Cross Functional Integration Dependencies [18](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[3.13 Support / Closing Considerations [19](#support-closing-considerations)](#support-closing-considerations)

[4. Authorization Roles [19](#authorization-roles)](#authorization-roles)

[4.1 Authorization Roles [19](#authorization-roles-1)](#authorization-roles-1)

[5. Document Types and Document Flow [19](#document-types-and-document-flow)](#document-types-and-document-flow)

[6. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [20](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[6.1 Reports [20](#reports)](#reports)

[6.1.1 Standard Reports [20](#standard-reports)](#standard-reports)

[6.1.2 HC Requested Reports [20](#hc-requested-reports)](#hc-requested-reports)

[6.2 Interfaces [20](#interfaces)](#interfaces)

[6.3 Conversions [21](#conversions)](#conversions)

[6.4 Enhancements [21](#enhancements)](#enhancements)

[6.5 Forms [21](#forms)](#forms)

[6.6 Workflows [21](#workflows)](#workflows)

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

- Major design issues that need to be resolved in order to move forward in Realize stage (e.g., Internal Orders vs. Project Systems​)

- Place on the Issues Log, assign owner and due date, manage​ issue

- Complete Key Design Decision document and escalate (PMO then Executive Sponsor)

If you have any items that may withhold signature it is your responsibility to escalate as soon as possible

# J62 Fixed Assets {#j62-fixed-assets .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

Asset accounting, a subsidiary ledger of the general ledger, is used to manage and document fixed asset transactions in detail. In general ledger accounting, you update depreciation and changes to asset balance sheet values in asset accounting. You make various account assignments to cost accounting for these transactions. Because of the integration in SAP S/4HANA Cloud Public Edition, Asset Accounting (FI-AA) transfers data directly to and from other components from SAP S/4HANA Cloud Public Edition such as Financial Accounting (FI) components.

## Business Reason {#business-reason .LS_Heading-3}

- Create asset master

- Acquire assets

- Retire assets

- Valuate assets

- Perform month-end closing

- Perform year-end closing

- Purchase asset from purchase order

- Create legacy assets

## Business Benefits {#business-benefits .LS_Heading-3}

- Get a transparent view of asset acquisition

- Provide efficient automated processing

- Calculate values for depreciation

- Record depreciation

# Process Scope Design {#process-scope-design .LS_Heading-1}

##  Master dater {#master-dater .LS_Heading-3}

## Depreciation Areas {#depreciation-areas .LS_Heading-3}

Depreciation area is used for handling legal and reporting requirement.

Home Control would like to keep different depreciation calculation methods for Group reporting, Local reporting and Local tax reporting.

Following are the details of depreciation areas with posting parameters.

  ------------------------------------------------------------------------------------------------------------
  **Company Code**   **Ledger**   **Depreciation Area**   **Name of Depreciation Area**   **Valuation View**
  ------------------ ------------ ----------------------- ------------------------------- --------------------
  SG21               0L           32                      IFRS                            0IFRS_0032

  SG21               2L           1                       Book Depreciation               0SG_0001

  CN13               0L           32                      IFRS                            0IFRS_0032

  CN13               2L           1                       Book Depreciation               0CN_0001

  CN17               0L           32                      IFRS                            0IFRS_0032

  CN17               2L           1                       Book Depreciation               0CN_0001
  ------------------------------------------------------------------------------------------------------------

In HOME CONTROL, most of the assets will be purchased with Purchase Order (MM).

In SAP, Asset master will be created prior to creation of Purchase Requisition. Asset master data will be created by Local Finance team.

## Asset Class {#asset-class .LS_Heading-3}

Asset class will represent the nature of assets. Asset Class will determine following parameters.

a\. Asset Number Range

b\. Asset Master Field Status

c\. Asset GL Account determination

d\. Rule for determining depreciation start date

e\. Asset useful life

Following are examples of Asset Class applicable for Home Control group. Final listing will be confirmed during Realization phase

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    **No** **Asset Class**   **Asset class name**   **Asset class description**                   **Account Determination**   **Number Range Number**   **Number from**   **Number to**
  -------- ----------------- ---------------------- --------------------------------------------- --------------------------- ------------------------- ----------------- ---------------
         1 ZA008000          Goodwill costs         Goodwill costs                                ZA008000                    01                        000010000000      000019999999

         2 ZA035000          Lease assets           Lease assets                                  ZA035000                    01                        000010000000      000019999999

         3 ZH000000          Patents & trademarks   Patents & trademarks                          ZH000                       01                        000010000000      000019999999

         4 ZH020000          Software tbe marketd   Software intended to be marketed              ZH020                       01                        000010000000      000019999999

         5 ZH040000          Business Application   Business Application Services                 ZH040                       01                        000010000000      000019999999

         6 ZH041000          Network Application    Network Application Services                  ZH041                       01                        000010000000      000019999999

         7 ZH042000          Wide Area Network Se   Wide Area Network Services                    ZH042                       01                        000010000000      000019999999

         8 ZH043000          Local Infrastructure   Local Infrastructure                          ZH043                       01                        000010000000      000019999999

         9 ZH060000          Contract based asset   Contract based assets                         ZH060                       01                        000010000000      000019999999

        10 ZH102000          Buildings ex inv pr    Buildings excl. investment property           ZH102                       02                        000020000000      000029999999

        11 ZH103000          Bldng- leased ex inv   Buildings - leased excl investment property   ZH103                       02                        000020000000      000029999999

        12 ZH300000          Machin. & installa.    Machinery and installations                   ZH300                       03                        000030000000      000039999999

        13 ZH303000          Machinery - leased     Machinery - leased                            ZH303                       03                        000030000000      000039999999

        14 ZH400000          Spec.tools 1           Specific tools 1                              ZH400                       04                        000040000000      000049999999

        15 ZH450300          IT equipment hardwar   IT equipment hardware                         ZH451A                      04                        000040000000      000049999999

        16 ZH450410          Office equipment       Office equipment & furniture                  ZH451                       04                        000040000000      000049999999

        17 ZH450500          Transport equipment    Transport equipment                           ZH452                       04                        000040000000      000049999999

        18 ZH450520          Transp mater - cars    Transport material - cars                     ZH452                       04                        000040000000      000049999999
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[Note:]{.mark}

[For main assets, only internal number assignment is supported.]{.mark}

  -----------------------------------
  No.   No.FROM No.    TO No.
  ----- -------------- --------------
  01    000010000000   000019999999

  02    000020000000   000029999999

  03    000030000000   000039999999

  04    000040000000   000049999999

  05    000050000000   000059999999

  06    000060000000   000069999999

  07    000070000000   000079999999

  08    000080000000   000089999999

  09    000090000000   000099999999
  -----------------------------------

[Creation of new asset class only allowed for customer namespace \'Z\']{.mark}

## Depreciation Key {#depreciation-key .LS_Heading-3}

Depreciation keys determine calculation methods, start date of depreciation and useful life. User can enter a separate depreciation key for each depreciation area in the asset master record.

Depreciation Key applicable for Home Control

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Accounting Principle**   **Valuation View**   **ChDep**   **Depreciation Key**   **Name for Whole Depreciation**                    **comments**
  -------------------------- -------------------- ----------- ---------------------- -------------------------------------------------- -------------------------------------------------------
  SGAP                       0SG_0001             6110        0000                   No depreciation and no interest                    　

  SGAP                       0SG_0001             6110        LINK                   Str.-line frm acq.value to zero without interest   　

  CNAP                       0CN_0001             1310        0000                   No depreciation and no interest                    　

  CNAP                       0CN_0001             1310        CD00                   Str.-Line /to 0% scrap value/no int/next month     　

  IFRS                       0IFRS_0032           IFRS        0000                   No depreciation and no interest                    　

  IFRS                       0IFRS_0032           IFRS        LINE                   Straight line (depreciation to the day)            Depreciation start date will be 1st day of next month
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[Note]{.mark}

[You cannot create any new depreciation keys and you can also not change any existing depreciation keys.]{.mark}

[Please add the default Useful life for each fixed assets class.]{.mark}

  -----------------------------------------------------------------------------------------------------------------------------------
                                                                              **No** **Asset Class**   **Useful life**   **Period**
  ---------------------------------------------------------------------------------- ----------------- ----------------- ------------
                                                                                   1 ZA008000          　                　

                                                                                   2 ZA035000          　                　

                                                                                   3 ZH000000          　                　

                                                                                   4 ZH020000          　                　

                                                                                   5 ZH040000          　                　

                                                                                   6 ZH041000          　                　

                                                                                   7 ZH042000          　                　

                                                                                   8 ZH043000          　                　

                                                                                   9 ZH060000          　                　

                                                                                  10 ZH102000          　                　

                                                                                  11 ZH103000          　                　

                                                                                  12 ZH300000          　                　

                                                                                  13 ZH303000          　                　

                                                                                  14 ZH400000          　                　

                                                                                  15 ZH450300          　                　

                                                                                  16 ZH450410          　                　

                                                                                  17 ZH450500          　                　

    18![](media/media/image2.png){width="0.1875in" height="2.7343613298337708e-2in"} ZH450520          　                　
  -----------------------------------------------------------------------------------------------------------------------------------

## Asset GL Account Determination  {#asset-gl-account-determination .LS_Heading-3}

This table will be confirmed during the project realization phase.

<table style="width:100%;">
<colgroup>
<col style="width: 8%" />
<col style="width: 2%" />
<col style="width: 11%" />
<col style="width: 10%" />
<col style="width: 9%" />
<col style="width: 9%" />
<col style="width: 9%" />
<col style="width: 9%" />
<col style="width: 9%" />
<col style="width: 10%" />
<col style="width: 9%" />
</colgroup>
<thead>
<tr>
<th style="text-align: center;"><strong>Acct.det</strong></th>
<th style="text-align: center;"><strong>Ar.</strong></th>
<th style="text-align: center;"><strong>Accnt: APC</strong></th>
<th style="text-align: center;"><strong>ClearngRev</strong></th>
<th style="text-align: center;"><strong>Gain</strong></th>
<th style="text-align: center;"><strong>Loss</strong></th>
<th style="text-align: center;"><strong>Scrap loss</strong></th>
<th style="text-align: center;"><p><strong>Ct.acc.</strong></p>
<p><strong>APC</strong></p></th>
<th><strong>Ret.affil.comp.</strong></th>
<th><strong>Acq.Affil.Co.</strong></th>
<th><strong>KTENAK</strong></th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align: center;"><strong>　</strong></td>
<td style="text-align: center;"><strong>？</strong></td>
<td style="text-align: center;"><strong>KTANSW原值</strong></td>
<td><strong>KTANSG 抵销科目: 购置成本过账</strong></td>
<td><strong>KTMEHR总账科目: 资产报废收益</strong></td>
<td><strong>KTMIND资产报废损失的总账科目</strong></td>
<td><strong>KTREST报废时账面净值的总账科目</strong></td>
<td><strong>？</strong></td>
<td><strong>？</strong></td>
<td><strong>？</strong></td>
<td><strong>资产后续资本化的收入科目</strong></td>
</tr>
<tr>
<td style="text-align: center;">ZA008000</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">80900</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6217900</td>
<td>　</td>
<td style="text-align: right;">9043903</td>
<td>　</td>
<td style="text-align: right;">9043900</td>
</tr>
<tr>
<td style="text-align: center;">ZA035000</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">350900</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6204970</td>
<td>　</td>
<td style="text-align: right;">9043903</td>
<td>　</td>
<td style="text-align: right;">9043900</td>
</tr>
<tr>
<td style="text-align: center;">ZH000</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6211900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH020</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">20905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6213900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH040</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">40905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6215900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH041</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">41905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6215900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH042</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">42905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6215900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH043</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">43905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6215900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH060</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">60905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6219900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH102</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">102905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6202900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH103</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">103905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6204970</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH300</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">300905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6202900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH303</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">303905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6204970</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH400</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">400905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6202900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH451</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">451905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6202900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH451A</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">451905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6202900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
<tr>
<td style="text-align: center;">ZH452</td>
<td style="text-align: right;">1</td>
<td style="text-align: right;">452905</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043900</td>
<td style="text-align: right;">9053900</td>
<td style="text-align: right;">6202900</td>
<td style="text-align: right;">9043901</td>
<td style="text-align: right;">9043903</td>
<td style="text-align: right;">9043902</td>
<td style="text-align: right;">9043901</td>
</tr>
</tbody>
</table>

## Manage Asset Master Data {#manage-asset-master-data .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+----------------------------------------------------------------------------------------------------------+------------------+---------------------+------------------------------+
| Process Step                                                                                             | Business Role    | Transaction/App     | Expected Results             |
+==========================================================================================================+==================+=====================+==============================+
| 1.  BU provides Finance with Fixed Assets information                                                    |                  | N/A                 | N/A                          |
+----------------------------------------------------------------------------------------------------------+------------------+---------------------+------------------------------+
| 2.  If the Fixed Asset information is okay, Finance will create Asset Master Data                        | AA Administrator | Manage Fixed Assets | Asset Master Data is created |
+----------------------------------------------------------------------------------------------------------+------------------+---------------------+------------------------------+
| 3.  Finance will notify BU the Fixed Asset number which they will use in their Asset Procurement process | AA Administrator | N/A                 | N/A                          |
+----------------------------------------------------------------------------------------------------------+------------------+---------------------+------------------------------+

1.  

    1.  

## Manage Capitalization of Assets {#manage-capitalization-of-assets .LS_Heading-3}

![](media/media/image4.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+-----------------------------------------------------------------------------------------------------------------------------+---------------+------------------+-------------------+
| Process Step                                                                                                                | Business Role | Transaction/App  | Expected Results  |
+=============================================================================================================================+===============+==================+===================+
| 1.  If the asset is project-based, check Product Costing form on the shared folder                                          | AA Executive  | N/A              | N/A               |
+-----------------------------------------------------------------------------------------------------------------------------+---------------+------------------+-------------------+
| 2.  If the asset is non-project-based, requestor raises request for Capitalization of non-project-based assets for approval | Requestor     | N/A              | N/A               |
+-----------------------------------------------------------------------------------------------------------------------------+---------------+------------------+-------------------+

## Manage Sale of Asset {#manage-sale-of-asset .LS_Heading-3}

![](media/media/image5.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

+----------------------------------------------------------------------------------------------------+---------------+------------------------------------------------------------------+------------------------------------------+
| Process Step                                                                                       | Business Role | Transaction/App                                                  | Expected Results                         |
+====================================================================================================+===============+==================================================================+==========================================+
| 1.  Notification of retirement of asset will be received from asset owner/ BU/ cost center manager |               | N/A                                                              | N/A                                      |
+----------------------------------------------------------------------------------------------------+---------------+------------------------------------------------------------------+------------------------------------------+
| 2.  Perform asset sales without customers                                                          | AA executive  | Manage Fixed Assets-Post Retirement - Retirement without Revenue | Fixed Asset is retired                   |
+----------------------------------------------------------------------------------------------------+---------------+------------------------------------------------------------------+------------------------------------------+
| 3.  Checks asset report                                                                            | AA executive  | Asset History Sheet                                              | Check Fixed Asset retirement transaction |
+----------------------------------------------------------------------------------------------------+---------------+------------------------------------------------------------------+------------------------------------------+

## Manage Transfer of Asset {#manage-transfer-of-asset .LS_Heading-3}

![](media/media/image6.emf)

## Business Process Steps {#business-process-steps-3 .LS_Heading-3}

+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------+
| Process Step                                                                                                                                                                                                                                                                    | Business Role    | Transaction/App                                                         | Expected Results                                                |
+=================================================================================================================================================================================================================================================================================+==================+=========================================================================+=================================================================+
| 1.  Business Unit transfer of asset                                                                                                                                                                                                                                             | N/A              | N/A                                                                     | N/A                                                             |
|                                                                                                                                                                                                                                                                                 |                  |                                                                         |                                                                 |
| When a particular department or cost center identifies that an asset has to be transferred, the person responsible for that department or cost center should prepare the Fixed Asset Transfer Request form for approval accordingly before the asset is transferred physically. |                  |                                                                         |                                                                 |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------+
| 2.  If the asset is transferred within company codes, the Fixed Asset Master Data will be transferred within company codes accordingly                                                                                                                                          | AA administrator | Manage Fixed Assets-\>Post Transfer-\>Post Transfer Within Company Code | The Fixed Asset Master Data is transferred within company codes |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------+
| 3.  Perform transfer posting -- Intra company                                                                                                                                                                                                                                   | AA executive     |                                                                         | The Fixed Asset Master Data is transferred across company codes |
|                                                                                                                                                                                                                                                                                 |                  |                                                                         |                                                                 |
| Once the new asset master data is created, use "Manage Fixed Assets-\>Post Transfer-\>Post Transfer Across Company Code" to post the transfer of the acquisition cost and accumulated depreciation of the asset being transferred into the newly created asset master record.   |                  |                                                                         |                                                                 |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------+-------------------------------------------------------------------------+-----------------------------------------------------------------+

## Manage Scrapping of Asset {#manage-scrapping-of-asset .LS_Heading-3}

![](media/media/image7.emf)

## Business Process Steps {#business-process-steps-4 .LS_Heading-3}

+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+---------------------------------------+----------------------------------------------------------+
| Process Step                                                                                                                                                                                                                                                                                                                                           | Business Role | Transaction/App                       | Expected Results                                         |
+========================================================================================================================================================================================================================================================================================================================================================+===============+=======================================+==========================================================+
| 1.  When an asset is identified for retirement, the requesting department should raise a fixed asset disposal form for approval                                                                                                                                                                                                                        | N/A           | N/A                                   | N/A                                                      |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+---------------------------------------+----------------------------------------------------------+
| 2.  Perform asset scrapping                                                                                                                                                                                                                                                                                                                            | AA executive  | Manage Fixed Assets-\>Post Retirement | The Fixed Asse is retired                                |
|                                                                                                                                                                                                                                                                                                                                                        |               |                                       |                                                          |
| When asset scrapping is posted in SAP, the acquisition cost and accumulated depreciation of the fixed asset will be written off and any remaining net book value at the time of asset disposal will be posted to loss on asset disposal. If this is a complete asset retirement, the asset master data will also be updated with the deactivation date |               |                                       |                                                          |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+---------------------------------------+----------------------------------------------------------+
| 3.  Check report                                                                                                                                                                                                                                                                                                                                       | AA executive  | Asset History Sheet                   | Review the account postings, as well as the asset values |
|                                                                                                                                                                                                                                                                                                                                                        |               |                                       |                                                          |
| The asset accountant should review the account postings, as well as the asset values                                                                                                                                                                                                                                                                   |               |                                       |                                                          |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------+---------------------------------------+----------------------------------------------------------+

## Manage Asset Impairments {#manage-asset-impairments .LS_Heading-3}

![](media/media/image8.emf)

## Business Process Steps {#business-process-steps-5 .LS_Heading-3}

+------------------------------------------------------------------------------------------------------------------------+---------------+--------------------------------------------------+----------------------------+
| Process Step                                                                                                           | Business Role | Transaction/App                                  | Expected Results           |
+========================================================================================================================+===============+==================================================+============================+
| 1.  The BU reviews and identifies Assets for impairment.                                                               | N/A           | N/A                                              | N/A                        |
+------------------------------------------------------------------------------------------------------------------------+---------------+--------------------------------------------------+----------------------------+
| 2.  The BU prepares and raises the list of Assets for impairment to FI Controller for approval                         | N/A           | N/A                                              | N/A                        |
+------------------------------------------------------------------------------------------------------------------------+---------------+--------------------------------------------------+----------------------------+
| 3.  If the request for Asset impairment is approved, the Administrator/ Asset Accountant will make posting accordingly | AA Executive  | Manage Fixed Assets-\>Miscellaneous Transactions | The Fixed Asse is impaired |
|                                                                                                                        |               |                                                  |                            |
|                                                                                                                        |               | Transaction type select 640 or 650               |                            |
+------------------------------------------------------------------------------------------------------------------------+---------------+--------------------------------------------------+----------------------------+

## Manage Assets Under Construction {#manage-assets-under-construction .LS_Heading-3}

![](media/media/image9.emf)

## Business Process Steps {#business-process-steps-6 .LS_Heading-3}

+-----------------------------------------------------------------------------------------------------------------------------------+------------------+----------------------------------------+------------------------------------------+
| Process Step                                                                                                                      | Business Role    | Transaction/App                        | Expected Results                         |
+===================================================================================================================================+==================+========================================+==========================================+
| 1.  Create Statistical Project                                                                                                    | CO Administrator | Project Control - Enterprise Projects  | Project is created                       |
|                                                                                                                                   |                  |                                        |                                          |
|                                                                                                                                   |                  | Project Profile is Statistical Project |                                          |
+-----------------------------------------------------------------------------------------------------------------------------------+------------------+----------------------------------------+------------------------------------------+
| 2.  Allocate the expense outlays (not included in AUC) and capitalized expenditures (included in AUC) to the project              | CO Administrator | Manage Journal Entries                 |                                          |
+-----------------------------------------------------------------------------------------------------------------------------------+------------------+----------------------------------------+------------------------------------------+
| 3.  Query the actual expenses of the project                                                                                      | CO Administrator | Project -- Actual                      | Query the actual expenses of the project |
+-----------------------------------------------------------------------------------------------------------------------------------+------------------+----------------------------------------+------------------------------------------+
| 4.  If it has reached the status for transfer to fixed assets, the Finance creates and Capitalize Asset Master                    | AA Executive     | Manage Fixed Assets                    | Fixed asset is created and capitalized   |
|                                                                                                                                   |                  |                                        |                                          |
|                                                                                                                                   |                  | Journal entry:                         |                                          |
|                                                                                                                                   |                  |                                        |                                          |
|                                                                                                                                   |                  | Debit: Fixed Assets\                   |                                          |
|                                                                                                                                   |                  | Credit: Asset Acquisition Liquidation  |                                          |
+-----------------------------------------------------------------------------------------------------------------------------------+------------------+----------------------------------------+------------------------------------------+
| 5.  Transfer the capitalized expenditures allocated to the project (included in AUC) to the Asset Acquisition Liquidation account | CO Administrator | Manage Journal Entries                 | Journal entry is created                 |
|                                                                                                                                   |                  |                                        |                                          |
|                                                                                                                                   |                  | Journal entry:                         |                                          |
|                                                                                                                                   |                  |                                        |                                          |
|                                                                                                                                   |                  | Debit: Asset Acquisition Liquidation\  |                                          |
|                                                                                                                                   |                  | Credit: AUC WBS                        |                                          |
+-----------------------------------------------------------------------------------------------------------------------------------+------------------+----------------------------------------+------------------------------------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- Integration with procurement

- System should support manual asset creation.

- The system should have the functionality to register assets data.

- Ability to maintain multiple depreciation books, e.g. for a separate book for local accounting depreciation, tax depreciation and group accounting depreciation.

- System should support flexibility for each entity in the group to maintain different fixed asset useful life policies for accounting and tax depreciation separately.

- System should support automated computation of periodic depreciation for depreciable assets based on specified useful life and depreciation basis.

- Ability to maintain multiple depreciation books with different depreciation rules, e.g. for a separate book for local accounting depreciation, tax depreciation and group accounting depreciation.

- System should support simulation of test depreciation runs, without posting, by cost center, asset class.

- System should support automated generation of journal entries for depreciation.

- System should support reconciliation of total in asset sub-ledger with general ledger.

- System should allow user to generate report that reflect Net Book Value by asset ID, cost center, asset class.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Standard Documents / Settings  {#standard-documents-settings .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- Home Control SAP system provides the solution to settle AUC through project management.

- Following Business Process Transactions will be used to capitalize Asset under Construction

<!-- -->

- Distribute

- Settle

<!-- -->

- Asset retirement is the removal of an asset or part of an asset from the asset portfolio. This removal of an asset (or part of an asset) is posted from a bookkeeping perspective as an asset retirement. In HOME CONTROL, the following types of retirement will be used:

<!-- -->

- Retirement without customer

<!-- -->

- There are different types of intra-company asset transfers in Asset Accounting, depending on the reason for the transfer:

<!-- -->

- The location of the asset changes. As a result, you need to change the organizational assignments in the asset master data (e.g. cost center, personnel).

- The asset class changes. To convert an asset from one asset class to another where asset transfer is used to change assignment to asset class.

<!-- -->

- Asset retirement without revenue is used when fixed assets are being written off such as scrapping. If an asset write-off transaction is identified, the AA executive will be responsible to post the retirement in SAP via transaction asset retirement without revenue.

  This transaction will automatically create a debit posting to the losses from asset disposal G/L account for the assets net book value, a credit posting to the asset account for the entire book value and a debit posting to the accumulated depreciation account of the asset.

- Home Control system has the ability to increase depreciation amount of a fixed asset if there is a permanent impairment of its value. Generally, this additional depreciation amount of the asset value is shown separately from the original plan depreciation, through the standard function Special Valuation.

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- With the Financial Accounting (FI-GL) module: Changes in fixed assets (such as acquisition, depreciation, and scrapping) automatically generate general ledger vouchers, updating corresponding asset accounts, depreciation expense accounts, etc., to ensure that asset values are consistent with general ledger data.

- With the Materials Management (MM) module: When acquiring fixed assets through the procurement process, links in the MM module such as purchase orders, goods receipt, and invoice verification trigger the capitalization of assets in the FI-AA module, automatically creating asset master data and updating values.

- With the Controlling (CO) module: Depreciation of fixed assets is allocated to the CO module according to dimensions such as cost centers and internal orders, affecting cost accounting and profit analysis as cost elements. Meanwhile, internal orders in CO can be used to collect costs during asset construction, which are ultimately settled to fixed assets.

- With the Project System (PS) module: For capitalized projects (such as construction in progress), project costs collected by the PS module can be settled to the FI-AA module to form the value of fixed assets, realizing the conversion from project costs to assets.

- With the Sales and Distribution (SD) module: When disposing of fixed assets (such as sales), the sales process in the SD module triggers the scrapping of assets in the FI-AA module, synchronously updating asset values and generating relevant accounting vouchers.

- With the Material Ledger (ML): If ML is activated, value changes related to fixed assets (such as evaluation differences) will undergo parallel currency accounting and difference adjustments through ML.

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

+-------------------+-----------------------------------------------------------------+--------------------------------+--------------------------+
| **Business Role** | **Role Description**                                            | **Authorization Restrictions** | **Baseline ZRS Role(s)** |
+===================+=================================================================+================================+==========================+
| AA Administrator  | - Responsible to create asset master data at company code level | Std Roles                      | - BR_AA_ACCOUNTANT       |
+-------------------+-----------------------------------------------------------------+--------------------------------+--------------------------+
| AA executive      | - Responsible to execute asset sales with revenue               | Std Roles                      | - BR_AA_ACCOUNTANT       |
+-------------------+-----------------------------------------------------------------+--------------------------------+--------------------------+
| AA executive      | - Responsible to post asset transfer documents                  | Std Roles                      | - BR_AA_ACCOUNTANT       |
+-------------------+-----------------------------------------------------------------+--------------------------------+--------------------------+
| AA executive      | - Responsible to scrap asset in fixed asset module              | Std Roles                      | - BR_AA_ACCOUNTANT       |
+-------------------+-----------------------------------------------------------------+--------------------------------+--------------------------+
| AA executive      | - Responsible to post Asset impairment                          | Std Roles                      | - BR_AA_ACCOUNTANT       |
+-------------------+-----------------------------------------------------------------+--------------------------------+--------------------------+

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

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **SAP App**              **Description / Usage**
  ------------------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Asset History Sheet      Records key information throughout the fixed asset lifecycle, including historical data such as original value, accumulated depreciation, and changes in usage status, presenting the evolution of asset value and status.

  Asset Transactions       Focuses on details of various business transactions involving fixed assets, such as acquisitions, disposals, transfers, and valuations, reflecting changes in asset quantities and related transaction information like amounts and dates.

  Depreciation Lists       Summarizes depreciation data of fixed assets for a specific period, including periodic depreciation amounts, accumulated depreciation, and depreciation methods, used to verify the accuracy of depreciation calculations and cost allocation.
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
