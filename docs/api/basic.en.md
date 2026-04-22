# Basic Operations

## Get Control List

Get all interactive controls in the current active window.

```http
GET /api/controls
```

**Response Example:**

```json
[
  {
    "tag": "AB",
    "name": "OK",
    "controlType": "Button",
    "className": "Button",
    "bounds": {
      "x": 100,
      "y": 200,
      "width": 80,
      "height": 30
    },
    "isEnabled": true,
    "isOffscreen": false
  }
]
```

**Field Description:**

| Field | Type | Description |
|-------|------|-------------|
| tag | string | Control tag (two letters) |
| name | string | Control name |
| controlType | string | Control type |
| className | string | Class name |
| bounds | object | Bounding rectangle |
| isEnabled | bool | Is enabled |
| isOffscreen | bool | Is offscreen |

---

## Screenshot

Take a screenshot of the current screen.

```http
GET /api/screenshot
```

**Response:** PNG image

**Example:**

```bash
curl http://localhost:8080/api/screenshot -o screenshot.png
```

---

## Get Window List

Get all visible windows list.

```http
GET /api/windows
```

**Response Example:**

```json
[
  {
    "handle": 12345,
    "title": "Notepad",
    "className": "Notepad",
    "bounds": {
      "x": 100,
      "y": 100,
      "width": 800,
      "height": 600
    },
    "isActive": true
  }
]
```

**Field Description:**

| Field | Type | Description |
|-------|------|-------------|
| handle | int | Window handle |
| title | string | Window title |
| className | string | Class name |
| bounds | object | Bounding rectangle |
| isActive | bool | Is active window |

---

## Get Status

Get program running status.

```http
GET /api/status
```

**Response Example:**

```json
{
  "running": true,
  "version": "1.0.0",
  "uptime": 3600,
  "controlsCount": 42
}
```

---

## Health Check

Check if service is running.

```http
GET /api/health
```

**Response:**

```json
{
  "status": "ok"
}
```
