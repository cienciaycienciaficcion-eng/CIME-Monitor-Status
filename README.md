# CIME Monitor - Public Status

This repository publishes a deliberately limited, public status feed for the CIME Monitor Android app.

## Public files

- `status.json`: latest overall monitor state, last heartbeat time, service names and states, and incident summary.
- `events.json`: a rolling history of the latest 200 sanitized events.

## Privacy

This repository is public. Do not place credentials, tokens, internal IP addresses, hostnames, Windows details, boot identifiers, diagnostic output, device identifiers, or personal information here.

The source-of-truth state and operational workflows remain in the private `CIME-Monitor` repository. A private GitHub Actions workflow publishes only sanitized fields here.

## Android read URLs

- https://raw.githubusercontent.com/cienciaycienciaficcion-eng/CIME-Monitor-Status/main/status.json
- https://raw.githubusercontent.com/cienciaycienciaficcion-eng/CIME-Monitor-Status/main/events.json

Clients should treat the data as stale if `last_seen` is older than the app's configured threshold. The raw content delivery network may cache responses briefly; clients can add a timestamp query parameter to bypass client-side caches.

## Schema

`status.json`:

```json
{
  "schema_version": 1,
  "monitor": "CIME-SERVER-01",
  "site": "CIME-3D",
  "status": "online",
  "last_seen": "2026-11-18T12:00:00Z",
  "last_event": "heartbeat",
  "services": {
    "control_reactivos": "ONLINE"
  },
  "incident": {
    "open": false,
    "started_at": null,
    "age_seconds": 0
  },
  "updated_at": "2026-11-18T12:00:00Z"
}
```

The contents are public by design. Do not use this feed to publish sensitive operational details.
