# 📄 Signature Detection SDK

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
![Demo](../images/signature_sample.png)

---

### How It Works
1. Input: Base64 image of a document
2. Steps:
   - Detects signature
   - Segments signature
   - Enhances signature
   - Outputs enhanced signature
