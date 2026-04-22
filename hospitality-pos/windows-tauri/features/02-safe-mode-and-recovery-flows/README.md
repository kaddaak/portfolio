# Safe Mode and Recovery Flows

Safe mode keeps the register operational during internet, MQTT, or Raspberry outages: local work stays available, anything that depends on Raspberry authority, MQTT coordination, or external confirmation pauses, and queued work resumes automatically when connectivity returns.

<p align="center">
  <img src="./assets/safe-mode.gif" alt="Safe mode demo">
</p>

## Runtime Flow

```mermaid
flowchart TB
  subgraph T["Safe-mode triggers"]
    I["No internet connection"]
    M["MQTT connection lost"]
    R["Raspberry unavailable"]
  end

  I --> S["Enter safe mode"]
  M --> S
  R --> S

  S --> D["Degraded runtime"]
  S --> U["Visible operator cues<br/>toast + forced theme + lock states"]
  D --> L["Local operator workflows stay usable"]
  D --> H["Recovery queues halted"]

  subgraph RT["Recovery trigger"]
    X["Raspberry / connectivity restored"]
  end

  X --> C["Safe mode cleared"]
  C --> Y["Restore runtime state"]
  Y --> Z["Resume queued work + restore full features"]
```

## How It Works

- Safe mode starts when internet, MQTT, or Raspberry connectivity is lost.
- The UI makes degraded state obvious with warning toasts, a forced safe-mode theme, lock indicators, and unavailable backend-dependent views.
- Local durable work stays available while Raspberry-backed actions and recovery queues pause.
- When connectivity returns, the app restores runtime state and resumes queued work.

## Why It Matters

This makes degraded operation explicit and predictable: operators can keep working, correctness-sensitive work stays on the right side of the backend boundary, and recovery happens automatically when the site comes back.
