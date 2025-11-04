# AI Agent

An intelligent AI agent that uses LLM routing to determine when web search is needed, combining the power of Groq's LLM API with Tavily's web search capabilities.

## Features

- **Intelligent Routing**: The agent uses an LLM to decide whether a query requires real-time web search
- **Web Search Integration**: Powered by Tavily API for real-time information retrieval
- **RAG (Retrieval-Augmented Generation)**: Combines web search results with LLM responses for accurate, up-to-date answers
- **Fast LLM Inference**: Uses Groq's fast inference API with Llama 3.1 8B Instant model

## Architecture

The agent follows a two-stage decision process:

1. **Routing Stage**: The LLM analyzes the query to determine if web search is needed
2. **Execution Stage**: 
   - If search is required: Performs web search → Retrieves results → Generates final answer using RAG
   - If search is not needed: Provides direct answer from LLM knowledge

## Setup

### Prerequisites

- Python 3.9+
- API keys for:
  - [Groq](https://console.groq.com/) (for LLM)
  - [Tavily](https://tavily.com/) (for web search)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/AliHamm/AIAgent.git
cd AIAgent
```

2. Create a virtual environment:
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Create a `.env` file in the root directory:
```env
GROQ_API_KEY=your_groq_api_key_here
TAVILY_API_KEY=your_tavily_api_key_here
```

## Usage

Run the agent with example queries:

```bash
python agent.py
```

Or use the `run_agent()` function programmatically:

```python
from agent import run_agent

run_agent("What is the weather in Tokyo?")
run_agent("What is the capital of France?")
```

## Example Queries

The agent handles both real-time information queries and general knowledge questions:

- **Real-time queries** (requires web search): "What is the weather in Tokyo?"
- **General knowledge** (direct LLM answer): "What is the capital of France?"
- **Technical questions**: "What is the quickest way to add a new user to a Linux system?"
- **Learning recommendations**: "What is the best way to learn Python?"

## Dependencies

- `requests` - HTTP library for API calls
- `python-dotenv` - Environment variable management
- `tavily` - Web search API client

## Project Structure

```
AIAgent/
├── agent.py          # Main agent implementation
├── .env              # Environment variables (not committed)
├── .gitignore        # Git ignore rules
└── README.md         # This file
```

## License

This project is open source and available under the MIT License.

