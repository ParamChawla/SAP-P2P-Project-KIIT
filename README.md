# SAP S/4HANA Cloud – Procure-to-Pay (P2P) Cycle Simulation

> **Student:** Param Chawla | **Roll No:** 2330318  
> **Course:** SAP Fiori – LTIMindtree | **Institution:** KIIT University  
> **Date:** April 18, 2026  

---

##  Project Overview

This project demonstrates the complete **Procure-to-Pay (P2P) cycle** executed hands-on on the **SAP S/4HANA Cloud Trial system** using the **SAP Fiori** interface.

The P2P cycle is an end-to-end procurement process that covers all steps from identifying a material need to making payment to the supplier. This simulation was performed for **Velotics Inc.** procuring **10 units of 26ECR-BATTERY** from **Carbon Tec Inc.**

---

##  Business Scenario

| Field | Details |
|-------|---------|
| Company | Velotics Inc. (Company Code: 1710) |
| Supplier | Carbon Tec Inc. (17300002) |
| Material | 26ECR-BATTERY (MZ-RM-26ECR-1) |
| Quantity | 10 PC |
| Unit Price | 22.83 USD |
| Total Value | 228.30 USD |
| System | SAP S/4HANA Cloud Trial |
| Interface | SAP Fiori Launchpad |

---

##  P2P Process Flow

```
Purchase Requisition → Purchase Order → Goods Receipt → Invoice Verification → Payment
```

---

##  SAP Documents Generated

| Step | Document Type | Document Number | Status |
|------|--------------|-----------------|--------|
| 1 | Purchase Requisition | **10006734** | Release Completed|
| 2 | Purchase Order | **4500064017** | In Approval |
| 3 | Material Document (GR) | **5000064067/2026** | Posted  |
| 4 | Supplier Invoice | **5105662751/2026** | Posted |

---

##  Step-by-Step Execution

### Step 1 – Purchase Requisition (PR)
- **App:** Process Purchase Requisitions (SAP Fiori)
- **T-Code equivalent:** ME51N
- Material: 26ECR-BATTERY, Qty: 10 PC, Plant: 1710, Delivery: 30.04.2026
- **PR Generated:** 10006734 | Status: Release Completed

### Step 2 – Purchase Order (PO)
- **App:** Manage Purchase Orders (SAP Fiori)
- **T-Code equivalent:** ME21N
- Supplier: Carbon Tec Inc. (17300002), Standard PO (NB)
- Referenced PR 10006734 via "Add from Document"
- **PO Generated:** 4500064017 | Status: In Approval

### Step 3 – Goods Receipt (GR)
- **App:** Post Goods Receipt for Purchasing Document (SAP Fiori)
- **T-Code equivalent:** MIGO
- Referenced PO 4500064017, Storage Location: 171R
- 10 PC of 26ECR-BATTERY received at Plant 1 US (1710)
- **Material Document Generated:** 5000064067/2026

### Step 4 – Invoice Verification (3-Way Match)
- **App:** Create Supplier Invoice (SAP Fiori)
- **T-Code equivalent:** MIRO
- Gross Amount: 228.30 USD, Referenced PO: 4500064017
- **Balance: 0.00 USD** — 3-Way Match Successful 
- **Invoice Generated:** 5105662751/2026

### Step 5 – Payment
- Processed via SAP FI (Financial Accounting) module
- Clears vendor open item after invoice posting

---

## Three-Way Match Result

| Document | Number | Amount | Qty |
|----------|--------|--------|-----|
| Purchase Order | 4500064017 | 228.30 USD | 10 PC |
| Goods Receipt | 5000064067/2026 | 228.30 USD | 10 PC |
| Supplier Invoice | 5105662751/2026 | 228.30 USD | 10 PC |
| **Result** | **MATCH ** | **Balance: 0.00** | **No Variance** |

---

##  Repository Structure

```
SAP-P2P-Project-KIIT/
│
├── README.md
├── SAP_P2P_Report_Param_Chawla_2330318.pdf
│
└── screenshots/
    ├── 01_procurement_dashboard.png
    ├── 02_process_pr_screen.png
    ├── 03_create_pr_form.png
    ├── 04_pr_item_filled.png
    ├── 05_pr_release_completed.png
    ├── 06_new_po_form.png
    ├── 07_add_from_document_po.png
    ├── 08_pr_selected_for_po.png
    ├── 09_po_item_with_price.png
    ├── 10_po_4500064017_created.png
    ├── 11_goods_receipt_screen.png
    ├── 12_gr_success_5000064067.png
    ├── 13_material_document_detail.png
    ├── 14_supplier_invoice_form.png
    ├── 15_purchasing_doc_references_empty.png
    ├── 16_invoice_3way_match.png
    ├── 17_invoice_balance_zero.png
    ├── 18_invoice_po_reference_assigned.png
    └── 19_invoice_success_5105662751.png
```

---

##  Tools & Technology

- **System:** SAP S/4HANA Cloud Public Edition (Trial)
- **Interface:** SAP Fiori Launchpad
- **Module:** SAP MM – Materials Management
- **Course:** SAP Fiori by LTIMindtree
- **Institution:** KIIT University

---

##  Key Learnings

- The P2P cycle is an integrated end-to-end process — each document builds on the previous
- SAP Fiori provides a modern tile-based UI that simplifies traditional SAP transactions
- Master data (Material Master, Supplier Master) is foundational to procurement
- The Three-Way Match protects organisations from overpayment and financial fraud
- Account Assignment Categories (Asset, Cost Centre, Project) affect downstream processes

---

*Submitted as part of KIIT SAP Project Work | SAP Fiori – LTIMindtree | April 2026*
