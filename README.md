# static
A place for static files.


# Templates
**E-mail** templates are written in `mjml` and converted to `html` by `generate_html_templates.sh`

## Adding new platforms
1. Create appropriate folder in `/email-templates/` and `/receipt-templates/`
2. Add that folder to `generate_fixture.py`'s template_dirs variable
3. Add new templates to the app's folder in the correct language folder
4. Add the required templates to the `FIXTURE_TEMPLATE_EMAILS.json` or `FIXTURE_TEMPLATE_RECEIPTS.json`
5. Proceed to generate the templates as explained below

#### Usage
```
static > ./email-templates/generate_html_templates.sh 
[+] Running MJML server...
9c359e6d7259961e80e1a7db15fcc37d30a9d4fa5e983cd0e33bc2f06584e46a
...
[+] Done!
static > ./fixtures/generate_fixture.py email
Processing...
...
Writing /home/c03/Work/static/fixtures/build/default_email_templates.json
```

**Receipt** templates are written in `html` and converted to PDF by flow.
#### Usage

```
static > ./fixtures/generate_fixture.py receipt
Processing...
...
Writing /home/c03/Work/static/fixtures/build/receipt_templates.json
```

# Django fixtures
Django fixtures can be generated from the `html` files for both email and receipt `html` templates. Use the `generate_fixture.py` script in the `fixtures` folder.

# Email variables
Note: Variables for specific emails are written as comments in the emial mjml files

Variable name | Description
------------ | -------------
{{ due_date_extended }} | Original due date + 27 days
{{ invoice_number }} | invoice number
{{ invoice_amount }} | Invoice amount
{{ company_name }} | Name of seller company
{{ payer_company_name }} | Name of payer company
{{ outstanding_balance }} | Invoice amount + late fee 100 kr.
{{ payment_reg_number }} | reg number for incoming payments
{{ payment_account_number }} | account number for incoming payments
{{ reminder_fee }} | 100 kr. reminder fee
{{ due_date }} | Invoice due date
{{ signee_name }} | Signee name for seller company
{{ approved_customer_name }} | Company name for approved payer companies
{{ factoring_amount }} | Invoice amount minus fee and VAT
{{ account_number }} | four last digits on seller bank account
{{ fee_amount }} | factoring fee amount in DKK
{{ vat_amount }} | VAT amount in DKK
{{ total_fee_amount }} | Factoring fee amount + VAT amount in DKK
{{ company_email }} | The email address the company onboarded with

# Receipt variables

Variable name | Description
------------ | -------------
{{ company_name }} | Name of seller company
{{ signee_name }} | Name of signee of seller company
{{ company_street }} | Street of seller company
{{ company_city }} | city of seller company
{{ company_country }} | Country of seller company
{{ company_crn }} | CVR of seller company
{{ invoice_number }} | invoice number
{{ factoring_amount }} | Payout amount (invoice amount - fee & VAT)
{{ receipt date }} | Date of creation of receipt
{{ receipt_number }} | Receipt number
{{ fee_amount }} | Amount of the credited fee
{{ vat_amount }} | VAT of the credited fee
{{ vat_percent }} | VAT percentage
{{ total_fee_amount }} | Total amount of credit note (Fee+VAT)

# Credit note variables

Variable name | Description
------------ | -------------
{{ company_name }} | Name of seller company
{{ company_street }} | Street of seller company
{{ company_city }} | city of seller company
{{ company_country }} | Country of seller company
{{ company_crn }} | CVR of seller company
{{ invoice_number }} | invoice number
{{ date }} | Date of creation of credit note
{{ fee_amount }} | Amount of the credited fee
{{ vat_amount }} | VAT of the credited fee
{{ vat_percent }} | VAT percentage
{{ total_fee_amount }} | Total amount of credit note (Fee+VAT)
