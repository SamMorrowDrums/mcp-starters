# Canonical MCP Starter Interface

All MCP starter repos should expose **exactly** this interface for consistency across languages.

## Schema Conventions

### Tools
- **`name`**: Tool identifier (snake_case, e.g., `get_weather`)
- **`title`**: Human-readable name (e.g., "Get Weather")
- **`description`**: Model-readable explanation
- **`annotations`**: Metadata hints for clients (e.g., `readOnlyHint`, `destructiveHint`)
- **`outputSchema`**: (Optional) JSON Schema describing the tool's return value

### Input Schema Properties
- Use `description` field only (NOT `title`)
- Use `camelCase` for parameter names (e.g., `taskName`, `maxTokens`)
- Include `default` values where applicable

---

## Tools (7 total)

### 1. hello
- **Name:** `hello`
- **Title:** `Hello`
- **Description:** `Say hello to a person`
- **Annotations:** `{ readOnlyHint: true }`
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
- **Annotations:** `{ readOnlyHint: true }`
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
- **Output Schema:**
```json
{
  "type": "object",
  "properties": {
    "city": {
      "type": "string",
      "description": "City name"
    },
    "temperature": {
      "type": "number",
      "description": "Temperature in Celsius"
    },
    "conditions": {
      "type": "string",
      "description": "Weather conditions description"
    }
  },
  "required": ["city", "temperature", "conditions"]
}
```

### 3. long_task
- **Name:** `long_task`
- **Title:** `Long Task`
- **Description:** `Simulate a long-running task with progress updates`
- **Annotations:** `{ readOnlyHint: true }`
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
- **Annotations:** `{ readOnlyHint: false }`
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
- **Annotations:** `{ readOnlyHint: true }`
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
- **Annotations:** `{ readOnlyHint: true }`
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
- **Annotations:** `{ readOnlyHint: true }`
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
