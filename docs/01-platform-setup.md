# 01 · Platform Setup

[← Back to README](../README.md)

| Step | Detail |
|---|---|
| 1. Node-RED add-on | Install from the HA add-on store; enable **start on boot** and the **watchdog** |
| 2. HA websocket nodes | `node-red-contrib-home-assistant-websocket` (bundled with the add-on). Server config: the local HA URL |
| 3. Access | A **dedicated HA user** for Node-RED, non-admin where possible, with a long-lived token stored in Node-RED's credentials (never in exported flows) |
| 4. Versions | Record the add-on and node versions; update deliberately, one at a time (same rule as the ESPHome fleet) |
| 5. Backups | Included in HA backups; plus flows exported to this repo (`flows/`) after each change, with credentials stripped |
| 6. Projects (optional) | Node-RED Projects for Git-based flow versioning |

## Conventions
- **One tab per function** (e.g. "OSS - Optimum start/stop"), plus a "SUP - Supervisor health" tab.
- **Entity naming:** supervisor helpers in HA prefixed `sup_` (e.g. `input_boolean.sup_oss_shadow_mode`).
- **Comments in every flow:** purpose, inputs, outputs, failure behaviour.
