# Sensibo (sensibo)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
