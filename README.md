# Chat with PDF Using RAG Pipeline  

## Overview  

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline for interacting with semi-structured data in PDF files. The system can process multiple PDFs, extract and embed the data, store it in a vector database for efficient retrieval, and answer user queries using an LLM (Large Language Model). Additionally, it supports comparison queries for analyzing and comparing information across multiple PDF files.

---

## Features  

### 1. **Data Ingestion**  
- Extracts text and structured information from PDFs.  
- Segments data into manageable chunks for better granularity.  
- Converts chunks into vector embeddings using a pre-trained embedding model (`sentence-transformers/all-MiniLM-L6-v2`).  
- Stores embeddings in a FAISS vector database for fast similarity-based retrieval.

### 2. **Query Handling**  
- Converts user queries into vector embeddings.  
- Performs similarity searches in the vector database to retrieve relevant chunks.  
- Uses retrieved data and an LLM model (`ChatGroq`) to generate accurate and context-rich responses.

### 3. **Comparison Queries**  
- Supports comparison tasks across multiple PDF files.  
- Aggregates relevant data and presents structured responses, such as tables or bullet-point summaries.  

### 4. **Response Generation**  
- Combines retrieved chunks and user queries with RAG prompts to generate precise and factual responses.  
- Ensures responses include direct references to extracted data.

---

## Requirements  

- Python 3.8 or above  
- Libraries:
  - `pdfminer.six`
  - `PyMuPDF` (`fitz`)
  - `langchain`
  - `langchain-groq`
  - `sentence-transformers`
  - `FAISS`
  - `google-colab` (if running on Colab)

---

## How to Run  

### Step 1: Install Dependencies  
Install the required libraries:  
```bash
pip install pdfminer.six pymupdf langchain langchain-groq sentence-transformers faiss google-colab
```

### Step 2: Prepare Environment  
- **Google Colab**: Open the script in a new Colab notebook for the easiest setup.  
- **Local Environment**: Ensure Python is installed and configured with the libraries listed above.

### Step 3: Run the Code  
1. Copy the script and execute it in your environment.  
2. When prompted, upload your PDF files.  
3. The script will:  
   - Extract text and images from the PDFs.  
   - Embed and store text chunks in a FAISS vector database.  

### Step 4: Ask Questions  
- Enter your natural language query when prompted.  
- Example query:  
  - **Extract Data**: "What is the unemployment information based on the type of degree from page 2?"  
  - **Tabular Data**: "Retrieve the tabular data from page 6."  
- The system will process your query and provide a response.

### Step 5: Comparison Queries  
- Example query: "Compare the unemployment rates for bachelor's and master's degrees across all uploaded PDFs."  
- The system will retrieve, process, and generate a structured comparison.

---

## Example Output  

- **Text Extraction**: Extracted text chunks saved into embeddings.  
- **Images**: Saved in the `extracted_images/` folder.  
- **Query Result**:  
  - Input: "Retrieve the unemployment information from page 2 based on the type of degree."  
  - Output: *"Unemployment rate for Bachelor's degree holders is 6.8%, Master's degree holders is 4.1%, etc."*

---

## Notes  

- Ensure all PDFs are correctly formatted; semi-structured data with readable text works best.  
- For detailed responses, queries should be specific and contextual.
