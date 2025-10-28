# HR RAG Assistant 🤖

A Retrieval-Augmented Generation (RAG) system designed to help employees get accurate answers to HR-related questions by leveraging company-specific documentation.

## 📋 Overview

This project demonstrates the power of RAG by comparing traditional LLM chat responses with context-aware responses powered by company documentation. The system processes HR handbooks and policies to provide accurate, context-specific answers to employee questions.

## 🎯 Key Features

- **Document Processing**: Automatically chunks and processes HR documentation
- **Vector Search**: Uses ChromaDB for efficient document retrieval
- **Multi-Model Support**: Compatible with both OpenAI GPT and Google Gemini models
- **Interactive Interface**: Gradio-powered chat interface for easy interaction
- **Conversation Memory**: Maintains chat history for context-aware conversations
- **3D Visualization**: Interactive visualization of the vector store embeddings
- **Comparative Analysis**: Side-by-side comparison of RAG vs regular chat responses

## 🏗️ Architecture

```
HR Data → Text Chunking → Embeddings → Vector Store (ChromaDB) → Retrieval → LLM → Response
```

The system follows these steps:
1. **Document Loading**: Processes HR handbook text files
2. **Text Chunking**: Splits documents into manageable chunks (400 chars with 20 char overlap)
3. **Embedding Generation**: Creates vector embeddings using OpenAI or Google embeddings
4. **Vector Storage**: Stores embeddings in ChromaDB for fast similarity search
5. **Query Processing**: Retrieves relevant context for user questions
6. **Response Generation**: Uses LLM with retrieved context to generate accurate answers

## 📁 Project Structure

```
hr-rag-assistant/
├── rag_workflow.ipynb          # Main notebook with complete RAG implementation
├── hr_data/
│   └── hr_handbook.txt         # Sample HR documentation
├── chroma_db/                  # Vector database (created after first run)
└── README.md                   # This file
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- API key from either:
  - [OpenAI Platform](https://platform.openai.com/settings/organization/api-keys)
  - [Google AI Studio](https://makersuite.google.com/app/apikey)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/nurudeen19/hr-rag-assistant.git
   cd hr-rag-assistant
   ```

2. **Install dependencies:**
   ```bash
   pip install langchain langchain-google-genai langchain-community langchain-openai langchain-chroma python-dotenv matplotlib plotly scikit-learn requests gradio
   ```

3. **Set up API credentials:**
   - For OpenAI: Set `OPENAI_API_KEY` environment variable
   - For Google: Set `GOOGLE_API_KEY` environment variable

4. **Run the notebook:**
   - Open `rag_workflow.ipynb` in Jupyter/VS Code
   - Execute cells sequentially
   - Or try it in [Google Colab](https://colab.research.google.com/drive/1EXAtHelIPywc7lGkWdNhBejNOa8c2Qus?usp=sharing)

## 💻 Usage

### Basic Setup

```python
# Configure your preferred model
MODEL_NAME = "gpt-4o-mini"  # or "gemini-2.0-flash"

# Initialize the RAG system
# The notebook handles document processing, embedding generation, 
# and vector store creation automatically
```

### Example Queries

The system can answer questions like:
- "What is our company's leave policy?"
- "Who is the IT administrator?"
- "How do I apply for remote work?"
- "What are the working hours?"
- "What benefits do we offer?"

### Interactive Chat

Launch the Gradio interface for real-time conversations:

```python
gradio.ChatInterface(rag_chat, type="messages").launch()
```

## 📊 What's Included

### Sample HR Data

The project includes a comprehensive HR handbook covering:
- **Leave Policy**: Vacation, sick leave, and parental leave policies
- **Working Hours**: Standard hours and flexible arrangements
- **Employee Benefits**: Health insurance, retirement plans, professional development
- **Code of Conduct**: Professional behavior and IT security guidelines
- **Employee Directory**: Complete staff profiles with roles and experience
- **Remote Work Policy**: Detailed remote work procedures and expectations

### Visualization Features

- **3D Vector Visualization**: Interactive plot showing how documents are embedded in vector space
- **Comparative Analysis**: Side-by-side comparison of regular chat vs RAG responses

## 🛠️ Configuration Options

### Model Settings
```python
# Temperature: Controls creativity (0.0 = deterministic, 1.0 = creative)
temperature = 0.7

# Max tokens: Response length limit
max_tokens = 1000

# Chunk size: Document chunk size for processing
CHUNK_SIZE = 400
CHUNK_OVERLAP = 20

# Retrieval: Number of relevant documents to retrieve
TOP_K_RESULTS = 3
```

### Supported Models

**OpenAI Models:**
- gpt-4o-mini
- gpt-4o
- gpt-3.5-turbo

**Google Models:**
- gemini-2.0-flash
- gemini-1.5-pro

## 🔍 How It Works

### Traditional Chat vs RAG

**Traditional Chat:**
- Relies only on model's training data
- May provide generic or outdated information
- Cannot access company-specific policies

**RAG-Powered Chat:**
- Searches company documents for relevant context
- Provides accurate, up-to-date information
- Cites specific company policies and procedures

### The RAG Process

1. **Query Reception**: User asks a question
2. **Document Retrieval**: System searches vector database for relevant content
3. **Context Assembly**: Retrieved documents are prepared as context
4. **LLM Processing**: Model generates response using both the question and context
5. **Response Delivery**: User receives accurate, context-aware answer

## 🎨 Customization

### Adding Your Own Data

1. Replace `hr_data/hr_handbook.txt` with your organization's documentation
2. Ensure documents are in plain text format
3. The system will automatically process and index new content

### Extending Functionality

- **Multiple File Types**: Extend the loader to support PDF, Word, or other formats
- **Different Embeddings**: Experiment with different embedding models
- **Advanced Retrieval**: Implement semantic search with metadata filtering
- **Custom UI**: Build a custom web interface beyond Gradio

## 📈 Performance

The system is optimized for:
- **Fast Retrieval**: ChromaDB provides efficient similarity search
- **Memory Efficiency**: Document chunking prevents memory overload
- **Scalability**: Can handle large document collections
- **Accuracy**: Context-aware responses reduce hallucinations

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is available under the MIT License. See LICENSE file for details.

## 🆘 Support

- **Issues**: Report bugs or request features via GitHub Issues
- **Questions**: Check existing issues or start a discussion
- **Documentation**: Refer to the notebook comments for detailed implementation notes

## 🌟 Future Enhancements

- [ ] Multi-document support with source attribution
- [ ] Advanced query understanding with intent classification
- [ ] Integration with popular HR systems (BambooHR, Workday)
- [ ] Analytics dashboard for common queries
- [ ] Multi-language support
- [ ] Role-based access control

---

**Built with ❤️ using LangChain, ChromaDB, and modern LLMs**

*Streamline your HR operations with the power of AI and your company's knowledge base.*