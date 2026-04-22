# Mouse & Keyboard

## Mouse Operations

### Move Mouse

Move mouse to the specified coordinates.

```http
GET /api/mouse/move/{x}/{y}
```

**Example:**

```bash
curl http://localhost:8080/api/mouse/move/500/300
```

---

### Get Mouse Position

Return current mouse position.

```http
GET /api/mouse/position
```

**Response:**

```json
{
  "x": 500,
  "y": 300
}
```

---

### Mouse Scroll

Scroll the mouse wheel.

```http
POST /api/mouse/scroll
Content-Type: application/json

{"delta": 1}
```

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| delta | int | Scroll amount, positive for up, negative for down |

---

## Keyboard Operations

### Send Text

Send text keystrokes.

```http
POST /api/keys
Content-Type: application/json

{"keys": "Hello World"}
```

---

### Send Hotkey

Send combination hotkeys.

```http
POST /api/hotkey
Content-Type: application/json

{"keys": ["ctrl", "c"]}
```

**Common Hotkeys:**

| Hotkey | Description |
|--------|-------------|
| `["ctrl", "c"]` | Copy |
| `["ctrl", "v"]` | Paste |
| `["ctrl", "a"]` | Select All |
| `["ctrl", "s"]` | Save |
| `["alt", "f4"]` | Close Window |
| `["ctrl", "z"]` | Undo |

---

## Supported Key Names

```
enter, tab, escape, space, backspace, delete
up, down, left, right, home, end, pageup, pagedown
f1, f2, f3, f4, f5, f6, f7, f8, f9, f10, f11, f12
ctrl, alt, shift, win
insert, capslock, numlock, scrolllock
```

---

## Input Examples

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:8080"
    
    # Move mouse
    requests.get(f"{base}/api/mouse/move/100/100")
    
    # Type text
    requests.post(f"{base}/api/keys", json={"keys": "Hello"})
    
    # Send hotkey
    requests.post(f"{base}/api/hotkey", json={"keys": ["ctrl", "a"]})
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:8080";
    
    // Move mouse
    fetch(`${base}/api/mouse/move/100/100`);
    
    // Type text
    fetch(`${base}/api/keys`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({keys: "Hello"})
    });
    
    // Send hotkey
    fetch(`${base}/api/hotkey`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({keys: ["ctrl", "a"]})
    });
    ```
