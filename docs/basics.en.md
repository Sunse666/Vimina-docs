# Basic Usage

## Scan Window

Open any application window, press ++alt+f++ to show control labels.

Vimina will automatically identify all interactive controls in the window and generate a two-letter label for each control.

## Keyboard Click

Type the label letters (e.g., `DJ`), and Vimina will automatically click the corresponding control.

!!! tip "Tip"
    Label input has a timeout, default is 2 seconds. If timeout occurs, the entered letters will be cleared.

## Hide Labels

Press ++alt+f++ again or press ++esc++ to hide labels.

## Common Shortcuts

| Shortcut | Function |
|----------|----------|
| ++alt+f++ | Show/Hide labels |
| ++esc++ | Hide labels |
| ++alt+q++ | Exit program |

## Background Click

Vimina supports background clicking, which means you can click controls without activating the window. This is useful when operating on background windows.

You can achieve background clicking through HTTP API:

```bash
curl -X POST http://localhost:51401/api/clickAt \
  -H "Content-Type: application/json" \
  -d '{"x": 100, "y": 200, "useBackend": true}'
```

## Next Steps

- Learn [HTTP API](api/index.md) for automation integration
- Learn [VMA Script](vma/index.md) to write automation tasks
