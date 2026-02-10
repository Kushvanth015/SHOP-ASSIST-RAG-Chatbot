# 🤖 SHOP ASSIST RAG Chatbot (LangChain + FAISS + Ollama)

A **production-style local AI chatbot** that allows users to chat with **PDF/TXT documents** using **RAG (Retrieval-Augmented Generation)** — without using any paid APIs.

This project is built like real-world support chatbots (Amazon / Flipkart style), where answers come from internal documents such as:

✅ Policies  
✅ Orders / returns  
✅ FAQs  
✅ Product manuals  
✅ Knowledge base PDFs  

---
# USER
<img width="1920" height="1080" alt="Screenshot (298)" src="https://github.com/user-attachments/assets/e992eb1b-c731-44ae-ad7f-1fee1802c32f" />

---
# ADMIN
<img width="1920" height="1080" alt="Screenshot (299)" src="https://github.com/user-attachments/assets/26cfdb07-619e-4634-a3ee-5f8a92fa26f6" />

---
## 🚀 Project Motto

**"Make AI chatbots private, local, and document-grounded — with real-world deployment features."**

---

## 📌 What This Project Does

This chatbot provides:

### 👤 Users
- Login and ask questions from uploaded documents
- Get answers based only on company PDFs
- Chat continuously with conversation memory

### 👨‍💼 Admin
- Upload multiple PDFs/TXT files
- Build & update FAISS index
- Save index locally (no need to upload again)
- Enable Developer Mode (evidence + score + debug)

---

## 🔥 Key Features

### ✅ 1. Fully Local (No OpenAI API Needed)
- Runs on your laptop using **Ollama**
- Works offline after models + index are ready

### ✅ 2. Multi-file Upload (Admin Only)
- Admin can upload multiple PDFs/TXTs together
- All documents are added into one FAISS index

### ✅ 3. Saved FAISS Index
- Index is stored locally in `faiss_index/`
- Next time app runs, it loads automatically

### ✅ 4. Strict Mode (Document-only Answers)
- When enabled, chatbot answers only from document context
- If context is missing → responds:
  > "I don't know based on the document."

### ✅ 5. Admin/User Authentication (Roles)
- Admin can manage index
- Users can only chat

### ✅ 6. Conversation Memory Per Document Index
- Chat memory is stored per FAISS index
- Helps follow-up questions and continuity

### ✅ 7. Developer Mode (Admin only)
Developer mode shows:

- Retrieved chunks
- Evidence
- Groundedness score
- Source file + page number

In production, this is hidden from users.

---

## 🧠 Tech Stack

| Component | Tool |
|----------|------|
| Frontend UI | Streamlit |
| LLM | Ollama (Qwen2.5:3B) |
| Embeddings | nomic-embed-text |
| Vector DB | FAISS |
| RAG Framework | LangChain |
| Language | Python |

---

## 🏗️ Architecture (High Level)
<img width="1536" height="1024" alt="ChatGPT Image Feb 9, 2026, 08_27_19 PM" src="https://github.com/user-attachments/assets/26663bad-32fd-4713-9e84-ede3c7e06077" />

1. Admin uploads PDFs/TXTs  
2. Documents are split into chunks  
3. Chunks are converted into embeddings  
4. FAISS stores embeddings for fast retrieval  
5. User asks a question  
6. Retriever fetches top chunks  
7. LLM generates answer using retrieved context  
8. Response is shown in chat UI  

---

## 📂 Folder Structure

```bash
rag-chatbot/
│
├── app.py
├── users.json
├── faiss_index/           # auto created after indexing
│
├── utils/
│   ├── loader.py
│   ├── vectorstore.py
│   ├── rag_chain.py
│
├── requirements.txt
└── README.md


