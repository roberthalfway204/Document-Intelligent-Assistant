# 🤖: Document Intelligent Assistant 

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![OCR](https://img.shields.io/badge/OCR-Tesseract-green)
![AI](https://img.shields.io/badge/AI-Claude%20API-orange)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

A Python-based AI pipeline that transforms messy physical documents — like receipts, handwritten notes, and textbook pages — into structured, searchable digital data.

---

## 🎯: Project Goals

- **Automation** — Eliminate manual typing of information from images or PDFs
- **Searchability** — Enable text search on scanned documents that were previously just "dead" images
- **Data Structuring** — Identify key-value pairs like `Total Price`, `Date`, `Name` from documents
- **Accessibility** — Foundation for a tool that can read text aloud for those with visual impairments

---

## 📋: Pipeline Overview

```
Input Image
     ↓
Phase 1 — Image Pre-processing   (OpenCV)
     ↓
Phase 2 — Text Extraction        (Tesseract OCR)
     ↓
Phase 3 — Layout Analysis        (Tesseract built-in)
     ↓
Phase 4 — LLM Post-processing    (Claude API)
     ↓
Structured JSON Output
```

---

## ⌛: Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core programming language |
| OpenCV | Image pre-processing |
| Tesseract OCR | Text extraction from images |
| pytesseract | Python wrapper for Tesseract |
| Anthropic Claude API | LLM post-processing and structuring |
| Pillow | Image handling |

---

## 📘: Project Structure

```
document-intelligent-assistant/
├── pipeline.py            # Master pipeline — runs all phases
├── preprocess.py          # Phase 1: Image pre-processing
├── ocr.py                 # Phase 2: OCR text extraction
├── layout.py              # Phase 3: Layout analysis
├── llm_processor.py       # Phase 4: LLM post-processing
├── batch_processor.py     # Phase 5: Batch processing
├── requirements.txt       # Project dependencies
├── input_images/          # Single image testing folder
├── batch_input/           # Batch processing folder
└── output/                # All generated output files
```

---

## 🛠️: Installation

**1 — Clone the repository**
```bash
git clone https://github.com/yourusername/document-intelligent-assistant.git
cd document-intelligent-assistant
```

**2 — Create and activate virtual environment**
```bash
python -m venv ocr_env
ocr_env\Scripts\activate
```

**3 — Install dependencies**
```bash
pip install -r requirements.txt
```

**4 — Install Tesseract OCR**

Download and install from:
```
https://github.com/UB-Mannheim/tesseract/wiki
```
Then update this line in `ocr.py` and `layout.py` with your install path:
```python
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
```

**5 — Set your Anthropic API key**
```bash
export ANTHROPIC_API_KEY=your_api_key_here
```

---

## 🚀 Usage

**Single image:**
```bash
python pipeline.py
```

**Batch processing (entire folder):**
```bash
python batch_processor.py
```

---

## 📤 Output Files

For every processed image, the pipeline generates:

| File | Description |
|------|-------------|
| `*_processed.png` | Pre-processed clean image |
| `*_extracted.txt` | Raw OCR extracted text |
| `*_layout.json` | Detected layout structure |
| `*_result.json` | Final structured JSON from Claude |
| `batch_report.json` | Summary report for batch runs |

---

## 📜: Example Output

```json
{
  "document_type": "computer screenshot",
  "title": "Document Title",
  "summary": "Brief description of the document content",
  "key_information": {
    "field_name": "value",
    "another_field": "value"
  },
  "full_text_cleaned": "Complete cleaned text in reading order",
  "ocr_corrections": ["teh -> the", "recieve -> receive"],
  "confidence": "high"
}
```

---

## 🪛: Future Improvements

- [ ] Add Surya or LayoutLM for advanced layout analysis
- [ ] Support PDF input files
- [ ] Add Markdown output format option
- [ ] Build a simple web interface
- [ ] Add text-to-speech for accessibility
- [ ] Support multiple languages

---

## 👤: Author

**Suraj**
- GitHub: [@Suraj210620](https://github.com/Suraj210620)

---

## 📋: License

This project is open source and available under the [MIT License](LICENSE).
