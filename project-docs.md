# RAG Pipeline with LangChain and Ollama

A simple Retrieval Augmented Generation (RAG) pipeline implementation using LangChain and Ollama. This project demonstrates how to create a question-answering system that uses document context to provide more accurate and relevant responses.

## Features

- Document loading and processing using PyPDFLoader
- Vector embeddings using Ollama
- In-memory vector storage with DocArrayInMemorySearch
- Question answering using LangChain's chain mechanism
- Customizable prompt templates
- Batch question processing capability

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/rag-pipeline.git
cd rag-pipeline
```

2. Create and activate a virtual environment:
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows, use `.venv\Scripts\activate`
```

3. Install the required packages:
```bash
pip install -r requirements.txt
```

4. Install and start Ollama:
- Follow the installation instructions at [Ollama's official website](https://ollama.ai/)
- Pull the required model:
```bash
ollama pull llama2
```

## Usage

1. Place your PDF documents in the project directory

2. Run the Jupyter notebook:
```bash
jupyter notebook
```

3. Open `notebook.ipynb` and follow the implementation steps:
- Load and process documents
- Create embeddings
- Set up the retriever
- Configure the RAG pipeline
- Ask questions and get contextualized answers

## Example Usage

```python
# Create the RAG pipeline
chain = (
    {"context": itemgetter("question") | retriever, "question": itemgetter("question")}
    | prompt 
    | model 
    | parser 
)

# Ask a single question
response = chain.invoke({
    "question": "Why is management important?"
})

# Process multiple questions
questions = [
    "How to Advance Your Career with Business Skills?",
    "Why Read Business Articles and Blogs?",
    "Why Your Resume is important?",
]

for question in questions:
    answer = chain.invoke({"question": question})
    print(f"Question: {question}")
    print(f"Answer: {answer}\n")
```

## Project Structure

```
rag-pipeline/
├── notebook.ipynb        # Main implementation notebook
├── requirements.txt      # Project dependencies
├── README.md            # Project documentation
└── career.pdf           # Sample document for testing
```

## Requirements

- Python 3.8+
- Ollama
- LangChain
- DocArray
- PyPDF2
- Jupyter

See `requirements.txt` for complete list of dependencies.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request


