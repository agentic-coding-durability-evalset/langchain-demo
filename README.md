# LangChain Demo

一个基于 [LangChain](https://www.langchain.com/) 的 Python AI 应用示例项目。展示了如何使用 LangChain 构建 AI 代理和工具调用应用。

## 技术栈

- **Python**: 3.13+
- **LangChain**: 1.0.2+
- **LangChain Anthropic**: 1.0.0+ (Claude 支持)
- **LangChain DeepSeek**: 1.0.0+ (DeepSeek 支持)
- **LangChain OpenAI**: 1.0.1+ (OpenAI 支持)
- **Python-dotenv**: 1.1.1+ (环境变量管理)

## 项目结构

```
langchain-demo/
├── agent-demo.py         # AI 代理示例
├── deepseek-demo.py      # DeepSeek 模型示例
├── pyproject.toml        # 项目配置和依赖
├── .env                  # 环境变量（需自行创建）
└── README.md
```

## 功能特性

- AI 代理创建
- 工具调用支持
- 多模型支持（OpenAI, Anthropic, DeepSeek）
- 环境变量配置
- 简单的代理示例

## 快速开始

### 前置要求

- Python 3.13 或更高版本
- API 密钥（OpenAI、Anthropic 或 DeepSeek）

### 安装和运行

```bash
# 克隆项目
git clone <repository-url>
cd langchain-demo

# 创建虚拟环境（推荐）
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 安装依赖
pip install -e ".[dev]"

# 或使用 uv（更快）
uv pip install -e ".[dev]"

# 创建 .env 文件
cat > .env << EOF
OPENAI_API_KEY=your-openai-api-key
ANTHROPIC_API_KEY=your-anthropic-api-key
DEEPSEEK_API_KEY=your-deepseek-api-key
EOF

# 运行代理示例
python agent-demo.py

# 运行 DeepSeek 示例
python deepseek-demo.py
```

## 代码说明

### 代理示例 (`agent-demo.py`)

展示了如何创建和使用 LangChain 代理：

```python
from langchain.agents import create_agent

# 定义工具函数
def get_weather(city: str) -> str:
    """Get weather for a given city."""
    return f"It's always sunny in {city}!"

# 创建代理
agent = create_agent(
    model="openai:gpt-4.1",
    tools=[get_weather],
    system_prompt="You are a helpful assistant",
)

# 运行代理
result = agent.invoke({
    "messages": [{"role": "user", "content": "what is the weather in sf"}]
})
```

### 关键概念

- **代理 (Agent)**: 可以调用工具和做出决策的 AI 系统
- **工具 (Tools)**: 代理可以调用的函数
- **模型**: 支持多种 LLM 提供商
- **提示 (Prompts)**: 系统提示和用户消息

## 模型支持

### OpenAI

```python
model="openai:gpt-4.1"
# 或
model="openai:gpt-3.5-turbo"
```

### Anthropic (Claude)

```python
model="anthropic:claude-3-opus"
# 或
model="anthropic:claude-3-sonnet"
```

### DeepSeek

```python
model="deepseek:deepseek-chat"
```

## 工具开发

### 创建自定义工具

```python
def my_custom_tool(param: str) -> str:
    """Tool description for the agent."""
    # 实现工具逻辑
    return result
```

### 工具要求

- 函数必须有文档字符串（用作工具描述）
- 参数应该有类型提示
- 返回值应该是字符串或可序列化的对象

## 环境变量

项目使用 `python-dotenv` 管理环境变量：

```bash
# .env
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
DEEPSEEK_API_KEY=sk-...
```

## 测试

### 运行测试

```bash
# 运行所有测试
pytest

# 运行特定测试
pytest tests/
```

## 开发

### 添加新功能

1. 创建新的 Python 文件
2. 导入 LangChain 组件
3. 定义工具和代理
4. 实现业务逻辑

### 调试

使用 Python 调试器：

```bash
python -m pdb agent-demo.py
```

## 最佳实践

### 工具设计

- 提供清晰的工具描述
- 使用类型提示
- 处理错误情况
- 返回有意义的错误消息

### 提示工程

- 编写清晰的系统提示
- 提供上下文信息
- 使用示例（few-shot learning）

### 错误处理

```python
try:
    result = agent.invoke(messages)
except Exception as e:
    print(f"Error: {e}")
```

## 参考资源

- [LangChain 文档](https://python.langchain.com/)
- [LangChain 工具文档](https://python.langchain.com/docs/modules/tools/)
- [LangChain 代理文档](https://python.langchain.com/docs/modules/agents/)
- [LangChain GitHub](https://github.com/langchain-ai/langchain)
