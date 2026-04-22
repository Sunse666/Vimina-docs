# Click Operations

## Click by Tag

Click the control with the specified tag.

```http
POST /api/click
Content-Type: application/json

{"tag": "AB"}
```

**Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| tag | string | Yes | Control tag |

---

## Coordinate Click

Click at the specified coordinates.

```http
GET /api/click/{x}/{y}
```

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| x | int | X coordinate |
| y | int | Y coordinate |

**Example:**

```bash
curl http://localhost:8080/api/click/100/200
```

---

## Coordinate Right Click

Right click at the specified coordinates.

```http
GET /api/clickR/{x}/{y}
```

---

## Coordinate Double Click

Double click at the specified coordinates.

```http
GET /api/dblclick/{x}/{y}
```

---

## Background Coordinate Click

Supports background clicking without moving the mouse.

```http
POST /api/clickAt
Content-Type: application/json

{
  "x": 100,
  "y": 200,
  "background": true
}
```

**Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| x | int | Yes | X coordinate |
| y | int | Yes | Y coordinate |
| background | bool | No | Background click, default false |

---

## Click by Window Title

Click by window title and coordinates, supports background operation.

```http
POST /api/clickByTitle
Content-Type: application/json

{
  "title": "Notepad",
  "x": 100,
  "y": 200,
  "background": true
}
```

**Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| title | string | Yes | Window title (supports fuzzy match) |
| x | int | Yes | X coordinate relative to window |
| y | int | Yes | Y coordinate relative to window |
| background | bool | No | Background click |

---

## Click Examples

=== "Python"

    ```python
    import requests
    
    # Click by tag
    requests.post("http://localhost:8080/api/click", json={"tag": "AB"})
    
    # Click by coordinate
    requests.get("http://localhost:8080/api/click/100/200")
    
    # Background click
    requests.post("http://localhost:8080/api/clickAt", 
        json={"x": 100, "y": 200, "background": True})
    ```

=== "JavaScript"

    ```javascript
    // Click by tag
    fetch("http://localhost:8080/api/click", {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({tag: "AB"})
    });
    
    // Click by coordinate
    fetch("http://localhost:8080/api/click/100/200");
    
    // Background click
    fetch("http://localhost:8080/api/clickAt", {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({x: 100, y: 200, background: true})
    });
    ```
