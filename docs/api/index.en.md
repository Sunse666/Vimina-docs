---
icon: material/api
---

# HTTP API

Vimina provides a complete HTTP API interface, listening on `http://localhost:51401` by default.

## Overview

The API is designed in RESTful style and supports the following features:

- **Basic Operations** - Control scanning, screenshots, window list, etc.
- **Click Operations** - Coordinate click, label click, background click, etc.
- **Window Management** - Activate, close, minimize, maximize windows
- **Mouse & Keyboard** - Mouse movement, keyboard input, hotkeys, etc.
- **VMA Scripts** - Execute VMA scripts

## Basic Information

| Item | Value |
|------|-------|
| Base URL | `http://localhost:51401` |
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
    # Show labels and scan
    curl -X POST http://localhost:51401/api/show
    
    # Get scan results (interactive controls only)
    curl http://localhost:51401/api/scan
    
    # Scan all controls (including text, images, etc.)
    curl http://localhost:51401/api/scanAll
    
    # Scan by window title
    curl "http://localhost:51401/api/scanByTitle?title=Notepad"
    
    # Click at coordinates
    curl http://localhost:51401/api/click/100/200
    
    # Send text
    curl -X POST http://localhost:51401/api/input \
      -H "Content-Type: application/json" \
      -d '{"text": "Hello World"}'
    ```

=== "Python"

    ```python
    import requests
    
    base_url = "http://localhost:51401"
    
    # Show labels and scan
    requests.post(f"{base_url}/api/show")
    
    # Get scan results (interactive controls only)
    result = requests.get(f"{base_url}/api/scan").json()
    
    # Scan all controls (suitable for AI to understand window content)
    result = requests.get(f"{base_url}/api/scanAll").json()
    
    # Click at coordinates
    requests.get(f"{base_url}/api/click/100/200")
    
    # Send text
    requests.post(f"{base_url}/api/input", json={"text": "Hello World"})
    ```

=== "JavaScript"

    ```javascript
    const baseUrl = "http://localhost:51401";
    
    // Show labels and scan
    fetch(`${baseUrl}/api/show`, {method: "POST"});
    
    // Get scan results
    fetch(`${baseUrl}/api/scan`)
      .then(r => r.json())
      .then(console.log);
    
    // Scan all controls
    fetch(`${baseUrl}/api/scanAll`)
      .then(r => r.json())
      .then(console.log);
    
    // Click at coordinates
    fetch(`${baseUrl}/api/click/100/200`);
    
    // Send text
    fetch(`${baseUrl}/api/input`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({text: "Hello World"})
    });
    ```

## Detailed Documentation

Please refer to the following sections for detailed API documentation:

- [Basic Operations](basic.md) - Control scanning, screenshots, window list
- [Click Operations](click.md) - Various click methods
- [Window Management](window.md) - Window operations
- [Mouse & Keyboard](input.md) - Input control
- [VMA Scripts](vma.md) - Script execution
