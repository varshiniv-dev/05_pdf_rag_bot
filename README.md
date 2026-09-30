# Ask My PDF Bot — RAG Chatbot

## Core pipeline
PDF upload → PyMuPDF extraction → chunking → SentenceTransformer embeddings → FAISS vector search → answer generation → page/source citation.

This directly follows the guide's basic/advanced RAG path. Gemini is optional. If `GEMINI_API_KEY` is missing, the app returns a retrieval-based extractive answer instead of inventing an LLM response.

## Run
```bash
pip install -r requirements.txt
streamlit run app.py
```

Optional Gemini setup:

Windows PowerShell:
```powershell
$env:GEMINI_API_KEY="YOUR_KEY"
streamlit run app.py
```

Linux/macOS:
```bash
export GEMINI_API_KEY="YOUR_KEY"
streamlit run app.py
```

Upload one or more PDFs and ask questions. Answers show the retrieved page sources.

## Architecture
PDFs → text + page metadata → chunks → embeddings → FAISS → top-k retrieval → Gemini/extractive answer → citations.
