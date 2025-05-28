
# RAG based Chatbot for PDF with Agents 

## Local Setup: 
- pip install \
    langchain \
    langchain-openai \
    langchain-community \
    langchain-core \
    langchain-deepseek \
    openai \
    crewai \
    crewai-tools \
    PyPDF2 \
    faiss-cpu \
    neo4j \
    pyvis \
    streamlit \
    ipython


This python file couldnt run on jupyter notebook as i used streamlit.
isntead convert the ipynb files to python files and streamlit run filename.py
 - streamlit run basic_rag.py
This is the working video for the BASIC RAG chatbot - https://drive.google.com/file/d/1G5swtCnlRIBFxqAOZCY7eU151uML-2XI/view?usp=sharing

THis video shows the generation of knowledge graph  - 


This project implements a Retrieval Augmented Generation (RAG) chatbot with streamlit interface using LLMs to interact with content from a PDF document . The system incorporates:
- KV Caching
- Conversational History Awareness
- Knowledge Graph Generation (Neo4j)
- Agentic RAG for Enhanced Multi-Agent Reasoning (using crewAI)

![image](https://github.com/user-attachments/assets/947ebbbd-7ff7-4b82-ba68-f15bc47d4fd1)


---

##  Code Workflow (with BONUS & EXTRA BONUS)

1. **Extract Raw Text from PDF**
   - Used PdfPlumber to extract textual content.

2. **Chunking**
   - Used RecursiveCharacterTextSplitter (langchain) to split text into manageable chunks.

3. **Embeddings & Vector Store**
   - Generated embeddings via OpenAI Embedding Model
     - (Deepseek not supported in Langchain embedding module)
   - Stored embeddings in FAISS vector store.

4. **Similarity Search**
   - For each user query, retrieve top-k (typically 4) most relevant chunks from the vector store.

5. **Prompt Formatting**
   - **Answer Generation Prompt:** Includes context + user query + conversation history.
   - **Document Summarization Prompt:** Returns concise summary with entities and relations.
   - **Cypher Generation Prompt:** Converts summary into Cypher format for Neo4j Knowledge Graph.

6. **KV Caching**
   - Used a Python dictionary as a cache.
   - If a question has been asked before, return cached value.
   - Else, generate new answer and store the key-value pair.

7. **Answer Generation**
   - Used Deepseek for generating final LLM-based answers.

8. **History Awareness**
   - Maintained a conversation history dictionary (role: user/AI) and message content.

9. **Streamlit UI**
     - Upload PDF
     - Continuously chat with document context in the session

10. **Agentic RAG (Extra Bonus)**
    - Followed CrewAI’s tutorials for multi agent coordination.
    - Created 3 agents with specific tasks.
    - Instructed each to output in structured JSON format under 'expected_output'.

---

##  Experiments

- ✅ Attempted Pinecone: Faced complexity & reliability issues; settled on FAISS.
- ✅ Tried Langchain’s Conversation Pipeline for the chatbot But seemed too complex.
- ✅ Experimented with summarizing conversation history: Was slow, decided to pass full history directly.
- ✅ Tweaked Cypher prompt for better formatting output (initial attempts were giving errors).

---

##  Error Handling

- **Streamlit Session Bug**:
  - Initially placed variables (like history) outside the main Streamlit function.
  - Realized Streamlit re-runs code on each interaction, resetting variables.
  -  Fixed by using st.session_state to persist session specific data.

---

##  Resources(medium blogs and yt vids)

- [RAG Basics to Advanced (Medium)](https://medium.com/@tejpal.abhyuday/retrieval-augmented-generation-rag-from-basics-to-advanced-a2b068fd576c)
- [Agentic RAG with CrewAI (YouTube)](https://www.youtube.com/watch?v=mVNMrgexxoM)
- [PDF QA with RAG (Medium)](https://medium.com/@drjulija/how-i-built-a-basic-rag-for-pdf-qa-in-a-few-lines-of-python-code-9849c32e59f0)
- [Langchain RAG Implementation](https://medium.com/data-science/retrieval-augmented-generation-rag-from-theory-to-langchain-implementation-4e9bd5f6a4f2)
- [CrewAI Agentic RAG (Medium)](https://medium.com/ai-advances/agentic-rag-build-an-enhanced-multi-agent-retrieval-augmented-generation-rag-system-with-crew-ai-904670aaffc2)

---

##  Architecture Summary

```
          [PDF Upload]
                ↓
        [Text Extraction]
                ↓
           [Chunking]
                ↓
         [Questions and Doc Embedding + FAISS]
                ↓
          [Similarity Search]
                ↓
        [Prompt Formatting]
                ↓
        [Deepseek (LLM Call)]
                ↓
[KV Cache] ←→ [Conversation History]
                ↓
        [Streamlit Chat UI]
                ↓
     [Neo4j Knowledge Graph UI]
                ↓
     [Agentic Coordination (CrewAI)]
```

---

