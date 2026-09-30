# 📄 Ask My PDF Bot — RAG Chatbot

A Retrieval-Augmented Generation (RAG) chatbot that allows users to upload PDF documents and ask questions about their contents.

The application extracts PDF text, creates semantic embeddings, stores them in a FAISS vector index, retrieves relevant sections, and generates an answer using either Gemini or an extractive fallback.

> ⚠️ This project is an educational/internship prototype. The quality of answers depends on the uploaded document, retrieval quality, and the configured language model.

---

## 📌 Project Overview

The project demonstrates an end-to-end PDF question-answering pipeline:

```text
PDF Upload
    ↓
PyMuPDF Text Extraction
    ↓
Text Chunking
    ↓
SentenceTransformer Embeddings
    ↓
FAISS Vector Search
    ↓
Relevant Chunk Retrieval
    ↓
Gemini / Extractive Answer
    ↓
Page & Source Information
```
# ✨ Features
Upload PDF documents
Extract text from PDFs using PyMuPDF
Preserve page-level metadata
Split extracted text into smaller chunks
Generate semantic embeddings using SentenceTransformers
Store embeddings using FAISS
Retrieve relevant document sections
Ask natural-language questions
Generate answers using Gemini when configured
Use an extractive retrieval-based fallback when Gemini is unavailable
Display retrieved source/page information
# 🧠 RAG Architecture

The application follows this architecture:

PDF
 ↓
Text + Page Metadata
 ↓
Chunking
 ↓
SentenceTransformer Embeddings
 ↓
FAISS Index
 ↓
Top-K Retrieval
 ↓
Gemini Answer Generation
        OR
Extractive Fallback
 ↓
Answer + Source/Page Information
# 📚 PDF Processing

Uploaded PDFs are processed using PyMuPDF.

The application extracts:

Text content
Page information
Document metadata used for source references

The extracted text is divided into chunks before generating embeddings.

# 🔎 Semantic Search

The project uses SentenceTransformers to convert text chunks into numerical embeddings.

These embeddings are stored in a FAISS vector index.

When a user asks a question:

The question is converted into an embedding.
FAISS searches for the most relevant chunks.
The retrieved chunks are passed to the answer-generation stage.
Relevant page/source information is displayed with the answer.
# 🤖 Answer Generation
Gemini Mode

If GEMINI_API_KEY is configured, the application can use Gemini to generate a natural-language answer based on the retrieved document content.

Extractive Fallback

If no Gemini API key is configured, the application uses a retrieval-based extractive fallback instead of requiring an external LLM.

This allows the basic RAG pipeline to run without a Gemini API key.

⚠️ The fallback is not equivalent to full LLM-based generation. It is included so that the application remains usable when Gemini is unavailable.

# 🖥️ Streamlit Application

The project provides an interactive Streamlit interface where users can:

Upload a PDF.
Process the document.
Ask a question.
Retrieve relevant document content.
View the generated/extracted answer.
View page/source information.
# 📸 Application Screenshots

Add the final application screenshots to:

screenshots/

The screenshots demonstrate:

PDF upload and processing
Question answering
Retrieved source/page information
# 📁 Project Structure
05_pdf_rag_bot/
│
├── screenshots/
│   └── ...
│
├── app.py
├── requirements.txt
├── README.md
└── .gitignore
# ⚙️ Installation

Install the required dependencies:

pip install -r requirements.txt
🚀 Run the Application

Run:

python -m streamlit run app.py

The application will open in the browser.

🔑 Optional Gemini Configuration

Gemini is optional.

Windows PowerShell
$env:GEMINI_API_KEY="YOUR_KEY"
python -m streamlit run app.py
Linux/macOS
export GEMINI_API_KEY="YOUR_KEY"
python -m streamlit run app.py

🔒 Never commit your API key to GitHub. Keep .env files and secrets excluded from version control.

# ⚠️ Limitations

This is an internship-level RAG prototype and has several limitations:

Answer quality depends on the quality of PDF text extraction.
Retrieval quality depends on chunking and embedding similarity.
Scanned/image-only PDFs may require OCR, which is not implemented in the current MVP.
The application does not guarantee factual correctness.
Gemini requires an API key for LLM-based answer generation.
The extractive fallback is simpler than an LLM-generated answer.
No advanced reranking pipeline is implemented.
No hybrid BM25 + vector retrieval is implemented.
No conversational memory is implemented.
No production authentication or multi-user system is included.
No production monitoring or evaluation pipeline is included.
# 🔮 Future Improvements

Possible future improvements include:

Add OCR support for scanned PDFs.
Add hybrid BM25 + vector retrieval.
Add reranking models.
Add conversational memory.
Add query expansion techniques such as HyDE.
Improve chunking strategies.
Add answer-quality evaluation.
Add document-level access control.
Add FastAPI backend support.
Containerize using Docker.
Deploy using cloud infrastructure.
Add monitoring and usage analytics.
# 🛡️ Disclaimer

This project is intended for educational, research, and internship demonstration purposes.

The chatbot should not be treated as an authoritative source. Users should verify important information against the original PDF documents.

# 📌 Project Status

Completed — Internship Prototype

The project demonstrates a functional PDF-based RAG workflow using PyMuPDF, SentenceTransformers, FAISS, optional Gemini generation, and Streamlit.