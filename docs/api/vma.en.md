# VMA Script Execution

Execute VMA scripts through HTTP API.

## Execute Script

```http
POST /api/vma/run
Content-Type: application/json

{
  "script": "click(100, 100)\nsleep(500)\ntype(\"Hello\")"
}
```

**Response:**

```json
{
  "success": true,
  "output": "Script executed successfully"
}
```

---

## Parameter Description

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| script | string | Yes | VMA script content |

---

## Execution Examples

=== "Python"

    ```python
    import requests
    
    script = """
    // Auto login example
    click(200, 150)
    sleep(100)
    type("admin")
    click(200, 200)
    sleep(100)
    type("password123")
    click(200, 250)
    """
    
    response = requests.post(
        "http://localhost:8080/api/vma/run",
        json={"script": script}
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const script = `
    // Auto login example
    click(200, 150)
    sleep(100)
    type("admin")
    click(200, 200)
    sleep(100)
    type("password123")
    click(200, 250)
    `;
    
    fetch("http://localhost:8080/api/vma/run", {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({script})
    })
      .then(r => r.json())
      .then(console.log);
    ```

---

## Integration with AI Assistant

VMA scripts are perfect for integration with AI assistants:

```python
# AI assistant generates script and executes
def ai_automate(user_request):
    # AI understands user intent, generates VMA script
    script = ai_generate_script(user_request)
    
    # Execute script
    response = requests.post(
        "http://localhost:8080/api/vma/run",
        json={"script": script}
    )
    
    return response.json()

# Example
ai_automate("Open notepad, type Hello World, and save to desktop")
```

See [VMA Script Syntax](../vma/index.md) for more details.
