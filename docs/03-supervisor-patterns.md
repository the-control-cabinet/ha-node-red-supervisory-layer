# 03 · Supervisor Patterns

[← Back to README](../README.md)

| Pattern | Implementation | Why |
|---|---|---|
| **Heartbeat** | Node-RED updates `input_datetime.sup_heartbeat` every minute; an HA automation alerts if it's older than 5 min | Detects a stalled supervisor from outside it |
| **Stale-data guard** | Every input checked for age before use (e.g. > 10 min = stale) | Never act on old data |
| **Fail-safe by design** | Commands are temporary; field controllers keep safe baselines | A dead supervisor reverts to safe behaviour automatically |
| **Shadow mode** | A per-function switch: compute and log, don't act | Validate before giving a function authority |
| **Kill switch** | `input_boolean.sup_enabled` gates all plant-tier writes | One switch to stand the supervisor down |
| **Alarm hooks** | Failed read-backs, stale inputs and missed heartbeats go to the alarm and trend strategy (#6) | Supervisor faults are visible |
