# 📊 Personal Finance RAG Assistant

A Retrieval-Augmented Generation (RAG) powered AI assistant that answers personal finance questions using content extracted directly from your own PDF documents — grounded, not hallucinated.

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-Vector%20Search-00A98F?style=for-the-badge)
![Gemini](https://img.shields.io/badge/Google%20Gemini-8E75B2?style=for-the-badge&logo=googlegemini&logoColor=white)

---

## 🚀 What This Project Does

1. Reads multiple PDF files from the `documents/` folder
2. Extracts and chunks the text
3. Generates semantic embeddings **locally** using Sentence Transformers
4. Stores the embeddings in a FAISS vector database
5. Retrieves the most relevant context for a user's query via similarity search
6. Uses **Google Gemini** to generate a grounded answer from that context

The system only answers from the uploaded financial documents — no making things up.

---

## 🏗️ Architecture Overview

```
PDF Documents
     │
     ▼
Text Extraction (PyPDF)
     │
     ▼
Chunking
     │
     ▼
Local Embeddings (SentenceTransformer — all-MiniLM-L6-v2)
     │
     ▼
FAISS Vector Database
     │
     ▼
Similarity Search
     │
     ▼
Gemini (Answer Generation)
     │
     ▼
Streamlit Frontend
```

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Language | Python |
| Embeddings | Sentence Transformers (`all-MiniLM-L6-v2`) |
| Vector Search | FAISS |
| LLM | Google Gemini API |
| Frontend | Streamlit |
| PDF Parsing | PyPDF |

---

## 📂 Project Structure

```
personal-finance-RAG-assistant/
│
├── documents/           # Drop your source PDFs here
├── app.py               # Streamlit app entry point
├── main2.py             # RAG pipeline logic
├── requirements.txt
├── .gitignore
└── README.md
```

---

## ⚙️ Installation & Setup

**1️⃣ Clone the repository**
```
git clone https://github.com/GouravK1107/personal-finance-RAG-assistant.git
cd personal-finance-RAG-assistant
```

**2️⃣ Create a virtual environment**
```
python -m venv venv
source venv/bin/activate     # Linux / macOS
venv\Scripts\activate        # Windows
```

**3️⃣ Install dependencies and add your Gemini API key**
```
pip install -r requirements.txt
```
Create a `.env` file in the project root:
```
GEMINI_API_KEY=your_gemini_api_key_here
```
Then drop your personal finance PDFs into the `documents/` folder.

**4️⃣ Run the application**
```
streamlit run app.py
```
The app will open automatically in your browser.

---

## 💡 Example Questions

- What is budgeting?
- How does compound interest work?
- What are different investment options?
- What is an emergency fund?
- How does retirement planning work?

---

## 🔒 Why Local Embeddings?

Embeddings were initially generated via the Gemini API — but API rate limits caused quota issues when processing large PDFs.

**The fix:**
- Embeddings are now generated **locally** using Sentence Transformers
- Gemini is used **only** for final answer generation
- No embedding API limits
- Faster overall performance
- A more scalable architecture

---

## 📈 Future Improvements

- 📤 File upload feature directly in the UI
- 🏷️ Answer metadata (source file name + page number)
- 💾 Persist the FAISS index to disk instead of rebuilding each run
- ☁️ Deploy to Streamlit Cloud
- 📊 Add retrieval/answer evaluation metrics

---

## 🎯 Project Goal

This project is a portfolio-level implementation of a production-style RAG pipeline, demonstrating:

- Open-source local embeddings
- Efficient vector similarity search
- LLM-based grounded answer generation
- A functional, interactive web interface

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome.
Fork → create a branch → commit → push → open a pull request.

---

## ⭐ Support

If this project helped you, consider giving it a ⭐ on GitHub.

---

## 👨‍💻 Author

**Gourav R**
Backend Developer | Applied AI Developer — exploring RAG pipelines & applied LLM systems

GitHub: https://github.com/GouravK1107
Portfolio: https://gouravk1107.github.io/my-portfolio/

---

Made with ❤️, FAISS, and a lot of PDFs.
