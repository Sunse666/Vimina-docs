---
icon: material/api
---

# HTTP API

Vimina provides a complete HTTP API interface, listening on `http://localhost:8080` by default.

## Overview

The API is designed in RESTful style and supports the following features:

- **Basic Operations** - Get control list, screenshots, window list, etc.
- **Click Operations** - Coordinate click, label click, background click, etc.
- **Window Management** - Activate, close, minimize, maximize windows
- **Mouse & Keyboard** - Mouse movement, keyboard input, hotkeys, etc.
- **VMA Script** - Execute VMA scripts

## Basic Information

| Item | Value |
|------|-------|
| Base URL | `http://localhost:8080` |
| Data Format | JSON |
| Character Encoding | UTF-8 |
| CORS | Supported |

## Response Format

All API responses are in JSON format:

```json
{
  "success": true,
  "data": { ... },
  "message": "Operation successful"
}
```

Error response:

```json
{
  "success": false,
  "error": "Error message"
}
```

## Quick Examples

=== "curl"

    ```bash
    # Get control list
    curl http://localhost:8080/api/controls
    
    # Click coordinate
    curl http://localhost:8080/api/click/100/200
    
    # Send text
    curl -X POST http://localhost:8080/api/keys \
      -H "Content-Type: application/json" \
      -d '{"keys": "Hello World"}'
    ```

=== "Python"

    ```python
    import requests
    
    base_url = "http://localhost:8080"
    
    # Get control list
    response = requests.get(f"{base_url}/api/controls")
    controls = response.json()
    
    # Click coordinate
    requests.get(f"{base_url}/api/click/100/200")
    
    # Send text
    requests.post(f"{base_url}/api/keys", json={"keys": "Hello World"})
    ```

=== "JavaScript"

    ```javascript
    const baseUrl = "http://localhost:8080";
    
    // Get control list
    fetch(`${baseUrl}/api/controls`)
      .then(r => r.json())
      .then(console.log);
    
    // Click coordinate
    fetch(`${baseUrl}/api/click/100/200`);
    
    // Send text
    fetch(`${baseUrl}/api/keys`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({keys: "Hello World"})
    });
    ```

## Detailed Documentation

See the following sections for detailed API documentation:

- [Basic Operations](basic.md) - Control list, screenshots, window list
- [Click Operations](click.md) - Various click methods
- [Window Management](window.md) - Window operations
- [Mouse & Keyboard](input.md) - Input control
- [VMA Script](vma.md) - Script execution
