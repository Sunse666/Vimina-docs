# Mouse & Keyboard

## Mouse Operations

### Move Mouse

Move mouse to the specified coordinates.

```bash
curl http://localhost:51401/api/move/500/300
```

---

### Get Mouse Position

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

### Drag Operation

Drag from start point to end point.

```bash
# Drag from 100,100 to 500,300
curl http://localhost:51401/api/drag/100/100/500/300
```

---

## Keyboard Operations

### Send Text

Simulate keyboard text input.

```bash
curl -X POST http://localhost:51401/api/input \
  -H "Content-Type: application/json" \
  -d '{"text": "Hello World"}'
```

---

## Input Examples

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # Move mouse
    requests.get(f"{base}/api/move/100/100")
    
    # Get mouse position
    pos = requests.get(f"{base}/api/mouse").json()
    
    # Drag operation
    requests.get(f"{base}/api/drag/100/100/500/300")
    
    # Input text
    requests.post(f"{base}/api/input", json={"text": "Hello"})
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // Move mouse
    fetch(`${base}/api/move/100/100`);
    
    // Get mouse position
    fetch(`${base}/api/mouse`)
      .then(r => r.json())
      .then(console.log);
    
    // Drag operation
    fetch(`${base}/api/drag/100/100/500/300`);
    
    // Input text
    fetch(`${base}/api/input`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({text: "Hello"})
    });
    ```
