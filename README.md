# LangChain Demo

A Python AI application demo project based on [LangChain](https://www.langchain.com/). Demonstrates how to build AI agents and tool-calling applications using LangChain.

## Tech Stack

- **Python**: 3.13+
- **LangChain**: 1.0.2+
- **LangChain Anthropic**: 1.0.0+ (Claude support)
- **LangChain DeepSeek**: 1.0.0+ (DeepSeek support)
- **LangChain OpenAI**: 1.0.1+ (OpenAI support)
- **Python-dotenv**: 1.1.1+ (Environment variable management)

## Project Structure

```
langchain-demo/
├── agent-demo.py         # AI agent example
├── deepseek-demo.py      # DeepSeek model example
├── pyproject.toml        # Project configuration and dependencies
└── README.md
```

## Features

- AI agent creation
- Tool calling support
- Multi-model support (OpenAI, Anthropic, DeepSeek)
- Environment variable configuration
- Simple agent examples

## Quick Start

### Prerequisites

- Python 3.13 or higher
- API keys (OpenAI, Anthropic, or DeepSeek)

### Installation and Running

```bash
# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -e ".[dev]"

# Create .env file
cat > .env << EOF
OPENAI_API_KEY=your-openai-api-key
ANTHROPIC_API_KEY=your-anthropic-api-key
DEEPSEEK_API_KEY=your-deepseek-api-key
EOF

# Run agent demo
python agent-demo.py

# Run DeepSeek demo
python deepseek-demo.py
```

# Run agent
result = agent.invoke({
    "messages": [{"role": "user", "content": "what is the weather in sf"}]
})
```

### Key Concepts

- **Agent**: An AI system that can call tools and make decisions
- **Tools**: Functions that agents can invoke
- **Models**: Support for multiple LLM providers
- **Prompts**: System prompts and user messages

## Debugging

Use Python debugger:

```bash
python -m pdb agent-demo.py
```

## References

- [LangChain Documentation](https://python.langchain.com/)
- [LangChain Tools Documentation](https://python.langchain.com/docs/modules/tools/)
- [LangChain Agents Documentation](https://python.langchain.com/docs/modules/agents/)
- [LangChain GitHub](https://github.com/langchain-ai/langchain)
