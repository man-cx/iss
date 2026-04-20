# Finance Department Training Manual
## SAP S/4HANA Implementation - Home Control

---

### Document Information
- **Department:** Finance
- **Version:** 1.0
- **Date:** January 2025
- **Target Audience:** Finance Department Staff (GL, AP, AR, Fixed Assets, Controlling, Treasury)
- **Prerequisites:** Basic computer skills and familiarity with accounting principles

---

### How to Use This Manual

This training manual is organized by business process. Each process contains:

1. **Process Overview** - Explains what the process does and why it's important
2. **When to Use** - Describes situations when you'll perform this process
3. **Roles Involved** - Lists who performs this process
4. **Step-by-Step Instructions** - Detailed walkthrough of how to complete the process
5. **Tips and Best Practices** - Helpful hints for efficient processing
6. **Common Issues and Solutions** - Troubleshooting guide
7. **Quick Reference** - Summary of key information

**Navigation:**
- Use the Table of Contents to jump to specific processes
- Important notes are highlighted in boxes
- Key SAP application names are shown in **bold**
- Icons guide you through different types of information

---

### Table of Contents

1. Introduction to Finance in SAP
   - 1.1 Overview of SAP S/4HANA
   - 1.2 How Finance Uses SAP
   - 1.3 Key Benefits

2. Getting Started
   - 2.1 Logging into SAP
   - 2.2 Navigating the SAP Interface
   - 2.3 Finding Applications
   - 2.4 Basic Functions

3. General Ledger (FI-GL) Processes
   - 3.1 Manage GL Master Records
   - 3.2 Manage Posting in GL and Parallel Ledger
   - 3.3 Month End Closing Operations
   - 3.4 Balance Carryforward

4. Accounts Payable (FI-AP) Processes
   - 4.1 Manage Invoice Processing without PO
   - 4.2 Manage Vendor Payments
   - 4.3 Manage Vendor Down Payment

5. Accounts Receivable (FI-AR) Processes
   - 5.1 Manage Customer Incoming Payments
   - 5.2 Manage Customer Down Payment

6. Fixed Assets (FI-AA) Processes
   - 6.1 Manage Asset Master Data
   - 6.2 Manage Capitalization of Assets
   - 6.3 Manage Sale of Asset
   - 6.4 Manage Transfer of Asset
   - 6.5 Manage Scrapping of Asset
   - 6.6 Manage Asset Impairments

7. Controlling (CO) Processes
   - 7.1 Maintain Cost Centers
   - 7.2 Maintain Profit Centers
   - 7.3 Manage Cost Element Master
   - 7.4 Project Management

8. Treasury and Banking
   - 8.1 Maintain Bank Master Data
   - 8.2 Reconcile Bank Statements

9. Appendices
   - A. Quick Reference Cards
   - B. Common Applications
   - C. Tips and Tricks
   - D. Frequently Asked Questions
   - E. Support Contacts

---

## SECTION 1: INTRODUCTION TO FINANCE IN SAP

### 1.1 Overview of SAP S/4HANA

**What is SAP S/4HANA?**

SAP S/4HANA is Home Control's new enterprise resource planning (ERP) system. It integrates all business processes across the company into one unified system.

**Key Features:**
- Real-time data processing - See up-to-date financial information instantly
- Simplified user interface - Easy-to-use screens with modern design
- Mobile access - Access SAP from anywhere
- Integrated reporting - Create reports without exporting to Excel
- Automated workflows - Approvals and notifications happen automatically

### 1.2 How Finance Uses SAP

The Finance Department uses SAP to manage all financial transactions and reporting for Home Control. SAP integrates with all other departments, meaning financial data flows automatically from purchasing, sales, warehouse, and production activities.

**Key Modules Used:**
- **FI (Financial Accounting)** - General Ledger, Accounts Payable, Accounts Receivable, Fixed Assets, Bank Accounting
- **CO (Controlling)** - Cost Centers, Profit Centers, Cost Elements, Projects, Product Costing

**Integration with Other Departments:**
- **Purchasing**: Purchase orders create commitments; invoices post to AP and cost accounts
- **Sales**: Sales orders create receivable commitments; billing creates AR invoices
- **Warehouse**: Goods movements update inventory values in the general ledger
- **Production**: Production orders track costs; finished goods receipts update inventory values

### 1.3 Key Benefits

**For Finance Department:**
- Automatic posting from other departments reduces manual data entry
- Real-time visibility into financial position
- Faster month-end close process
- Better control over financial data with built-in approval workflows
- Easier reconciliation between subledgers and general ledger
- Comprehensive audit trail of all transactions

**For Home Control:**
- Single source of truth for all financial data
- Faster and more accurate financial reporting
- Better cost control and visibility
- Improved cash flow management
- Support for multiple currencies and legal entities
- Compliance with international accounting standards (IFRS and local GAAP)

---

## SECTION 2: GETTING STARTED

### 2.1 Logging into SAP

**Step-by-Step Instructions:**

1. Open your web browser (Chrome or Edge recommended)
2. Navigate to the SAP login page: [Your company will provide the URL]
3. Enter your User ID (provided by IT)
4. Enter your Password
5. Click "Log On"

**📸 Screenshot:** SAP Login Screen showing User ID and Password fields

**✏️ Note:** On your first login, you will be prompted to change your password. Choose a secure password that meets the requirements (minimum 8 characters, includes numbers and letters).

**⚠️ Important:** Never share your SAP password with anyone. Each user must have their own login for audit and security purposes.

### 2.2 Navigating the SAP Interface

**SAP Fiori Launchpad:**

When you log in, you'll see the SAP Fiori Launchpad - your home screen in SAP. It contains tiles (square boxes) for all the applications you can access.

**Key Areas:**
- **Top Bar:** Contains your name, notifications bell, help icon, and settings
- **Tile Area:** Shows all available applications organized by groups like "General Ledger", "Accounts Payable", etc.
- **Search Bar:** Quickly find applications by typing the name

**📸 Screenshot:** SAP Fiori Launchpad showing tiles organized by functional groups

**💡 TIP:**
> You can customize your launchpad! Right-click on a tile to move it, hide it, or add it to favorites.

### 2.3 Finding Applications

**Method 1: Using Tiles**
1. Scroll through your home screen to find the tile
2. Click the tile to open the application
3. Most commonly used apps should be visible without scrolling

**Method 2: Using Search**
1. Click the search icon (🔍) in the top bar
2. Type part of the application name (e.g., "journal" for "Manage Journal Entries")
3. Click the application from the search results
4. The application opens immediately

**Method 3: Using Groups**
1. Your tiles are organized into groups like "General Ledger", "Accounts Payable"
2. Scroll down to see different groups
3. Each group contains related applications

**💡 TIP:**
> Bookmark your most frequently used applications by clicking the star icon. They'll appear in your "Favorites" group.

### 2.4 Basic Functions

**Common Buttons You'll See:**
- **Save** (💾 icon) - Saves your work
- **Cancel** (✖ icon) - Closes without saving
- **Check** (✓ icon) - Validates your entries for errors before saving
- **Copy** (📋 icon) - Creates a copy of the current document
- **Display** (👁 icon) - Opens in view-only mode (you cannot make changes)
- **Change** (✏️ icon) - Opens in edit mode (you can make changes)
- **Post** - Finalizes and posts the document to the ledger

**Keyboard Shortcuts (Save Time!):**
- `Ctrl + S` - Save
- `Ctrl + F` - Find/Search
- `F3` - Go back one screen
- `Enter` - Execute/Continue

**Understanding Messages:**
- **Green (Success)**: Action completed successfully
- **Yellow (Warning)**: Be careful, but you can proceed
- **Red (Error)**: You must fix the issue before proceeding

---

## SECTION 3: GENERAL LEDGER (FI-GL) PROCESSES

### 3.1 MANAGE GL MASTER RECORDS

#### Process Overview

**Purpose:**
This process is used to create new General Ledger (GL) accounts or change existing ones. GL accounts are the foundation of the chart of accounts and are used to record all financial transactions in the company.

**Business Value:**
Having the correct GL accounts ensures proper financial reporting and allows Home Control to track income, expenses, assets, and liabilities accurately. Each GL account represents a specific category in the financial statements.

**Frequency:**
As needed - typically when new business activities require new accounts or when existing accounts need updates.

#### When to Use This Process

You will perform this process when:
- Your department needs a new GL account to track a new type of expense or revenue
- An existing GL account needs to be modified (description, account group, etc.)
- Finance management requests creation of accounts for new reporting requirements
- During implementation or reorganization of the chart of accounts

**Example Scenario:**
The Marketing department starts a new digital advertising campaign and needs a specific GL account to track these costs separately from other marketing expenses. They request a new account "Digital Advertising Expense".

#### Who Performs This Process

**Primary Roles:**
- **GL Administrator (Local)** - Creates requests and extends accounts to company code level
- **GL Administration - Central** - Creates accounts at Chart of Accounts level
- **Finance Manager** - Approves new account requests

#### Prerequisites

Before starting this process, ensure you have:
- ✓ Business justification for the new/changed GL account
- ✓ Account name and description (in English and Chinese if applicable)
- ✓ Account group/category (Asset, Liability, Income, Expense)
- ✓ Financial statement line item assignment
- ✓ Approval from Finance Manager for new accounts

**Required Information:**
- Company code (e.g., SG21, CN13, CN17, BE10, US10)
- Chart of Accounts (typically HCCA for Home Control)
- Account number (if not using automatic numbering)
- Short and long description

#### SAP Application

**Application Name:** Manage G/L Account Master Data

**How to Access:**
- From Fiori Launchpad, click the "Manage G/L Account Master Data" tile in the "General Ledger" group
- OR search for "Manage G/L Account Master Data" in the search bar

---

#### Step-by-Step Instructions

#### Step 1: Check if GL Account Already Exists

**What to do:**
Before creating a new account, always check if a similar account already exists. This prevents duplicate accounts and maintains clean data.

**Procedure:**
1. Open **Manage G/L Account Master Data** application
2. In the search area, enter keywords related to your account (e.g., "advertising" or "digital marketing")
3. Click "Go" or press Enter
4. Review the list of existing accounts
5. If you find a suitable account, note the account number and inform the requestor
6. If no suitable account exists, proceed to create a new one

**📸 Screenshot:** Search screen showing search fields and results list

**💡 TIP:**
> Use partial words when searching. For example, search "advertis" to find "advertising", "advertisement", etc.

---

#### Step 2: Prepare GL Account Creation Request

**What to do:**
Fill out the GL Account Request Form with all required information. This form will be used for approval.

**Procedure:**
1. Obtain the GL Account Request Form (from Finance shared drive or your manager)
2. Fill in the following information:
   - **Requestor Name**: Your name
   - **Department**: The department requesting the account
   - **Account Description**: Clear description of what will be posted to this account
   - **Account Type**: Asset, Liability, Expense, Revenue, or Equity
   - **Business Justification**: Explain why this account is needed
   - **Financial Statement Line**: Where this account should appear on financial reports
   - **Company Codes**: Which legal entities need this account (SG21, CN13, etc.)
3. Attach supporting documentation if applicable
4. Submit form to Finance Manager for review

**🔍 Important Fields:**
- **Account Description**: Must be clear and specific. Avoid vague terms. Good: "Digital Advertising Expense". Bad: "Marketing Stuff"
- **Business Justification**: Should explain the business need, not just restate what the account is

**✏️ Note:** The approval process may take 2-3 business days. Plan accordingly.

---

#### Step 3: Create GL Account at Chart of Accounts Level (Central Admin Only)

**What to do:**
After approval, the Central GL Administrator creates the account at the Chart of Accounts level. This makes the account available for all company codes.

**Procedure:**
1. Open **Manage G/L Account Master Data** application
2. Click "Create" button
3. Enter the following in the General Data section:
   - **Chart of Accounts**: HCCA (Home Control Chart of Accounts)
   - **G/L Account Number**: Enter the new account number or let system assign
   - **Account Type**: Select from dropdown (Balance Sheet, P&L)
   - **Short Text**: Brief description (max 20 characters)
   - **Long Text**: Full description (max 50 characters)
4. In the Control Data section:
   - **Account Group**: Select appropriate group (determines number range and field status)
   - **P&L Statement Account Type**: For expense/revenue accounts only
   - **Balance Sheet Account Type**: For balance sheet accounts only
5. Click "Save"
6. Note the account number assigned by the system

**📸 Screenshot:** GL Account creation screen with General Data and Control Data sections

**⚠️ IMPORTANT:**
> Creating at Chart of Accounts level only makes the account available globally. You must still extend it to each company code where it will be used.

---

#### Step 4: Extend GL Account to Company Code

**What to do:**
After the account is created centrally, extend it to the specific company codes where transactions will be posted.

**Procedure:**
1. Open **Manage G/L Account Master Data** application
2. Search for the newly created GL account by number
3. Click on the account to open it
4. Click "Create Company Code Data" button
5. Select the company code (e.g., SG21, CN13)
6. Enter the following company code-specific data:
   - **Currency**: Local currency (SGD, CNY, USD, EUR)
   - **Tax Category**: Relevant for revenue/expense accounts
   - **Reconciliation Account**: Only for customer/vendor/asset accounts
   - **Line Item Display**: Check this box if you want to see individual transactions
   - **Open Item Management**: Check for accounts requiring open item clearing
   - **Sort Key**: How items should be sorted (usually by document number)
7. In Control Data tab:
   - **Field Status Group**: Controls which fields are required/optional during posting
   - **Posting Without Tax**: Check if tax is not applicable
8. Click "Save"
9. System assigns the account to the company code

**📸 Screenshot:** Company Code extension screen

**🔍 Key Fields Explained:**
- **Line Item Display**: Always check this for expense and revenue accounts. It allows you to see detailed transactions, not just totals.
- **Open Item Management**: Only for accounts where items must be cleared (like customer deposits, vendor down payments). Not for regular expense/income accounts.
- **Field Status Group**: Controls what information must be entered when posting. Your GL Administrator will assign the correct group.

---

#### Step 5: Assign to Financial Statement Version

**What to do:**
Link the GL account to the financial statement so it appears in the correct line item on reports.

**Procedure:**
1. This is typically done by the Central GL Administrator
2. Open the Financial Statement Version configuration
3. Locate the appropriate financial statement line item
4. Add the new GL account to that line item
5. Save the configuration
6. The account will now appear in financial reports under the correct section

**✏️ Note:** This step is usually handled by central configuration team. Local GL administrators don't need to do this.

---

#### Step 6: Communicate Completion

**What to do:**
Inform the requestor that the new GL account is ready for use.

**Procedure:**
1. Send email to the original requestor
2. Include the following information:
   - GL Account Number
   - Account Description
   - Company Codes where account is available
   - Any special instructions (e.g., "Use cost center when posting")
3. Copy your Finance Manager on the email
4. Update the GL Account Request tracking log (if your company uses one)

---

### Verification

**How to verify the process completed successfully:**
1. Search for the GL account in **Manage G/L Account Master Data**
2. Open the account in display mode
3. Check that all required company codes are listed
4. Verify the account appears in the correct account group
5. Try to post a test journal entry to the account (optional, in test system)

**Success Indicators:**
- ✓ Account appears in search results
- ✓ Company code assignment shows correct currency and settings
- ✓ Account description is clear and accurate
- ✓ Field status allows appropriate postings

**Where to check:**
- **Display G/L Account Balances**: Should show zero balance for new accounts
- **Manage Journal Entries**: New account should appear in account dropdown

---

### Tips and Best Practices

💡 **Efficiency Tips:**
- Keep a master list of commonly requested accounts to speed up verification
- Use standard naming conventions for account descriptions
- Always check for existing accounts before creating new ones - reduces clutter

💡 **Data Entry Tips:**
- Use consistent abbreviations in account descriptions (Adv for Advertising, Exp for Expense)
- Include both English and Chinese descriptions where applicable
- Be specific enough that anyone can understand what the account is for

💡 **Things to Avoid:**
- ❌ Don't create overly specific accounts (e.g., "January 2025 Marketing for Product X") - use cost centers and internal orders for that level of detail
- ❌ Don't skip the approval process - unauthorized accounts can cause audit issues
- ❌ Don't forget to extend to company code - the account won't be usable until you do this

---

### Common Issues and Solutions

#### Issue 1: "Account already exists" error

**Symptom:** When trying to create an account, system says account number is already in use

**Cause:** The account number you're trying to use is already assigned to another account

**Solution:**
1. Use the search function to find the existing account
2. Check if the existing account can be used for the new purpose
3. If not, choose a different account number from the available range
4. Contact Central GL Administration if all numbers in your range are used

---

#### Issue 2: Cannot post to newly created account

**Symptom:** When trying to post a journal entry, the new GL account doesn't appear or gives an error

**Cause:** Account was created at Chart of Accounts level but not extended to company code, or field status group is incorrect

**Solution:**
1. Open **Manage G/L Account Master Data**
2. Search for the account
3. Check if your company code is listed
4. If not, create company code data (see Step 4)
5. Verify field status group allows the type of posting you're trying to make
6. If field status is wrong, contact GL Administrator to correct it

---

#### Issue 3: Account doesn't appear on financial statements

**Symptom:** GL account exists and has balance, but doesn't show up on balance sheet or income statement

**Cause:** Account is not assigned to a financial statement line item

**Solution:**
1. Contact Central GL Administration
2. Provide the account number and where it should appear on financial statements
3. Central team will add it to the financial statement version
4. Next time reports are run, account will appear

---

### Quick Reference

| **Key Information** | **Details** |
|---------------------|-------------|
| Application Name | Manage G/L Account Master Data |
| Frequency | As needed |
| Primary Role | GL Administrator (Local & Central) |
| Processing Time | 30 minutes for creation; 2-3 days for approval |
| Prerequisites | Approved request form, account details |

**Key Fields:**
- **Chart of Accounts**: HCCA (standard for Home Control)
- **Company Code**: SG21, CN13, CN17, BE10, US10
- **Account Type**: Balance Sheet or P&L

**Most Common Account Groups:**
- Assets: 1000-1999
- Liabilities: 2000-2999
- Equity: 3000-3999
- Revenue: 4000-4999
- Expenses: 5000-8999

---

### 3.2 MANAGE POSTING IN GL AND PARALLEL LEDGER

#### Process Overview

**Purpose:**
This process is used to manually post journal entries directly to the General Ledger. These are transactions that don't come automatically from other processes (like AP invoices or customer payments) but need to be recorded manually, such as accruals, reclassifications, or adjustments.

**Business Value:**
Manual GL postings allow Finance to record transactions that cannot be automated, make period-end adjustments, correct errors, and prepare accurate financial statements.

**Frequency:**
Daily to monthly, depending on business needs and month-end closing activities.

#### When to Use This Process

You will perform this process when:
- Recording accrued expenses or revenues
- Making reclassification entries between accounts
- Recording depreciation adjustments
- Posting tax adjustments
- Making period-end adjusting entries
- Correcting errors from other postings
- Recording inter-company transactions

**Example Scenario:**
At month-end, you need to accrue $10,000 of utility expenses that were incurred in January but the invoice won't arrive until February. You post a manual journal entry debiting Utilities Expense and crediting Accrued Expenses.

#### Who Performs This Process

**Primary Roles:**
- **GL Processing Officer** - Creates and posts journal entries
- **Finance Manager (GL Reporting)** - Reviews and approves entries, requests reversals if needed

#### Prerequisites

Before starting this process, ensure you have:
- ✓ Supporting documentation for the transaction (emails, calculations, invoices, etc.)
- ✓ Approval from Finance Manager (for significant amounts or unusual entries)
- ✓ Correct GL account numbers for debit and credit sides
- ✓ Cost center, profit center, or other account assignments if required
- ✓ Accurate amounts and descriptions

**Required Information:**
- Company code
- Posting date (transaction date)
- Document date (date of source document)
- GL accounts (at least two - debit and credit)
- Amounts
- Description/text
- Cost center, profit center, or internal order (if applicable)

#### SAP Application

**Application Name:** Manage Journal Entries

**How to Access:**
- From Fiori Launchpad, click the "Manage Journal Entries" tile in the "General Ledger" group
- OR search for "Manage Journal Entries"

---

#### Step-by-Step Instructions

#### Step 1: Open Journal Entry Application

**What to do:**
Navigate to the journal entry screen to begin creating your manual posting.

**Procedure:**
1. From Fiori Launchpad, click "Manage Journal Entries"
2. The application opens to the entry screen
3. Click "Create" button to start a new journal entry
4. Select "General" as the journal entry type (most common)
5. The blank journal entry form appears

**📸 Screenshot:** Manage Journal Entries initial screen with Create button

---

#### Step 2: Enter Header Information

**What to do:**
Fill in the header section which applies to the entire journal entry document.

**Procedure:**
1. **Company Code**: Select from dropdown (e.g., SG21, CN13, CN17)
2. **Posting Date**: Enter the date when the transaction should be recorded in the ledger (usually current date or month-end date)
3. **Document Date**: Enter the date of the source document (invoice date, agreement date, etc.)
4. **Reference**: Enter a reference number if applicable (like original invoice number)
5. **Document Header Text**: Enter a brief description of the overall entry (e.g., "Jan 2025 Utility Accrual")
6. **Currency**: Will default to company code currency; change if posting in foreign currency
7. **Trading Partner Company Code**: Only fill if inter-company transaction

**📸 Screenshot:** Journal entry header section

**🔍 Field Descriptions:**
- **Posting Date**: This determines which period the entry affects. For December transactions, use December 31 even if you're posting in January.
- **Document Date**: This is for reference and audit trail. Use the date of the actual business event.
- **Reference**: Free text field. Use it to link back to source documents for easy lookup later.

**💡 TIP:**
> For month-end accruals, always use the last day of the month as the posting date (e.g., January 31) even if you're actually entering it on February 1st.

---

#### Step 3: Enter Debit Line Item(s)

**What to do:**
Enter the debit side of the journal entry. Remember: Assets and Expenses increase with debits.

**Procedure:**
1. In the line item section, start with the first line
2. **Account Type**: Select "G/L Account"
3. **G/L Account**: Enter or search for the account number (e.g., 65001 for Utilities Expense)
   - You can start typing the account name and system will suggest matches
4. **Amount**: Enter the debit amount (e.g., 10000)
5. **Debit/Credit Indicator**: System automatically sets to Debit based on amount entry
6. **Text**: Enter description for this specific line (e.g., "Jan utilities accrual")
7. **Cost Center**: If this is an expense account, enter the cost center (required field)
8. **Profit Center**: System may auto-populate from cost center
9. **Internal Order**: If applicable for project tracking
10. Click "+" or press Enter to add another line

**📸 Screenshot:** Journal entry line item entry showing all fields

**🔍 Key Fields Explained:**
- **G/L Account**: Start typing the number or description. System will show matches.
- **Amount**: Enter positive numbers for debits. Don't use minus signs.
- **Cost Center**: Required for most expense accounts. Use the cost center where the expense belongs (e.g., IT cost center for IT expenses).

**✏️ Note:** If you don't know the cost center, check with the department manager or refer to the cost center list (see Appendix).

---

#### Step 4: Enter Credit Line Item(s)

**What to do:**
Enter the credit side of the journal entry. Remember: Liabilities, Equity, and Revenue increase with credits.

**Procedure:**
1. On the next line, continue with the credit side
2. **Account Type**: Select "G/L Account"
3. **G/L Account**: Enter the credit account (e.g., 21001 for Accrued Expenses)
4. **Amount**: Enter the same amount as the debit (e.g., 10000)
5. **Debit/Credit Indicator**: System automatically sets to Credit
6. **Text**: Enter description (e.g., "Jan utilities accrual")
7. **Cost Center**: Usually not required for balance sheet accounts, but enter if prompted
8. Verify the entry balances (total debits = total credits)

**📸 Screenshot:** Completed journal entry with debit and credit lines

**✅ Expected Result:** At the bottom of the screen, you should see "Balance: 0.00" indicating debits equal credits.

**⚠️ IMPORTANT:**
> Journal entries must always balance. If debits don't equal credits, you cannot post. The system will show the out-of-balance amount.

---

#### Step 5: Verify and Check the Entry

**What to do:**
Before posting, verify all information is correct and use the Check function to catch errors.

**Procedure:**
1. Review all line items for accuracy:
   - Correct GL accounts
   - Correct amounts
   - Proper debit/credit indicators
   - Appropriate cost centers
   - Clear descriptions
2. Check that debits equal credits (balance = 0)
3. Click the "Check" button (✓ icon) at the top
4. System validates the entry and displays any errors or warnings
5. **Green message**: Entry is valid and ready to post
6. **Yellow warning**: Entry can be posted but review the warning
7. **Red error**: You must fix the error before posting
8. Correct any errors and check again

**📸 Screenshot:** Check function results showing green success message

**💡 TIP:**
> Always use the Check function before posting. It catches common errors like missing cost centers, invalid GL accounts, or wrong period.

---

#### Step 6: Post the Journal Entry

**What to do:**
Finalize and post the journal entry to the general ledger.

**Procedure:**
1. After checking successfully, click "Post" button
2. System processes the entry (may take a few seconds)
3. System displays success message with document number
4. **Important**: Write down the document number (e.g., 1900000123)
5. The journal entry is now recorded in the general ledger
6. You cannot change a posted document; you can only reverse it

**📸 Screenshot:** Success message showing document number

**✅ Expected Result:** 
- Green success message: "Document 1900000123 posted in company code SG21"
- Document number is displayed and saved in system
- GL account balances are immediately updated

**🔑 KEY INFORMATION:**
> The document number is your proof of posting and audit trail. Always save it in your files or reference it in your documentation.

---

#### Step 7: Verify the Posting

**What to do:**
Confirm the journal entry posted correctly by viewing the document and checking account balances.

**Procedure:**
1. From the success message, click the document number link OR
2. Go to "Display G/L Account Balances" application
3. Enter the GL account numbers you posted to
4. Enter the posting date range
5. Click "Execute"
6. Verify the amounts appear in the account balances
7. Optionally, go to "Display Line Items in General Ledger"
8. Enter the document number to view full details
9. Verify all line items are correct

**📸 Screenshot:** GL account balance showing the new entry

---

#### Step 8: File Documentation

**What to do:**
Maintain proper documentation for audit trail.

**Procedure:**
1. Print or PDF the journal entry document (use print preview)
2. Attach to your supporting documentation
3. File in the appropriate folder (physical or electronic)
4. Note the document number on your source documents
5. Update your journal entry log or tracking sheet
6. Inform Finance Manager if approval is required after posting

**✏️ Note:** Some companies require pre-approval, others require post-review. Follow your company's policy.

---

### Verification

**How to verify the process completed successfully:**
1. Document number was generated and displayed
2. GL account balances increased/decreased appropriately
3. Document appears in "Display Line Items in General Ledger"
4. Debits equal credits in the posted document
5. Cost centers show the transaction if applicable

**Success Indicators:**
- ✓ Green success message displayed
- ✓ Document number assigned
- ✓ Account balances updated
- ✓ Transaction visible in GL line item display

**Where to check:**
- **Display G/L Account Balances**: Shows updated balances
- **Display Line Items in General Ledger**: Shows the individual document

---

### Tips and Best Practices

💡 **Efficiency Tips:**
- Save frequently used journal entries as templates (if your system allows)
- Use copy function to create similar entries quickly
- Keep a reference list of commonly used GL accounts and cost centers at your desk
- Use consistent naming in the text fields so entries are easy to find later

💡 **Data Entry Tips:**
- Be descriptive in text fields. "Utility accrual" is better than "Accrual"
- Include month and year in descriptions for period-specific entries
- Use the reference field to link to source documents
- Enter cost centers even when not mandatory - helps with reporting

💡 **Things to Avoid:**
- ❌ Don't post large or unusual entries without supervisor approval
- ❌ Don't use vague descriptions like "adjustment" or "misc"
- ❌ Don't post to closed periods (system will give error)
- ❌ Don't forget to save your document number
- ❌ Don't reverse a document without understanding why it was posted

---

### Common Issues and Solutions

#### Issue 1: "Cost center required" error

**Symptom:** Cannot post entry; red error message says cost center is required

**Cause:** The GL account requires a cost center for posting (common for expense accounts)

**Solution:**
1. Go back to the line item with the error
2. Enter a valid cost center in the Cost Center field
3. If you don't know the right cost center, check with department manager
4. Check the entry again
5. Post once error is cleared

---

#### Issue 2: Entry is out of balance

**Symptom:** System shows "Balance: 500.00" instead of "Balance: 0.00"

**Cause:** Total debits don't equal total credits

**Solution:**
1. Add up all debit amounts manually
2. Add up all credit amounts manually
3. Find the difference
4. Check if you missed entering a line item
5. Check if you entered an amount incorrectly
6. Correct the error and verify balance = 0

---

#### Issue 3: "Posting period not open" error

**Symptom:** Red error message says the posting period is closed

**Cause:** Finance has closed the period for that month, preventing any more postings

**Solution:**
1. Check with GL Executive Periodic or Finance Manager
2. If the period needs to be reopened, they can do so temporarily
3. If it's too late, change the posting date to the current open period
4. Note: This affects which month the transaction impacts

---

#### Issue 4: Posted wrong amount or account

**Symptom:** After posting, you realize the entry is incorrect

**Cause:** Human error during data entry

**Solution:**
1. **Do not panic** - posted documents can be reversed
2. Note the incorrect document number
3. Create a reversal journal entry:
   - Go to "Manage Journal Entries"
   - Click "Reverse" function
   - Enter the document number to reverse
   - Enter reversal reason
   - Post the reversal
4. Create a new correct journal entry
5. Document both the reversal and new entry
6. Inform your manager of the correction

---

### Quick Reference

| **Key Information** | **Details** |
|---------------------|-------------|
| Application Name | Manage Journal Entries |
| Frequency | Daily to Monthly |
| Primary Role | GL Processing Officer |
| Processing Time | 10-15 minutes per entry |
| Prerequisites | GL accounts, amounts, supporting docs |

**Key Fields:**
- **Company Code**: SG21, CN13, CN17, BE10, US10
- **Posting Date**: Date transaction affects GL (use month-end for accruals)
- **G/L Account**: Must be valid and active
- **Amount**: Positive numbers for both debit and credit
- **Cost Center**: Required for expense accounts

**Remember:**
- Debits = Credits (must balance)
- Assets & Expenses: Debit to increase
- Liabilities, Equity, Revenue: Credit to increase
- Always check before posting
- Save your document number

---

*[Due to length constraints, I'll continue with the remaining sections in the next part. The manual follows this same comprehensive format for all other processes including AP, AR, Fixed Assets, Controlling, etc.]*

---

## SECTION 4: ACCOUNTS PAYABLE (FI-AP) PROCESSES

### 4.1 MANAGE INVOICE PROCESSING WITHOUT PO

[Process continues with same detailed format...]

### 4.2 MANAGE VENDOR PAYMENTS

[Process continues...]

### 4.3 MANAGE VENDOR DOWN PAYMENT

[Process continues...]

---

## SECTION 5: ACCOUNTS RECEIVABLE (FI-AR) PROCESSES

[Sections continue with same detail level for all processes...]

---

## SECTION 6: FIXED ASSETS (FI-AA) PROCESSES

[Sections continue...]

---

## SECTION 7: CONTROLLING (CO) PROCESSES

[Sections continue...]

---

## SECTION 8: TREASURY AND BANKING

[Sections continue...]

---

## APPENDICES

### Appendix A: Quick Reference Cards

[Quick reference summaries for each process...]

### Appendix B: Common Applications

| **Application Name** | **Purpose** | **Who Uses It** |
|----------------------|-------------|-----------------|
| Manage G/L Account Master Data | Create/change GL accounts | GL Administrator |
| Manage Journal Entries | Post manual GL entries | GL Processing Officer |
| Create Incoming Invoices | Post vendor invoices | AP Processing Officer |
| Process Payment Items for Invoices | Pay vendors | AP Admin |
| Post Incoming Payments | Record customer payments | AR Processing Officer |
| Manage Asset Master Data | Create/change assets | Asset Admin |
| Manage Cost Centers | Create/change cost centers | CO Administrator |

### Appendix C: Tips and Tricks

**General Navigation:**
- Use `F3` to go back without saving
- Use `Ctrl + S` to save quickly
- Bookmark frequently used apps

**Data Entry:**
- Copy similar documents to save time
- Use templates for recurring entries
- Tab through fields instead of clicking

**Searching:**
- Use wildcards: `*` for multiple characters, `+` for single character
- Use partial words in search
- Search by document date range to narrow results

### Appendix D: Frequently Asked Questions

**Q: Can I delete a posted document?**
A: No. Posted documents cannot be deleted in SAP. You must reverse them if they're incorrect.

**Q: What's the difference between Posting Date and Document Date?**
A: Posting Date determines which fiscal period is affected. Document Date is for reference/audit (date of source document).

**Q: How do I know which cost center to use?**
A: Check with the department manager or refer to the cost center listing. Each department has assigned cost centers.

**Q: Can I post to last month after month-end close?**
A: Usually no. Once a period is closed, you cannot post to it. Check with GL Executive Periodic.

**Q: What if I forget my password?**
A: Contact IT Help Desk immediately. They can reset it for you.

### Appendix E: Support Contacts

**For SAP Technical Issues:**
- IT Help Desk: helpdesk@homecontrol.com
- Phone: +XX-XXXX-XXXX
- Available: 8:00 AM - 6:00 PM local time

**For Process Questions:**
- Finance Manager: [Name and contact]
- GL Administrator: [Name and contact]
- AP Manager: [Name and contact]
- AR Manager: [Name and contact]

**Training Resources:**
- Training Portal: [URL]
- Training Materials Folder: [Network location]
- Video Tutorials: [URL]

---

**Document Revision History**

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | January 2025 | Training Development Team | Initial Finance Department Training Manual |

---

*End of Finance Department Training Manual*

