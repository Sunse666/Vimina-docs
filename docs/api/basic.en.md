# Basic Operations

## Show Labels and Scan

Show labels and scan controls in the current active window.

```bash
curl -X POST http://localhost:51401/api/show
```

---

## Hide Labels

Hide all displayed labels.

```bash
curl -X POST http://localhost:51401/api/hide
```

---

## Get Scan Results

Get the results of the most recent scan (interactive controls only).

```bash
curl http://localhost:51401/api/scan
```

**Response Example:**

```json
{
  "success": true,
  "timestamp": "2024-01-01T12:00:00",
  "window": {
    "title": "Notepad",
    "className": "Notepad",
    "handle": 123456
  },
  "summary": {
    "totalControls": 15,
    "description": "Window 'Notepad' has 15 interactive controls"
  },
  "controls": [
    {
      "name": "File",
      "type": "MenuItem",
      "typeDesc": "Menu Item",
      "isInteractive": true,
      "x": 10,
      "y": 30,
      "width": 50,
      "height": 20,
      "centerX": 35,
      "centerY": 40,
      "label": "DJ"
    }
  ]
}
```

---

## Scan All Controls

Scan all controls, including non-interactive elements like text and images (suitable for AI to understand window content).

```bash
curl http://localhost:51401/api/scanAll
```

**Response Example:**

```json
{
  "success": true,
  "summary": {
    "totalControls": 45,
    "byType": {
      "Text": 20,
      "Button": 5,
      "Edit": 3,
      "Image": 2,
      "Pane": 15
    }
  },
  "controls": [...]
}
```

---

## Scan by Window Title

### Scan Interactive Controls

```bash
curl "http://localhost:51401/api/scanByTitle?title=Notepad"
```

Or POST method:

```bash
curl -X POST http://localhost:51401/api/scanByTitle \
  -H "Content-Type: application/json" \
  -d '{"title": "Notepad"}'
```

### Scan All Controls

```bash
curl "http://localhost:51401/api/scanAllByTitle?title=Notepad"
```

Or POST method:

```bash
curl -X POST http://localhost:51401/api/scanAllByTitle \
  -H "Content-Type: application/json" \
  -d '{"title": "Notepad"}'
```

**Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| title | string | Yes | Window title (supports fuzzy matching) |

> [!TIP]
> - `/api/scan` and `/api/scanByTitle` only return interactive controls (buttons, input fields, etc.)
> - `/api/scanAll` and `/api/scanAllByTitle` return all controls, including non-interactive elements like text and images
> - All scan results are saved to the `data/scan_result.json` file

---

## Get Window List

Get all visible windows list.

```bash
curl http://localhost:51401/api/windows
```

**Response Example:**

```json
{
  "success": true,
  "count": 5,
  "windows": [
    {
      "hwnd": 123456,
      "title": "Notepad",
      "className": "Notepad",
      "processId": 1234
    },
    {
      "hwnd": 789012,
      "title": "bilibili",
      "className": "Chrome_WidgetWin_1",
      "processId": 5678
    }
  ]
}
```

**Field Description:**

| Field | Type | Description |
|-------|------|-------------|
| hwnd | int | Window handle |
| title | string | Window title |
| className | string | Class name |
| processId | int | Process ID |

---

## Get Mouse Position

Return current mouse position.

```bash
curl http://localhost:51401/api/mouse
```

**Response:**

```json
{
  "x": 500,
  "y": 300
}
```

---

## Get Status

Get program running status.

```bash
curl http://localhost:51401/api/status
```

**Response Example:**

```json
{
  "running": true,
  "hasData": true,
  "lastScan": "2024-01-01T12:00:00",
  "mousePosition": {"x": 500, "y": 300},
  "screen": [1920, 1080]
}
```

---

## Raw Data Endpoints

### Get Raw Scan Results

```bash
curl http://localhost:51401/api/raw/scan
```

### Get Raw Label Mapping

```bash
curl http://localhost:51401/api/raw/labels
```

---

## Usage Examples

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # Show labels and scan
    requests.post(f"{base}/api/show")
    
    # Get scan results (interactive controls only)
    result = requests.get(f"{base}/api/scan").json()
    
    # Scan all controls (suitable for AI to understand window content)
    result = requests.get(f"{base}/api/scanAll").json()
    
    # Scan by title
    result = requests.get(f"{base}/api/scanByTitle?title=Notepad").json()
    result = requests.get(f"{base}/api/scanAllByTitle?title=Notepad").json()
    
    # Get window list
    windows = requests.get(f"{base}/api/windows").json()
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // Show labels and scan
    fetch(`${base}/api/show`, {method: "POST"});
    
    // Get scan results
    fetch(`${base}/api/scan`)
      .then(r => r.json())
      .then(console.log);
    
    // Scan all controls
    fetch(`${base}/api/scanAll`)
      .then(r => r.json())
      .then(console.log);
    
    // Scan by title
    fetch(`${base}/api/scanByTitle?title=Notepad`)
      .then(r => r.json())
      .then(console.log);
    
    // Get window list
    fetch(`${base}/api/windows`)
      .then(r => r.json())
      .then(console.log);
    ```
