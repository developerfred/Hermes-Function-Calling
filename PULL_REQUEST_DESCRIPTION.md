# LangChain Integration for Hermes Function Calling

This pull request adds full LangChain integration to the Hermes Function Calling framework. The integration allows Hermes tools to be used within LangChain agents and vice versa, expanding the capabilities of both frameworks.

## Changes Made

1. Added `langchain` and `langchain-core` to `requirements.txt`
2. Added `get_langchain_tools()` function to `functions.py` to expose Hermes tools as LangChain tools
3. Created `langchain_integration.py` with utilities for integrating Hermes tools with LangChain agents:
   - `HermesToolAdapter`: Adapter to convert Hermes tools to LangChain tools
   - `create_hermes_agent`: Function to create a LangChain agent that can use Hermes tools
   - `execute_tool_call`: Function to execute a Hermes tool call
   - `convert_hermes_result_to_langchain`: Function to convert Hermes tool results to LangChain ToolMessages
   - `run_hermes_with_langchain`: Example function showing how to run a query using Hermes tools through LangChain
4. Created `test_langchain_integration.py` to demonstrate the integration

## Benefits

This integration provides several benefits:

1. Access to LangChain's ecosystem of tools, chains, and agents
2. Ability to use Hermes tools within LangChain workflows
3. Enhanced tool composition and chaining capabilities
4. Improved agent creation and management through LangChain's abstractions

## Usage

After installing the required dependencies, you can use the integration as follows:

```python
from langchain.llms import Ollama
from langchain_integration import run_hermes_with_langchain

# Initialize LLM
llm = Ollama(model="phi3")

# Run a query using Hermes tools through LangChain
result = run_hermes_with_langchain(llm, "What's the current stock price of Apple (AAPL)?")
print(result)
```

Fixes #23