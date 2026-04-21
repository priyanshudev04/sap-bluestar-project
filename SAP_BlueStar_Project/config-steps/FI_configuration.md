# FI — Financial Accounting Configuration Steps

**Module:** SAP FI (Financial Accounting)  
**Company Code:** BSMP — BlueStar Manufacturing Pvt. Ltd.  
**SPRO Path:** SAP Customizing > Financial Accounting > Financial Accounting Global Settings

---

## Step 1 — Define Company

**T-Code:** OX15  
- Company ID: BLST  
- Name: BlueStar Group  
- Country: IN | Currency: INR | Language: EN

---

## Step 2 — Define Company Code

**T-Code:** OX02  
- Company Code: BSMP  
- Name: BlueStar Manufacturing Pvt. Ltd.  
- City: Bhubaneswar | Country: IN  
- Currency: INR | Language: EN  
- Assign Company Code BSMP to Company BLST

---

## Step 3 — Assign Chart of Accounts

**T-Code:** OB62  
- Company Code: BSMP  
- Chart of Accounts: CAIN (India Standard)

---

## Step 4 — Define Fiscal Year Variant

**T-Code:** OB29  
- Variant: V3  
- Description: April–March (Indian FY)  
- 12 Normal Periods + 4 Special Periods  
- Period 1 = April, Period 12 = March

**T-Code:** OB37 — Assign Fiscal Year Variant V3 to Company Code BSMP

---

## Step 5 — Define Posting Period Variant

**T-Code:** OBBO  
- Variant: BSMP  
- Description: BlueStar Posting Periods

**T-Code:** OBBP — Assign Posting Period Variant BSMP to Company Code BSMP

---

## Step 6 — Define Document Types & Number Ranges

**T-Code:** OBA7  

| Doc Type | Description | Number Range |
|----------|-------------|-------------|
| SA | G/L Account Document | 01 (100000–199999) |
| KR | Vendor Invoice | 19 (190000000–199999999) |
| KZ | Vendor Payment | 15 |
| DR | Customer Invoice | 18 |
| DZ | Customer Payment | 14 |

---

## Step 7 — Define Field Status Variants

**T-Code:** OBC4  
- Variant: BSMP  
- Make "Cost Centre" and "Tax Code" mandatory fields for posting

**T-Code:** OBC5 — Assign Field Status Variant to Company Code BSMP

---

## Step 8 — Configure Tax (GST)

**T-Code:** OBYZ  
- Tax Procedure: TAXIN (India — assigned to country IN)  
- Condition Types: CGST, SGST, IGST  
- Access Sequence: MWST

**T-Code:** FTXP  
- Define Tax Codes: I5 (5% GST), I12 (12% GST), I18 (18% GST)

---

## Step 9 — Define G/L Accounts (Key Accounts)

**T-Code:** FS00  

| G/L Account | Description | Type |
|-------------|-------------|------|
| 100001 | Cash Account | Asset |
| 113000 | Bank — HDFC Current | Asset |
| 130000 | Accounts Receivable (Recon) | Asset |
| 210000 | Accounts Payable (Recon) | Liability |
| 300000 | Raw Material Inventory | Asset |
| 400000 | Revenue from Sales | P&L Revenue |
| 500000 | Cost of Goods Sold | P&L Expense |
| 220000 | GST Payable | Liability |

---

## Step 10 — Automatic Account Determination

**T-Code:** OBYC  

| Transaction Key | Description | G/L Account |
|-----------------|-------------|-------------|
| BSX | Stock Posting (Inventory) | 300000 |
| WRX | GR/IR Clearing Account | 191000 |
| GBB / VBR | Consumption Posting | 500000 |
| PRD | Price Difference | 281000 |

---

## Step 11 — Define Credit Control Area

**T-Code:** OB45  
- Credit Control Area: BSCA  
- Currency: INR  
- Update: 12 (Update from SD open orders + deliveries + billing)

**T-Code:** OB38 — Assign Credit Control Area BSCA to Company Code BSMP

---

## Step 12 — Define Business Areas

**T-Code:** OX03  
- BA01 — Industrial Equipment Manufacturing  
- BA02 — After-Sales & Services

---

## Validation / Testing Steps

1. Post a test G/L document via **T-Code FB50** (G/L Account Posting)
2. Create a test vendor invoice via **T-Code FB60**
3. Create a test customer invoice via **T-Code FB70**
4. Run **Trial Balance** via T-Code F.01 to verify postings
