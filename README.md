# Basic RAG System with FastAPI

This project demonstrates a simple Retrieval-Augmented Generation (RAG) system built using **FastAPI**, **Pinecone**, and **Google Generative AI**. It allows users to upload documents (PDF/DOCX), index their contents for efficient retrieval, and query the indexed documents to receive AI-generated responses.

---

## Features

- Upload multiple PDF and DOCX files for indexing.
- Automatic chunking of documents for efficient retrieval.
- Query the system to receive AI-powered answers based on uploaded content.
- Powered by **Pinecone** for vector similarity search and **Google Generative AI** for language model-based responses.

---

## Folder Structure

```
├── app.py               # Main FastAPI application
├── example.env          # Example environment variables file
├── requirements.txt     # Python dependencies for the project
```

---

## Prerequisites

Before running the project, ensure you have the following:

1. Python 3.8+ installed on your machine.
2. Access to the following API keys:
   - Pinecone API Key
   - Google API Key
3. Docker (optional, for containerized deployment).

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone <repository-url>
cd <repository-name>
```

### 2. Create and Activate a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Rename `example.env` to `.env` and update the following variables with your credentials:

```env
PINECONE_API_KEY=<your-pinecone-api-key>
GOOGLE_API_KEY=<your-google-api-key>
```

### 5. Run the FastAPI Server

```bash
uvicorn app:app --reload
```

The server will start at [http://127.0.0.1:8000](http://127.0.0.1:8000).

---

## API Endpoints

### **1. Upload Documents**
- **URL**: `/upload_documents/`
- **Method**: `POST`
- **Description**: Upload one or more documents (PDF/DOCX) to index their content.
- **Request Body**: Form data containing file uploads.
- **Response**: JSON message indicating the number of indexed document chunks.

### **2. Query System**
- **URL**: `/query/`
- **Method**: `GET`
- **Description**: Query the system and get an AI-generated response based on the indexed documents.
- **Query Parameter**: `query` (string) - The question to ask.
- **Response**: JSON containing the query and the generated answer.

---

## Example Usage

### Uploading Documents

```bash
curl -X POST "http://127.0.0.1:8000/upload_documents/" \
-H "accept: application/json" \
-F "files=@example.pdf" \
-F "files=@example.docx"
```

### Querying the System

```bash
curl -X GET "http://127.0.0.1:8000/query/?query=What is data preprocessing?" \
-H "accept: application/json"
```

---

## Dependencies

This project uses the following Python libraries:

- `fastapi`
- `uvicorn`
- `pinecone`
- `langchain_google_genai`
- `langchain_community`
- `langchain_core`

Refer to `requirements.txt` for the full list.

---