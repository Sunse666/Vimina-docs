# Window Management

## Activate Window

Activate window by title (bring to foreground).

```bash
curl "http://localhost:51401/api/activate?title=Notepad"
```

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| title | string | Window title (supports fuzzy matching) |

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

## Operate by Window Title

### Scan Window Controls

```bash
# Scan interactive controls (will save)
curl "http://localhost:51401/api/scanByTitle?title=Notepad"

# Scan all controls (will save to scan_result.json, scan_result_lite.json and scan_result_tree.json)
curl "http://localhost:51401/api/scanAllByTitle?title=Notepad"

# View saved data
curl http://localhost:51401/api/scan
```

> [!NOTE]
> - `scan_result_lite.json`: Simplified format with labels, types, coordinates
> - `scan_result_tree.json`: Control tree structure (only name/x/y/children), use with lite file
> - AI should read both files: lite for click coordinates, tree for layout understanding

### Click Window Controls

```bash
# Click by title
curl "http://localhost:51401/api/clickByTitle?title=Notepad&x=500&y=300"

# Background click
curl "http://localhost:51401/api/clickByTitle?title=Notepad&x=500&y=300&useBackend=1"

# Click and bring to foreground
curl "http://localhost:51401/api/clickByTitle?title=Notepad&x=500&y=300&bringToFront=1&useBackend=0"
```

---

## Window Operation Examples

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # Get window list
    windows = requests.get(f"{base}/api/windows").json()
    
    # Activate window
    requests.get(f"{base}/api/activate?title=Notepad")
    
    # Scan controls by title
    result = requests.get(f"{base}/api/scanByTitle?title=Notepad").json()
    
    # Background click by title
    requests.get(f"{base}/api/clickByTitle?title=Notepad&x=500&y=300&useBackend=1")
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // Get window list
    fetch(`${base}/api/windows`)
      .then(r => r.json())
      .then(windows => {
        const notepad = windows.find(w => w.title.includes("Notepad"));
        if (notepad) {
          console.log(notepad);
        }
      });
    
    // Activate window
    fetch(`${base}/api/activate?title=Notepad`);
    
    // Scan controls by title
    fetch(`${base}/api/scanByTitle?title=Notepad`)
      .then(r => r.json())
      .then(console.log);
    
    // Background click by title
    fetch(`${base}/api/clickByTitle?title=Notepad&x=500&y=300&useBackend=1`);
    ```

> [!TIP]
> Browser windows have protection mechanisms that don't allow forced activation to foreground via API. For browser windows, it's recommended to use background click (useBackend=1).
