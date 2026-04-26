# 基础操作

## 显示标签并扫描

显示标签并扫描当前活动窗口的控件。

```bash
curl -X POST http://localhost:51401/api/show
```

---

## 隐藏标签

隐藏所有显示的标签。

```bash
curl -X POST http://localhost:51401/api/hide
```

---

## 获取扫描结果

获取最近一次扫描的结果（仅可交互控件）。

```bash
curl http://localhost:51401/api/scan
```

**响应示例：**

```json
{
  "success": true,
  "timestamp": "2024-01-01T12:00:00",
  "window": {
    "title": "记事本",
    "className": "Notepad",
    "handle": 123456
  },
  "summary": {
    "totalControls": 15,
    "description": "窗口「记事本」共有 15 个可交互控件"
  },
  "controls": [
    {
      "name": "文件",
      "type": "MenuItem",
      "typeDesc": "菜单项",
      "isInteractive": true,
      "x": 10,
      "y": 30,
      "width": 50,
      "height": 20,
      "centerX": 35,
      "centerY": 40,
      "label": "DJ"
    }
  ]
}
```

---

## 扫描所有控件

扫描所有控件，包括文本、图片等不可交互元素（适合 AI 理解窗口内容）。

```bash
curl http://localhost:51401/api/scanAll
```

**响应示例：**

```json
{
  "success": true,
  "summary": {
    "totalControls": 45,
    "byType": {
      "Text": 20,
      "Button": 5,
      "Edit": 3,
      "Image": 2,
      "Pane": 15
    }
  },
  "controls": [...]
}
```

---

## 通过窗口标题扫描

### 扫描可交互控件

```bash
curl "http://localhost:51401/api/scanByTitle?title=记事本"
```

或 POST 方式：

```bash
curl -X POST http://localhost:51401/api/scanByTitle \
  -H "Content-Type: application/json" \
  -d '{"title": "记事本"}'
```

### 扫描所有控件

```bash
curl "http://localhost:51401/api/scanAllByTitle?title=记事本"
```

或 POST 方式：

```bash
curl -X POST http://localhost:51401/api/scanAllByTitle \
  -H "Content-Type: application/json" \
  -d '{"title": "记事本"}'
```

**参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| title | string | 是 | 窗口标题（支持模糊匹配） |

> [!TIP]
> - `/api/scan` 和 `/api/scanByTitle` 只返回可交互控件（按钮、输入框等）
> - `/api/scanAll` 和 `/api/scanAllByTitle` 返回所有控件，包括文本、图片等不可交互元素
> - 所有扫描结果都会保存到 `data/scan_result.json` 文件中

---

## 获取窗口列表

获取所有可见窗口列表。

```bash
curl http://localhost:51401/api/windows
```

**响应示例：**

```json
{
  "success": true,
  "count": 5,
  "windows": [
    {
      "hwnd": 123456,
      "title": "记事本",
      "className": "Notepad",
      "processId": 1234
    },
    {
      "hwnd": 789012,
      "title": "bilibili",
      "className": "Chrome_WidgetWin_1",
      "processId": 5678
    }
  ]
}
```

**字段说明：**

| 字段 | 类型 | 说明 |
|------|------|------|
| hwnd | int | 窗口句柄 |
| title | string | 窗口标题 |
| className | string | 类名 |
| processId | int | 进程ID |

---

## 获取鼠标位置

返回当前鼠标位置。

```bash
curl http://localhost:51401/api/mouse
```

**响应：**

```json
{
  "x": 500,
  "y": 300
}
```

---

## 获取状态

获取程序运行状态。

```bash
curl http://localhost:51401/api/status
```

**响应示例：**

```json
{
  "running": true,
  "hasData": true,
  "lastScan": "2024-01-01T12:00:00",
  "mousePosition": {"x": 500, "y": 300},
  "screen": [1920, 1080]
}
```

---

## 原始数据接口

### 获取原始扫描结果

```bash
curl http://localhost:51401/api/raw/scan
```

### 获取原始标签映射

```bash
curl http://localhost:51401/api/raw/labels
```

---

## 使用示例

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # 显示标签并扫描
    requests.post(f"{base}/api/show")
    
    # 获取扫描结果（仅可交互控件）
    result = requests.get(f"{base}/api/scan").json()
    
    # 扫描所有控件（适合AI理解窗口内容）
    result = requests.get(f"{base}/api/scanAll").json()
    
    # 通过标题扫描
    result = requests.get(f"{base}/api/scanByTitle?title=记事本").json()
    result = requests.get(f"{base}/api/scanAllByTitle?title=记事本").json()
    
    # 获取窗口列表
    windows = requests.get(f"{base}/api/windows").json()
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // 显示标签并扫描
    fetch(`${base}/api/show`, {method: "POST"});
    
    // 获取扫描结果
    fetch(`${base}/api/scan`)
      .then(r => r.json())
      .then(console.log);
    
    // 扫描所有控件
    fetch(`${base}/api/scanAll`)
      .then(r => r.json())
      .then(console.log);
    
    // 通过标题扫描
    fetch(`${base}/api/scanByTitle?title=记事本`)
      .then(r => r.json())
      .then(console.log);
    
    // 获取窗口列表
    fetch(`${base}/api/windows`)
      .then(r => r.json())
      .then(console.log);
    ```
