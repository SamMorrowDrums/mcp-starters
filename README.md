# 🚀 MCP Starters

Feature-complete **Model Context Protocol** (MCP) server implementations across multiple languages. Each repository demonstrates best practices for building MCP servers with tools, resources, prompts, and advanced features.

## 🗂️ Language-Specific Repositories

| Language | Repository | SDK | Features |
|----------|------------|-----|----------|
| 🐹 **Go** | [mcp-go-starter](https://github.com/SamMorrowDrums/mcp-go-starter) | [go-sdk](https://github.com/modelcontextprotocol/go-sdk) | Tools with icons, sampling, progress, elicitation |
| 🐍 **Python** | [mcp-python-starter](https://github.com/SamMorrowDrums/mcp-python-starter) | [python-sdk](https://github.com/modelcontextprotocol/python-sdk) | FastMCP, tools with icons, sampling, elicitation |
| 📘 **TypeScript** | [mcp-typescript-starter](https://github.com/SamMorrowDrums/mcp-typescript-starter) | [typescript-sdk](https://github.com/modelcontextprotocol/typescript-sdk) | Zod schemas, sampling, progress, elicitation |
| 💜 **C#** | [mcp-csharp-starter](https://github.com/SamMorrowDrums/mcp-csharp-starter) | [csharp-sdk](https://github.com/modelcontextprotocol/csharp-sdk) | Attribute-based, icons, sampling, elicitation |
| 🦀 **Rust** | [mcp-rust-starter](https://github.com/SamMorrowDrums/mcp-rust-starter) | [rmcp](https://crates.io/crates/rmcp) | Macro-based, async, resource templates |
| 🐘 **PHP** | [mcp-php-starter](https://github.com/SamMorrowDrums/mcp-php-starter) | [php-sdk](https://github.com/modelcontextprotocol/php-sdk) | Attribute-based discovery, HTTP/stdio |
| 🟣 **Kotlin** | [mcp-kotlin-starter](https://github.com/SamMorrowDrums/mcp-kotlin-starter) | [kotlin-sdk](https://github.com/modelcontextprotocol/kotlin-sdk) | Coroutines, Ktor HTTP, type-safe DSL |

## ✨ Common Features

All starters demonstrate core MCP capabilities:

### 🔧 Tools
- **hello** - Basic greeting tool
- **get_weather** - Structured output (simulated)
- **calculate** - Arithmetic operations
- **echo** - Echo messages back

### 📚 Resources
- Static resources (server info, example files)
- Configuration data

### 💬 Prompts
- **greet** - Personalized greeting generation
- **code_review** - Structured code review template

## ⚡ Advanced Features (Mature SDKs)

The Go, Python, TypeScript, and C# starters include advanced MCP features:

### 🏷️ Tool Annotations
- `readOnlyHint` - Tool doesn't modify state
- `destructiveHint` - Tool can delete/modify data
- `idempotentHint` - Safe to retry
- `openWorldHint` - Accesses external systems

### 🤖 LLM Sampling
- **ask_llm** - Tool that invokes LLM sampling/completion

### 📊 Progress Reporting
- **long_task** - Demonstrates progress notifications during execution

### 🔄 Dynamic Tool Loading
- **load_bonus_tool** - Dynamically registers new tools at runtime
- **bonus_calculator** - Tool added via `tools/list_changed`

### 🗣️ Elicitation (User Input)
Request information from users during tool execution:
- **confirm_action** - Schema elicitation with form fields
- **get_feedback** - URL elicitation opening browser

### 📂 Resource Templates
- URI templates with parameters (e.g., `data://items/{id}`)

## 📋 MCP Protocol Feature Matrix

| Feature | Go | Python | TypeScript | C# | Rust | PHP | Kotlin |
|---------|:--:|:------:|:----------:|:--:|:----:|:---:|:------:|
| **Tools** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Resources** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Prompts** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Tool Annotations** | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ |
| **Tool Icons** | ✅ | ✅ | ❌ | ✅ | ✅ | ❌ | ❌ |
| **LLM Sampling** | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Progress Reporting** | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Dynamic Tool Loading** | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Elicitation (Form)** | ✅ | ✅ | ✅ | ✅ | ⚠️ | ❌ | ❌ |
| **Elicitation (URL)** | ✅ | ✅ | ✅ | ✅ | ⚠️ | ❌ | ❌ |
| **Resource Templates** | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| **stdio Transport** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **HTTP Transport** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

**Legend:** ✅ Implemented | ❌ Not implemented | ⚠️ Placeholder/stub

## 🛠️ Repository Feature Matrix

| Feature | Go | Python | TypeScript | C# | Rust | PHP | Kotlin |
|---------|:--:|:------:|:----------:|:--:|:----:|:---:|:------:|
| **DevContainer** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Live Reload** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **AGENTS.md** | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ |
| **VS Code Tasks** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **CI Workflow** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Conformance Test** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

## 🔄 Live Reload Development

| Language | Command | Tool |
|----------|---------|------|
| 🐹 Go | `air` | [air](https://github.com/air-verse/air) |
| 🐍 Python | `uv run mcp-python-starter` | uv auto-reload |
| 📘 TypeScript | `npm run dev` | tsx watch |
| 💜 C# | `dotnet watch run` | .NET Hot Reload |
| 🦀 Rust | `cargo watch -x 'run --bin mcp-rust-starter-stdio'` | [cargo-watch](https://crates.io/crates/cargo-watch) |
| 🐘 PHP | `composer run-script dev` | PHP built-in server |
| 🟣 Kotlin | `./gradlew runStdio --continuous` | Gradle continuous |

## 🚀 Quick Start

### Go
```bash
git clone https://github.com/SamMorrowDrums/mcp-go-starter
cd mcp-go-starter
air  # Live reload development
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
npm install && npm run dev
```

### C#
```bash
git clone https://github.com/SamMorrowDrums/mcp-csharp-starter
cd mcp-csharp-starter
dotnet watch run
```

### Rust
```bash
git clone https://github.com/SamMorrowDrums/mcp-rust-starter
cd mcp-rust-starter
cargo run --bin mcp-rust-starter-stdio
```

### PHP
```bash
git clone https://github.com/SamMorrowDrums/mcp-php-starter
cd mcp-php-starter
composer install
php bin/server-stdio.php
```

### Kotlin
```bash
git clone https://github.com/SamMorrowDrums/mcp-kotlin-starter
cd mcp-kotlin-starter
./gradlew fatJar
java -jar build/libs/mcp-kotlin-starter-1.0.0-all.jar
```

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
