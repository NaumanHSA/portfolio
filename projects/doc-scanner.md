# 📄 AI Document Scanner SDK

A cross-platform SDK for automated extraction of:
- Full Name
- MRZ info
- Nationality, DOB
- Visa data
- Embedded photo and signature

**Tech Stack**:
- Python, FastAPI
- OpenCV, Tesseract
- Deployed as a REST API

### Demo
![Demo](../images/doc_scanner_demo.gif)

---

### How It Works
1. Input: Base64 image of a document
2. Steps:
   - Detects document type (ID, visa, passport)
   - Applies preprocessing
   - OCR + field-specific parsing
   - Outputs structured JSON
