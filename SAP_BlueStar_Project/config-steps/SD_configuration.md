# SD — Sales & Distribution Configuration Steps

**Module:** SAP SD (Sales & Distribution)  
**Company Code:** BSMP | **Sales Org:** BSSO  
**SPRO Path:** SAP Customizing > Sales and Distribution

---

## Step 1 — Define Sales Organization

**T-Code:** OVX5  
- Sales Org: BSSO  
- Description: BlueStar Sales Organization  
- Country: IN | Currency: INR

**T-Code:** OVX3 — Assign BSSO to Company Code BSMP

---

## Step 2 — Define Distribution Channels

**T-Code:** OVXI  

| Distribution Channel | Description |
|----------------------|-------------|
| 01 | Direct Sales |
| 02 | Dealer / Channel Partner |

**T-Code:** OVXK — Assign Distribution Channels to Sales Org BSSO

---

## Step 3 — Define Divisions

**T-Code:** OVXA  

| Division | Description |
|----------|-------------|
| 10 | Industrial Equipment |
| 20 | Spare Parts & Accessories |

**T-Code:** OVXB — Assign Divisions to Sales Org BSSO

---

## Step 4 — Set Up Sales Area

**T-Code:** OVXG — Combine Sales Org + Distribution Channel + Division  

| Sales Area | Description |
|-----------|-------------|
| BSSO / 01 / 10 | Direct Sales — Industrial Equipment |
| BSSO / 02 / 10 | Dealer Sales — Industrial Equipment |
| BSSO / 01 / 20 | Direct Sales — Spare Parts |

---

## Step 5 — Define Shipping Points

**T-Code:** OVXD  
- Shipping Point: SP01  
- Description: Bhubaneswar Dispatch Hub  
- Factory Calendar: IN (India)

**T-Code:** OVXC — Assign Shipping Point SP01 to Plant BP01

---

## Step 6 — Define Sales Office & Sales Group

**T-Code:** OVX1  
- Sales Office: SO01 — Bhubaneswar Regional Office

**T-Code:** OVX4  
- Sales Group: SG01 — Key Accounts | SG02 — SME Accounts

---

## Step 7 — Define Customer Account Groups

**T-Code:** OVT0  

| Account Group | Description | Number Range |
|--------------|-------------|-------------|
| SOLD | Sold-to Party | 1000000–1999999 |
| SHIP | Ship-to Party | 2000000–2999999 |
| BILL | Bill-to Party | 3000000–3999999 |
| PAYR | Payer | 4000000–4999999 |

---

## Step 8 — Define Sales Document Types

**T-Code:** VOV8  

| Doc Type | Description |
|----------|-------------|
| OR | Standard Sales Order |
| RE | Returns Order |
| CR | Credit Memo Request |
| DR | Debit Memo Request |

---

## Step 9 — Configure Pricing Procedure

**T-Code:** V/08 — Define Pricing Procedure ZPRIND  

| Step | Cond. Type | Description |
|------|-----------|-------------|
| 10 | PR00 | Base Price |
| 20 | K007 | Customer Discount (%) |
| 30 | K005 | Material Discount |
| 40 | MWST | Output Tax (GST) |
| 50 | VPRS | Cost (statistical) |
| 60 | ZBPR | Net Revenue (subtotal) |

**T-Code:** OVKK — Assign Pricing Procedure ZPRIND to Sales Area BSSO/01/10

---

## Step 10 — Define Condition Types & Records

**T-Code:** VK11 — Create Condition Records  
- PR00: Base price per material per Sales Org  
  - BIM-200 Industrial Motor → INR 85,000 per unit  
- K007: Customer-specific discount  
  - Key Account customers → 5% discount

---

## Step 11 — Configure Output Types

**T-Code:** NACE — Application V1 (Sales)  

| Output Type | Description | Medium |
|------------|-------------|--------|
| BA00 | Order Confirmation | Print / Email |
| RD00 | Invoice / Billing Doc | Print / Email |
| LIEF | Delivery Note | Print |

---

## Step 12 — Credit Management Setup

**T-Code:** OVA8 — Define Automatic Credit Control  
- Credit Control Area: BSCA  
- Risk Category: 001 (Low), 002 (Medium), 003 (High)  
- Check at: Sales Order + Delivery

**T-Code:** FD32 — Set Customer Credit Limit  
- Default credit limit for new customers: INR 10,00,000  
- Key Account customers: INR 50,00,000

---

## Step 13 — Create Customer Master (Sample)

**T-Code:** XD01  
- Customer: C100001  
- Sales Area: BSSO / 01 / 10  
- Name: Odisha Power Transmission Corp.  
- Recon Account: 130000 (AR Reconciliation)  
- Payment Terms: N030 (Net 30 days)  
- Credit Limit: INR 25,00,000

---

## Validation / Testing — Complete O2C Cycle

1. Create Sales Order → **T-Code VA01** (Doc Type OR)
2. Check Credit → **T-Code VKM1** (release if blocked)
3. Create Outbound Delivery → **T-Code VL01N**
4. Post Goods Issue → **T-Code VL02N** (Mvmt Type 601)
5. Create Billing Document → **T-Code VF01**
6. Verify FI document created → **T-Code VF03** → Accounting
7. Customer Payment → **T-Code F-28**
8. Clear Open Items → **T-Code F-32**
