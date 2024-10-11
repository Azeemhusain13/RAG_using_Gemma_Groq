**Gemma Model Document Q&A - Retrieval-Augmented Generation (RAG)**
This project implements a Q&A system using the Groq API, FAISS vector store, and Google Generative AI embeddings. The system allows users to upload PDF documents, convert them into vectors, and use those vectors to retrieve relevant information based on user queries. The response is generated through the Groq-powered Large Language Model (LLM) and the Gemma API.

**Key Features**
**PDF Data Ingestion:** Users can upload a set of PDF documents that are ingested into the application.
**Vector Embeddings:** The documents are split into smaller chunks, converted into vector embeddings, and stored in a FAISS vector store for fast retrieval.
**Q&A Using Groq and Gemma API:** Users can enter a question, and the system will retrieve relevant document chunks and use the Groq-powered LLM to generate a context-aware response.
**Real-time Embedding Creation:** The vector embeddings for documents are created using the Google Generative AI embeddings model.
**Low-latency Retrieval:** The system supports rapid document search using FAISS and provides answers in real time.

**Usage**
**1. Start the Application**
To run the Streamlit application, use the following command:
**streamlit run app.py**

**2. Embedding Documents**
Click the "Documents Embedding" button to load the PDF documents and create vector embeddings from the documents. This operation will prepare the FAISS vector database for retrieval tasks.
**3. Ask Questions**
Enter a question into the input box, and the system will:
Retrieve relevant documents from the FAISS vector store.
Use the Groq-powered LLM model to generate an answer based on the retrieved documents.
Display the answer and document similarity context.
Code Walkthrough
**Loading the Groq API:**

The ChatGroq object is instantiated with the provided API key, and the Llama3-8b-8192 model is used for document-based question answering.
**Document Embedding:**

The PDF files are loaded using PyPDFDirectoryLoader, and the documents are split into manageable chunks using RecursiveCharacterTextSplitter.
The Google Generative AI Embeddings model (embedding-001) is used to create vector representations of these chunks.
The FAISS vector store stores these embeddings for fast document retrieval.
Q&A Process:

When a user enters a question, the system retrieves the relevant document chunks from FAISS using as_retriever().
The ChatPromptTemplate generates a prompt based on the retrieved chunks and the user's question.
The LLM processes the input and provides an answer.
**Execution Time:**

The processing time for retrieving documents and generating the response is displayed.
**Dependencies**
**streamlit:** Web app framework for creating interactive UI.
**langchain:** Framework for building LLM applications.
**groq:** API to use the Groq hardware accelerator for AI workloads.
**faiss-cpu:** FAISS library for efficient similarity search and clustering.
**langchain_community.vectorstores:** Integration of vector stores with LangChain.
**langchain_google_genai:** Embeddings model from Google Generative AI.
**pypdf:** Library for reading and processing PDF documents.
**python-dotenv:** Library for managing environment variables.

**Future Improvements**
Add functionality to upload documents dynamically via the web interface.
Implement more advanced document processing, such as text extraction from non-textual PDFs.
Add support for different types of document formats, such as Word or Excel.
