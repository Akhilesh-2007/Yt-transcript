# YouTube Transcript RAG with LangChain and Ollama

This project contains a Jupyter notebook that builds a retrieval-augmented generation (RAG) workflow from a YouTube video's transcript. It uses:

- **YouTube Transcript API** to fetch English captions
- **LangChain** to split the transcript, retrieve relevant chunks, and build a question-answering chain
- **FAISS** for local vector search
- **Ollama** for local text embeddings and chat completions

The notebook is [Copy of rag-using-langchain.ipynb](./Copy%20of%20rag-using-langchain.ipynb).

## Requirements

- Python and Jupyter (or Visual Studio Code with the Jupyter extension)
- [Ollama](https://ollama.com/) installed and running
- The `llama3.2:3b` chat model and `nomic-embed-text` embedding model

Pull the models in a terminal:

```powershell
ollama pull llama3.2:3b
ollama pull nomic-embed-text
```

Install the Python dependencies in the environment used by your notebook:

```powershell
python -m pip install -U youtube-transcript-api langchain-text-splitters langchain-ollama langchain-community faiss-cpu
```

## Run

1. Clone this repository and open the notebook.
2. Select the Python environment where you installed the dependencies.
3. Confirm Ollama is running and both models are available (`ollama list`).
4. Run the notebook cells in order.
5. Change `video_id` in the transcript-ingestion cell to the YouTube video ID you want to query. The video must have English captions available.

The notebook splits the transcript into overlapping chunks, embeds them with `nomic-embed-text`, retrieves the four most relevant chunks for a question, and generates an answer with `llama3.2:3b`. It also demonstrates composing the steps into a LangChain runnable chain.
