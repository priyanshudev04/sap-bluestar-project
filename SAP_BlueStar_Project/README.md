# 🏭 SAP Company Blueprint — BlueStar Manufacturing Pvt. Ltd.

> **KIIT Capstone Project | SAP Track**  
> Student: Priyanshu Pandey | Roll No: 2305313 | Batch: 2023-2027 | B.Tech CSE-04

---

## 📋 Project Overview

This project presents a complete **SAP Company Blueprint** for a fictitious company — **BlueStar Manufacturing Pvt. Ltd.** — a mid-sized Indian industrial equipment manufacturer based in Bhubaneswar, Odisha.

The blueprint covers the design, organizational structure, master data, and SPRO configuration steps for three core SAP functional modules:

| Module | Full Name | Purpose |
|--------|-----------|---------|
| **FI** | Financial Accounting | General Ledger, AP, AR, Tax |
| **MM** | Materials Management | Procurement, Inventory, Vendors |
| **SD** | Sales & Distribution | Sales Orders, Delivery, Billing |

---

## 🏢 Company Details

| Parameter | Value |
|-----------|-------|
| Company Name | BlueStar Manufacturing Pvt. Ltd. |
| Industry | Industrial Equipment Manufacturing |
| Headquarters | Bhubaneswar, Odisha, India |
| SAP Client | 100 |
| Company Code | BSMP |
| Fiscal Year | April – March (Variant V3) |
| Currency | INR |
| Chart of Accounts | CAIN (India Standard) |

---

## 📁 Repository Structure

```
SAP_BlueStar_Project/
│
├── README.md                        ← You are here
│
├── docs/
│   ├── SAP_Blueprint_BlueStar.docx  ← Full project report (Word)
│   └── project_summary.md           ← Text summary of the blueprint
│
├── config-steps/
│   ├── FI_configuration.md          ← Financial Accounting SPRO steps
│   ├── MM_configuration.md          ← Materials Management SPRO steps
│   └── SD_configuration.md          ← Sales & Distribution SPRO steps
│
└── screenshots/
    └── README.md                    ← Placeholder for SAP screenshots
```

---

## 🏗️ Organizational Structure

### FI — Financial Accounting
- **Company Code:** BSMP → Assigned to Client 100
- **Chart of Accounts:** CAIN (India Standard)
- **Fiscal Year Variant:** V3 (April–March)
- **Controlling Area:** BSCA
- **Business Areas:** BA01 (Manufacturing), BA02 (After-Sales)

### MM — Materials Management
- **Plants:** BP01 (Bhubaneswar Main), BP02 (Cuttack Warehouse)
- **Storage Locations:** SL01 (Raw Materials), SL02 (Finished Goods)
- **Purchasing Org:** BSPO (Central)
- **Purchasing Groups:** PG01 (Raw Materials), PG02 (Spare Parts)

### SD — Sales & Distribution
- **Sales Org:** BSSO
- **Distribution Channels:** 01 (Direct), 02 (Dealer)
- **Divisions:** 10 (Equipment), 20 (Spare Parts)
- **Shipping Point:** SP01 (Plant BP01)

---

## 🔗 Key Integration Points

```
Procure-to-Pay:   MM ──► FI   (GR/IR via automatic account determination)
Order-to-Cash:    SD ──► FI   (Billing document creates FI posting)
Inventory Value:  MM ──► FI   (Goods movement posts to stock account)
Credit Check:     SD ◄─► FI   (Sales order checks customer credit limit)
```

---

## ⚙️ Tech Stack

- **ERP Platform:** SAP ECC 6.0 / SAP S/4HANA
- **Modules:** FI, MM, SD
- **Config Tool:** SPRO (IMG — Implementation Guide)
- **Database:** SAP HANA
- **Language:** ABAP
- **Reporting:** ALV Reports, SAP Query

---

## 📄 Project Documentation

The full project report (PDF format) is available in the `/docs` folder.  
It includes: Problem Statement, Org Structure, Master Data, SPRO Steps, Screenshots, Tech Stack, and Future Improvements.

---

## 🚀 Future Improvements

- Extend to **PP (Production Planning)** module
- Integrate **SAP HR/HCM** for payroll linked to FI cost centres  
- Implement **SAP Fiori** dashboards for real-time KPIs
- Plan **S/4HANA migration** roadmap with Universal Journal

---

## 📌 Submission Info

- **Deadline:** April 21, 2026 — 11:59 PM
- **Submitted via:** KIIT Google Form
- **Evaluation Test:** April 23, 2026 (expected)
