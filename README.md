# Chat_with_Multiple_PDFs_using_Mistral-7B-and-FAISS

#### **Description:**  
This project implements an interactive chatbot capable of processing multiple PDF files and answering user queries based on their content. It leverages **Mistral-7B-Instruct** as the language model, FAISS for efficient vector search, and **sentence-transformers/all-MiniLM-L6-v2** for embedding text chunks. The system loads PDFs, splits them into manageable chunks, generates vector embeddings, and retrieves relevant information to answer queries.  

### **Features:**  
✅ **Multi-PDF Support:** Load and process multiple PDFs at once.  
✅ **Efficient Retrieval:** Uses FAISS for fast similarity search on text chunks.  
✅ **Customizable Embeddings:** Uses Sentence Transformers for high-quality embeddings.  
✅ **Mistral-7B LLM:** A powerful instruction-tuned model for natural language understanding.  
✅ **Interactive Chat Interface:** Allows users to continuously query the chatbot.  

### **How it Works:**  
1. **Load PDFs:** Extract text from all PDFs in the specified directory using `PyPDFDirectoryLoader`.  
2. **Text Splitting:** Uses `RecursiveCharacterTextSplitter` to break text into chunks (10,000 tokens with 20-token overlap).  
3. **Embedding Generation:** Converts text chunks into dense vector representations using `sentence-transformers/all-MiniLM-L6-v2`.  
4. **Vector Storage:** FAISS stores embeddings, enabling fast similarity searches.  
5. **LLM-based Querying:** The chatbot uses **Mistral-7B** to generate human-like responses by retrieving the most relevant chunks.  
6. **Real-time Q&A:** Users can input queries in an interactive loop, retrieving answers from the processed PDFs.  

### **Limitations & Areas for Improvement:**  
🔴 **Memory Intensive:** Mistral-7B requires a high amount of VRAM, making it challenging for low-resource devices.  
🔴 **Latency Issues:** Large models like Mistral-7B may introduce latency in query processing.  
🔴 **Chunking Strategy:** Fixed chunk sizes might break the logical flow of content, affecting retrieval quality.  
🔴 **Limited Context Window:** Despite using `n_ctx=4096`, long documents may not fit within the model’s attention span.  
🔴 **No Web UI:** The project currently runs in a command-line interface (CLI). A web-based front end would improve usability.  

### **Possible Improvements:**  
✅ **Use a Smaller Model:** Replace Mistral-7B with a lighter model like LLaMA 2 7B, Falcon 7B, or Phi-2 for better performance on limited hardware.  
✅ **Better Chunking Strategies:** Implement an adaptive chunking approach using semantic segmentation to improve retrieval accuracy.  
✅ **Use a More Advanced Embedding Model:** Upgrade to `bge-large-en-v1.5` or `text-embedding-ada-002` for better embeddings.  
✅ **Hybrid Search (BM25 + FAISS):** Combine sparse retrieval (BM25) with dense retrieval (FAISS) for improved accuracy.  
✅ **Add a Web Interface:** Integrate Streamlit, Gradio, or FastAPI for a more interactive UI.  
✅ **Optimize FAISS Indexing:** Experiment with **HNSW** or other FAISS index types to speed up retrieval.  

### **Alternative Implementations:**  
🟢 **Using LangChain Agents:** Implement LangChain agents to support multi-step reasoning.  
🟢 **Using LlamaIndex (GPT Index):** Indexing documents with LlamaIndex can enhance retrieval efficiency.  
🟢 **Using OpenAI's GPT-4-turbo API:** If real-time inference is required, using an API-based LLM reduces computational overhead.  
🟢 **Using Haystack:** This open-source NLP framework supports advanced retrieval-augmented generation (RAG).  
🟢 **Using Weaviate or Pinecone Instead of FAISS:** These vector databases offer cloud-based and scalable indexing solutions.  

This project provides a strong foundation for AI-powered document-based Q&A and can be expanded with additional features. 🚀  

