# FreightMatch-TMS

An easy-to-use document reader and checker for shipping and freight paperwork.

---

## 1. What This Program Does

When boxes and shipping containers travel across the ocean on big cargo ships, they come with lots of important papers:
- **Bills of Lading:** Papers that prove who owns the boxes on the ship.
- **Invoices:** Bills that show how much money items cost.
- **Packing Lists:** Lists that count every single item and state its weight.

Normally, humans must read each paper by hand and type numbers into a computer one by one.

**FreightMatch-TMS** does this work automatically:
1. It reads photos or PDF scans of the papers.
2. It finds names, weights, prices, container numbers, and tax codes.
3. It checks the math to make sure nobody made a mistake.
4. It prepares clean data ready for shipping software to save.

---

## 2. Try the Live Demo

You can try the program right now in your web browser:

👉 **[Click Here to Open the Live Demo](https://freightmatch-tms.streamlit.app)**

1. Open the link above.
2. Drag and drop any shipping paper or invoice into the upload box.
3. Click the button to read the document.
4. Watch the computer pull out all the details on screen.

---

## 3. How the Program Works in 4 Steps

```
[ Step 1: Upload Paper ]
        │
        ▼
[ Step 2: Computer Vision Reads the Words ]
        │
        ▼
[ Step 3: Math Checker Fixes Mistakes ]
        │
        ▼
[ Step 4: Send Clean Data to Shipping System ]
```

- **Step 1 (Upload Paper):** A user uploads a picture or a PDF file.
- **Step 2 (Read Words):** An artificial intelligence model looks at the image and writes down every word and number.
- **Step 3 (Check Math):** The computer adds up the numbers. If `Price x Quantity` does not equal `Total`, or if the cargo weights do not match, it shows a warning.
- **Step 4 (Save Data):** The clean numbers are bundled together so any company database can store them safely.

---

## 4. Test Files Included in This Project

Inside the `sample_documents` folder, there are 3 real sample files ready for testing:

1. `sample bill of ladling.webp` - A real shipping paper showing ship names and container box numbers.
2. `sample commercial invoice.png` - A bill showing items, prices, and taxes.
3. `sample packing list.webp` - A list showing box weights in kilograms.

---

## 5. How to Run This on Your Own Computer

Follow these 5 simple steps in your terminal or command prompt:

### Step 1: Download the Project
```bash
git clone https://github.com/AllenFletcherAI/FreightMatch-TMS.git
cd FreightMatch-TMS
```

### Step 2: Make a Safe Python Box
```bash
python -m venv venv
```
Now turn on the safe box:
- On Windows:
  ```bash
  venv\Scripts\activate
  ```
- On Mac or Linux:
  ```bash
  source venv/bin/activate
  ```

### Step 3: Install the Tools
```bash
pip install -r requirements.txt
```

### Step 4: Add Your Secret Key
Make a new file named `.env` and paste your key inside:
```env
GEMINI_API_KEY="your-key-goes-here"
```

### Step 5: Start the App
```bash
streamlit run app.py
```
Open your browser to `http://localhost:8501` to use the app.

---

## 6. Tools Used

- **Python:** The main computer language used to build the program.
- **Streamlit:** The tool that builds the buttons and web screen.
- **Gemini Vision AI:** The artificial intelligence that reads text inside photos.
- **PyPDF:** The tool that opens and reads PDF files.

---

## 7. License

This project is free to use and study under the MIT License.