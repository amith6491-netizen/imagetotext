# Image to Text (OCR)

A fast, private, client-side Optical Character Recognition (OCR) web tool that extracts clean text from multiple images and screenshots directly in your browser.

![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)
![Technology](https://img.shields.io/badge/Tech-HTML5%20%7C%20Vanilla%20JS%20%7C%20Tesseract.js-orange.svg)
![Privacy](https://img.shields.io/badge/Privacy-100%25%20Client--Side-brightgreen.svg)

---

live Demo :https://amith6491-netizen.github.io/imagetotext/
## 🌟 Overview

**Image to Text** allows you to extract textual content from photos, documents, and screenshots without uploading anything to a remote server. Built with **Tesseract.js** (WebAssembly / Web Workers), all optical character recognition and image filtering execute locally on your machine.

---

## ✨ Features

- **🔒 100% Client-Side & Private**: Your images never leave your computer. Processing happens entirely within the browser via Web Workers and WebAssembly.
- **📁 Batch Processing**: Drag and drop or browse multiple images at once (`PNG`, `JPG`, `WEBP`, `BMP`).
- **📸 Smart Screenshot Mode**:
  - **Dark-Mode Auto-Inversion**: Analyzes background brightness; automatically inverts dark screenshots (white text on dark backgrounds) to maximize OCR contrast and accuracy.
  - **Resolution Scaling**: Automatically upscales images with width under 800px (2x scale) to improve character recognition.
  - **Noise & UI Cleanup**: Intelligently identifies and removes stray icon characters, UI symbols, and single-letter artifacts common in mobile/desktop screenshots.
- **🔤 Letters-Only Filtering**:
  - Automatically filters out numbers, punctuation marks, and unwanted symbols.
  - Retains alphabetic characters (supporting Unicode letters and combining marks `\p{L}\p{M}`) and normalizes whitespace.
  - Enforces strict character whitelisting when English is selected.
- **🌐 Multilingual OCR Support**: Choose from 8 supported languages:
  - English (`eng`)
  - Hindi (`hin`)
  - Kannada (`kan`)
  - Tamil (`tam`)
  - Telugu (`tel`)
  - French (`fra`)
  - German (`deu`)
  - Spanish (`spa`)
- **📋 Export & Clipboard Tools**:
  - Individual copy buttons for each processed image.
  - Combined output area concatenating all extracted text.
  - One-click copy with fallback support (works seamlessly on `file://`, `http`, and `https`).
  - One-click download as `.txt` (`extracted-text.txt`).
- **🌓 Responsive & Theme-Aware UI**:
  - Clean, modern layout designed with CSS custom properties.
  - Automatically matches system dark or light appearance (`prefers-color-scheme`).
  - Mobile and desktop friendly.

---

## 🔄 How It Works

```
┌─────────────────────┐
│ Upload / Drop Image │ (PNG, JPG, WEBP, BMP)
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Preprocessing       │ ➜ 2x scaling for low-res images
│ (Canvas API)        │ ➜ Dark-mode inversion if background luminance < 128
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Tesseract.js Worker │ ➜ Language-specific OCR model loaded on-demand
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Post-Processing     │ ➜ Strip numbers, symbols & punctuation
│ & Noise Cleanup     │ ➜ Remove rogue UI icon letters & clean whitespace
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ Display & Export    │ ➜ Individual & aggregated text (Copy / Download .txt)
└─────────────────────┘
```

---

## 🚀 Getting Started

### Prerequisites

No installation, build steps, or server dependencies are required. All you need is an internet connection on first run so the browser can load the Tesseract.js engine and language models from the CDN.

### How to Run

1. Open `imagetotext.html` directly in your favorite web browser (e.g. double-click or right-click > **Open with** > Chrome / Edge / Firefox / Safari).
2. Alternatively, serve the folder with any static HTTP server:
   ```bash
   # Using Python
   python -m http.server 8000

   # Or using Node.js / npx
   npx serve .
   ```
3. Navigate to `http://localhost:8000/imagetotext.html` in your browser.

---

## 📖 How to Use

1. **Select Language**: Pick the language matching your images from the dropdown menu (default is **English**).
2. **Toggle Screenshot Mode**: Keep checked if processing UI screenshots with dark backgrounds or UI icons.
3. **Add Images**:
   - Drag and drop image files directly onto the drop box, or
   - Click the box to browse and select multiple files.
4. **Convert**: Click the **Convert to text** button to begin OCR extraction.
5. **Review & Copy**:
   - Inspect individual extracted text cards under each image.
   - Use the **Copy** button per item or scroll to the bottom to copy/download all combined text into a single `.txt` file.

---

## 📂 Project Structure

```
imagetotext/
├── imagetotext.html   # Main self-contained application (HTML, CSS, JavaScript)
├── LICENSE            # Apache License 2.0
└── README.md          # Project documentation
```

---

## 🛠️ Built With

- **HTML5 & CSS3**: Modern variables, responsive flexbox/grid layout, and dark mode media queries.
- **Vanilla JavaScript**: Lightweight DOM manipulation, Canvas image pre-processing, and Clipboard management.
- **[Tesseract.js](https://tesseract.projectnaptha.com/)** (`v5.1.1`): Pure JavaScript / WebAssembly port of the Tesseract OCR engine.

---

## 📄 License

This project is licensed under the **Apache License 2.0**. See the [LICENSE](file:///d:/chitte/imagetotext/LICENSE) file for details.
