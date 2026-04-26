# VMA Script Execution

Execute VMA scripts via HTTP API.

## Execute Script Content

```bash
curl -X POST http://localhost:51401/api/vma/run \
  -H "Content-Type: application/json" \
  -d '{"script": "click(100, 100)\nsleep(500)\ninput(\"Hello\")"}'
```

**Response:**

```json
{
  "success": true,
  "log": ["Done"],
  "linesExecuted": 3
}
```

---

## Execute Script File

```bash
curl -X POST http://localhost:51401/api/vma/runFile \
  -H "Content-Type: application/json" \
  -d '{"file": "C:\\path\\to\\script.vma"}'
```

---

## Parameters

### /api/vma/run

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| script | string | Yes | VMA script content |

### /api/vma/runFile

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| file | string | Yes | VMA script file path |

---

## Get Script Status

```bash
curl http://localhost:51401/api/vma/status
```

**Response:**

```json
{
  "running": true,
  "paused": false,
  "currentLine": 15,
  "totalLines": 30,
  "variables": {"x": 10, "y": 20}
}
```

---

## Stop Script

```bash
curl -X POST http://localhost:51401/api/vma/stop
```

---

## Execution Examples

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # Execute script content
    script = """
    // Automation example
    click(200, 150)
    sleep(100)
    input("admin")
    click(200, 200)
    sleep(100)
    input("password123")
    click(200, 250)
    """
    
    response = requests.post(
        f"{base}/api/vma/run",
        json={"script": script}
    )
    print(response.json())
    
    # Execute script file
    response = requests.post(
        f"{base}/api/vma/runFile",
        json={"file": "C:\\scripts\\login.vma"}
    )
    print(response.json())
    
    # Get script status
    status = requests.get(f"{base}/api/vma/status").json()
    print(status)
    
    # Stop script
    requests.post(f"{base}/api/vma/stop")
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // Execute script content
    const script = `
    // Automation example
    click(200, 150)
    sleep(100)
    input("admin")
    click(200, 200)
    sleep(100)
    input("password123")
    click(200, 250)
    `;
    
    fetch(`${base}/api/vma/run`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({script})
    })
      .then(r => r.json())
      .then(console.log);
    
    // Execute script file
    fetch(`${base}/api/vma/runFile`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({file: "C:\\\\scripts\\\\login.vma"})
    })
      .then(r => r.json())
      .then(console.log);
    
    // Get script status
    fetch(`${base}/api/vma/status`)
      .then(r => r.json())
      .then(console.log);
    
    // Stop script
    fetch(`${base}/api/vma/stop`, {method: "POST"});
    ```

---

## Integration with AI Assistant

VMA scripts are well-suited for integration with AI assistants:

```python
import requests

# AI assistant generates and executes script
def ai_automate(user_request):
    # AI understands user intent, generates VMA script
    script = ai_generate_script(user_request)
    
    # Execute script
    response = requests.post(
        "http://localhost:51401/api/vma/run",
        json={"script": script}
    )
    
    return response.json()

# Example
ai_automate("Open Notepad, type Hello World, then save to desktop")
```

For more VMA syntax, please refer to [VMA Script Syntax](../vma/index.md).
