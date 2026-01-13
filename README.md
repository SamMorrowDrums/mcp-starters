# 🚀 MCP Starters

Feature-complete **Model Context Protocol** (MCP) server implementations across multiple languages. Each repository demonstrates best practices for building MCP servers with tools, resources, prompts, and advanced features.

## 🗂️ Language-Specific Repositories

| Language | Repository | SDK | Features |
|----------|------------|-----|----------|
| 🐹 **Go** | [mcp-go-starter](https://github.com/SamMorrowDrums/mcp-go-starter) | [go-sdk](https://github.com/modelcontextprotocol/go-sdk) | Tools with icons, sampling, progress, dynamic loading |
| 🐍 **Python** | [mcp-python-starter](https://github.com/SamMorrowDrums/mcp-python-starter) | [python-sdk](https://github.com/modelcontextprotocol/python-sdk) | FastMCP, tools with icons, sampling, progress |
| 📘 **TypeScript** | [mcp-typescript-starter](https://github.com/SamMorrowDrums/mcp-typescript-starter) | [typescript-sdk](https://github.com/modelcontextprotocol/typescript-sdk) | Zod schemas, annotations, dynamic tools |
| 💜 **C#** | [mcp-csharp-starter](https://github.com/SamMorrowDrums/mcp-csharp-starter) | [csharp-sdk](https://github.com/modelcontextprotocol/csharp-sdk) | Attribute-based, DI, HTTP/stdio |
| 🦀 **Rust** | [mcp-rust-starter](https://github.com/SamMorrowDrums/mcp-rust-starter) | [rmcp](https://crates.io/crates/rmcp) | Macro-based, async, type-safe |

## ✨ Common Features

All starters demonstrate:

### 🔧 Tools
- **hello** - Basic greeting with annotations
- **get_weather** - Structured output (simulated)
- **ask_llm** - LLM sampling/completion
- **long_task** - Progress reporting
- **load_bonus_tool** - Dynamic tool registration
- **bonus_calculator** - Dynamically loaded tool

### 📚 Resources
- Static resources (server info, example files)
- Resource templates with URI parameters

### 💬 Prompts
- **greeting** - Personalized greeting generation
- **code_review** - Structured code review template

### 🏷️ Tool Annotations
Every tool includes proper annotations:
- `readOnlyHint` - Tool doesn't modify state
- `destructiveHint` - Tool can delete/modify data
- `idempotentHint` - Safe to retry
- `openWorldHint` - Accesses external systems

## 🚀 Quick Start

### Go
```bash
git clone https://github.com/SamMorrowDrums/mcp-go-starter
cd mcp-go-starter
make run-stdio
```

### Python
```bash
git clone https://github.com/SamMorrowDrums/mcp-python-starter
cd mcp-python-starter
uv run mcp-python-starter --stdio
```

### TypeScript
```bash
git clone https://github.com/SamMorrowDrums/mcp-typescript-starter
cd mcp-typescript-starter
npm install && npm run stdio
```

### C#
```bash
git clone https://github.com/SamMorrowDrums/mcp-csharp-starter
cd mcp-csharp-starter
dotnet run
```

### Rust
```bash
git clone https://github.com/SamMorrowDrums/mcp-rust-starter
cd mcp-rust-starter
cargo run
```

## 📋 Feature Matrix

| Feature | Go | Python | TypeScript | C# | Rust |
|---------|:--:|:------:|:----------:|:--:|:----:|
| Tool Annotations | ✅ | ✅ | ✅ | ✅ | ✅ |
| Tool Icons (base64) | ✅ | ✅ | ❌ | ❌ | ❌ |
| LLM Sampling | ✅ | ✅ | ✅ | ✅ | ❌ |
| Progress Reporting | ✅ | ✅ | ✅ | ✅ | ❌ |
| Dynamic Tool Loading | ✅ | ✅ | ✅ | ✅ | ❌ |
| Resources | ✅ | ✅ | ✅ | ✅ | ✅ |
| Resource Templates | ✅ | ✅ | ✅ | ❌ | ✅ |
| Prompts | ✅ | ✅ | ✅ | ✅ | ✅ |
| stdio Transport | ✅ | ✅ | ✅ | ✅ | ✅ |
| HTTP Transport | ✅ | ✅ | ✅ | ✅ | ❌ |
| Server Instructions | ✅ | ✅ | ✅ | ✅ | ✅ |
| DevContainer | ✅ | ✅ | ✅ | ✅ | ✅ |
| AGENTS.md | ✅ | ✅ | ✅ | ✅ | ✅ |

## 📖 Documentation

- [MCP Specification](https://modelcontextprotocol.io/)
- [MCP Tools Documentation](https://modelcontextprotocol.io/docs/concepts/tools)
- [MCP Resources Documentation](https://modelcontextprotocol.io/docs/concepts/resources)
- [MCP Prompts Documentation](https://modelcontextprotocol.io/docs/concepts/prompts)

## 🤝 Contributing

Contributions are welcome! Each repository has its own contributing guidelines. General improvements or new language implementations can be proposed via issues.

## 📄 License

All repositories are licensed under the MIT License.
