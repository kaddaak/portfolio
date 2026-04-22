# DataForgeAI

DataForgeAI is an analytics prototype for uploaded business data, chat-driven exploration, and generated charts.

Its core design choice is that the backend, not the model, owns project scope. Uploads, chat threads, generated charts, and pinned dashboard cards all belong to a backend-defined project, while the AI service only processes jobs the backend prepares and scopes.

## Runtime Topology

```mermaid
%%{init: {"flowchart": {"nodeSpacing": 130, "rankSpacing": 30}} }%%
flowchart LR
  USER["User"]

  subgraph FRONTEND_BOX["Frontend Service"]
    direction TB
    FRONTEND["Next.js App"]
  end

  subgraph BROWSER_BOX["Browser Runtime"]
    direction TB
    FE["Browser UI"]
    WORKER["MQTT SharedWorker"]
  end

  subgraph EMQX_BOX["MQTT Broker Service"]
    direction TB
    MQTT[("EMQX Broker")]
  end

  subgraph BACKEND_BOX["Backend Service"]
    direction TB
    API["Spring Backend"]
  end

  subgraph DB_BOX["PostgreSQL Service"]
    direction TB
    DB[("PostgreSQL")]
  end

  subgraph OBJECT_BOX["Object Storage Service"]
    direction TB
    OBJECT[("Object Storage")]
  end

  subgraph AI_BOX["AI Service"]
    direction TB
    AI["Python AI Service"]
  end

  USER --> FE
  FRONTEND -->|"serves app"| FE
  FE <-->|"HTTP"| API
  WORKER <-->|"MQTT over WebSocket"| MQTT
  FE <-->|"UI events"| WORKER
  API <-->|"prompt jobs, project events, AI replies"| MQTT
  MQTT -->|"prompts with project context"| AI
  AI -->|"AI replies, graph payloads"| MQTT
  API <-->|"projects, chats, dashboard state"| DB
  API <-->|"uploads, generated artifacts"| OBJECT
```

## Key Ideas

- Next.js frontend for project interaction and chart workflows
- Spring backend as the source of truth for projects, chats, and dashboard state
- MQTT-based job and event flow between backend and AI service
- Python AI service restricted to backend-scoped jobs rather than free-form model access

## Core Invariants

- A project is the durable state boundary for uploads, chats, graphs, and pinned outputs.
- The backend decides which project data an AI job can see and remains the persistence authority for results.
- The AI service executes prompt interpretation and chart generation against backend-scoped context.
- The browser shares one MQTT runtime across tabs through a SharedWorker.
