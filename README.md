# FreightMatch-TMS: Logistics Document Parser & Reconciliation Engine

An automated system that reads unstructured freight shipping documents, checks them for errors, and outputs clean, structured data for enterprise logistics software.

[Try the Live Web App](https://freightmatch-tms.streamlit.app) • [View GitHub Repository](https://github.com/AllenFletcherAI/FreightMatch-TMS)

---

## What This Project Does

Shipping companies receive thousands of paper, PDF, and image files from around the world. People usually have to type this data by hand into databases, which causes delays and human error.

FreightMatch-TMS automates this entire process:

1. **Reads Any File**: Accepts scanned pictures, PDFs, or photos of shipping records.
2. **Sorts the Documents**: Automatically figures out if a file is an Invoice, Bill of Lading, Packing List, or Customs form.
3. **Pulls Out the Data**: Reads container numbers, weights, prices, tax codes, and dates.
4. **Checks for Mistakes (3-Way Matching)**: Compares the numbers across documents to catch missing stamps, math errors, or weight mismatches.
5. **Prepares the Output**: Formats everything into a clean JSON message ready to send directly to central logistics software.

---

## System Flowchart

Here is the exact path a file takes through the system:

```text
  [ Upload Document: Scanned Image or PDF ]
                      │
                      ▼
  [ Step 1: Read File & Extract Text/Pixels ]
                      │
                      ▼
  [ Step 2: Identify Document Type & Extract Fields ]
                      │
                      ▼
  [ Step 3: Run Automatic Math & Consistency Checks ]
                      │
                      ▼
  [ Step 4: Emit Final Structured JSON Data ]
```

---

## Document Types Handled

The engine organizes files into four main groups:

* **Commercial & Financial**: Invoices, payment requests, and price sheets.
* **Transport & Title**: Bills of Lading, sea waybills, and airway bills.
* **Cargo Specifications**: Packing manifests, weight sheets, and size records.
* **Customs & Compliance**: Export papers, origin certificates, and safety sheets.

---

## What the System Checks Automatically

Before saving any data, the engine checks for three common real-world problems:

* **Math Check**: Multiplies unit prices by quantities to ensure the total line items match the final balance and tax totals.
* **Weight & Volume Check**: Compares gross weight (cargo plus container) against net weight (cargo only) to ensure weights and volumes make physical sense.
* **Compliance Check**: Verifies that required official seal numbers, signatures, and international 6-digit tariff codes are present and valid.

---

## Testing With Sample Files

Three test files are included inside the `sample_documents/` folder in this repository:

1. `sample_documents/sample commercial invoice.png`: Tests price calculations and line-item totals.
2. `sample_documents/sample bill of ladling.webp`: Tests sea cargo title parsing and container number matching.
3. `sample_documents/sample packing list.webp`: Tests weight, package counts, and cargo measurements.

To test them without installing anything on your computer, open the [Live Demo](https://freightmatch-tms.streamlit.app) and drag any of these three files directly onto the screen.

---

## How to Run This Project on Your Computer

Follow these 5 simple steps. You will need Python installed on your computer.

### Step 1: Download the Code
Open your terminal (Command Prompt on Windows or Terminal on Mac/Linux) and run:

```bash
git clone https://github.com/AllenFletcherAI/FreightMatch-TMS.git
cd FreightMatch-TMS
```

### Step 2: Set Up an Isolated Python Environment
Run this command to create and enter a clean workspace:

```bash
# Create the virtual environment
python -m venv venv

# Turn on the environment (Windows)
venv\Scripts\activate

# Turn on the environment (Mac or Linux)
source venv/bin/activate
```

### Step 3: Install Required Libraries
Run this command to install the required tools automatically:

```bash
pip install -r requirements.txt
```

### Step 4: Add Your Gemini API Key
Create a plain text file named `.env` in the main folder and add your key:

```env
GEMINI_API_KEY="your-gemini-api-key-goes-here"
```

*(You can generate a free key at [Google AI Studio](https://aistudio.google.com/apikey).)*

### Step 5: Start the Application
Run this final command:

```bash
streamlit run app.py
```

Your web browser will open automatically with the interface running locally at `http://localhost:8501`.

---

## Technology Stack

* **Programming Language**: Python 3.11+
* **User Interface**: Streamlit
* **Document Processing**: PyPDF, Pillow (PIL), NumPy
* **Vision & Extraction Engine**: Google Gemini API
* **Data Contracts**: Standard JSON Schemas

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for full details.