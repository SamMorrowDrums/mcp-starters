# Canonical MCP Starter Interface

All MCP starter repos should expose **exactly** this interface for consistency across languages.

## Schema Conventions
- **Use BOTH `title` AND `description`** on all properties
  - `title`: Human-readable label (e.g., "Task Name")
  - `description`: Model-readable explanation (e.g., "Name for this task")
- Use `camelCase` for parameter names (e.g., `taskName`, `maxTokens`)
- Include `default` values where applicable

---

## Tools (7 total)

### 1. hello
- **Description:** `Say hello to a person`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "name": {
      "type": "string",
      "title": "Name",
      "description": "Name of the person to greet"
    }
  },
  "required": ["name"]
}
```

### 2. get_weather
- **Description:** `Get the current weather for a city`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "city": {
      "type": "string",
      "title": "City",
      "description": "City name to get weather for"
    }
  },
  "required": ["city"]
}
```

### 3. long_task
- **Description:** `Simulate a long-running task with progress updates`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "taskName": {
      "type": "string",
      "title": "Task Name",
      "description": "Name for this task"
    },
    "steps": {
      "type": "integer",
      "title": "Steps",
      "description": "Number of steps to simulate",
      "default": 5
    }
  },
  "required": ["taskName"]
}
```

### 4. load_bonus_tool
- **Description:** `Dynamically register a new bonus tool`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {},
  "required": []
}
```

### 5. ask_llm
- **Description:** `Ask the connected LLM a question using sampling`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "prompt": {
      "type": "string",
      "title": "Prompt",
      "description": "The question or prompt to send to the LLM"
    },
    "maxTokens": {
      "type": "integer",
      "title": "Max Tokens",
      "description": "Maximum tokens in response",
      "default": 100
    }
  },
  "required": ["prompt"]
}
```

### 6. confirm_action
- **Description:** `Request user confirmation before proceeding`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "action": {
      "type": "string",
      "title": "Action",
      "description": "Description of the action to confirm"
    },
    "destructive": {
      "type": "boolean",
      "title": "Destructive",
      "description": "Whether the action is destructive",
      "default": false
    }
  },
  "required": ["action"]
}
```

### 7. get_feedback
- **Description:** `Request feedback from the user`
- **Input Schema:**
```json
{
  "type": "object",
  "properties": {
    "question": {
      "type": "string",
      "title": "Question",
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
    "title": "Code",
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
    "title": "Name",
    "description": "Name of the person to greet",
    "required": true
  },
  {
    "name": "style",
    "title": "Style",
    "description": "Greeting style (formal/casual)",
    "required": false
  }
]
```
