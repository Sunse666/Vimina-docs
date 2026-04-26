# 窗口管理

## 激活窗口

通过窗口标题激活窗口（切换到前台）。

```bash
curl "http://localhost:51401/api/activate?title=记事本"
```

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| title | string | 窗口标题（支持模糊匹配） |

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

## 通过窗口标题操作

### 扫描窗口控件

```bash
# 扫描可交互控件（现在会保存）
curl "http://localhost:51401/api/scanByTitle?title=记事本"

# 扫描所有控件（会保存）
curl "http://localhost:51401/api/scanAllByTitle?title=记事本"

# 查看保存的数据
curl http://localhost:51401/api/scan
```

### 点击窗口控件

```bash
# 通过标题点击
curl "http://localhost:51401/api/clickByTitle?title=记事本&x=500&y=300"

# 后台点击
curl "http://localhost:51401/api/clickByTitle?title=记事本&x=500&y=300&useBackend=1"

# 点击并切换到前台
curl "http://localhost:51401/api/clickByTitle?title=记事本&x=500&y=300&bringToFront=1&useBackend=0"
```

---

## 窗口操作示例

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # 获取窗口列表
    windows = requests.get(f"{base}/api/windows").json()
    
    # 激活窗口
    requests.get(f"{base}/api/activate?title=记事本")
    
    # 通过标题扫描控件
    result = requests.get(f"{base}/api/scanByTitle?title=记事本").json()
    
    # 通过标题后台点击
    requests.get(f"{base}/api/clickByTitle?title=记事本&x=500&y=300&useBackend=1")
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // 获取窗口列表
    fetch(`${base}/api/windows`)
      .then(r => r.json())
      .then(windows => {
        const notepad = windows.find(w => w.title.includes("记事本"));
        if (notepad) {
          console.log(notepad);
        }
      });
    
    // 激活窗口
    fetch(`${base}/api/activate?title=记事本`);
    
    // 通过标题扫描控件
    fetch(`${base}/api/scanByTitle?title=记事本`)
      .then(r => r.json())
      .then(console.log);
    
    // 通过标题后台点击
    fetch(`${base}/api/clickByTitle?title=记事本&x=500&y=300&useBackend=1`);
    ```

> [!TIP]
> 浏览器窗口有保护机制，不允许通过 API 强行激活到前台。对于浏览器窗口，建议使用后台点击（useBackend=1）。
