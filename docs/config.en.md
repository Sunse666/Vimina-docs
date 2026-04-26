# Configuration

Vimina's configuration file is located at `config.json` in the program directory.

## Label Settings

### labelStyle

Label display style.

```json
{
  "labelStyle": {
    "fontSize": 14,
    "fontFamily": "Consolas",
    "backgroundColor": "#4CAF50",
    "textColor": "#FFFFFF",
    "borderRadius": 4,
    "padding": 4
  }
}
```

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| fontSize | int | 14 | Font size |
| fontFamily | string | Consolas | Font name |
| backgroundColor | string | #4CAF50 | Background color |
| textColor | string | #FFFFFF | Text color |
| borderRadius | int | 4 | Border radius |
| padding | int | 4 | Padding |

### labelTimeout

Label input timeout (milliseconds).

```json
{
  "labelTimeout": 2000
}
```

## Filter Settings

### controlFilter

Control filter rules.

```json
{
  "controlFilter": {
    "minWidth": 10,
    "minHeight": 10,
    "ignoreDisabled": true,
    "ignoreOffscreen": true,
    "ignoreTypes": ["Pane", "Image"]
  }
}
```

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| minWidth | int | 10 | Minimum width |
| minHeight | int | 10 | Minimum height |
| ignoreDisabled | bool | true | Ignore disabled controls |
| ignoreOffscreen | bool | true | Ignore offscreen controls |
| ignoreTypes | array | [] | Control types to ignore |

### windowFilter

Window filter rules.

```json
{
  "windowFilter": {
    "ignoreMinimized": true,
    "ignoreNoTitle": false,
    "ignoreClasses": ["Shell_TrayWnd", "Progman"]
  }
}
```

## Click Settings

### clickMode

Click mode settings.

```json
{
  "clickMode": {
    "method": "simulate",
    "moveMouse": true,
    "restorePosition": true
  }
}
```

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| method | string | simulate | Click method: simulate/invoke |
| moveMouse | bool | true | Move mouse or not |
| restorePosition | bool | true | Restore mouse position or not |

## Performance Settings

### performance

Performance related settings.

```json
{
  "performance": {
    "scanInterval": 100,
    "maxControls": 500,
    "cacheEnabled": true
  }
}
```

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| scanInterval | int | 100 | Scan interval (ms) |
| maxControls | int | 500 | Maximum controls |
| cacheEnabled | bool | true | Enable cache |

## API Settings

### api

HTTP API settings.

```json
{
  "api": {
    "enabled": true,
    "port": 8080,
    "host": "localhost",
    "cors": true
  }
}
```

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| enabled | bool | true | Enable API |
| port | int | 51401 | Listen port |
| host | string | localhost | Listen address |
| cors | bool | true | Enable CORS |

## Hotkey Settings

### hotkeys

Hotkey settings.

```json
{
  "hotkeys": {
    "showLabels": "Alt+F",
    "hideLabels": "Escape",
    "exit": "Alt+Q"
  }
}
```

## Complete Configuration Example

```json
{
  "labelStyle": {
    "fontSize": 14,
    "fontFamily": "Consolas",
    "backgroundColor": "#4CAF50",
    "textColor": "#FFFFFF",
    "borderRadius": 4,
    "padding": 4
  },
  "labelTimeout": 2000,
  "controlFilter": {
    "minWidth": 10,
    "minHeight": 10,
    "ignoreDisabled": true,
    "ignoreOffscreen": true,
    "ignoreTypes": []
  },
  "windowFilter": {
    "ignoreMinimized": true,
    "ignoreNoTitle": false,
    "ignoreClasses": ["Shell_TrayWnd", "Progman"]
  },
  "clickMode": {
    "method": "simulate",
    "moveMouse": true,
    "restorePosition": true
  },
  "performance": {
    "scanInterval": 100,
    "maxControls": 500,
    "cacheEnabled": true
  },
  "api": {
    "enabled": true,
    "port": 51401,
    "host": "localhost",
    "cors": true
  },
  "hotkeys": {
    "showLabels": "Alt+F",
    "hideLabels": "Escape",
    "exit": "Alt+Q"
  }
}
```
