# NetBill V2
## Internet Billing Management System

**NetBill V2** is a browser-based Internet Billing Management System designed to manage customer accounts, monthly billing, balances, payments, receipts, customer ledgers, collection reports, and advance payments.

The system is designed for day-to-day ISP billing operations and supports desktop and mobile use.

**Powered by CM Philippines**

---

# 1. System Overview

NetBill V2 provides centralized management of:

- Customer accounts
- Internet plans and monthly rates
- Activation and billing dates
- Existing customer migration
- Monthly billing
- Automatic recurring billing
- Previous and outstanding balances
- Regular and partial payments
- Advance payments
- Payment receipts
- Advance-payment receipts
- Customer ledgers
- Collection history
- Monthly and yearly reports
- Collector audit information
- Receivables
- Account status
- Real-time date and time
- Customer transaction cleanup

The current version uses **Supabase** for persistent customer, billing, and payment data while retaining browser-side functionality where required by the application.

---

# 2. Main Navigation

NetBill V2 contains the following primary sections:

1. Dashboard
2. Customers
3. Billing
4. Payments
5. Ledger
6. Reports
7. ADV. PAYMENT RCPT
8. Logout

---

# 3. Login

NetBill V2 includes a login screen requiring:

- Email
- Password

The main billing interface remains hidden until authentication is completed successfully.

A Logout option is available from the main navigation.

---

# 4. Installation / App Mode

NetBill V2 includes a web-app manifest and supports installation as a standalone application on supported devices.

The application includes:

- NetBill application name
- Standalone display mode
- Theme configuration
- Application icons
- Mobile-friendly layout

Where installation enforcement is active, the system displays an **Install NetBill App** screen before normal system use.

---

# 5. Dashboard

The Dashboard provides an overview of current billing operations.

### Dashboard Metrics

The system displays:

- Total Customers
- Active Accounts
- Unpaid / Overdue Accounts
- Total Collected
- Outstanding Balance

### Recent Customers

The Dashboard also displays recent customer records including:

- Account Number
- Customer Name
- Internet Plan
- Balance
- Status

---

# 6. System Date & Time

NetBill V2 displays:

**SYSTEM DATE & TIME**

in the upper-right portion of the dark NetBill header.

The displayed clock uses the current system/device date and time and updates continuously.

The production billing and advance-payment functions also use real-date processing.

---

# 7. Customer Management

The Customers section manages subscriber information.

Each customer may contain:

- Account Number
- Full Name
- Address
- Contact Number
- Internet Plan
- Monthly Rate
- Activation Date
- Due Date
- Current Bill
- Outstanding Balance
- Account Status

Customer records can be searched by name or account number.

Customers can also be filtered according to status:

- Paid
- Unpaid
- Overdue

---

# 8. Add New Customer

The normal **+ Add Customer** function is intended for newly activated subscribers.

A new customer may include:

- Account Number
- Full Name
- Address
- Contact Number
- Internet Plan
- Monthly Rate
- Activation Date
- Due Date
- Initial Payment Status

The system supports two initial payment conditions:

### Paid Upon Activation

If the customer pays upon activation:

- The activation payment is recorded.
- The activation charge is treated as paid.
- The customer does not carry the activation charge as an unpaid balance.
- A clean activation transaction is reflected in the transaction history.

### Unpaid Upon Activation

If the initial bill is unpaid:

- The monthly charge becomes part of the customer's outstanding balance.
- The amount remains collectible.
- The transaction is reflected in the customer's billing/ledger history.

---

# 9. Add Existing Customer

NetBill V2 includes a separate:

**+ Add Existing Customer**

function.

This is intended for subscribers who already existed before being migrated into NetBill.

Required/available information includes:

- Full Name
- Address
- Contact Number
- Internet Plan
- Monthly Rate
- Due Date
- Existing Balance

### Existing Customer Rules

Existing customers do not require a new activation date.

Their entered **Due Date** becomes the basis for their first recurring billing cycle in NetBill.

The system can also carry an existing unpaid balance into the migrated account.

This prevents migrated customers from being treated as newly activated subscribers.

---

# 10. Account Number Generation

NetBill generates customer account numbers for customer records.

Account numbers are used throughout:

- Customer management
- Payments
- Billing
- Ledger
- Receipts
- Reports

---

# 11. Customer Status

Customer accounts can be classified as:

### Paid
No current outstanding amount requiring payment.

### Unpaid
The account contains an unpaid balance that has not yet reached overdue classification.

### Overdue
The account contains an unpaid balance beyond the applicable due date.

Status information is reflected throughout the system where applicable.

---

# 12. Billing

The Billing section allows the operator to view and manage customer billing.

Information includes:

- Account Number
- Customer
- Current Bill
- Balance
- Due Date
- Status

A manual **Create / Update Bill** function is also available.

The operator can select:

- Customer
- Billing Amount
- Due Date

---

# 13. Automatic Monthly Billing

NetBill V2 supports automatic recurring monthly billing.

For newly activated customers, recurring billing follows the customer's activation/billing cycle.

For migrated existing customers, recurring billing uses the entered due date as the starting billing reference.

### Automatic Billing Behavior

The system can:

- Detect billing cycles that have become due
- Generate monthly charges
- Add new charges to existing unpaid balances
- Update the customer's balance
- Update the customer's due date
- Persist billing information
- Record the billing transaction
- Prevent the same billing cycle from being repeatedly generated

If the system was not opened during an earlier billing cycle, the automatic billing process can process applicable missed cycles when the system runs again.

---

# 14. Previous Balance Carry-Forward

Outstanding balances are not discarded when a new monthly bill is generated.

Example:

Previous Balance: ₱500  
New Monthly Charge: ₱1,500  

New Running Balance:

**₱2,000**

This allows NetBill to maintain continuous customer receivables.

---

# 15. Duplicate Billing Protection

Automatic monthly billing includes protection against generating the same billing cycle repeatedly.

Refreshing or reopening the system should not intentionally create another copy of an already processed monthly billing cycle.

---

# 16. Payments

The Payments section allows operators to record customer payments.

Payment information includes:

- Customer
- Amount Paid
- Payment Date
- Payment Time
- Reference Number
- Collected By

A customer search field is available to simplify customer selection, especially when the subscriber list becomes large.

---

# 17. Payment Date & Time

NetBill stores payment date and payment time separately.

This allows operators to record:

- Payments made at the current time
- Late-entered transactions
- Transactions that need their actual payment date/time recorded

The receipt displays the recorded payment date and payment time.

---

# 18. Collected By

Every payment can record the staff member or collector responsible for receiving the payment.

The collector information is used in:

- Payment History
- Receipts
- Monthly reports
- Yearly reports
- Collector audit reports

The receipt displays this as:

**Payment Received By**

---

# 19. Partial Payments

Regular customer payments may reduce an existing balance.

The system tracks:

- Balance Before
- Amount Paid
- Balance After

This allows partial payments without losing the remaining collectible balance.

---

# 20. Regular Payment Validation

If a customer currently has an outstanding balance, regular payment processing is used first.

Payments should not incorrectly bypass an existing outstanding balance and become advance payments.

This separates:

- Payment of existing debt
- Payment for a future billing period

---

# 21. Advance Payment

NetBill V2 includes an **Advance Payment** option beside the Amount Paid field.

Advance Payment is intended for customers who want to pay a future monthly bill before its due date.

### Advance Payment Conditions

An advance payment is accepted when:

- The customer's current outstanding balance is zero.
- The advance payment amount equals the customer's monthly rate.

If an outstanding balance exists, that balance must be settled before a separate advance payment is recorded.

---

# 22. Advance Payment Amount

An advance payment corresponds to one monthly billing amount.

Example:

Monthly Rate: **₱1,500**

Valid Advance Payment:

**₱1,500**

This allows each advance transaction to be associated clearly with one future billing due date.

---

# 23. Advance Payment Covered Due Date

Each advance payment is assigned a future **Covered Due Date**.

The system checks the customer's due-date sequence and existing advance reservations.

If the next due date has already been covered by another advance payment, the new advance payment is allocated to the next available billing month.

Example:

First Advance Payment  
Covered Due Date: **October 25**

Second Advance Payment  
Covered Due Date: **November 25**

This prevents multiple advance payments from unintentionally covering the same billing period.

---

# 24. Advance Payment Database Information

Advance-payment transactions use advance-payment information including:

- `is_advance`
- `advance_for_date`

These fields identify:

- Whether a payment is an advance payment
- Which future due date the payment covers

Legacy advance-payment data may also exist from earlier development/testing stages.

---

# 25. Advance Payment Receipt

An advance payment generates an official payment receipt when the payment is originally received.

The receipt clearly displays:

**ADVANCE PAYMENT**

and:

**For Due Date: YYYY-MM-DD**

This allows both the operator and customer to identify which future billing period has already been paid.

---

# 26. ADV. PAYMENT RCPT Section

NetBill V2 contains a dedicated:

**ADV. PAYMENT RCPT**

navigation section.

This section is used to surface advance payments whose **Covered Due Date is today**.

The section does not simply display every advance payment continuously.

Its purpose is to remind the operator that a customer's previously paid advance payment now corresponds to the current billing due date.

---

# 27. Advance Receipt Due-Today Detection

The system compares the current date with each advance payment's covered due date.

If:

**Covered Due Date = Today**

the applicable advance-payment receipt appears in the ADV. PAYMENT RCPT section.

If no advance payment covers the current date, the section displays:

**No advance payment receipts due today.**

---

# 28. Advance Payment Receipt Notification

When an advance-payment receipt is due today, the:

**ADV. PAYMENT RCPT**

navigation button provides a visual notification.

### Notification Behavior

If a receipt is due today and the ADV. PAYMENT RCPT section is not active:

**The button blinks white.**

If the operator opens ADV. PAYMENT RCPT:

**The button becomes steady blue.**

If the operator leaves the section while the due-today record still exists:

**The white blinking resumes.**

The blinking continues throughout the applicable covered due date.

It is not permanently dismissed merely because the operator viewed the receipt.

---

# 29. Advance Receipt View Function

Due advance-payment records include a **View** action.

Selecting View opens the original official advance-payment receipt.

The receipt retains the original transaction information, including:

- Original Receipt Number
- Original Payment Date
- Original Payment Time
- Account Number
- Customer
- Internet Plan
- Reference
- Payment Received By
- Amount Paid
- Remaining Balance
- Covered Due Date

The original payment date is not replaced by the later covered due date.

---

# 30. Official Payment Receipt

NetBill V2 generates an official payment receipt for recorded payments.

Receipt information can include:

- Receipt Number
- Payment Date
- Payment Time
- Account Number
- Customer Name
- Internet Plan
- Reference
- Payment Received By
- Amount Paid
- Remaining Balance
- Receipt Created Date & Time

For advance payments, the receipt additionally displays:

- ADVANCE PAYMENT
- Covered Due Date

---

# 31. Receipt Numbering

NetBill generates receipt numbers for payment transactions.

Receipt numbers provide transaction identification and are used in:

- Payment History
- Receipts
- Ledger references
- Reports
- Audit tracking

---

# 32. Receipt Created Date & Time (CDT)

Receipts include a separate receipt creation timestamp.

This allows NetBill to distinguish between:

### Payment Date & Time
The date/time the payment was actually recorded as having occurred.

### CDT
The date/time the receipt was generated/viewed.

This is useful when older payments are entered or when a receipt is viewed again later.

---

# 33. Downloadable Receipt

NetBill supports downloading payment receipts for:

- Record keeping
- Customer copies
- Messaging
- Digital sharing
- Printing through supported applications/devices

Receipt functionality was designed to work conveniently on mobile devices.

---

# 34. Payment History

Recorded payments are displayed in Payment History.

Information can include:

- Date
- Receipt Number
- Customer
- Amount
- Reference
- Issued/Collected By
- Balance After
- Receipt View action

---

# 35. Customer Ledger

NetBill V2 includes a per-customer ledger.

The operator selects a customer and can view:

- Customer Name
- Account Number
- Current Balance

Ledger transactions contain:

- Date
- Type
- Description
- Previous Balance
- Charge
- Payment
- Running Balance
- Reference

---

# 36. Ledger Transaction Types

The ledger can represent billing and payment activity such as:

- Activation billing
- Monthly billing
- Payments
- Balance changes

This provides a running financial history for each subscriber.

---

# 37. Ledger Running Balance

Each ledger transaction records the resulting running balance.

This allows the operator to trace how the customer's balance changed over time rather than viewing only the latest balance.

---

# 38. Mobile Ledger Layout

On smaller screens, the customer ledger is converted into a mobile-friendly card-style layout.

This improves readability on smartphones without requiring a full desktop-sized table.

---

# 39. Reports

The Reports section provides summary information including:

- Total Payments
- Total Revenue
- Total Receivables
- Account Status Summary

NetBill also provides historical collection reporting.

---

# 40. Collection History

Collection History allows the operator to generate:

### Monthly Reports

Select:

- Year
- Month

The report can contain individual payment transactions for the selected month.

### Yearly Reports

Select:

- Year

The report summarizes collection activity across January through December.

---

# 41. XLSX Reports

NetBill V2 supports true `.xlsx` report generation.

Reports are designed for use in:

- Microsoft Excel
- WPS Office
- Similar spreadsheet applications

The reports use structured worksheets and readable formatting.

---

# 42. Monthly Detailed Report

Monthly payment reports can include:

- Date
- Receipt Number
- Client
- Account Number
- Reference
- Amount Paid
- Outstanding Balance
- Collected By

The monthly report also provides collection totals.

---

# 43. Yearly Payment Audit

Yearly reporting includes detailed payment audit information.

The detailed transaction structure follows the collection reporting format and supports historical reconciliation.

---

# 44. Collector Audit / Summary

Collection reports include collector accountability information.

This allows management to review:

- Collector/Staff Name
- Number of Payments
- Amount Collected

This supports collection reconciliation and audit requirements.

---

# 45. Outstanding Balance Reports

Reports can include current outstanding customer balances.

Information may include:

- Account Number
- Customer
- Status
- Due Date
- Outstanding Balance

This helps identify current receivables.

---

# 46. Search and Filtering

NetBill includes search/filter functionality in applicable sections.

Examples include:

### Customer Search
Search using customer name or account number.

### Customer Status Filter
Filter by:

- Paid
- Unpaid
- Overdue

### Payment Customer Search
Search for the customer before recording payment.

### Report Filters
Select reporting year/month or report type.

---

# 47. Customer Editing

Existing customer records can be edited.

Editable information may include customer and billing-related account information according to the customer form.

Changes are persisted to the connected database.

---

# 48. Customer Deletion

NetBill V2 supports permanent customer deletion.

The operator receives a confirmation prompt before deletion.

Deletion behavior was tested during V2 development to ensure that removed test customers do not continue appearing in active system information.

Related payment/history cleanup behavior was also tested during V2 development.

---

# 49. Supabase Persistence

NetBill V2 uses Supabase-backed data for core billing operations.

Important data areas include:

### Clients
Customer/account information.

### Billing
Generated billing records and billing-cycle information.

### Payments
Payment transactions, receipt information, balances, collector information, and advance-payment information.

---

# 50. Billing Persistence

Automatic billing is persisted rather than being treated only as temporary browser data.

The system updates relevant customer and billing information so that billing information remains available across devices/sessions connected to the same backend.

---

# 51. Payment Persistence

Payment transactions are stored with relevant information such as:- Customer
- Amount
- Payment Date
- Payment Time
- Receipt Number
- Reference
- Collector
- Balance Before
- Balance After
- Advance Payment Flag
- Covered Due Date

---

# 52. Real-Time Production Date Logic

After development testing, NetBill V2 was restored to real-date processing.

The Advance Payment Receipt system uses the current system date.

Automatic monthly billing also uses the current system date through the application's date-processing functions.

The visible SYSTEM DATE & TIME uses the device/system clock.

Temporary dates used during development testing are not intended for production operation.

---

# 53. Tested Advance-Payment Workflow

The advance-payment feature was tested using controlled future-date simulations.

Testing confirmed:

### Covered Due Date

On the exact covered due date:

- The ADV. PAYMENT RCPT notification activates.
- The applicable advance receipt appears.
- View opens the correct original advance-payment receipt.

### One Day Before Due Date

Before the next covered due date:

- No advance receipt appears for that future date.
- No due-date notification is triggered for that future receipt.

### Next Covered Due Date

On the next reserved covered due date:

- The next applicable advance receipt appears.
- The notification activates.
- The correct original receipt can be viewed.

After testing, temporary test dates were removed and production real-date logic was restored.

---

# 54. Mobile Support

NetBill V2 includes responsive/mobile behavior.

Mobile improvements include:

- Compact navigation
- Responsive Dashboard
- Mobile-friendly metric cards
- Mobile-friendly forms
- Responsive typography
- Responsive tables
- Mobile Ledger cards
- Mobile payment workflow
- App installation support

---

# 55. Cache Busting

NetBill uses version query strings for important frontend resources.

Example:

```html
<link rel="stylesheet" href="style.css?v=XX">
<script src="app.js?v=XX"></script>
```

When `style.css` or `app.js` is changed, the corresponding version can be incremented to help force the browser and GitHub Pages to load the latest file instead of an older cached copy.

---

# 56. Important Operational Rules

Operators should observe the following:

1. Verify the correct customer before recording payment.
2. Enter the correct payment date and payment time.
3. Enter the responsible collector.
4. Existing outstanding balances should be settled before recording a separate advance payment.
5. An advance payment must correspond to the customer's monthly rate.
6. Verify the Covered Due Date shown on an advance receipt.
7. Do not use temporary testing dates during normal production operation.
8. Select the correct reporting period when generating historical reports.
9. Confirm carefully before permanently deleting a customer.

---

# 57. Advance-Payment Notification Rules

The ADV. PAYMENT RCPT notification follows these rules:

**Advance receipt due today + ADV. PAYMENT RCPT inactive = Blinking notification**

**Advance receipt due today + ADV. PAYMENT RCPT active = Steady blue**

**Leave the section while a receipt is still due today = Blinking resumes**

**No advance receipt due today = No blinking**

---

# 58. V2 Development History

NetBill V2 has undergone multiple improvements including:

- Mobile navigation improvements
- Responsive Dashboard improvements
- Customer Ledger
- Previous balance carry-forward
- Running customer balance
- Ledger migration
- Automatic monthly billing
- Paid/Unpaid activation handling
- Activation ledger cleanup
- Duplicate activation protection
- Cache-busting support
- Customer deletion improvements
- Monthly collection reports
- Monthly/yearly historical reporting
- Formatted spreadsheet reports
- True XLSX reports
- Downloadable payment receipts
- Collector information
- Audit-ready collection reports
- Outstanding balance reporting
- Supabase-backed billing/payment persistence
- Existing customer migration
- Advance Payment
- Sequential advance due-date allocation
- Advance Payment Receipt
- ADV. PAYMENT RCPT section
- Due-date notification
- Live System Date & Time
- Real-date automatic billing
- Real-date advance-receipt detection

---

# 59. V2 as Reference for Other NetBill Versions

NetBill V2 can be used as the reference implementation when transferring newer features to another NetBill version.

Before transferring features:

- Review the destination database structure.
- Review the destination `app.js`.
- Review the destination `index.html`.
- Review the destination `style.css`.
- Transfer features incrementally.
- Test every transferred feature.
- Do not assume line numbers are identical between versions.

This is especially important when transferring V2 improvements to NetBill V1 because the two versions may contain different code and production data.

---

# 60. Core Files

The main NetBill V2 frontend files include:

```text
index.html
style.css
app.js
manifest.json
README.md
```

Application icons and other supporting assets may also be included in the repository.

---

# 61. Technology

NetBill V2 uses:

- HTML
- CSS
- JavaScript
- Supabase
- GitHub
- GitHub Pages
- Progressive Web App manifest support
- XLSX spreadsheet generation for reporting

---

# 62. Deployment

NetBill V2 is deployed through GitHub Pages.

After frontend changes:

1. Save the modified file.
2. Commit the change to the repository.
3. Update the appropriate cache version when required.
4. Allow GitHub Pages to deploy the new commit.
5. Refresh or reopen NetBill.
6. Verify that the change works correctly before making another major modification.

---

# 63. Backup and Change Control

Before making major production changes:

- Preserve the current working version.
- Make one controlled change at a time.
- Test the change before proceeding.
- Avoid changing unrelated working functions.
- Confirm database behavior before changing billing or payment logic.

Because NetBill manages billing and payment transactions, changes affecting financial records should be tested carefully before normal production use.

---

# NetBill V2

**Internet Billing Management System**

Powered by **CM Philippines**
