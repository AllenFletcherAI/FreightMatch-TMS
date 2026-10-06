<div align="center">

# FreightMatch-TMS // Autonomous Logistics Intake Engine

**Deterministic Multimodal Document Parsing & 3-Way Reconciliation for Enterprise Transportation Management Systems (TMS)**

[![Live Interactive App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://freightmatch-tms.streamlit.app)
[![Python 3.11+](https://img.shields.io/badge/Python-3.11%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Target Interface: Enterprise TMS](https://img.shields.io/badge/Target-BLU4U%20%7C%20Enterprise%20TMS-orange.svg)]()

[**Launch Live Interactive Pipeline ->**](https://freightmatch-tms.streamlit.app)

</div>

---

## Overview

In global project freight forwarding, maritime operations, and international logistics, manual intake of multi-party shipping documents represents the primary operational bottleneck to real-time cargo visibility and settlement integrity.

**FreightMatch-TMS** is an enterprise-oriented multimodal document ingestion service engineered to ingest raw, uncalibrated transport and financial files, classify them across four core umbrella categories, extract structured logistics entities, execute automated 3-way reconciliation audits, and serialize staging payloads (`POST /api/v1/shipments/stage`) configured for direct asynchronous integration with modern TMS backends such as BLU4U.

---

## Key Functional Capabilities

* **Adaptive 4-Umbrella Taxonomy:**
  * **Commercial & Financial:** Commercial Invoices, Freight Billing Statements, Rate Cards.
  * **Transport & Title:** Multimodal Ocean Bills of Lading (B/L), Sea Waybills, Air Waybills (AWB).
  * **Cargo Specifications:** Packing Lists, Measurement Tallies, Out-of-Gauge (OOG) Stagger Sheets.
  * **Customs & Statutory:** Export/Import Declarations, Certificates of Origin, Dangerous Goods (IMDG) filings.
* **Deterministic Layout & Entity Extraction:** Parses dense raster images and multi-page PDFs to extract line-item totals, 6-digit Harmonized Tariff (HS) codes, ISO container numbers, seal verification checksums, metric gross/net weights, Incoterms 2020 definitions, vessel IMO identifiers, and port pairs.
* **Automated 3-Way Reconciliation Engine:**
  * **Arithmetic Consistency:** Audits line-item unit pricing and quantities against declared invoice totals and calculated taxes.
  * **Metric Weight & Volume Discrepancies:** Detects variance across declared gross kg, net kg, and total cubic meters (CBM).
  * **Regulatory & Statutory Integrity:** Flags missing endorsements, non-compliant container seals, and HS classification mismatches prior to settlement.
* **TMS Staging Webhook Serialization:** Formats parsed and validated outputs into strict, typed JSON contracts designed for asynchronous integration with downstream staging tables.

---

## System Architecture

```text
 ┌────────────────────────────────────────────────────────┐
 │ Inbound Logistics Stream (Scanned Raster / Native PDF) │
 └───────────────────────────┬────────────────────────────┘
                             │
                             ▼
 ┌────────────────────────────────────────────────────────┐
 │ Multi-Modal Document Decomposition                     │
 │ (PyPDF Text Scrape + Raster High-Resolution Fallback)  │
 └───────────────────────────┬────────────────────────────┘
                             │
                             ▼
 ┌────────────────────────────────────────────────────────┐
 │ Adaptive Classification & Schema Routing               │
 │ (Deterministic Entity Extraction & JSON Enforcement)   │
 └───────────────────────────┬────────────────────────────┘
                             │
                             ▼
 ┌────────────────────────────────────────────────────────┐
 │ 3-Way Reconciliation & Verification Engine             │
 │ (Rate Variance, Weight Deltas, Seal Integrity Checks)  │
 └───────────────────────────┬────────────────────────────┘
                             │
                             ▼
 ┌────────────────────────────────────────────────────────┐
 │ Validated Staging Payload Ready for TMS Ingestion      │
 │ (POST /api/v1/shipments/stage)                         │
 └────────────────────────────────────────────────────────┘
```

---

## Sample Testing Documents

Test logistics documents are available directly in the `sample_documents/` directory:
* `sample_documents/sample bill of ladling.webp` - Multimodal title transport document with container and seal numbers.
* `sample_documents/sample commercial invoice.png` - Multi-line commercial freight invoice for arithmetic reconciliation.
* `sample_documents/sample packing list.webp` - Metric cargo specification breakdown (gross vs. net weight / CBM).

*Drag and drop any of these sample files into the [Live Interactive App](https://freightmatch-tms.streamlit.app) to evaluate the extraction pipeline in real time.*

---

## Local Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AllenFletcherAI/FreightMatch-TMS.git
   cd FreightMatch-TMS
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On Linux/macOS:
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment:**
   Create a `.env` file in the root directory:
   ```env
   GEMINI_API_KEY="your-gemini-api-key-here"
   ```

5. **Start the pipeline:**
   ```bash
   streamlit run app.py
   ```

---

## Technology Stack

* **Core Runtime:** Python 3.11+
* **Interface & Presentation:** Streamlit (Custom Dark Industrial Design System)
* **Model Inference Engine:** Google GenAI Multimodal Vision Architecture
* **Document Decomposition:** PyPDF, Pillow (PIL), NumPy
* **Data Validation:** Strict JSON Schema Contracts

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.