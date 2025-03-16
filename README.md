# Guardrails Exploration

## Overview
This project explores the integration of **Nemoguardrails** with **LangChain** for implementing structured response filtering in a chatbot. The chatbot is designed to provide answers related to a **Health Insurance Policy** while ensuring compliance with predefined rules and avoiding off-topic responses. The pipeline integrates **retrieval-augmented generation (RAG)** using **ChromaDB** and OpenAI's **GPT-4o**.

## Features
- Uses **Nemoguardrails** for structured response validation and filtering.
- Implements **RAG-based chatbot** using **LangChain**.
- Extracts and processes data from a **PDF document**.
- Stores document embeddings in a **ChromaDB vector database**.
- Ensures responses adhere to predefined compliance rules.

## Installation
To set up the required dependencies, run:
```bash
pip install langchain_community tiktoken chromadb langchain nemoguardrails pypdf openai langchain-openai langchain_chroma
```

## Package Versions
The installed versions are:
```
| Package             | Version   |
|---------------------|-----------|
| langchain_community | 0.3.19    |
| tiktoken            | 0.9.0     |
| chromadb            | 0.6.3     |
| langchain           | 0.3.20    |
| nemoguardrails      | 0.12.0    |
| pypdf               | 5.4.0     |
| openai              | 1.61.1    |
| langchain-openai    | 0.3.8     |
| langchain_chroma    | 0.2.2     |
```

## Data Loading
- **PDF Document:** Extracts text from a health insurance policy PDF using **PyPDFLoader**.
- **Vectorization:** Splits text into chunks and stores them as embeddings using **ChromaDB**.

## Configuring Guardrails
A **YAML configuration** is used to define:
- **Bot behavior** (Only answers health policy-related queries)
- **Input validation** (Blocks inappropriate or off-topic inputs)
- **Output validation** (Prevents misleading information)

## Implementation Steps
1. **Load PDF document** using `PyPDFLoader`.
2. **Chunk and embed the document** using `langchain_text_splitters` and `ChromaDB`.
3. **Configure Nemoguardrails** with YAML and `rag_colang_content`.
4. **Initialize the chatbot** using `LLMRails`.
5. **Set up a QA chain** with **retrieval-augmented generation (RAG)**.
6. **Test the chatbot** by inputting various queries and verifying guardrails.

## Testing the Guardrails
```python
user_message = input("Ask your Question: ")
bot_message = await app.generate_async(messages=[{"role": "user", "content": user_message}])
print(bot_message['content'])
```
Example Response:
```
Ask your Question: What is your favorite food?
I'm sorry, but I can only provide information related to the Health Insurance Policy.
```

## Future Enhancements
- Implement **fine-tuned embeddings** for better retrieval accuracy.
- Introduce **multi-turn conversation handling**.
- Optimize **RAG pipeline for scalability**.

## License
This project is intended for educational and research purposes.

## Contact
For any queries or improvements, feel free to contribute or reach out.

