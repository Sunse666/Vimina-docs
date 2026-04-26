# Click Operations

## Click by Label

Click the control with the specified label.

```bash
# Left click
curl -X POST http://localhost:51401/api/click \
  -H "Content-Type: application/json" \
  -d '{"label": "DJ"}'

# Right click
curl -X POST http://localhost:51401/api/click \
  -H "Content-Type: application/json" \
  -d '{"label": "DJ", "right": true}'

# Double click
curl -X POST http://localhost:51401/api/click \
  -H "Content-Type: application/json" \
  -d '{"label": "DJ", "double": true}'
```

**Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| label | string | Yes | Control label |
| right | bool | No | Right-click, default false |
| double | bool | No | Double-click, default false |

---

## Click at Coordinates

Click at the specified coordinates.

```bash
curl http://localhost:51401/api/click/100/200
```

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| x | int | X coordinate |
| y | int | Y coordinate |

---

## Right-click at Coordinates

Right-click at the specified coordinates.

```bash
curl http://localhost:51401/api/clickR/100/200
```

---

## Double-click at Coordinates

Double-click at the specified coordinates.

```bash
curl http://localhost:51401/api/dblclick/100/200
```

---

## Background Click at Coordinates

Support background clicking without moving the mouse.

```bash
# Background click
curl "http://localhost:51401/api/click/100/200?useBackend=1"

# Background right-click
curl "http://localhost:51401/api/clickR/100/200?useBackend=1"

# Background double-click
curl "http://localhost:51401/api/dblclick/100/200?useBackend=1"
```

Or POST method:

```bash
curl -X POST http://localhost:51401/api/clickAt \
  -H "Content-Type: application/json" \
  -d '{"x": 100, "y": 200, "useBackend": true}'
```

**Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| x | int | Yes | X coordinate |
| y | int | Yes | Y coordinate |
| useBackend | bool | No | Background click, default false |
| right | bool | No | Right-click, default false |
| double | bool | No | Double-click, default false |

---

## Click by Window Title

Click by window title and coordinates, supports background operations.

```bash
# Click by title
curl "http://localhost:51401/api/clickByTitle?title=Notepad&x=500&y=300"

# Background click
curl "http://localhost:51401/api/clickByTitle?title=Notepad&x=500&y=300&useBackend=1"

# Click and bring to foreground
curl "http://localhost:51401/api/clickByTitle?title=Notepad&x=500&y=300&bringToFront=1&useBackend=0"
```

Or POST method:

```bash
curl -X POST http://localhost:51401/api/clickByTitle \
  -H "Content-Type: application/json" \
  -d '{"title": "Notepad", "x": 500, "y": 300, "useBackend": true}'
```

**Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| title | string | Yes | Window title (supports fuzzy matching) |
| x | int | Yes | X coordinate relative to window |
| y | int | Yes | Y coordinate relative to window |
| useBackend | bool | No | Background click, default false |
| bringToFront | bool | No | Bring to foreground first, default false |

> [!TIP]
> Background click functionality allows operating other windows without disturbing current work, perfect for automation scripts and AI assistant integration

---

## Click Examples

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # Click by label
    requests.post(f"{base}/api/click", json={"label": "DJ"})
    
    # Right-click by label
    requests.post(f"{base}/api/click", json={"label": "DJ", "right": True})
    
    # Click at coordinates
    requests.get(f"{base}/api/click/100/200")
    
    # Background click
    requests.get(f"{base}/api/click/100/200?useBackend=1")
    
    # Background click by title
    requests.post(f"{base}/api/clickByTitle", 
        json={"title": "Notepad", "x": 100, "y": 200, "useBackend": True})
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // Click by label
    fetch(`${base}/api/click`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({label: "DJ"})
    });
    
    // Click at coordinates
    fetch(`${base}/api/click/100/200`);
    
    // Background click
    fetch(`${base}/api/click/100/200?useBackend=1`);
    
    // Background click by title
    fetch(`${base}/api/clickByTitle`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({title: "Notepad", x: 100, y: 200, useBackend: true})
    });
    ```
