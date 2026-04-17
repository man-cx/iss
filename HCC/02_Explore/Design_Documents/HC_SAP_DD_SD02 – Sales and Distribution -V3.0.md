**Sales and distribution**

**销售与分销流程**

**Scenario and Design Document**

![A logo with blue lines and text Description automatically generated with medium confidence](media/media/image1.png){width="3.0773807961504813in" height="1.0761701662292213in"}

**Document****: HC_SAP_DD_SD02_Sales and Distribution**

**Version 3.0**

PREPARED BY:

  --------------------- ------------------------- -----------------------
      PRINTED NAME                TITLE              SIGNATURE / DATE

        Warner Yu                SD Lead                15/08/2025
  --------------------- ------------------------- -----------------------

APPROVED BY:

  ------------------ ---------------------------- ------------------------
     PRINTED NAME               TITLE                 SIGNATURE / DATE

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  

                                                  
  ------------------ ---------------------------- ------------------------

**Table of Contents**

[1. Guidelines [6](#guidelines)](#guidelines)

[1.1 Design Document Approval Overview [6](#design-document-approval-overview)](#design-document-approval-overview)

[1.2 Design Document Approval Options​ [6](#design-document-approval-options)](#design-document-approval-options)

[2. Standard Sales To Customers [6](#standard-sales-to-customers)](#standard-sales-to-customers)

[2.1 Purpose [6](#purpose)](#purpose)

[2.2 Business Reason [7](#business-reason)](#business-reason)

[2.3 Business Benefits [7](#business-benefits)](#business-benefits)

[3. Direct Sales [7](#direct-sales)](#direct-sales)

[3.1 Purpose [7](#purpose-1)](#purpose-1)

[3.2 Business Reason [7](#business-reason-1)](#business-reason-1)

[3.3 Business Benefits [7](#business-benefits-1)](#business-benefits-1)

[4. Free of Charge Sales Order [8](#free-of-charge-sales-order)](#free-of-charge-sales-order)

[4.1 Purpose [8](#purpose-2)](#purpose-2)

[4.2 Business Reason [8](#business-reason-2)](#business-reason-2)

[4.3 Business Benefits [8](#business-benefits-2)](#business-benefits-2)

[5. Free Goods Sales [8](#free-goods-sales)](#free-goods-sales)

[5.1 Purpose [8](#purpose-3)](#purpose-3)

[5.2 Business Reason [8](#business-reason-3)](#business-reason-3)

[5.3 Business Benefits [8](#business-benefits-3)](#business-benefits-3)

[6. Kitting Sales [9](#kitting-sales)](#kitting-sales)

[6.1 Purpose [9](#purpose-4)](#purpose-4)

[6.2 Business Reason [9](#business-reason-4)](#business-reason-4)

[6.3 Business Benefits [9](#business-benefits-4)](#business-benefits-4)

[7. Consignment Sales [10](#consignment-sales)](#consignment-sales)

[7.1 Purpose [10](#purpose-5)](#purpose-5)

[7.2 Business Reason [10](#business-reason-5)](#business-reason-5)

[7.3 Business Benefits [10](#business-benefits-5)](#business-benefits-5)

[8. Customer Return [10](#customer-return)](#customer-return)

[8.1 Purpose [10](#purpose-6)](#purpose-6)

[8.2 Business Reason [11](#business-reason-6)](#business-reason-6)

[8.3 Business Benefits [11](#business-benefits-6)](#business-benefits-6)

[9. Process Scope Design [12](#process-scope-design)](#process-scope-design)

[9.1 Business Process for Sales To Customers 流程图 [12](#business-process-for-sales-to-customers-流程图)](#business-process-for-sales-to-customers-流程图)

[9.1.1 Business Process Steps [12](#business-process-steps)](#business-process-steps)

[9.2 HC Functional Requirements [15](#hc-functional-requirements)](#hc-functional-requirements)

[9.3 HC Delegation Of Authority [16](#hc-delegation-of-authority)](#hc-delegation-of-authority)

[9.4 Design Considerations / Key Assumptions [16](#design-considerations-key-assumptions)](#design-considerations-key-assumptions)

[9.5 Cross Functional Integration Dependencies [16](#cross-functional-integration-dependencies)](#cross-functional-integration-dependencies)

[9.6 Support / Closing Considerations [16](#support-closing-considerations)](#support-closing-considerations)

[10. Process Scope Design [17](#process-scope-design-1)](#process-scope-design-1)

[10.1 Business Process for DIRECT SALES流程图 [17](#business-process-for-direct-sales流程图)](#business-process-for-direct-sales流程图)

[10.1.1 Business Process Steps [17](#business-process-steps-1)](#business-process-steps-1)

[10.2 HC Functional Requirements [20](#hc-functional-requirements-1)](#hc-functional-requirements-1)

[10.3 HC Delegation Of Authority [20](#hc-delegation-of-authority-1)](#hc-delegation-of-authority-1)

[10.4 Design Considerations / Key Assumptions [21](#design-considerations-key-assumptions-1)](#design-considerations-key-assumptions-1)

[10.5 Cross Functional Integration Dependencies [21](#cross-functional-integration-dependencies-1)](#cross-functional-integration-dependencies-1)

[10.6 Support / Closing Considerations [21](#support-closing-considerations-1)](#support-closing-considerations-1)

[11. Process Scope Design [21](#process-scope-design-2)](#process-scope-design-2)

[11.1 Business Process for FREE OF CHARGE SALES ORDER 流程图 [21](#business-process-for-free-of-charge-sales-order-流程图)](#business-process-for-free-of-charge-sales-order-流程图)

[11.1.1 Business Process Steps [21](#business-process-steps-2)](#business-process-steps-2)

[11.2 HC Functional Requirements [23](#hc-functional-requirements-2)](#hc-functional-requirements-2)

[11.3 HC Delegation Of Authority [23](#hc-delegation-of-authority-2)](#hc-delegation-of-authority-2)

[11.4 Design Considerations / Key Assumptions [23](#design-considerations-key-assumptions-2)](#design-considerations-key-assumptions-2)

[11.5 Cross Functional Integration Dependencies [23](#cross-functional-integration-dependencies-2)](#cross-functional-integration-dependencies-2)

[11.6 Support / Closing Considerations [23](#support-closing-considerations-2)](#support-closing-considerations-2)

[12. Process Scope Design [24](#process-scope-design-3)](#process-scope-design-3)

[12.1 Business Process for Free Goods Sales流程图 [24](#business-process-for-free-goods-sales流程图)](#business-process-for-free-goods-sales流程图)

[12.1.1 Business Process Steps [24](#business-process-steps-3)](#business-process-steps-3)

[12.2 HC Functional Requirements [27](#hc-functional-requirements-3)](#hc-functional-requirements-3)

[12.3 HC Delegation Of Authority [28](#hc-delegation-of-authority-3)](#hc-delegation-of-authority-3)

[12.4 Design Considerations / Key Assumptions [28](#design-considerations-key-assumptions-3)](#design-considerations-key-assumptions-3)

[12.5 Cross Functional Integration Dependencies [28](#cross-functional-integration-dependencies-3)](#cross-functional-integration-dependencies-3)

[12.6 Support / Closing Considerations [28](#support-closing-considerations-3)](#support-closing-considerations-3)

[13. Process Scope Design [28](#process-scope-design-4)](#process-scope-design-4)

[13.1 Business Process for Kitting Sales流程图 [28](#business-process-for-kitting-sales流程图)](#business-process-for-kitting-sales流程图)

[13.1.1 Business Process Steps [29](#business-process-steps-4)](#business-process-steps-4)

[13.2 HC Functional Requirements [30](#hc-functional-requirements-4)](#hc-functional-requirements-4)

[13.3 HC Delegation Of Authority [30](#hc-delegation-of-authority-4)](#hc-delegation-of-authority-4)

[13.4 Design Considerations / Key Assumptions [31](#design-considerations-key-assumptions-4)](#design-considerations-key-assumptions-4)

[13.5 Cross Functional Integration Dependencies [31](#cross-functional-integration-dependencies-4)](#cross-functional-integration-dependencies-4)

[13.6 Support / Closing Considerations [31](#support-closing-considerations-4)](#support-closing-considerations-4)

[14. Process Scope Design [31](#process-scope-design-5)](#process-scope-design-5)

[14.1 Business Process for Consignment Sales流程图 [31](#business-process-for-consignment-sales流程图)](#business-process-for-consignment-sales流程图)

[14.1.1 Business Process Steps [31](#business-process-steps-5)](#business-process-steps-5)

[14.2 HC Functional Requirements [33](#hc-functional-requirements-5)](#hc-functional-requirements-5)

[14.3 HC Delegation Of Authority [33](#hc-delegation-of-authority-5)](#hc-delegation-of-authority-5)

[14.4 Design Considerations / Key Assumptions [33](#design-considerations-key-assumptions-5)](#design-considerations-key-assumptions-5)

[14.5 Cross Functional Integration Dependencies [33](#cross-functional-integration-dependencies-5)](#cross-functional-integration-dependencies-5)

[14.6 Support / Closing Considerations [33](#support-closing-considerations-5)](#support-closing-considerations-5)

[15. Process Scope Design [33](#process-scope-design-6)](#process-scope-design-6)

[15.1 Business Process for Customer Return流程图 [33](#business-process-for-customer-return流程图)](#business-process-for-customer-return流程图)

[15.1.1 Customer Return Business Process Steps [34](#customer-return-business-process-steps)](#customer-return-business-process-steps)

[15.1.2 Consignment Return Business Process Steps [37](#consignment-return-business-process-steps)](#consignment-return-business-process-steps)

[15.2 HC Functional Requirements [38](#hc-functional-requirements-6)](#hc-functional-requirements-6)

[15.3 HC Delegation Of Authority [38](#hc-delegation-of-authority-6)](#hc-delegation-of-authority-6)

[15.4 Design Considerations / Key Assumptions [38](#design-considerations-key-assumptions-6)](#design-considerations-key-assumptions-6)

[15.5 Cross Functional Integration Dependencies [38](#cross-functional-integration-dependencies-6)](#cross-functional-integration-dependencies-6)

[15.6 Support / Closing Considerations [38](#support-closing-considerations-6)](#support-closing-considerations-6)

[16. Authorization Roles [38](#authorization-roles)](#authorization-roles)

[16.1 Authorization Roles [38](#authorization-roles-1)](#authorization-roles-1)

[17. Document Types and Document Flow [39](#document-types-and-document-flow)](#document-types-and-document-flow)

[18. Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows [39](#reports-interfaces-conversions-enhancements-forms-and-workflows)](#reports-interfaces-conversions-enhancements-forms-and-workflows)

[18.1 Reports [39](#reports)](#reports)

[18.1.1 Standard Reports [39](#standard-reports)](#standard-reports)

[18.1.2 HC Requested Reports [39](#hc-requested-reports)](#hc-requested-reports)

[18.2 Interfaces [40](#interfaces)](#interfaces)

[18.3 Conversions [40](#conversions)](#conversions)

[18.4 Enhancements [41](#enhancements)](#enhancements)

[18.5 Forms [41](#forms)](#forms)

[18.6 Workflows [42](#workflows)](#workflows)

[19. Legend for Process Flow [42](#legend-for-process-flow)](#legend-for-process-flow)

**Document Version History**

  ------------- --------------------------------------------- --------------------
   **Version**              **Summary of Change**              **Effective Date**

       1.0       Create the initial version of the document.       28/07/2025

       2.0             Change Customer Return process              11/08/2025

       2.0                   Change after review                   15/08/2025
  ------------- --------------------------------------------- --------------------

# Guidelines {#guidelines .LS_Heading-1}

## Design Document Approval Overview {#design-document-approval-overview .LS_Heading-3}

The SAP Implementation Project Design Documents are the result of the Fit / Gap workshops.  All Project Design Documents must be reviewed and approved by the Home Control team to confirm we have captured the appropriate requirements as well as gaps, proposed solutions, and RICEFW objects​ from the workshops.

SAP Design Documents are living, breathing documents. As the SAP system is configured, tested, modified, and approved, the design documents may be updated to reflect the final design​.

Home Control Team Leads create the original design documents​. Should Home Control decide to update the Design Documents, it is up to Home Control to perform the updates.

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

# Standard Sales To Customers {#standard-sales-to-customers .LS_Heading-1}

2.  

<!-- -->

1.  

## Purpose {#purpose .LS_Heading-3}

This process begins with the creation of a customer and a standard sales order, tailored to the specific customer and their requirements. Upon completion of order picking, the shipping specialist updates the inventory to reflect the outgoing stock. This inventory relief step documents the precise quantity of goods being shipped to the customer. With the posting of the goods issue, revenue is formally recognized, and the cost of goods sold is recorded in the financial accounting system. Once the goods are delivered, the delivery can be invoiced. For preliminary alignment with customers, an optional preliminary billing document can be generated from the billing due list items. This allows for any necessary adjustments before the final billing documents, which customers are expected to settle, are created.

## Business Reason {#business-reason .LS_Heading-3}

This process describes the B2B business scenario for Home Control including domestic sales and export sales. Companies (SG21, CN17, CN13,BE01 and US01) will be involved in this business process.

For example, Home Control Singapore (SG21) receives customer orders, and goods are sourced and delivered directly from Home Control Singapore (SG21) to customer.

## Business Benefits {#business-benefits .LS_Heading-3}

- Perform an availability check when order is entered

- Determine shipping point automatically

- Create billing document

- Make postings to FI and CO

# Direct Sales {#direct-sales .LS_Heading-1}

3.  

<!-- -->

2.  

## Purpose {#purpose-1 .LS_Heading-3}

This process describe that a company has an affiliate company that delivers trading goods directly to a customer in intercompany sales. The affiliate company posts the intercompany billing document to the ordering company. The intercompany invoice is also posted automatically to the accounts payables of the ordering company.

## Business Reason {#business-reason-1 .LS_Heading-3}

This process describes the transactions between inter-companies. Goods are shipped out directly from the assigned plants. Companies (CN17, BE01, SG21 and US01) will be involved in this business process.

For example, Home Control Singapore (SG21) receives a customer purchase order, and goods are sourced and delivered from Home Control Solutions (CN17) to customer. In this process, Home Control Singapore (SG21) will post a Sales Order and issue a Delivery Note to that customer. Plant CN7X under Home Control Solutions (CN17) will ship out the goods and issue two invoices - one standard invoice to the customer and one inter-company invoice to Home Control Singapore (SG21).

## Business Benefits {#business-benefits-1 .LS_Heading-3}

- Predefined configuration for creating intercompany sales orders

- Intercompany billing

# Free of Charge Sales Order {#free-of-charge-sales-order .LS_Heading-1}

4.  

<!-- -->

3.  

## Purpose {#purpose-2 .LS_Heading-3}

A unique sales order type is created that allows free of charge orders. The order is confirmed based on the availability of goods. A delivery is created. The goods are then picked, confirmed, and delivered to the customer. The process supports creation of billing documents at the end even it is a free of charge process. This assures hand over of data to FI/CO area.

## Business Reason {#business-reason-2 .LS_Heading-3}

This process describes the business scenario when Home Control will provide customers free products, i.e. giving out free samples according to the customer contract terms. Companies (SG21, CN17, BE01 and US01) will be involved in this business process.

## Business Benefits {#business-benefits-2 .LS_Heading-3}

- System integrated Free of Charge sales order processing

- The process allows regular invoice with zero value or proforma invoice with values

# Free Goods Sales {#free-goods-sales .LS_Heading-1}

5.  

<!-- -->

4.  

## Purpose {#purpose-3 .LS_Heading-3}

The process starts with the creation of a customer standard sales order using a material for which a free goods condition record is maintained. Depending on the ordered quantities, customers receive free goods.

After the completion of picking, the shipping specialist relieves the inventory. This inventory relief is the actual recording of the physical quantity that is being shipped to the customer.

With the goods issue posting revenue is recognized and cost of goods sold is recorded in Financial Accounting.

Once goods are delivered, you can invoice the delivery.

## Business Reason {#business-reason-3 .LS_Heading-3}

Free goods are usually directly related to a company\'s sales strategies, customer relationship maintenance, or business process requirements.

General reasons:

- Market promotion and customer development

- Customer evaluation and testing needs

- Promotional activities or brand promotion

- Compliance and process standardization

- System process adaptation

## Business Benefits {#business-benefits-3 .LS_Heading-3}

- Perform availability check upon order entry

- Determine shipping point automatically

- Determine inclusive free goods automatically

- Create a billing document

- Make postings to FI and CO

# Kitting Sales {#kitting-sales .LS_Heading-1}

6.  

<!-- -->

5.  

## Purpose {#purpose-4 .LS_Heading-3}

Companies often want to sell single products bundled into a sales kit (such as selling a PC together with monitor, keyboard, computer mouse, and so on). Sales kits are commonly used when the products that are part of the sales kit can also be sold independently as single products.

Customers want to have an easy way to use sales kits during order taking and follow up processes without a need to use production BOMs, variant configuration, or other functions that don\'t fit or are too complex for this use case.

There are multiple ways to process a bill of material in sales. Once you\'ve entered a bill of material in a sales order, the system runs pricing and execution at the following levels:

- Header level (ERLA): usually used when product is assembled

- Item level (LUMF): usually used when product isn\'t assembled

- Pricing on header level, logistics on item level (CPFH): usually used when product isn\'t assembled, but the header should carry the total price

- Logistics on header level, pricing on item level (DISH): usually used for displays if the main item is inventory managed and the components carry the price

## Business Reason {#business-reason-4 .LS_Heading-3}

This process describes the business scenario when Home Control sells kit sets to Brazil sub-contractors. The recipient companies can re-assemble the kitting sets and do the domestic sales after this. This business model is created due to the consideration of taxation in different regions. Company SG21 (Plant CN8C) and company CN17 (Plant CN7C) are involved in this process.

## Business Benefits {#business-benefits-4 .LS_Heading-3}

- Support sales kits with pricing and logistics on the header level or the item level of the sales kits

- Support sales kits with pricing on header level but with logistics on item level

- Support sales kits with logistics on header level but with pricing on item level

- Use sales kits within other scope items

# Consignment Sales {#consignment-sales .LS_Heading-1}

7.  

<!-- -->

6.  

## Purpose {#purpose-5 .LS_Heading-3}

In this scenario, the goods are initially posted to the customer consignment stock and thus remain the property of the company (consignment fill-up).

At regular intervals, the customer reports how many articles are sold and how many articles are in the current stock (inventory). When the inventory is performed, the batch number may be entered to do a correct material posting. A corresponding sales order is entered that documents the issue from the customer consignment, meaning that the goods are no longer the property of the company (consignment issue).

Goods that are not required can be returned from the consignment stock to the central warehouse. The goods must not be defective. They are posted directly into the free stock (consignment pick-up).

In some cases, goods are returned to the customer consignment stock (by its own customer or based on erroneous consumption posting) after the consignment issue has already taken place. A return order is then created (consignment return).

## Business Reason {#business-reason-5 .LS_Heading-3}

This process describes the business scenario when goods are sent to customers but remain the property of Home Control until they are actually consumed by the customer. The goods will be stored as a special stock -- Vendor Management Inventory (VMI) at the customers' side. However, the goods remain in the valuated stocks of the delivering plant. The transactions cannot be billed until the customers withdraw from the consignment stock and confirm the consumption. The transaction handles using consignment fill-up, consignment issue, consignment fill-up and consignment return order types.

## Business Benefits {#business-benefits-5 .LS_Heading-3}

- Save costs on inventory for consignor

- Restock as it sells -- beneficial for both parties

- Save time for consignor

- Use the consignment stock to generate product exposure (especially new or unknown products) for their customers

# Customer Return {#customer-return .LS_Heading-1}

8.  

<!-- -->

7.  

## Purpose {#purpose-6 .LS_Heading-3}

The progress of the return process can be monitored using returns overview.

In HC, we focus on below customer return scenario:

Return to seller: A returns order is created (optionally with reference to the original billing document or sales document). Once saved, a returns delivery is automatically generated. After goods receipt, the inspection takes place at the warehouse. The user can influence when the refunding documents are created: either directly, when releasing the returns order, or after the inspection. Finally, the user can decide on the compensation type for the customer: either shipping a replacement or paying a credit memo.

## Business Reason {#business-reason-6 .LS_Heading-3}

This process describes the business scenario when customer requires a sales return due to either invoice issue (i.e. price correction) or product quantity/ quality issue (i.e. wrong or defective products or wrong quantity). These types of customer complaints can be solved by 1) issuing a credit or debit memo to customers for invoice correction; or 2) taking back the goods from the customer (by creating a return order) and replacing the goods by using a replacement order or a free of charge delivery.

In the case when goods replacement is required, a return order will be created with reference to the original sales order or billing order. The returned stock will be returned to a special storage location RET in the same delivering plants. A return delivery note should be created with reference to the sales return order as a base to receive the returned goods back to the Home Control's warehouse. The return delivery is not relevant for picking process; thus, when the goods are physically received, the goods receipt can be posted in the system to close the return delivery. Goods receipt for return delivery in Home Control will increase the stock in the RET storage location in the corresponding warehouse.

In the case when no goods replacement is required such as the invoice correction or customers agree to accept the below-quality goods at a discounted price, a credit note needs to be created. Before that, the return order must be released for billing and the goods receipt should have been posted for the return delivery.

## Business Benefits {#business-benefits-6 .LS_Heading-3}

- Generate follow-up documents automatically

- Perform refund in one step

- Include goods inspection

- Provide end-to-end support and monitoring of the return process

- Increase process flexibility within returns order processing

- Enhance efficiency in the comprehensive returns process

# Process Scope Design {#process-scope-design .LS_Heading-1}

1.  

## Business Process for Sales To Customers 流程图 {#business-process-for-sales-to-customers-流程图 .LS_Heading-3}

![](media/media/image2.emf)

## Business Process Steps {#business-process-steps .LS_Heading-3}

+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| Process Step | Process Step Description                                                                                                                         | Transaction/App                    | Business Role |
+==============+==================================================================================================================================================+====================================+===============+
| 001          | The planner gathers new customer contract information.                                                                                           | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | *\* These information include the new customer, sold-to, ship-to, new material etc. is sent to the planners.*                                    |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 002          | Create a Contract in SAP based on the available information                                                                                      | VA43/                              | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              |                                                                                                                                                  | Manager sales contract version 2   |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 003          | Verify if it is a firm customer order                                                                                                            | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, record it down as a firmed SO in the PO filed & proceed to step 004                                                                    |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, record it down as a sales forecast in the PO filed & proceed to step 012                                                                  |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 004          | If it is a firm order, consider it as a customer firm SO                                                                                         | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 005          | Create a Sales Order in the SAP system (Customer Firm Order)                                                                                     | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 006          | Check the credit against the established credit limit based on customer number. Decide if the credit has exceeded the limit.                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 007.                                                                                                                   |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, proceed to step 008.                                                                                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 007          | If the customer credit has exceeded the limit, the Sales order credit is blocked. Credit admins need to approve for the credit release.          | Manage Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | *\* If not exceeding the limit, the SO processing will be directly going to the next step.*                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 008          | Save the Sales Order in the SAP system                                                                                                           | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | (Order acknowledgement document printed - only for US)                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 009          | The system will automatically include this SO into the MRP run upon the successful creation of the SO                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 010          | Check if the order has been fulfilled based on the result of MRP run                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 011 and inform the customers about the successful delivery                                                             |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - If no, proceed to step 012 and postpone the SO delivery so that it will be considered in the next-round MRP run again                          |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 011          | If the customer PO has not been fulfilled, postpone the So delivery date and go back to step 008 to re-conduct the MRP run.                      | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 012          | If the customer PO has been fulfilled, inform the customer about the successful delivery.                                                        | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 013          | If it is not a firm customer order, consider it as a customer forecast.                                                                          | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 014          | Create a Sales Order in the SAP system marked as Customer Forecast                                                                               | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 015          | Check the credit against the established credit limit based on customer number. Decide if the credit has exceeded the limit.                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 016                                                                                                                    |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, proceed to step 017.                                                                                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 016          | If the customer credit has exceeded the limit, the Sales order credit is blocked. Credit admins need to approve for the credit release.          | Manage Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | *\* If not exceeding the limit, the SO processing will be directly going to the next step.*                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 017          | Save the Sales Order in the SAP system                                                                                                           | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | (Order acknowledgement document printed - only for US)                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 018          | The system will automatically include this SO into the MRP run upon the successful creation of the SO                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 019          | Decide if the PO has been received.                                                                                                              | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, planner deletes the SO Schedule Line and re-write the PO as a firmed SO in the SAP system (proceed to step 004)                        |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, check the status with customers via phone call, email, etc (proceed to step 003)                                                          |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 020          | If the PO has been received, delete the SO schedule line and create a new SO (Customer Firmed SO); go back to step 004                           | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 021          | If the PO has not yet been received, check with the customer through phone call or email. Wait until there is a confirmation from the customers. | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
|              |                                                                                                                                                  |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| **流程步骤​​** | **​​流程说明**                                                                                                                                     | **​​事务代码/应用​​**                  | **​​业务角色​​**  |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 001          | 计划员收集新的客户合同信息。                                                                                                                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 这些信息包括新客户、售达方、送达方、新材料等，会发送给计划员。                                                                                 |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 002          | 根据现有信息在 SAP 中创建合同                                                                                                                    | VA43/                              | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              |                                                                                                                                                  | Manager sales contract version 2   |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 003          | 确认是否为确定的客户订单                                                                                                                         | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，在采购订单字段中记录为确定的销售订单，并进入步骤 004                                                                                     |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，在采购订单字段中记录为销售预测，并进入步骤 012                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 004          | 若是确定订单，则将其视为客户确定的销售订单                                                                                                       | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 005          | 在 SAP 系统中创建销售订单（客户确定订单）                                                                                                        | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 006          | 根据客户编号，对照既定信用额度检查信用情况。判断信用是否已超过额度。                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 007。                                                                                                                           |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，进入步骤 008。                                                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 007          | 若客户信用已超过额度，销售订单信用将被冻结。信用管理员需批准信用释放                                                                             | 管理已记录的信用决策               | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | - 若未超过额度，销售订单处理将直接进入下一步。                                                                                                   |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 008          |  在 SAP 系统中保存销售订单\                                                                                                                      | VA01                               | Planner       |
|              | （打印订单确认文件 - 仅适用于美国）                                                                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 009          | 销售订单成功创建后，系统将自动将该销售订单纳入物料需求计划（MRP）运行                                                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 010          | 根据物料需求计划运行结果，检查订单是否已履行                                                                                                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 011 并通知客户已成功交货                                                                                                        |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，进入步骤 012 并推迟销售订单交货时间，以便在下一轮物料需求计划运行中再次考虑                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 011          | 若客户采购订单未履行，推迟销售订单交货日期，并返回步骤 008 重新进行物料需求计划运行。                                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 012          | 若客户采购订单已履行，通知客户已成功交货。                                                                                                       | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 013          | 若不是确定的客户订单，则将其视为客户预测                                                                                                         | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 014          | 在 SAP 系统中创建标记为客户预测的销售订单                                                                                                        | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 015          | 根据客户编号，对照既定信用额度检查信用情况。判断信用是否已超过额度。                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 016                                                                                                                             |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | 若否，进入步骤 017。                                                                                                                             |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 016          | 若客户信用已超过额度，销售订单信用将被冻结。信用管理员需批准信用释放。                                                                           | Manage Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | 若未超过额度，销售订单处理将直接进入下一步。                                                                                                     |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 017          | 在 SAP 系统中保存销售订单\                                                                                                                       | VA01                               | Planner       |
|              | （打印订单确认文件 - 仅适用于美国）                                                                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 018          | 销售订单成功创建后，系统将自动将该销售订单纳入物料需求计划（MRP）运行                                                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 019          | 判断是否已收到采购订单。                                                                                                                         | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，计划员删除销售订单计划行，并在 SAP 系统中将采购订单重新记录为确定的销售订单（进入步骤 004）                                              |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，通过电话、电子邮件等方式与客户确认状态（进入步骤 003）                                                                                   |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 020          | 若已收到采购订单，删除销售订单计划行并创建新的销售订单（客户确定订单）；返回步骤 004                                                             | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 021          | 若尚未收到采购订单，通过电话或电子邮件与客户确认。等待客户确认。                                                                                 | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+

## HC Functional Requirements {#hc-functional-requirements .LS_Heading-3}

- Planner cannot change the price brought from sales condition records.

- Sales End Customer field to be added in Material group 2 in Material Master Data

- Sales Region field to be added in Material group 1 in Material Master Data

- IC DB field to be added in Material group 3 in Material Master Data

- Partner Function in Sales Contracts and then brought to Sales Orders：

  ----------------------------------------------------------------------------------
  Partner function   Partner function Description   Field to be assigned for
  ------------------ ------------------------------ --------------------------------
  ZM                 Employee Responsible           ODM/Subcon account manager

  EN                 Enduser for F.Trade            Maingroup account manager

  VE                 Sales Employee                 Subgroup account manager
  ----------------------------------------------------------------------------------

- Jean will need to mass change price in sales order.

## HC Delegation Of Authority {#hc-delegation-of-authority .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations .LS_Heading-3}

- N/A

# Process Scope Design {#process-scope-design-1 .LS_Heading-1}

2.  

## Business Process for DIRECT SALES流程图 {#business-process-for-direct-sales流程图 .LS_Heading-3}

![](media/media/image3.emf)

## Business Process Steps {#business-process-steps-1 .LS_Heading-3}

+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| Process Step | Process Step Description                                                                                                                         | Transaction/App                    | Business Role |
+==============+==================================================================================================================================================+====================================+===============+
| 001          | The planner gathers new customer contract information.                                                                                           | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | *\* These information include the new customer, sold-to, ship-to, new material etc. is sent to the planners.*                                    |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 002          | Create a Contract in SAP based on the available information                                                                                      | VA43/                              | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              |                                                                                                                                                  | Manager sales contract version 2   |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 003          | Verify if it is a firm customer order                                                                                                            | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, record it down as a firmed SO in the PO filed & proceed to step 004                                                                    |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, record it down as a sales forecast in the PO filed & proceed to step 012                                                                  |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 004          | If it is a firm order, consider it as a customer firm SO                                                                                         | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 005          | - Create a Sales Order in the SAP system (Customer Firm Order)\                                                                                  | VA01                               | Planner       |
|              |   Delivery Plant is intercompany plant.                                                                                                          |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 006          | Check the credit against the established credit limit based on customer number. Decide if the credit has exceeded the limit.                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 007.                                                                                                                   |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, proceed to step 008.                                                                                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 007          | If the customer credit has exceeded the limit, the Sales order credit is blocked. Credit admins need to approve for the credit release.          | Manage Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | *\* If not exceeding the limit, the SO processing will be directly going to the next step.*                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 008          | Save the Sales Order in the SAP system                                                                                                           | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | (Order acknowledgement document printed - only for US)                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 009          | The system will automatically include this SO into the MRP run upon the successful creation of the SO                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 010          | Check if the order has been fulfilled based on the result of MRP run                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 011 and inform the customers about the successful delivery                                                             |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, proceed to step 012 and postpone the SO delivery so that it will be considered in the next-round MRP run again                            |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 011          | If the customer PO has not been fulfilled, postpone the So delivery date and go back to step 008 to re-conduct the MRP run.                      | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 012          | If the customer PO has been fulfilled, inform the customer about the successful delivery.                                                        | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 013          | If it is not a firm customer order, consider it as a customer forecast.                                                                          | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 014          | Create a Sales Order in the SAP system marked as Customer Forecast                                                                               | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 015          | Check the credit against the established credit limit based on customer number. Decide if the credit has exceeded the limit.                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 016                                                                                                                    |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, proceed to step 017.                                                                                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 016          | If the customer credit has exceeded the limit, the Sales order credit is blocked. Credit admins need to approve for the credit release.          | Manage Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | *\* If not exceeding the limit, the SO processing will be directly going to the next step.*                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 017          | Save the Sales Order in the SAP system                                                                                                           | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | (Order acknowledgement document printed - only for US)                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 018          | The system will automatically include this SO into the MRP run upon the successful creation of the SO                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 019          | Decide if the PO has been received.                                                                                                              | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, planner deletes the SO Schedule Line and re-write the PO as a firmed SO in the SAP system (proceed to step 004)                        |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, check the status with customers via phone call, email, etc (proceed to step 003)                                                          |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 020          | If the PO has been received, delete the SO schedule line and create a new SO (Customer Firmed SO); go back to step 004                           | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 021          | If the PO has not yet been received, check with the customer through phone call or email. Wait until there is a confirmation from the customers. | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
|              |                                                                                                                                                  |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| **流程步骤​​** | **​​流程说明**                                                                                                                                     | **​​事务代码/应用​​**                  | **​​业务角色​​**  |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 001          | 计划员收集新的客户合同信息。                                                                                                                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 这些信息包括新客户、售达方、送达方、新材料等，会发送给计划员。                                                                                 |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 002          | 根据现有信息在 SAP 中创建合同                                                                                                                    | VA43/                              | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              |                                                                                                                                                  | Manager sales contract version 2   |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 003          | 确认是否为确定的客户订单                                                                                                                         | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，在采购订单字段中记录为确定的销售订单，并进入步骤 004                                                                                     |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，在采购订单字段中记录为销售预测，并进入步骤 012                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 004          | 若是确定订单，则将其视为客户确定的销售订单                                                                                                       | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 005          | - 在 SAP 系统中创建销售订单（客户确定订单）                                                                                                      | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | 交货工厂是集团内公司                                                                                                                             |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 006          | 根据客户编号，对照既定信用额度检查信用情况。判断信用是否已超过额度。                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 007。                                                                                                                           |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，进入步骤 008。                                                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 007          | 若客户信用已超过额度，销售订单信用将被冻结。信用管理员需批准信用释放                                                                             | 管理已记录的信用决策               | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | - 若未超过额度，销售订单处理将直接进入下一步。                                                                                                   |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 008          |  在 SAP 系统中保存销售订单\                                                                                                                      | VA01                               | Planner       |
|              | （打印订单确认文件 - 仅适用于美国）                                                                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 009          | 销售订单成功创建后，系统将自动将该销售订单纳入物料需求计划（MRP）运行                                                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 010          | 根据物料需求计划运行结果，检查订单是否已履行                                                                                                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 011 并通知客户已成功交货                                                                                                        |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，进入步骤 012 并推迟销售订单交货时间，以便在下一轮物料需求计划运行中再次考虑                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 011          | 若客户采购订单未履行，推迟销售订单交货日期，并返回步骤 008 重新进行物料需求计划运行。                                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 012          | 若客户采购订单已履行，通知客户已成功交货。                                                                                                       | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 013          | 若不是确定的客户订单，则将其视为客户预测                                                                                                         | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 014          | 在 SAP 系统中创建标记为客户预测的销售订单                                                                                                        | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 015          | 根据客户编号，对照既定信用额度检查信用情况。判断信用是否已超过额度。                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 016                                                                                                                             |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | <!-- -->                                                                                                                                         |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，进入步骤 017。                                                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 016          | 若客户信用已超过额度，销售订单信用将被冻结。信用管理员需批准信用释放。                                                                           | Manage Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | 若未超过额度，销售订单处理将直接进入下一步。                                                                                                     |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 017          | 在 SAP 系统中保存销售订单\                                                                                                                       | VA01                               | Planner       |
|              | （打印订单确认文件 - 仅适用于美国）                                                                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 018          | - 销售订单成功创建后，系统将自动将该销售订单纳入物料需求计划（MRP）运行                                                                          | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 019          | 判断是否已收到采购订单。                                                                                                                         | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，计划员删除销售订单计划行，并在 SAP 系统中将采购订单重新记录为确定的销售订单（进入步骤 004）                                              |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | <!-- -->                                                                                                                                         |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，通过电话、电子邮件等方式与客户确认状态（进入步骤 003）                                                                                   |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 020          | 若已收到采购订单，删除销售订单计划行并创建新的销售订单（客户确定订单）；返回步骤 004                                                             | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 021          | 若尚未收到采购订单，通过电话或电子邮件与客户确认。等待客户确认。                                                                                 | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+

## HC Functional Requirements {#hc-functional-requirements-1 .LS_Heading-3}

- Planner cannot change the price brought from sales condition records.

## HC Delegation Of Authority {#hc-delegation-of-authority-1 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-1 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-1 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-1 .LS_Heading-3}

- N/A

# Process Scope Design {#process-scope-design-2 .LS_Heading-1}

3.  

## Business Process for FREE OF CHARGE SALES ORDER 流程图 {#business-process-for-free-of-charge-sales-order-流程图 .LS_Heading-3}

![](media/media/image4.emf)

## Business Process Steps {#business-process-steps-2 .LS_Heading-3}

+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| Process Step | Process Step Description                                                                                                                                             | Transaction/App   | Business Role |
+==============+======================================================================================================================================================================+===================+===============+
| 001          | Customers want to receive a sample before purchase or meet the FOC requirement by bulk purchase. They will raise up a FOC Request.                                   | N/A               | Customer      |
|              |                                                                                                                                                                      |                   |               |
|              | *\** *This step is subject to the negotiation with key account managers and/ or individual contract terms.*                                                          |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 002          | Planners will receive a customer FOC requirement from the key account managers.                                                                                      | N/A               | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | *\* Customer information such as customer number, ship-to party, shipping address, SO/ billing number if any, etc. will be provided by key account manager as well.* |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 003          | Planner creates a Sales Order and fill in all available information and FOC requirement in SAP system.                                                               | VA01              | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | *\* This is to reserve the resource and prepare for the MRP run.*                                                                                                    |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 004          | Save the Sales Order in SAP system                                                                                                                                   | VA01              | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | *\* By this stage, the resources will be readily to ship out to address customers' FOC requirements.*                                                                |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 005          | The system will automatically include this SO into the MRP run upon the successful creation of the SO                                                                | N/A               | Planner       |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 006          | Check if the order has been fulfilled based on the result of MRP run                                                                                                 | N/A               | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | - If yes, proceed to step 007 and inform the customers about the successful delivery                                                                                 |                   |               |
|              |                                                                                                                                                                      |                   |               |
|              | If no, proceed to step 009 and postpone the SO delivery so that it will be considered in the next-round MRP run again                                                |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 007          | If the customer PO has been fulfilled, inform the customer about the successful delivery.                                                                            | N/A               | Planner       |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 008          | Sub-process: HC_SAP_DD_SD03 -- Delivery Processing                                                                                                                   | N/A               | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | Free goods will be shipped out. Please refer to the corresponding DD for details.                                                                                    |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 009          | If the customer PO has not been fulfilled, postpone the So delivery date and go back to step 005 to re-conduct the MRP run.                                          | VA02              | Planner       |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
|              |                                                                                                                                                                      |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| **流程步骤​​** | **​​流程说明**                                                                                                                                                         | **​​事务代码/应用​​** | **​​业务角色​​**  |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 001          | 客户希望在购买前收到样品，或通过批量采购满足免费赠送（FOC）要求。他们会提出免费赠送请求。                                                                            | N/A               | Customer      |
|              |                                                                                                                                                                      |                   |               |
|              | - 此步骤取决于与大客户经理的协商和 / 或个别合同条款。                                                                                                                |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 002          | 计划员将从大客户经理处收到客户的免费赠送需求。                                                                                                                       | N/A               | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | 大客户经理还将提供客户信息，如客户编号、送达方、送货地址、销售订单 / 账单编号（如有）等。                                                                            |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 003          | 计划员在 SAP 系统中创建销售订单，并填写所有可用信息和免费赠送需求。                                                                                                  | VA01              | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | - 此举是为了预留资源并为物料需求计划（MRP）运行做准备。                                                                                                              |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 004          | 在 SAP 系统中保存销售订单                                                                                                                                            | VA01              | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | - 至此阶段，资源将随时可以发出，以满足客户的免费赠送需求。                                                                                                           |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 005          | 销售订单成功创建后，系统将自动将该销售订单纳入物料需求计划（MRP）运行                                                                                                | N/A               | Planner       |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 006          | 根据物料需求计划运行结果，检查订单是否已履行                                                                                                                         | N/A               | Planner       |
|              |                                                                                                                                                                      |                   |               |
|              | - 若是，进入步骤 007 并通知客户已成功交货                                                                                                                            |                   |               |
|              |                                                                                                                                                                      |                   |               |
|              | 若否，进入步骤 009 并推迟销售订单交货时间，以便在下一轮物料需求计划运行中再次考虑                                                                                    |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 007          | 若客户采购订单已履行，通知客户已成功交货。                                                                                                                           |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 008          | 子流程：HC_SAP_DD_SD03 -- Delivery Process\                                                                                                                          | N/A               | Planner       |
|              | 免费商品将发出。详情请参阅相应的交付文件（DD）。                                                                                                                     |                   |               |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+
| 009          | 若客户采购订单未履行，推迟销售订单交货日期，并返回步骤 005 重新进行物料需求计划运行                                                                                  | VA02              | Planner       |
+--------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------+

## HC Functional Requirements {#hc-functional-requirements-2 .LS_Heading-3}

- Planner cannot change the price brought from sales condition records.

## HC Delegation Of Authority {#hc-delegation-of-authority-2 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-2 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-2 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-2 .LS_Heading-3}

- N/A

# Process Scope Design {#process-scope-design-3 .LS_Heading-1}

4.  

## Business Process for Free Goods Sales流程图 {#business-process-for-free-goods-sales流程图 .LS_Heading-3}

![](media/media/image5.emf)

## Business Process Steps {#business-process-steps-3 .LS_Heading-3}

+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| Process Step | Process Step Description                                                                                                                         | Transaction/App                    | Business Role |
+==============+==================================================================================================================================================+====================================+===============+
| 001          | The planner gathers new customer contract information.                                                                                           | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | *\* These information include the new customer, sold-to, ship-to, new material etc. is sent to the planners.*                                    |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 002          | Create a Contract in SAP based on the available information                                                                                      | VA43/                              | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              |                                                                                                                                                  | Manager sales contract version 2   |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 003          | Verify if it is a firm customer order                                                                                                            | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, record it down as a firmed SO in the PO filed & proceed to step 004                                                                    |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, record it down as a sales forecast in the PO filed & proceed to step 012                                                                  |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 004          | If it is a firm order, consider it as a customer firm SO                                                                                         | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 005          | Create a Sales Order in the SAP system (Customer Firm Order)                                                                                     | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              |  Configured free goods rules.                                                                                                                    |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 006          | Check the credit against the established credit limit based on customer number. Decide if the credit has exceeded the limit.                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 007.                                                                                                                   |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, proceed to step 008.                                                                                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 007          | If the customer credit has exceeded the limit, the Sales order credit is blocked. Credit admins need to approve for the credit release.          | Manage Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | *\* If not exceeding the limit, the SO processing will be directly going to the next step.*                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 008          | Save the Sales Order in the SAP system                                                                                                           | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | (Order acknowledgement document printed - only for US)                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 009          | The system will automatically include this SO into the MRP run upon the successful creation of the SO                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 010          | Check if the order has been fulfilled based on the result of MRP run                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 010 and inform the customers about the successful delivery                                                             |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, proceed to step 011 and postpone the SO delivery so that it will be considered in the next-round MRP run again                            |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 011          | If the customer PO has been fulfilled, inform the customer about the successful delivery.                                                        | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 012          | If the customer PO has not been fulfilled, postpone the So delivery date and go back to step 008 to re-conduct the MRP run.                      | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 013          | If it is not a firm customer order, consider it as a customer forecast.                                                                          | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 014          | Create a Sales Order in the SAP system marked as Customer Forecast                                                                               | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 015          | Decide if the PO has been received.                                                                                                              | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, planner deletes the SO Schedule Line and re-write the PO as a firmed SO in the SAP system (proceed to step 015)                        |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, check the status with customers via phone call, email, etc (proceed to step 016)                                                          |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 016          | If the PO has been received, delete the SO schedule line and create a new SO (Customer Firmed SO); go back to step 004                           | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 017          | If the PO has not yet been received, check with the customer through phone call or email. Wait until there is a confirmation from the customers. | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 018          | Check the credit against the established credit limit based on customer number. Decide if the credit has exceeded the limit.                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - If yes, proceed to step 019                                                                                                                    |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | If no, proceed to step 020.                                                                                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 019          | If the customer credit has exceeded the limit, the Sales order credit is blocked. Credit admins need to approve for the credit release.          | Manage Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | *\* If not exceeding the limit, the SO processing will be directly going to the next step.*                                                      |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 020          | Save the Sales Order in the SAP system                                                                                                           | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | (Order acknowledgement document printed - only for US)                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
|              |                                                                                                                                                  |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| **流程步骤​​** | **​​流程说明**                                                                                                                                     | **​​事务代码/应用​​**                  | **​​业务角色​​**  |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 001          | 计划员收集新的客户合同信息。                                                                                                                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 这些信息包括新客户、售达方、送达方、新材料等，会发送给计划员。                                                                                 |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 002          | 根据现有信息在 SAP 中创建合同                                                                                                                    | VA43/                              | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              |                                                                                                                                                  | Manager sales contract version 2   |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 003          | 确认是否为确定的客户订单                                                                                                                         | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，在采购订单字段中记录为确定的销售订单，并进入步骤 004                                                                                     |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，在采购订单字段中记录为销售预测，并进入步骤 012                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 004          | 若是确定订单，则将其视为客户确定的销售订单                                                                                                       | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 005          | 在 SAP 系统中创建销售订单（客户确定订单）                                                                                                        | VA01                               | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 配置了赠品规则                                                                                                                                 |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 006          | 根据客户编号，对照既定信用额度检查信用情况。判断信用是否已超过额度。                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 007。                                                                                                                           |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，进入步骤 008。                                                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 007          | 若客户信用已超过额度，销售订单信用将被冻结。信用管理员需批准信用释放                                                                             | 管理已记录的信用决策               | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | - 若未超过额度，销售订单处理将直接进入下一步。                                                                                                   |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 008          |  在 SAP 系统中保存销售订单\                                                                                                                      | VA01                               | Planner       |
|              | （打印订单确认文件 - 仅适用于美国）                                                                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 009          | 销售订单成功创建后，系统将自动将该销售订单纳入物料需求计划（MRP）运行                                                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 010          | 根据物料需求计划运行结果，检查订单是否已履行                                                                                                     | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 011 并通知客户已成功交货                                                                                                        |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，进入步骤 012 并推迟销售订单交货时间，以便在下一轮物料需求计划运行中再次考虑                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 011          | 若客户采购订单已履行，通知客户已成功交货。                                                                                                       | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 012          | 若客户采购订单未履行，推迟销售订单交货日期，并返回步骤 008 重新进行物料需求计划运行。                                                            | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 013          | 若不是确定的客户订单，则将其视为客户预测                                                                                                         | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 014          | 在 SAP 系统中创建标记为客户预测的销售订单                                                                                                        | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 015          | 判断是否已收到采购订单。                                                                                                                         | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，计划员删除销售订单计划行，并在 SAP 系统中将采购订单重新记录为确定的销售订单（进入步骤 004）                                              |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，通过电话、电子邮件等方式与客户确认状态（进入步骤 016）                                                                                   |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 016          | 若已收到采购订单，删除销售订单计划行并创建新的销售订单（客户确定订单）；返回步骤 004                                                             | VA01                               | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 017          | 若尚未收到采购订单，通过电话或电子邮件与客户确认。等待客户确认。                                                                                 | N/A                                | Planner       |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 018          | 根据客户编号，对照既定信用额度检查信用情况。判断信用是否已超过额度。                                                                             | N/A                                | Planner       |
|              |                                                                                                                                                  |                                    |               |
|              | - 若是，进入步骤 019                                                                                                                             |                                    |               |
|              |                                                                                                                                                  |                                    |               |
|              | - 若否，进入步骤 020。                                                                                                                           |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 019          | 若客户信用已超过额度，销售订单信用将被冻结。信用管理员需批准信用释放。                                                                           | 管理已记录的信用决策               | Credit admin  |
|              |                                                                                                                                                  |                                    |               |
|              | - 若未超过额度，销售订单处理将直接进入下一步。                                                                                                   |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+
| 020          | 在 SAP 系统中保存销售订单\                                                                                                                       | VA01                               | Planner       |
|              | （打印订单确认文件 - 仅适用于美国）                                                                                                              |                                    |               |
+--------------+--------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+---------------+

## HC Functional Requirements {#hc-functional-requirements-3 .LS_Heading-3}

- Planner cannot change the price brought from sales condition records.

- Sell 1000 with 3 free .(Enter 1000,3 will be expanded eg . Item 10 1000EA, Item 20 3EA, but not Item 10 997 EA, Item 20 3EA) . This is the standard function.

## HC Delegation Of Authority {#hc-delegation-of-authority-3 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-3 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-3 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-3 .LS_Heading-3}

- N/A

# Process Scope Design {#process-scope-design-4 .LS_Heading-1}

5.  

## Business Process for Kitting Sales流程图 {#business-process-for-kitting-sales流程图 .LS_Heading-3}

![](media/media/image6.emf)

## Business Process Steps {#business-process-steps-4 .LS_Heading-3}

+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| Process Step | Process Step Description                                                                                                                | Transaction/App                   | Business Role |
+==============+=========================================================================================================================================+===================================+===============+
| 001          | Receive customer request for Kitting order                                                                                              | N/A                               | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 002          | Create a Sales Order from the information retrieved from the Purchase Order                                                             | VA01                              | Planner       |
|              |                                                                                                                                         |                                   |               |
|              | *\* The information includes Sold-to, Ship-to, SalesArea, ShipMode, Inco. Term and Payment term.*                                       |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 003          | For sales order, BOM expansion automatically according to Order BOM.                                                                    | VA01                              | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 004          | Check or modify the item price or quantity                                                                                              | VA01                              | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 005          | Check the credit against the established credit limit based on customer number. Decide if the credit has exceeded the limit.            | N/A                               | Planner       |
|              |                                                                                                                                         |                                   |               |
|              | - If yes, proceed to step 007.                                                                                                          |                                   |               |
|              |                                                                                                                                         |                                   |               |
|              | If no, proceed to step 008.                                                                                                             |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 006          | If the customer credit has exceeded the limit, the Sales order credit is blocked. Credit admins need to approve for the credit release. | Mange Documented Credit Decisions | Credit admin  |
|              |                                                                                                                                         |                                   |               |
|              | *\* If not exceeding the limit, the SO processing will be directly going to the next step.*                                             |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 007          | Save the Sales Order in the SAP system                                                                                                  | VA01                              | Planner       |
|              |                                                                                                                                         |                                   |               |
|              | (Order acknowledgement document printed - only for US)                                                                                  |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 008          | The system will automatically include this SO into the MRP run upon the successful creation of the SO                                   | N/A                               | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 009          | Check if the order has been fulfilled based on the result of MRP run                                                                    | N/A                               | Planner       |
|              |                                                                                                                                         |                                   |               |
|              | - If yes, proceed to step 010 and inform the customers about the successful delivery                                                    |                                   |               |
|              |                                                                                                                                         |                                   |               |
|              | If no, proceed to step 011 and postpone the SO delivery so that it will be considered in the next-round MRP run again                   |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 010          | If the customer PO has been fulfilled, inform the customer about the successful delivery.                                               | N/A                               | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 011          | If the customer PO has not been fulfilled, postpone the So delivery date and go back to step 008 to re-conduct the MRP run.             | N/A                               | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| **流程步骤​​** | **​​流程说明**                                                                                                                            | **​​事务代码/应用​​**                 | **​​业务角色​​**  |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 001          | 接收客户的配套订单请求                                                                                                                  | N/A                               | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 002          | 根据从采购订单中获取的信息创建销售订单                                                                                                  | VA01                              | Planner       |
|              |                                                                                                                                         |                                   |               |
|              | - 这些信息包括售达方、送达方、销售区域、运输方式、国际贸易术语和付款条件。                                                              |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 003          | 该销售订单，根据订单BOM自动展开物料清单                                                                                                 | VA01                              | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 004          | 检查或修改物料数量                                                                                                                      | VA01                              | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 005          | 根据客户编号，对照既定信用额度检查信用情况。判断信用是否已超过额度。                                                                    | N/A                               | Planner       |
|              |                                                                                                                                         |                                   |               |
|              | - 若是，进入步骤 007。                                                                                                                  |                                   |               |
|              |                                                                                                                                         |                                   |               |
|              | - 若否，进入步骤 008。                                                                                                                  |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 006          | 若客户信用已超过额度，销售订单信用将被冻结。信用管理员需批准信用释放。                                                                  | 管理已记录的信用决策              | Credit admin  |
|              |                                                                                                                                         |                                   |               |
|              | - 若未超过额度，销售订单处理将直接进入下一步。                                                                                          |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 007          | 在 SAP 系统中保存销售订单\                                                                                                              | VA01                              | Planner       |
|              | （打印订单确认文件 - 仅适用于美国）                                                                                                     |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 008          | 销售订单成功创建后，系统将自动将该销售订单纳入物料需求计划（MRP）运行                                                                   | N/A                               | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 009          | 根据物料需求计划运行结果，检查订单是否已履行                                                                                            | N/A                               | Planner       |
|              |                                                                                                                                         |                                   |               |
|              | - 若是，进入步骤 010 并通知客户已成功交货                                                                                               |                                   |               |
|              |                                                                                                                                         |                                   |               |
|              | - 若否，进入步骤 011 并推迟销售订单交货时间，以便在下一轮物料需求计划运行中再次考虑                                                     |                                   |               |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 010          | 若客户采购订单已履行，通知客户已成功交货。                                                                                              | N/A                               | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+
| 011          | 若客户采购订单未履行，推迟销售订单交货日期，并返回步骤 008 重新进行物料需求计划运行。                                                   | N/A                               | Planner       |
+--------------+-----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+---------------+

## HC Functional Requirements {#hc-functional-requirements-4 .LS_Heading-3}

- Planner cannot change the price brought from sales condition records.

- For ERLA, pricing and inventory managed on the main item.

- For LUMF, pricing and inventory managed on the subitems.

## HC Delegation Of Authority {#hc-delegation-of-authority-4 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-4 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-4 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-4 .LS_Heading-3}

- N/A

# Process Scope Design {#process-scope-design-5 .LS_Heading-1}

6.  

## Business Process for Consignment Sales流程图 {#business-process-for-consignment-sales流程图 .LS_Heading-3}

![](media/media/image7.emf)

## Business Process Steps {#business-process-steps-5 .LS_Heading-3}

  --------------------------------------------------------------------------------------------------------------------------------------
  Process Step   Process Step Description                                               Transaction/App                  Business Role
  -------------- ---------------------------------------------------------------------- -------------------------------- ---------------
  101            Refer to the Contract to create a Consignment Fill-up Order            N/A                              **Planner**

  102            Post a Consignment Fill-up SO                                          VA01                             Planner

  103            Create Delivery Note                                                   VL01N/Manage Outbound Delivery   Planner

  104            Post Picking Note                                                      VL01N/Manage Outbound Delivery   Planner

  105            Post Goods Issue from restricted stock to W-Stock                      VL01N/Manage Outbound Delivery   Planner

                                                                                                                         

  201            Refer to the Consignment Fill-up Order to create a Consignment Issue                                    Planner

  202            Post a Consignment Issue SO                                            VA01                             Planner

  203            Post Delivery Note                                                     VL01N/Manage Outbound Delivery   Planner

  204            Post Picking Note                                                      VL01N/Manage Outbound Delivery   Planner

  205            Post Goods Issue from W-Stock                                          VL01N/Manage Outbound Delivery   Planner

  206            Billing Process                                                        N/A                              AR Admin

                                                                                                                         

  **流程步骤​​**   **​​流程说明**                                                           **​​事务代码/应用​​**                **​​业务角色​​**

  101            参考合同创建寄售补货订单                                               N/A                              **Planner**

  102            过账寄售补货销售订单                                                   VA01                             Planner

  103            创建交货单                                                             VL01N/管理出库交货               Planner

  104            过账拣货单                                                             VL01N/管理出库交货               Planner

  105            从受限库存发货至寄售库存                                               VL01N/管理出库交货               Planner

                                                                                                                         

  201            参考寄售补货订单创建寄售出库单                                                                          Planner

  202            过账寄售出库销售订单                                                   VA01                             Planner

  203            创建交货单                                                             VL01N/管理出库交货               Planner

  204            过账拣货单                                                             VL01N/管理出库交货               Planner

  205            从寄售库存发货                                                         VL01N/管理出库交货               Planner

  206            开票流程                                                               N/A                              AR Admin
  --------------------------------------------------------------------------------------------------------------------------------------

## HC Functional Requirements {#hc-functional-requirements-5 .LS_Heading-3}

- Planner cannot change the price brought from sales condition records.

## HC Delegation Of Authority {#hc-delegation-of-authority-5 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-5 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-5 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-5 .LS_Heading-3}

- N/A

# Process Scope Design {#process-scope-design-6 .LS_Heading-1}

7.  

## Business Process for Customer Return流程图 {#business-process-for-customer-return流程图 .LS_Heading-3}

![](media/media/image8.emf)

![](media/media/image9.emf)

## Customer Return Business Process Steps {#customer-return-business-process-steps .LS_Heading-3}

+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| Process Step | Process Step Description                                                                                                                                                                                                                                                                                                                                          | Transaction/App   | Business Role       |
+==============+===================================================================================================================================================================================================================================================================================================================================================================+===================+=====================+
| 001          | Customers raise up a complaint and request for goods return to their corresponding account managers.                                                                                                                                                                                                                                                              | N/A               | Customer            |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | *\* In Home Control, customer complaints are due to either invoice issue (e.g. cross-month price correction) or other customer return requests (e.g. product quality/ quantity).*                                                                                                                                                                                 |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 002          | Key account managers will finalize with customers if a return **rework order** is needed.                                                                                                                                                                                                                                                                         | N/A               | Key Account Manager |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | If need rework, go to step 004,                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | If no need rework, go to step 003                                                                                                                                                                                                                                                                                                                                 |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 003          | If rework not needed ,upon receiving customer complaints, key account managers will handle the complaints including noting down the reasons, verifying the return reasons (e.g. product quality/ quantity), handling the customer relationship and discussing with customers if they prefer replacements, accept the goods at a discounted price, or refund, etc. | N/A               | Key Account Manager |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | *\* All information will be communicated to planners* consistently.                                                                                                                                                                                                                                                                                               |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | If yes, go to step 010,                                                                                                                                                                                                                                                                                                                                           |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | If not , go to step 011                                                                                                                                                                                                                                                                                                                                           |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 004          | Planners will create a return SO(CBAR).                                                                                                                                                                                                                                                                                                                           | VA01              | Key Account Manager |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | \* Copy the reference from the original SO. These information include customer info, SO reference, return reason, etc.                                                                                                                                                                                                                                            |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | Essential fileds：\                                                                                                                                                                                                                                                                                                                                               |                   |                     |
|              | Follow-up Act.:                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 0001 Receive into Plant                                                                                                                                                                                                                                                                                                                                           |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | (Note:Receive into Block stock directly)                                                                                                                                                                                                                                                                                                                          |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 0002 Immediately Move to Free Available Stock                                                                                                                                                                                                                                                                                                                     |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | (Note:Receive into Unrestricted stock directly)                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | Refund Type:                                                                                                                                                                                                                                                                                                                                                      |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | Credit Memo (Note:As HC required, Set Create Credit Memo as default. Once Return order was created completely, the Credit Memo would be created directly)                                                                                                                                                                                                         |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | Replacement Material (Note: Create a free replacement order directly and no credit memo created)                                                                                                                                                                                                                                                                  |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 005          | Planner will note the WHS Admin to change the status of block stock                                                                                                                                                                                                                                                                                               | N/A               | Planner             |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 006          | WHS Admin will transfer the blocked stock to unrestricted stock in SAP                                                                                                                                                                                                                                                                                            | MIGO              | WHS Admin           |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 007          | Planners will create a SO(Order Type: OR) for replacement delivery.                                                                                                                                                                                                                                                                                               | VA01              |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | \* Copy the reference from the original SO. These information include customer info, SO reference, return reason, etc.                                                                                                                                                                                                                                            |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 008          | Link to process HC_SAP_DD_SD03_Delivery Process                                                                                                                                                                                                                                                                                                                   | N/A               | WHS Admin           |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 009          | Link to process HC_SAP_DD_SD04-01-\_Customer Billing                                                                                                                                                                                                                                                                                                              | N/A               | Planner             |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 010          | Previous Step 003.                                                                                                                                                                                                                                                                                                                                                | MIGO              | WHS Admin           |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | QA key account manager judge HC can make a replacement for customer directly.                                                                                                                                                                                                                                                                                     |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | So QA inform WHS Admin to post goods via cost center (App: MIGO---Movement Type 201)                                                                                                                                                                                                                                                                              |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | Need to remark SIV NO.                                                                                                                                                                                                                                                                                                                                            |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 011          | revious Step 003.                                                                                                                                                                                                                                                                                                                                                 | VA01              | Key Account Manager |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | QA key account manager judge HC can not make a replacement for customer directly.                                                                                                                                                                                                                                                                                 |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | In this step , QA will raise a Credit Memo request in SAP .                                                                                                                                                                                                                                                                                                       |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 012          | Link to process HC_SAP_DD_SD04_03-01-Credit Memo and Debit Memo Process                                                                                                                                                                                                                                                                                           | N/A               | AR Admin            |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| **流程步骤​​** | **​​流程说明**                                                                                                                                                                                                                                                                                                                                                      | **​​事务代码/应用​​** | **​​业务角色​​**        |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 001          | 客户向相应的客户经理提出投诉并要求退货                                                                                                                                                                                                                                                                                                                            | N/A               | Customer            |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 在Home Control中，客户投诉原因包括发票问题（如跨月价格调整）或其他客户退货请求（如产品质量 / 数量问题）。                                                                                                                                                                                                                                                         |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 002          | 大客户经理与客户确认是否需要退货返工订单                                                                                                                                                                                                                                                                                                                          | N/A               | Key Account Manager |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 如需返工，进入步骤 004;                                                                                                                                                                                                                                                                                                                                           |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 如无需返工，进入步骤 003                                                                                                                                                                                                                                                                                                                                          |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 003          | 如无需返工，大客户经理在收到客户投诉后，需处理投诉，包括记录原因、核实退货原因（如产品质量 / 数量问题）、维护客户关系，并与客户协商其是否倾向于换货、折价接受货物或退款等.                                                                                                                                                                                        | N/A               | Key Account Manager |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 所有信息需及时同步给计划员                                                                                                                                                                                                                                                                                                                                        |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 若可以直接免费换货，进入步骤 010；                                                                                                                                                                                                                                                                                                                                |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 若不可以免费换货，进入步骤 011。                                                                                                                                                                                                                                                                                                                                  |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 004          | 计划员创建退货销售订单（CBAR）                                                                                                                                                                                                                                                                                                                                    | VA01              | Key Account Manager |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 复制原始销售订单的相关信息，包括客户信息、销售订单编号、退货原因等。                                                                                                                                                                                                                                                                                              |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 关键字段：                                                                                                                                                                                                                                                                                                                                                        |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 后续操作：                                                                                                                                                                                                                                                                                                                                                        |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 0001 收至工厂（注：直接收至冻结库存）                                                                                                                                                                                                                                                                                                                             |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 0002 立即移至可用库存（注：直接收至非限制库存）                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 退款类型：                                                                                                                                                                                                                                                                                                                                                        |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 贷项凭证（注：根据 HC 要求，默认设置为创建贷贷项凭证。退货订单创建完成后，将直接生成贷项凭证）                                                                                                                                                                                                                                                                    |                   |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 换货（注：直接创建免费换货订单，不生成贷项凭证）                                                                                                                                                                                                                                                                                                                  |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 005          | 计划员通知仓库管理员（WHS Admin）更改冻结库存状态                                                                                                                                                                                                                                                                                                                 | N/A               | Planner             |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 006          | 仓库管理员在 SAP 系统中将冻结库存转移至非限制库存                                                                                                                                                                                                                                                                                                                 | MIGO              | WHS Admin           |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 007          | 计划员创建用于换货交付的销售订单（订单类型：OR）。                                                                                                                                                                                                                                                                                                                | VA01              |                     |
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
|              | 复制原始销售订单的相关信息，包括客户信息、销售订单编号、退货原因等。                                                                                                                                                                                                                                                                                              |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 008          | 链接至流程 HC_SAP_DD_SD03_Delivery Process                                                                                                                                                                                                                                                                                                                        | N/A               | WHS Admin           |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 009          | 链接至流程 HC_SAP_DD_SD04-01_Customer Billing                                                                                                                                                                                                                                                                                                                     | N/A               | Planner             |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 010          | 前序步骤 003。质量保证大客户经理判断 HC 可直接为客户换货。因此，质量保证部门通知仓库管理员通过成本中心过账货物（应用：MIGO--- 移动类型 201）。                                                                                                                                                                                                                    | MIGO              | WHS Admin           |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 011          | 前序步骤 003。质量保证大客户经理判断 HC 不能直接为客户换货。本步骤中，质量保证部门将在 SAP 系统中创建贷记通知单请求。                                                                                                                                                                                                                                             | VA01              | Key Account Manager |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
| 012          | 关联流程 HC_SAP_DD_SD04_03-01-Credit Memo and Debit Memo Process                                                                                                                                                                                                                                                                                                  | N/A               | AR Admin            |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+
|              |                                                                                                                                                                                                                                                                                                                                                                   |                   |                     |
+--------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+---------------------+

## Consignment Return Business Process Steps {#consignment-return-business-process-steps .LS_Heading-3}

+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| Process Step | Process Step Description                                              | Transaction/App                | Business Role |
+==============+=======================================================================+================================+===============+
| 001          | Planners need to check if the stock status is A or B .                | N/A                            | Planner       |
|              |                                                                       |                                |               |
|              | A: Return to W stock                                                  |                                |               |
|              |                                                                       |                                |               |
|              | B: W stock Return to Plant.                                           |                                |               |
|              |                                                                       |                                |               |
|              | If A, go to step 101;                                                 |                                |               |
|              |                                                                       |                                |               |
|              | If B, go to step 201.                                                 |                                |               |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 101          | Refer to the Consignment Issue to create a Consignment Return         | VA01                           | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 102          | Create a Consignment Return SO                                        | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 103          | Create Delivery Note                                                  | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 104          | Post Goods Receipt (Return the stock back to W-Stock)                 | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 105          | Billing Process                                                       | N/A                            | AR Admin      |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
|              |                                                                       |                                |               |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 201          | Refer to the Consignment Return to create a Consignment Pick-up Order | N/A                            | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 202          | Create a Consignment Pick-up SO                                       | VA01                           | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 203          | Create Delivery Note                                                  | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 204          | Post Goods Receipt from W-Stock to WHS/ Quality Stock                 | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
|              |                                                                       |                                |               |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| **流程步骤​​** | **​​流程说明**                                                          | **​​事务代码/应用​​**              | **​​业务角色​​**  |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 001          | 计划员需要检查库存的状态是A还是B                                      | N/A                            | Planner       |
|              |                                                                       |                                |               |
|              | A: 客户工厂退货至寄售仓                                               |                                |               |
|              |                                                                       |                                |               |
|              | B: 寄售仓退货至工厂                                                   |                                |               |
|              |                                                                       |                                |               |
|              | 如果是A， 进入步骤101；                                               |                                |               |
|              |                                                                       |                                |               |
|              | 如果是B，进入步骤201                                                  |                                |               |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 101          | 参考寄售发货创建寄售退货                                              | VA01                           | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 102          | 过账寄售退货销售订单（SO）                                            | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 103          | 过账交货单                                                            | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 104          | 过账收货（将库存退回至寄售库存（W-Stock））                           | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 105          | 开票流程                                                              | N/A                            | AR Admin      |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
|              |                                                                       |                                |               |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 201          | 参考寄售退货创建寄售拣配订单                                          | N/A                            | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 202          | 创建寄售拣配销售订单（SO）                                            | VA01                           | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 203          | 创建交货单                                                            | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+
| 204          | 从寄售库存（W-Stock）收货至仓库（WHS）/ 质检库存                      | VL01N/Manage Outbound Delivery | Planner       |
+--------------+-----------------------------------------------------------------------+--------------------------------+---------------+

## HC Functional Requirements {#hc-functional-requirements-6 .LS_Heading-3}

- Planner cannot change the price brought from sales condition records.

## HC Delegation Of Authority {#hc-delegation-of-authority-6 .LS_Heading-3}

- N/A

## Design Considerations / Key Assumptions {#design-considerations-key-assumptions-6 .LS_Heading-3}

- N/A

## Cross Functional Integration Dependencies {#cross-functional-integration-dependencies-6 .LS_Heading-3}

- N/A

## Support / Closing Considerations {#support-closing-considerations-6 .LS_Heading-3}

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

+-------------------+------------------------------------------------------+--------------------------------+---------------------------------+
| **Business Role** | **Role Description**                                 | **Authorization Restrictions** | **Baseline ZRS Role(s)**        |
+===================+======================================================+================================+=================================+
| Planner           | Create, Change & Display Contract & List of Contract | VA43,Manage Sales Contracts    | Z_Planner_CN                    |
|                   +------------------------------------------------------+--------------------------------+                                 |
|                   | Create, Change & Display SO & List of SO             | VA01, VA02, VA03, VA05,        |                                 |
|                   |                                                      |                                |                                 |
|                   |                                                      | Manage Sales Orders            |                                 |
|                   |                                                      |                                |                                 |
|                   |                                                      | List Sales Orders,             |                                 |
|                   |                                                      |                                |                                 |
|                   |                                                      | Track Sales Orders             |                                 |
+-------------------+------------------------------------------------------+--------------------------------+---------------------------------+
|                   |                                                      |                                |                                 |
+-------------------+------------------------------------------------------+--------------------------------+---------------------------------+

# Document Types and Document Flow {#document-types-and-document-flow .LS_Heading-1}

+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| **Document Type**    | **Document Flow**                                                                                                                              |
+======================+================================================================================================================================================+
| OR                   | CQ(Quantity Contract) 🡺OR (Standard Order) 🡺 LF (Delivery) 🡺 WL (material doc) 🡺 F2 (Invoice) -- with collective billing 🡺 RV (Accounting doc) |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| CBFD                 | CBFD (Deliv.Free of Chg Ex) 🡺 LF (Delivery) 🡺 WL (material doc)                                                                                |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| CBAR                 | CBAR(Standard Return)                                                                                                                          |
|                      |                                                                                                                                                |
|                      | F2 (Invoice) 🡺 CR (Credit memo Request) 🡺 LR (Returns Delivery) 🡺 WL (material doc) 🡺 CBRE (Credit for Returns)                                |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| CR                   | CR (Credit Memo Request) 🡺 G2 (Credit Memo)                                                                                                    |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| DR                   | DR (Debit Memo Request) 🡺 L2 (Debit Memo)                                                                                                      |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| CCFU                 | Consignment Fill-up order                                                                                                                      |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| CCIS                 | Consignment Issue                                                                                                                              |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| CCRE                 | Consignment Return                                                                                                                             |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
| CCPU                 | Consignment Pick-up                                                                                                                            |
+----------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

# Reports, Interfaces, Conversions, Enhancements, Forms, and Workflows  {#reports-interfaces-conversions-enhancements-forms-and-workflows .LS_Heading-1}

4.  

5.  

## Reports {#reports .LS_Heading-3}

## Standard Reports {#standard-reports .LS_Heading-3}

This solution is pre-configured to include the following Standard Reports.

  -------------------------------------------------------------------------------
  **SAP App**                      **Description / Usage**
  -------------------------------- ----------------------------------------------
  Sales Volume Flexible Analysis   

  Sales Volume Check Open Sales    

  Sales Volume Open Sales by Org   

  Sales Order Items Backorders     

  Track Sales Orders               

  List Sales Orders                

  Manage Sales Contracts           

  Manage Sales Orders              
  -------------------------------------------------------------------------------

## HC Requested Reports {#hc-requested-reports .LS_Heading-3}

Home Control has requested the following additional reports.

+------------------------------------------------------------------------------------------------------------------------+
| **Reports**                                                                                                            |
+-----------------+--------------------+----------------+------------------+----------------+----------------------------+
| **Report Name** | **Description**    | **Key Files**  | **Std.**         | **Complexity** | **Comment**                |
|                 |                    |                |                  |                |                            |
|                 |                    |                | **SAP App/Rprt** |                |                            |
+:================+====================+:===============+:=================+:===============+:===========================+
| ZSD010          | Sales Order Report |                |                  | L2             | multi customized CDS views |
+-----------------+--------------------+----------------+------------------+----------------+----------------------------+
| ZSD006          | CLISP report       |                |                  | L2             | BTP                        |
+-----------------+--------------------+----------------+------------------+----------------+----------------------------+

## Interfaces {#interfaces .LS_Heading-3}

The following interfaces have been identified as in scope:

+------------------------------------------------------------------------------------------------+
| **Interfaces**                                                                                 |
+------------------+------------------+------------------+------------------+--------------------+
| **Interface**    | **Description**  | **In Scope**     | **Complexity**   | **Comments**       |
+:=================+:=================+:=================+:=================+:===================+
| NA               |                  |                  |                  |                    |
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
| Open SO       |                   | Low                       | Med                        | TBD           |                |
|               |                   |                           |                            |               |                |
| 未清SO        |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
| Contracts     |                   | Low                       | Med                        | TBD           |                |
|               |                   |                           |                            |               |                |
| 合同          |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|               |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+
|               |                   |                           |                            |               |                |
+---------------+-------------------+---------------------------+----------------------------+---------------+----------------+

## Enhancements {#enhancements .LS_Heading-3}

The following solution enhancements have been identified as in scope:

+------------------------------------------------------------------------------------------------------------------------+
| **Enhancements**                                                                                                       |
+-------------------------+------------------+------------------+------------------+-------------------------------------+
| **Enhancement**         | **Description**  | **Complexity**   | **In Scope**     | **Comments**                        |
+=========================+==================+==================+==================+=====================================+
| Can not change SO price |                  |                  |                  | Need to judge different order tyep. |
+-------------------------+------------------+------------------+------------------+-------------------------------------+
|                         |                  |                  |                  |                                     |
+-------------------------+------------------+------------------+------------------+-------------------------------------+
| **增强项​​**              | **​​描述​​**         | **​​复杂度​​**       | **​​在范围内​​**     | **​​注释​​**                            |
+-------------------------+------------------+------------------+------------------+-------------------------------------+
| N/A                     |                  |                  |                  |                                     |
+-------------------------+------------------+------------------+------------------+-------------------------------------+
| 销售订单价格不允许修改  |                  | L1               |                  | 根据订单类型来。                    |
|                         |                  |                  |                  |                                     |
|                         |                  |                  |                  | CR/DR 类型的销售订单可以修改价格。  |
|                         |                  |                  |                  |                                     |
|                         |                  |                  |                  | OR/CCFU/CCIS/CCPU/CBRE不可修改。    |
+-------------------------+------------------+------------------+------------------+-------------------------------------+

## Forms {#forms .LS_Heading-3}

The following forms have been identified as in scope:

+---------------------------------------------------------------------------------------------------+
| **Forms**                                                                                         |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **Form**          | **Description**   | **Complexity**    | **In Scope**      | **Comments**      |
+===================+===================+===================+===================+===================+
| US Need SO Form   |                   |                   |                   | Provided          |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| **表单​​**          | **​​描述​​**          | **​​复杂度​​**        | **​​在范围内​​**      | **​​注释​​**          |
+-------------------+-------------------+-------------------+-------------------+-------------------+
| N/A               |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
+-------------------+-------------------+-------------------+-------------------+-------------------+
|                   |                   |                   |                   |                   |
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

# Legend for Process Flow {#legend-for-process-flow .LS_Heading-1}

![](media/media/image10.png){width="6.003662510936133in" height="2.5246161417322837in"}

[^1]: "Import Complexity" denotes the complexity involved in importing the data into SAP S/4 HANA.

[^2]: "Extract Complexity" indicates the complexity involved in extracting the data from the existing legacy systems

    ​**​"导入复杂度"​**​指将数据导入SAP S/4 HANA涉及的复杂性。\
    ​**​"提取复杂度"​**​指从现有遗留系统中提取数据涉及的复杂性。
