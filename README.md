# PDF Assistant Agent with Groq and Gemini Embedding  

This project is a **knowledge-based agent** that leverages the **Groq** model and **Gemini Embedder** for intelligent responses. The agent reads and processes PDF documents, stores vector embeddings in a PostgreSQL database with `pgvector`, and provides interactive assistance through a CLI.  

## How It Works  

- **Agent Functionality**: Acts as an assistant to interact with users based on the knowledge extracted from a PDF file.  
- **Knowledge Base**: Loads and indexes the content of a PDF document using vector embeddings.  
- **Storage**: Uses PostgreSQL to store chat history, knowledge vectors, and agent state for persistent sessions.  

## Prerequisites  

- Docker installed on your system.  
- API keys for **Groq** and **Google** services stored in an `.env` file.  
- Python 3.9+ installed.  

## Setup  

### Step 1: Start the PostgreSQL Vector Database  

Run the following Docker command to start a PostgreSQL instance with `pgvector`:  

```bash  
docker run -d \
  -e POSTGRES_DB=ai \
  -e POSTGRES_USER=ai \
  -e POSTGRES_PASSWORD=ai \
  -e PGDATA=/var/lib/postgresql/data/pgdata \
  -v pgvolume:/var/lib/postgresql/data \
  -p 5532:5432 \
  --name pgvector \
  phidata/pgvector:16  
```  

### Step 2: Install Dependencies  

Install the required Python libraries:  

```bash  
pip install typer phi dotenv psycopg2  
```  

### Step 3: Configure Environment Variables  

Create a `.env` file with the following content:  

```dotenv  
GROQ_API_KEY=your_groq_api_key  
GOOGLE_API_KEY=your_google_api_key  
```  

### Step 4: Load the PDF Knowledge Base  

This agent uses a sample PDF (`ThaiRecipes.pdf`) hosted at `https://phi-public.s3.amazonaws.com/recipes/ThaiRecipes.pdf`. You can modify the URL in the code to load your own PDF files.  

### Step 5: Start the Agent  

Run the agent with:  

```bash  
python your_script_name.py
```  

Replace `your_script_name.py` with the name of your script file.  

## Agent Features  

1. **Knowledge Integration**: Automatically loads and processes a PDF as its knowledge base.  
2. **State Persistence**: Maintains conversation history and states in a PostgreSQL database.  
3. **Interactive CLI**: Provides an interactive Command-Line Interface for querying.  
4. **Advanced NLP**: Utilizes the Groq `llama-3.3-70b-versatile` model and Gemini Embedder for intelligent text processing.  
5. **Search Capabilities**: Allows users to search and interact with the knowledge base dynamically.  

---

Let me know if you want to highlight any additional features or make further refinements!
