# 🚀 MCP Starters

Feature-complete **Model Context Protocol** (MCP) server implementations across multiple languages. Each repository demonstrates best practices for building MCP servers with tools, resources, prompts, and advanced features.

## 🗂️ Language-Specific Repositories

| Language | Repository | SDK | Features |
|----------|------------|-----|----------|
| 🐹 **Go** | [mcp-go-starter](https://github.com/SamMorrowDrums/mcp-go-starter) | [go-sdk](https://github.com/modelcontextprotocol/go-sdk) | Tools with icons, sampling, progress, elicitation |
| 🐍 **Python** | [mcp-python-starter](https://github.com/SamMorrowDrums/mcp-python-starter) | [python-sdk](https://github.com/modelcontextprotocol/python-sdk) | FastMCP, tools with icons, sampling, elicitation |
| 📘 **TypeScript** | [mcp-typescript-starter](https://github.com/SamMorrowDrums/mcp-typescript-starter) | [typescript-sdk](https://github.com/modelcontextprotocol/typescript-sdk) | Zod schemas, annotations, dynamic tools |
| 💜 **C#** | [mcp-csharp-starter](https://github.com/SamMorrowDrums/mcp-csharp-starter) | [csharp-sdk](https://github.com/modelcontextprotocol/csharp-sdk) | Attribute-based, DI, HTTP/stdio |
| 🦀 **Rust** | [mcp-rust-starter](https://github.com/SamMorrowDrums/mcp-rust-starter) | [rmcp](https://crates.io/crates/rmcp) | Macro-based, async, type-safe |
| 🐘 **PHP** | [mcp-php-starter](https://github.com/SamMorrowDrums/mcp-php-starter) | [php-sdk](https://github.com/modelcontextprotocol/php-sdk) | Attribute-based discovery, async support |
| 🟣 **Kotlin** | [mcp-kotlin-starter](https://github.com/SamMorrowDrums/mcp-kotlin-starter) | [kotlin-sdk](https://github.com/modelcontextprotocol/kotlin-sdk) | Coroutines, Ktor HTTP, type-safe DSL |

## ✨ Common Features

All starters demonstrate:

### 🔧 Tools
- **hello** - Basic greeting with annotations
- **get_weather** - Structured output (simulated)
- **ask_llm** - LLM sampling/completion
- **long_task** - Progress reporting
- **load_bonus_tool** - Dynamic tool registration
- **bonus_calculator** - Dynamically loaded tool

### 🗣️ Elicitation (User Input)
Request information from users during tool execution:
- **confirm_action** - Schema elicitation with form fields
- **get_feedback** - URL elicitation opening browser to feedback form

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

## 🔄 Live Reload Development

Each starter supports live reload for rapid development:

| Language | Command | Tool | DevContainer |
|----------|---------|------|--------------|
| 🐹 Go | `air` | [air](https://github.com/air-verse/air) | Pre-installed |
| 🐍 Python | `uv run mcp-python-starter` | Python auto-reload | Pre-installed |
| 📘 TypeScript | `npm run dev` | tsx watch | Pre-installed |
| 💜 C# | `dotnet watch run` | .NET Hot Reload | Built-in |
| 🦀 Rust | `cargo watch -x 'run --bin mcp-rust-starter-stdio'` | [cargo-watch](https://crates.io/crates/cargo-watch) | Pre-installed |
| 🐘 PHP | `composer run-script dev` | PHP built-in server | Pre-installed |
| 🟣 Kotlin | `./gradlew runStdio --continuous` | Gradle continuous | Pre-installed |

All DevContainers come with live reload tools pre-installed for immediate development.

## 🚀 Quick Start

### Go
```bash
git clone https://github.com/SamMorrowDrums/mcp-go-starter
cd mcp-go-starter
air  # Live reload development
# Or: make run-stdio
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
npm install && npm run dev  # Live reload development
```

### C#
```bash
git clone https://github.com/SamMorrowDrums/mcp-csharp-starter
cd mcp-csharp-starter
dotnet watch run  # Live reload development
```

### Rust
```bash
git clone https://github.com/SamMorrowDrums/mcp-rust-starter
cd mcp-rust-starter
cargo watch -x 'run --bin mcp-rust-starter-stdio'  # Live reload development
# Or: cargo run --bin mcp-rust-starter-stdio
```

### PHP
```bash
git clone https://github.com/SamMorrowDrums/mcp-php-starter
cd mcp-php-starter
composer install
php bin/server.php  # stdio mode
```

### Kotlin
```bash
git clone https://github.com/SamMorrowDrums/mcp-kotlin-starter
cd mcp-kotlin-starter
./gradlew fatJar
java -jar build/libs/mcp-kotlin-starter-1.0.0-all.jar  # stdio mode
```

## 📋 Feature Matrix

| Feature | Go | Python | TypeScript | C# | Rust | PHP | Kotlin |
|---------|:--:|:------:|:----------:|:--:|:----:|:---:|:------:|
| Tool Annotations | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Tool Icons (base64) | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| LLM Sampling | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| Progress Reporting | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| Dynamic Tool Loading | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| Elicitation (Form) | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Elicitation (URL) | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| Resources | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Resource Templates | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| Prompts | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| stdio Transport | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| HTTP Transport | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ✅ |
| Live Reload Dev | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Server Instructions | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| DevContainer | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| AGENTS.md | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

## 📖 Documentation

- [MCP Specification](https://modelcontextprotocol.io/)
- [MCP Tools Documentation](https://modelcontextprotocol.io/docs/concepts/tools)
- [MCP Elicitation Documentation](https://modelcontextprotocol.io/docs/concepts/elicitation)
- [MCP Resources Documentation](https://modelcontextprotocol.io/docs/concepts/resources)
- [MCP Prompts Documentation](https://modelcontextprotocol.io/docs/concepts/prompts)

## 🤝 Contributing

Contributions are welcome! Each repository has its own contributing guidelines. General improvements or new language implementations can be proposed via issues.

### Workshop Feedback

Used these starters at a workshop or event? [Submit feedback](https://github.com/SamMorrowDrums/mcp-starters/issues/new?template=workshop-feedback.yml) to help improve them!

## 📄 License

All repositories are licensed under the MIT License.
