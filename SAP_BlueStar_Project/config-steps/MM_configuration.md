# MM — Materials Management Configuration Steps

**Module:** SAP MM (Materials Management)  
**Company Code:** BSMP | **Purchasing Org:** BSPO  
**SPRO Path:** SAP Customizing > Materials Management

---

## Step 1 — Define Plant

**T-Code:** OX10  

| Plant | Name | City | Country |
|-------|------|------|---------|
| BP01 | BlueStar Main Plant | Bhubaneswar | IN |
| BP02 | BlueStar Warehouse | Cuttack | IN |

**T-Code:** OX18 — Assign Plants BP01 and BP02 to Company Code BSMP

---

## Step 2 — Define Storage Locations

**T-Code:** OX09  

| Plant | Storage Loc | Description |
|-------|-------------|-------------|
| BP01 | SL01 | Raw Materials Store |
| BP01 | SL02 | Finished Goods Store |
| BP02 | SL03 | Cuttack Warehouse Store |

---

## Step 3 — Define Purchasing Organization

**T-Code:** OX08  
- Purchasing Org: BSPO  
- Description: BlueStar Central Purchasing

**T-Code:** OX01 — Assign BSPO to Company Code BSMP  
**T-Code:** OX17 — Assign BSPO to Plants BP01 and BP02

---

## Step 4 — Define Purchasing Groups

**T-Code:** OME4  

| Purch. Group | Description |
|-------------|-------------|
| PG01 | Raw Material Buyers |
| PG02 | Spare Parts & Consumables |

---

## Step 5 — Define Material Types

**T-Code:** OMS2  

| Material Type | Description | Valuation |
|--------------|-------------|-----------|
| ROH | Raw Materials | Moving Average Price |
| FERT | Finished Goods | Standard Price |
| HALB | Semi-Finished Goods | Moving Average Price |
| HIBE | Operating Supplies | Moving Average Price |

---

## Step 6 — Define Number Ranges

**T-Code:** OMSL — Material Master Number Ranges  
- ROH: 100000000–199999999 (External)  
- FERT: 200000000–299999999 (External)

**T-Code:** OMH6 — Purchase Order Number Ranges  
- PO Range: 4500000000–4599999999

---

## Step 7 — Define Movement Types

**T-Code:** OMJJ  

| Mvmt Type | Description |
|-----------|-------------|
| 101 | GR for Purchase Order |
| 102 | Reversal of GR |
| 201 | Goods Issue to Cost Centre |
| 261 | GI for Production Order |
| 601 | GI for SD Delivery |
| 651 | Returns from Customer |

---

## Step 8 — Configure Valuation Area

**SPRO:** MM > Valuation and Account Assignment > Define Valuation Level  
- Valuation at Plant Level → Select Plant BP01 and BP02 as valuation areas

---

## Step 9 — Release Procedure for Purchase Orders

**T-Code:** OMGQ — Define Release Conditions  
- Release Group: 01  
- Release Code: M1 (Manager), M2 (Director)  
- Condition: Net PO Value > INR 5,00,000 requires M1 approval  
- Condition: Net PO Value > INR 25,00,000 requires M2 approval

---

## Step 10 — Define Account Assignment Categories

**T-Code:** OME9  

| Category | Description | Account Assignment |
|----------|-------------|-------------------|
| K | Cost Centre | Mandatory |
| P | Project (WBS) | Mandatory |
| A | Asset | Mandatory |

---

## Step 11 — Create Material Master (Sample)

**T-Code:** MM01  
- Material: STL-SHEET-01  
- Industry Sector: M (Mechanical Engineering)  
- Material Type: ROH  
- Views: Basic Data 1&2, Purchasing, MRP 1&2, Accounting 1&2  
- Plant: BP01 | Storage Location: SL01  
- MRP Type: PD (MRP with Planning Run)  
- Price Control: V (Moving Average)

---

## Step 12 — Create Vendor Master (Sample)

**T-Code:** XK01  
- Vendor: V100001  
- Company Code: BSMP | Purch. Org: BSPO  
- Name: Tata Steel Suppliers Ltd.  
- Recon Account: 210000 (AP Reconciliation)  
- Payment Terms: N030 (Net 30 days)

---

## Validation / Testing Steps

1. Create a Purchase Order via **T-Code ME21N**
2. Post Goods Receipt via **T-Code MIGO** (Movement Type 101)
3. Post Vendor Invoice via **T-Code MIRO**
4. Check Stock Overview via **T-Code MMBE**
5. Check FI document created automatically via **T-Code MR51**
