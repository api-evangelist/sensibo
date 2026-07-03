# Sensibo (sensibo)

Sensibo builds smart air conditioning controllers and indoor air quality monitors (Sensibo Sky, Air, Air Pro, and Elements) that add app, voice, and API control to existing mini-split, window, and portable AC and heat-pump units. The Sensibo REST API (base `https://home.sensibo.com/api/v2`) gives developers full control over enrolled devices ("pods") - reading temperature, humidity, and air quality measurements, getting and setting the AC state (power, mode, target temperature, fan, swing), configuring the Climate React smart automation, and managing schedules and timers. Authentication is a per-account API key passed as an `apiKey` query parameter, generated at [home.sensibo.com/me/api](https://home.sensibo.com/me/api). OAuth2 is available for commercial integrations.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/sensibo/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/sensibo/refs/heads/main/apis.yml)

## Tags

- Smart Home
- IoT
- Air Conditioning
- HVAC
- Air Quality
- Climate Control
- Connected Devices

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## APIs

### Sensibo Users API

The account entry point. List every device (pod) enrolled on the authenticated Sensibo account via `GET /users/me/pods`, optionally selecting which fields to return with the `fields` query parameter. This is how an integration discovers the pod IDs it will control with the other APIs.

- **Human URL:** [https://support.sensibo.com/api/](https://support.sensibo.com/api/)
- **Base URL:** `https://home.sensibo.com/api/v2`

#### Tags

- Users
- Account
- Devices

#### Properties

- [Documentation](https://support.sensibo.com/api/)
- [API Reference](https://support.sensibo.com/getting-started/api-documentation/)
- [OpenAPI](openapi/sensibo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensibo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensibo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sensibo Devices API

Retrieve full detail for a single device (pod) via `GET /pods/{device_id}` - product model, room name, connection status, firmware version, capabilities, and the last known AC state and measurements. Use the `fields` parameter to trim the response to only the properties you need.

- **Human URL:** [https://support.sensibo.com/api/](https://support.sensibo.com/api/)
- **Base URL:** `https://home.sensibo.com/api/v2`

#### Tags

- Devices
- Pods
- Status

#### Properties

- [Documentation](https://support.sensibo.com/api/)
- [OpenAPI](openapi/sensibo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensibo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensibo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sensibo AC States API

Read and command the air conditioner state. `GET /pods/{device_id}/acStates` returns the current and previous states; `POST` sets a complete new state (on/off, mode, target temperature, fan level, swing); and `PATCH /pods/{device_id}/acStates/{property}` changes a single property such as turning the unit on or bumping the target temperature.

- **Human URL:** [https://support.sensibo.com/api/](https://support.sensibo.com/api/)
- **Base URL:** `https://home.sensibo.com/api/v2`

#### Tags

- AC State
- Control
- Power

#### Properties

- [Documentation](https://support.sensibo.com/api/)
- [OpenAPI](openapi/sensibo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensibo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensibo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sensibo Measurements API

Read the latest sensor readings for a pod via `GET /pods/{device_id}/measurements` - temperature, relative humidity, feels-like, and on air-quality-capable hardware (Air Pro, Elements) indoor air quality signals such as TVOC, CO2, and particulate matter, plus RSSI and battery.

- **Human URL:** [https://support.sensibo.com/api/](https://support.sensibo.com/api/)
- **Base URL:** `https://home.sensibo.com/api/v2`

#### Tags

- Measurements
- Temperature
- Humidity
- Air Quality

#### Properties

- [Documentation](https://support.sensibo.com/api/)
- [OpenAPI](openapi/sensibo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensibo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensibo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sensibo Historical Data API

Pull time-series history for a pod. `GET /pods/{device_id}/historicalMeasurements` returns temperature and humidity (and air quality where available) over a requested window of up to seven days, and `GET /pods/{device_id}/events` returns the device event log. Event-log retention depends on the account's Sensibo Plus subscription.

- **Human URL:** [https://support.sensibo.com/api/](https://support.sensibo.com/api/)
- **Base URL:** `https://home.sensibo.com/api/v2`

#### Tags

- Historical Data
- Time Series
- Events

#### Properties

- [Documentation](https://support.sensibo.com/api/)
- [OpenAPI](openapi/sensibo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensibo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensibo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sensibo Climate React API

Configure Climate React, Sensibo's smart-mode automation that turns the AC on or off and adjusts settings when measured temperature or humidity crosses a threshold. `GET /pods/{device_id}/smartmode` reads the configuration, `PUT` enables or disables it, and `POST` sets the low/high thresholds and the AC states to apply at each boundary.

- **Human URL:** [https://support.sensibo.com/api/](https://support.sensibo.com/api/)
- **Base URL:** `https://home.sensibo.com/api/v2`

#### Tags

- Climate React
- Smart Mode
- Automation

#### Properties

- [Documentation](https://support.sensibo.com/api/)
- [OpenAPI](openapi/sensibo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensibo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensibo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sensibo Schedules API

Create and manage recurring schedules that apply a target AC state at a chosen time on chosen days of the week. List and create schedules under `/pods/{device_id}/schedules`, and get, enable/disable, or delete a specific one under `/pods/{device_id}/schedules/{schedule_id}`.

- **Human URL:** [https://support.sensibo.com/api/](https://support.sensibo.com/api/)
- **Base URL:** `https://home.sensibo.com/api/v2`

#### Tags

- Schedules
- Automation
- Scheduling

#### Properties

- [Documentation](https://support.sensibo.com/api/)
- [OpenAPI](openapi/sensibo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensibo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensibo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sensibo Timers API

Set a one-shot countdown timer that applies a target AC state after a number of minutes - the classic "turn the AC off in 30 minutes" behavior. `GET /pods/{device_id}/timer` reads the active timer, `PUT` sets one, and `DELETE` clears it.

- **Human URL:** [https://support.sensibo.com/api/](https://support.sensibo.com/api/)
- **Base URL:** `https://home.sensibo.com/api/v2`

#### Tags

- Timers
- Countdown
- Automation

#### Properties

- [Documentation](https://support.sensibo.com/api/)
- [OpenAPI](openapi/sensibo-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sensibo.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sensibo.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/Sensibo)
- [LinkedIn](https://www.linkedin.com/company/sensibo)
- [Website](https://sensibo.com)
- [Documentation](https://support.sensibo.com/api/)
- [Plans](plans/sensibo-plans-pricing.yml)
- [Rate Limits](rate-limits/sensibo-rate-limits.yml)
- [Fin Ops](finops/sensibo-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
