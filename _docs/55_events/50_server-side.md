---
title: Server-side
category: events
permalink: /events/server-side
last_modified_at: 2023-11-15
---

Server-side and mobile app data submissions are supported, allowing for the transmission of standard data points along with [metadata](/metadata). Access and analyze this data through the [Events Explorer](/events-explorer) or create [goals](/goals) for frequent event monitoring.

## Data submission

Developers can submit data to `https://queue.simpleanalyticscdn.com/events` using JSON format.

### User agent guidelines

To prevent misidentification as a robot, avoid using default user agents from request libraries. These often contain terms like `bot`, `crawl`, `python-requests/...`, `curl/...`, `node-fetch/...`, or `axios/...`. Instead, use a custom user agent format, such as `ServerSide/1.0 (+https://www.yourwebsite.com/)`.

### Event data structure

For event tracking, structure your payload as follows:

```json
{
  "type": "event",
  "hostname": "example.com",
  "event": "event-name",
  "ua": "User Agent"
}
```

### Page view data structure

Page view data uses the same endpoint, structured like this:

```json
{
  "type": "pageview",
  "hostname": "example.com",
  "event": "pageview",
  "ua": "User Agent"
}
```

## Testing with cURL

To send test data, use the following cURL command:

```bash
curl -X POST -H "Content-Type: application/json" -d '{
  "type": "event",
  "hostname": "mobile-app.example.com",
  "event": "consent",
  "metadata": {
    "button": "yes"
  },
  "ua": "Your User Agent"
}' https://queue.simpleanalyticscdn.com/events
```

Data should appear on your dashboard within minutes. You can always [export the raw latest data](/export-data) from our dashboard, or use the [Events Explorer](/events-explorer) to find your events.

## Additional data fields

Expand your data submission with additional fields:

```json
{
  "type": "event",
  "hostname": "example.com",
  "event": "event-name",
  "path": "/",
  "viewport_width": 1440,
  "viewport_height": 310,
  "language": "en-US",
  "screen_width": 1440,
  "screen_height": 900,
  "unique": true,
  "https": true,
  "timezone": "Europe/Amsterdam",
  "metadata": {
    "button": "yes"
  },
  "ua": "User Agent"
}
```
