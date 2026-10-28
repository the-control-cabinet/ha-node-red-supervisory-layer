# 04 · First Flows and the Functions It Hosts

[← Back to README](../README.md)

## Proof flow (first)
1. Read one zone's temperature and setpoint (RAMSES-II entities).
2. With the kill switch on and the zone unoccupied, send a **temporary** setpoint +0.5 °C with a 15-minute expiry.
3. Confirm read-back within 2 minutes; log it.
4. Confirm the zone **reverts** at expiry.
5. Stop Node-RED mid-test: confirm the zone still reverts (field-level fail-safe).

## Functions hosted (roadmap)
| Function | Repo | Status |
|---|---|---|
| Multi-zone optimum start/stop (#4) | [optimum-start-stop-supervisory](https://github.com/the-control-cabinet/optimum-start-stop-supervisory) | Design stage |
| OpenTherm preheat signal | [opentherm-boiler-control-esphome](https://github.com/the-control-cabinet/opentherm-boiler-control-esphome) | Design stage |
| Alarm and trend strategy (#6) | (planned) | Planned |
| Rig supervision: duty/standby and interlocks (#7/#9) | (planned) | Planned |
