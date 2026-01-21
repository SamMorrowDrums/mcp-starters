# Canonical MCP Starter Interface

All MCP starter repos should expose **exactly** this interface for consistency across languages.

## Schema Conventions

### Tools
- **`name`**: Tool identifier (snake_case, e.g., `get_weather`)
- **`title`**: Human-readable name (e.g., "Get Weather")
- **`description`**: Model-readable explanation
- **`annotations`**: Metadata hints for clients (e.g., `readOnlyHint`, `destructiveHint`)
- **`outputSchema`**: (Optional) JSON Schema describing the tool's return value - SDK dependent

### Input Schema Properties
- Use `description` field (NOT `title`) for property descriptions
- Use `camelCase` for parameter names (e.g., `taskName`, `maxTokens`)
- Include `default` values where applicable
- Note: `title` on properties is SDK-dependent and optional

### Icons
Tools should include icons as PNG files stored in the repository (e.g., `icons/hello.png`). At application startup, serialize these to data URIs:

```
data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Icons are **optional** - if your SDK doesn't easily support them, omit.

---

## Tools (7 total)

### 1. hello
- **Name:** `hello`
- **Title:** `Say Hello`
- **Description:** `Say hello to a person`
- **Annotations:** `{ readOnlyHint: true, destructiveHint: false, idempotentHint: true, openWorldHint: false }`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "description": "Name of the person to greet"
    }
  },
  "required": ["name"]
}
```

### 2. get_weather
- **Name:** `get_weather`
- **Title:** `Get Weather`
- **Description:** `Get the current weather for a city`
- **Annotations:** `{ readOnlyHint: true, destructiveHint: false, idempotentHint: false, openWorldHint: false }`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "city": {
      "type": "string",
      "description": "City name to get weather for"
    }
  },
  "required": ["city"]
}
```

### 3. long_task
- **Name:** `long_task`
- **Title:** `Long Running Task`
- **Description:** `Simulate a long-running task with progress updates`
- **Annotations:** `{ readOnlyHint: true, destructiveHint: false, idempotentHint: true, openWorldHint: false }`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "taskName": {
      "type": "string",
      "description": "Name for this task"
    },
    "steps": {
      "type": "integer",
      "description": "Number of steps to simulate",
      "default": 5
    }
  },
  "required": ["taskName"]
}
```

### 4. load_bonus_tool
- **Name:** `load_bonus_tool`
- **Title:** `Load Bonus Tool`
- **Description:** `Dynamically register a new bonus tool`
- **Annotations:** `{ readOnlyHint: false, destructiveHint: false, idempotentHint: true, openWorldHint: false }`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {},
  "required": []
}
```

### 5. ask_llm
- **Name:** `ask_llm`
- **Title:** `Ask LLM`
- **Description:** `Ask the connected LLM a question using sampling`
- **Annotations:** `{ readOnlyHint: true, destructiveHint: false, idempotentHint: false, openWorldHint: false }`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "prompt": {
      "type": "string",
      "description": "The question or prompt to send to the LLM"
    },
    "maxTokens": {
      "type": "integer",
      "description": "Maximum tokens in response",
      "default": 100
    }
  },
  "required": ["prompt"]
}
```

### 6. confirm_action
- **Name:** `confirm_action`
- **Title:** `Confirm Action`
- **Description:** `Request user confirmation before proceeding`
- **Annotations:** `{ readOnlyHint: true, destructiveHint: false, idempotentHint: false, openWorldHint: false }`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "action": {
      "type": "string",
      "description": "Description of the action to confirm"
    },
    "destructive": {
      "type": "boolean",
      "description": "Whether the action is destructive",
      "default": false
    }
  },
  "required": ["action"]
}
```

### 7. get_feedback
- **Name:** `get_feedback`
- **Title:** `Get Feedback`
- **Description:** `Request feedback from the user`
- **Annotations:** `{ readOnlyHint: true, destructiveHint: false, idempotentHint: false, openWorldHint: true }`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "question": {
      "type": "string",
      "description": "The question to ask the user"
    }
  },
  "required": ["question"]
}
```

---

## Resources (2 total)

### 1. About
- **Name:** `About`
- **URI:** `about://server`
- **Description:** `Information about this MCP server`
- **MIME Type:** `text/plain`

### 2. Example Document  
- **Name:** `Example Document`
- **URI:** `doc://example`
- **Description:** `An example document resource`
- **MIME Type:** `text/plain`

---

## Resource Templates (2 total)

### 1. Personalized Greeting
- **Name:** `Personalized Greeting`
- **URI Template:** `greeting://{name}`
- **Description:** `A personalized greeting for a specific person`
- **MIME Type:** `text/plain`

### 2. Item Data
- **Name:** `Item Data`
- **URI Template:** `item://{id}`
- **Description:** `Data for a specific item by ID`
- **MIME Type:** `application/json`

---

## Prompts (2 total)

### 1. code_review
- **Name:** `code_review`
- **Title:** `Code Review`
- **Description:** `Review code for potential improvements`
- **Arguments:**
```json
[
  {
    "name": "code",
    "description": "The code to review",
    "required": true
  }
]
```

### 2. greet
- **Name:** `greet`
- **Title:** `Greeting Prompt`
- **Description:** `Generate a greeting message`
- **Arguments:**
```json
[
  {
    "name": "name",
    "description": "Name of the person to greet",
    "required": true
  },
  {
    "name": "style",
    "description": "Greeting style (formal/casual)",
    "required": false
  }
]
```

---

## Notes on SDK Differences

Some differences are acceptable due to SDK limitations:

1. **`inputSchema.title`** on the schema itself (e.g., `"helloArguments"`) - SDK generated, can vary
2. **`inputSchema.$schema`** - SDK generated, can vary
3. **`outputSchema`** - Optional, SDK-dependent
4. **`execution`** field - SDK-specific
5. **Icon format** - Some SDKs may not support base64 PNG icons
6. **`capabilities`** in initialize - SDK-dependent features
7. **`serverInfo.version`** - Can vary per implementation
