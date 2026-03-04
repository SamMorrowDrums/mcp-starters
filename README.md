# 🚀 MCP Starters

Feature-complete **Model Context Protocol** (MCP) server implementations across 7 languages — designed as **workshop starter projects** for learning MCP.

Pick your language, clone the repo, and start building. Each server implements the same interface so you can focus on learning MCP concepts, not reverse-engineering different implementations.

## 🗂️ Choose Your Language

| Language | Repository | SDK |
|----------|------------|-----|
| 🐍 **Python** | [mcp-python-starter](https://github.com/SamMorrowDrums/mcp-python-starter) | [python-sdk](https://github.com/modelcontextprotocol/python-sdk) (FastMCP) |
| 📘 **TypeScript** | [mcp-typescript-starter](https://github.com/SamMorrowDrums/mcp-typescript-starter) | [typescript-sdk](https://github.com/modelcontextprotocol/typescript-sdk) |
| 🐹 **Go** | [mcp-go-starter](https://github.com/SamMorrowDrums/mcp-go-starter) | [go-sdk](https://github.com/modelcontextprotocol/go-sdk) |
| 🦀 **Rust** | [mcp-rust-starter](https://github.com/SamMorrowDrums/mcp-rust-starter) | [rmcp](https://crates.io/crates/rmcp) |
| 💜 **C#** | [mcp-csharp-starter](https://github.com/SamMorrowDrums/mcp-csharp-starter) | [csharp-sdk](https://github.com/modelcontextprotocol/csharp-sdk) |
| 🟣 **Kotlin** | [mcp-kotlin-starter](https://github.com/SamMorrowDrums/mcp-kotlin-starter) | [kotlin-sdk](https://github.com/modelcontextprotocol/kotlin-sdk) |
| 🐘 **PHP** | [mcp-php-starter](https://github.com/SamMorrowDrums/mcp-php-starter) | [php-sdk](https://github.com/modelcontextprotocol/php-sdk) |

## 🎯 What You'll Learn

Each starter demonstrates the same set of MCP concepts through 7 tools, 2 resources, 2 resource templates, and 2 prompts:

| Concept | What It Demonstrates | Tool/Feature |
|---------|---------------------|--------------|
| **Basic tools** | Simple request/response | `hello`, `get_weather` |
| **Progress reporting** | Streaming progress notifications during execution | `long_task` |
| **LLM sampling** | Server asking the client to generate a completion | `ask_llm` |
| **Dynamic tool loading** | Registering new tools at runtime + `tools/list_changed` notification | `load_bonus_tool` → `bonus_calculator` |
| **Elicitation** | Requesting user input during tool execution (form-based and URL-based) | `confirm_action`, `get_feedback` |
| **Resources** | Read-only data exposed to clients | `about://server`, `doc://example` |
| **Resource templates** | URI templates with parameters | `greeting://{name}`, `item://{id}` |
| **Prompts** | Reusable prompt templates with arguments | `greet`, `code_review` |
| **Tool annotations** | Metadata hints (readOnlyHint, idempotentHint, etc.) for safe tool usage | All tools |

### Recommended Workflow

Try the tools in this order to see each MCP concept build on the last:

1. `hello` → verify connectivity
2. `get_weather` → see structured output with typed schemas
3. `long_task` → watch progress notifications stream in real-time
4. `load_bonus_tool` → then re-list tools to see `bonus_calculator` appear dynamically
5. `ask_llm` → see the server request an LLM completion from the client
6. `confirm_action` / `get_feedback` → see elicitation (user input during tool execution)

## 🚀 Quick Start

Every repo includes DevContainers, VS Code tasks, and live reload. Clone → open in VS Code → start coding.

| Language | Run (stdio) | Live Reload |
|----------|------------|-------------|
| 🐍 Python | `uv run mcp-python-starter --stdio` | Built-in (uv auto-reload) |
| 📘 TypeScript | `npm install && npm run build && node dist/stdio.js` | `npm run dev` (tsx watch) |
| 🐹 Go | `go run ./cmd/stdio` | `air` |
| 🦀 Rust | `cargo run --bin mcp-rust-starter-stdio` | `cargo watch` |
| 💜 C# | `dotnet run -- --stdio` | `dotnet watch run` |
| 🟣 Kotlin | `./gradlew shadowJar && java -jar build/libs/mcp-kotlin-starter-1.0.0-all.jar` | `./gradlew runStdio --continuous` |
| 🐘 PHP | `composer install && php bin/server-stdio.php` | — |

## ✂️ Making It Your Own

These starters are designed to be trimmed down. To build your own server:

1. **Keep what you need** — the tools/resources/prompts that match your use case
2. **Comment out the rest** — each feature is self-contained and easy to remove
3. **Add your own tools** — follow the existing patterns in the code

The code is well-commented to explain MCP concepts — read the comments to understand what each piece does and why.

## 🔧 Server Instructions

Each server includes concise [server instructions](https://modelcontextprotocol.io/docs/concepts/servers#server-instructions) — short text sent during initialization that helps AI clients understand how to use the server. Instructions should focus on **workflows and multi-tool patterns**, not enumerate features (clients discover those via `tools/list`, `resources/list`, etc.).

## ⚠️ SDK-Level Differences

All servers implement the same interface, but some differences exist due to SDK behavior. These are documented so you know what's a language choice vs. an SDK constraint:

| Difference | Cause | Impact |
|-----------|-------|--------|
| `inputSchema.title` naming | SDK auto-generates (e.g., Python: `"helloArguments"`, Go: `"HelloInput"`) | Cosmetic only |
| `annotations.title` placement | Python SDK puts in `annotations`, others at top-level `title` | Cosmetic only |
| `outputSchema` format | SDK-specific schema generation | Cosmetic only |
| `prompts.listChanged` / `resources.listChanged` | Some SDKs hardcode `true` when handlers are registered (e.g., TypeScript) | Functionally equivalent |
| Resource templates (Kotlin) | Kotlin SDK lacks public `addResourceTemplate` API — templates registered as static resources | See [SDK_LIMITATIONS.md](https://github.com/SamMorrowDrums/mcp-kotlin-starter/blob/main/SDK_LIMITATIONS.md) |

For full details, see [CANONICAL_INTERFACE.md](./CANONICAL_INTERFACE.md) and each repo's `SDK_LIMITATIONS.md` (if present).

## 📋 Cross-Server Conformance

This repo includes a [GitHub Actions workflow](.github/workflows/cross-server-diff.yml) that runs [mcp-server-diff](https://github.com/SamMorrowDrums/mcp-server-diff) weekly to detect interface drift between servers. Results are posted as GitHub issues when differences are found.

## 📖 Documentation

- [MCP Specification](https://modelcontextprotocol.io/)
- [MCP SDK Documentation](https://modelcontextprotocol.io/docs/sdk)
- [Tools](https://modelcontextprotocol.io/docs/concepts/tools) · [Resources](https://modelcontextprotocol.io/docs/concepts/resources) · [Prompts](https://modelcontextprotocol.io/docs/concepts/prompts) · [Elicitation](https://modelcontextprotocol.io/docs/concepts/elicitation)

## 🤝 Contributing

Contributions welcome! Each repository has its own contributing guidelines. General improvements or new language implementations can be proposed via [issues](https://github.com/SamMorrowDrums/mcp-starters/issues).

### Workshop Feedback

Used these starters at a workshop? [Submit feedback](https://github.com/SamMorrowDrums/mcp-starters/issues/new?template=workshop-feedback.yml) to help improve them!

## 📄 License

All repositories are licensed under the MIT License.
