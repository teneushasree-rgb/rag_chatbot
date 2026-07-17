# 📄 PDF RAG (Retrieval-Augmented Generation) Chatbot

├── rag.py
├── data/
│   └── sample.pdf
└── README.md
```

---

## 🛠️ Technologies Used

- Python 3.x
- Sentence Transformers (Embeddings)
- NumPy
- FAISS or Custom Vector Store
- Large Language Model (LLM)

---

## 📦 Required Libraries

Install the required packages:

```bash
pip install sentence-transformers
pip install numpy
pip install faiss-cpu
pip install pypdf
pip install transformers
pip install torch
```

---

## 🚀 Workflow

### Step 1: Read the PDF

```python
text = extract_text("data/sample.pdf")
```

The PDF file is read and converted into plain text.

---

### Step 2: Split the Text

```python
chunks = chunk_text(text)
```

The extracted text is divided into smaller chunks to improve retrieval accuracy.

---

### Step 3: Generate Embeddings

```python
vectors = create_embeddings(chunks)
```

Each text chunk is converted into a numerical vector (embedding) that captures its semantic meaning.

---

### Step 4: Create the Vector Store

```python
store = VectorStore(vectors.shape[1])
```

A vector database is initialized to store the embeddings.

---

### Step 5: Store Embeddings

```python
store.add(vectors, chunks)
```

The embeddings and their corresponding text chunks are stored for efficient retrieval.

---

### Step 6: Ask Questions

```python
question = input("Ask a question or type exit")
```

The user enters a question related to the uploaded PDF.

---

### Step 7: Convert Question to Embedding

```python
query_vector = create_embeddings([question])[0]
```

The user's question is converted into an embedding.

---

### Step 8: Retrieve Relevant Chunks

```python
retrieved = store.search(query_vector, top_k=5)
```

The vector database retrieves the five most relevant chunks based on semantic similarity.

---

### Step 9: Build Context

```python
context = "\n\n".join(retrieved)
```

The retrieved chunks are combined to form the context passed to the language model.

---

### Step 10: Generate Answer

```python
answer = ask_llm(question, context)
```

The LLM generates an answer using the retrieved context and the user's question.

---

## 📊 Example Execution

```
PDF Uploaded Successfully

Ask a question or type exit:

> What is machine learning?

Answer:
Machine learning is a branch of artificial intelligence that enables systems to learn from data and improve their performance without being explicitly programmed.
```

---

## 📚 Modules Used

### `pdf_reader.py`

Extracts text from PDF files.

### `chunking.py`

Splits long documents into smaller text chunks.

### `embeddings.py`

Generates vector embeddings for text using a sentence embedding model.

### `vector_store.py`

Stores embeddings and performs similarity searches to retrieve relevant document chunks.

### `rag.py`

Sends the retrieved context and user query to a Large Language Model to generate the final response.

---

## 🔄 RAG Pipeline

```
PDF Document
      │
      ▼
Text Extraction
      │
      ▼
Text Chunking
      │
      ▼
Embedding Generation
      │
      ▼
Vector Database Storage
      │
      ▼
User Question
      │
      ▼
Question Embedding
      │
      ▼
Similarity Search
      │
      ▼
Relevant Context Retrieval
      │
      ▼
Large Language Model
      │
      ▼
Generated Answer
```

---

## 🎓 Learning Outcomes

By completing this project, you will understand:

- PDF text extraction
- Text chunking techniques
- Sentence embeddings
- Vector databases
- Semantic similarity search
- Retrieval-Augmented Generation (RAG)
- Context-aware question answering
- Large Language Model integration

---

## 🔮 Future Enhancements

- Support multiple PDF documents
- Build a web interface using Streamlit or Gradio
- Add conversational memory
- Store vectors in ChromaDB or Pinecone
- Support document upload through the UI
- Integrate OpenAI, Gemini, or Llama models
- Add citation and source highlighting for retrieved text

---

## 👩‍💻 Author

This project demonstrates the implementation of a **Retrieval-Augmented Generation (RAG) Chatbot** that answers user queries based on the content of uploaded PDF documents using embeddings, vector search, and a Large Language Model.
