---
layout: page
title: "Generic Thermostat"
description: "Turn Home Assistant into a thermostat"
date: 2015-03-23 19:59
sidebar: true
comments: false
sharing: true
footer: true
logo: heat-control.png
ha_category: Climate
ha_release: pre 0.7
---


The `generic_thermostat` climate platform is a thermostat implemented in Home Assistant. It uses a sensor and a switch connected to a heater under the hood. If the measured temperature is cooler then the target temperature, the heater will be turned on and turned off when required temperature is reached.

```yaml
# Example configuration.yaml entry
climate:
  - platform: generic_thermostat
    name: Study
    heater: switch.study_heater
    target_sensor: sensor.study_temperature
```

Configuration variables:

- **name** (*Required*): Name of thermostat
- **heater** (*Required*): `entity_id` for heater switch, must be a toggle device.
- **target_sensor** (*Required*): `entity_id` for a temperature sensor, target_sensor.state must be temperature.
- **min_temp** (*Optional*): Set minimum set point available (default: 7)
- **max_temp** (*Optional*): Set maximum set point available (default: 35)
- **target_temp** (*Optional*): Set initial target temperature. Failure to set this variable will result in target temperature being set to null on startup.
- **ac_mode** (*Optional*): Set the switch specified in the *heater* option to be treated as a cooling device instead of a heating device.
- **min_cycle_duration** (*Optional*): Set a minimum amount of time that the switch specified in the *heater* option must be in it's current state prior to being switched either off or on.
- **tolerance** (*Optional*): Set a minimum amount of temperature change that the sensor specified in the *target_sensor* option must change prior to being switched either off or on.

A full configuration example looks like the one below. `min_cycle_duration` must contains at least one of the following entries: `days:`, `hours:`, `minutes:`, `seconds:` or `milliseconds:`.

```yaml
# Full example configuration.yaml entry
climate:
  - platform: generic_thermostat
    name: Study
    heater: switch.study_heater
    target_sensor: sensor.study_temperature
    min_temp: 15
    max_temp: 21
    target_temp: 17
    tolerance: 0.3
    min_cycle_duration:
      seconds: 5
```
