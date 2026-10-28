# 02 · Command Authority

[← Back to README](../README.md)

Writes to plant are where a supervisor can do harm, so they follow the risk tiers of the [security baseline](https://github.com/the-control-cabinet/smart-home-security-baseline).

| Tier | Example | Rule in Node-RED |
|---|---|---|
| Read | Zone temperatures, demand, boiler state | Unrestricted |
| Comfort | Lights, notifications | Normal |
| **Plant** | Evohome temporary setpoints (RAMSES-II); OpenTherm preheat flag | **Temporary only** (with an expiry), **rate-limited**, **logged**, **read-back confirmed** |
| Safety / security | Alarm sounder, locks | **Not** commanded from Node-RED |

## RAMSES-II commands
- Sent through the HA **ramses_cc** services (e.g. a temporary zone-setpoint override with an end time) ⟨confirm exact service names and fields in the installed version⟩.
- Only reads and temporary setpoints are sent, the same set already covered by the gateway's **transmit audit**.
- **Rate limit:** no more than one command per zone per 10 minutes, and a global cap per hour, to protect the radio channel.
- **Read-back:** after each command, confirm the zone setpoint changed within 2 minutes; retry once, then alarm.

## Audit log
Every plant-tier command is written to a log (timestamp, function, zone, value, expiry, read-back result), kept as an HA logbook entry and a file, so any unexpected behaviour can be traced to its source.
