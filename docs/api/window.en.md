# Window Management

## Activate Window

Activate the window with the specified handle.

```http
GET /api/activate/{handle}
```

**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| handle | int | Window handle |

**Example:**

```bash
curl http://localhost:8080/api/activate/12345
```

---

## Close Window

Close the window with the specified handle.

```http
GET /api/close/{handle}
```

---

## Minimize Window

Minimize the window with the specified handle.

```http
GET /api/minimize/{handle}
```

---

## Maximize Window

Maximize the window with the specified handle.

```http
GET /api/maximize/{handle}
```

---

## Operate by Title

You can also operate by window title:

```http
POST /api/window/activate
Content-Type: application/json

{"title": "Notepad"}
```

```http
POST /api/window/close
Content-Type: application/json

{"title": "Notepad"}
```

---

## Window Operation Examples

=== "Python"

    ```python
    import requests
    
    # Get window list
    windows = requests.get("http://localhost:8080/api/windows").json()
    
    # Find notepad window
    for win in windows:
        if "Notepad" in win["title"]:
            # Activate window
            requests.get(f"http://localhost:8080/api/activate/{win['handle']}")
            break
    ```

=== "JavaScript"

    ```javascript
    // Get window list and activate notepad
    fetch("http://localhost:8080/api/windows")
      .then(r => r.json())
      .then(windows => {
        const notepad = windows.find(w => w.title.includes("Notepad"));
        if (notepad) {
          fetch(`http://localhost:8080/api/activate/${notepad.handle}`);
        }
      });
    ```
