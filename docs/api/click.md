# 点击操作

## 通过标签点击

点击指定标签的控件。

```bash
# 左键点击
curl -X POST http://localhost:51401/api/click \
  -H "Content-Type: application/json" \
  -d '{"label": "DJ"}'

# 右键点击
curl -X POST http://localhost:51401/api/click \
  -H "Content-Type: application/json" \
  -d '{"label": "DJ", "right": true}'

# 双击
curl -X POST http://localhost:51401/api/click \
  -H "Content-Type: application/json" \
  -d '{"label": "DJ", "double": true}'
```

**参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| label | string | 是 | 控件标签 |
| right | bool | 否 | 是否右键点击，默认 false |
| double | bool | 否 | 是否双击，默认 false |

---

## 坐标点击

点击指定坐标。

```bash
curl http://localhost:51401/api/click/100/200
```

**参数：**

| 参数 | 类型 | 说明 |
|------|------|------|
| x | int | X 坐标 |
| y | int | Y 坐标 |

---

## 坐标右键点击

在指定坐标右键点击。

```bash
curl http://localhost:51401/api/clickR/100/200
```

---

## 坐标双击

在指定坐标双击。

```bash
curl http://localhost:51401/api/dblclick/100/200
```

---

## 后台坐标点击

支持后台点击，不移动鼠标。

```bash
# 后台点击
curl "http://localhost:51401/api/click/100/200?useBackend=1"

# 后台右键点击
curl "http://localhost:51401/api/clickR/100/200?useBackend=1"

# 后台双击
curl "http://localhost:51401/api/dblclick/100/200?useBackend=1"
```

或 POST 方式：

```bash
curl -X POST http://localhost:51401/api/clickAt \
  -H "Content-Type: application/json" \
  -d '{"x": 100, "y": 200, "useBackend": true}'
```

**参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| x | int | 是 | X 坐标 |
| y | int | 是 | Y 坐标 |
| useBackend | bool | 否 | 是否后台点击，默认 false |
| right | bool | 否 | 是否右键点击，默认 false |
| double | bool | 否 | 是否双击，默认 false |

---

## 通过窗口标题点击

通过窗口标题和坐标点击，支持后台操作。

```bash
# 通过标题点击
curl "http://localhost:51401/api/clickByTitle?title=记事本&x=500&y=300"

# 后台点击
curl "http://localhost:51401/api/clickByTitle?title=记事本&x=500&y=300&useBackend=1"

# 点击并切换到前台
curl "http://localhost:51401/api/clickByTitle?title=记事本&x=500&y=300&bringToFront=1&useBackend=0"
```

或 POST 方式：

```bash
curl -X POST http://localhost:51401/api/clickByTitle \
  -H "Content-Type: application/json" \
  -d '{"title": "记事本", "x": 500, "y": 300, "useBackend": true}'
```

**参数：**

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| title | string | 是 | 窗口标题（支持模糊匹配） |
| x | int | 是 | 相对窗口的 X 坐标 |
| y | int | 是 | 相对窗口的 Y 坐标 |
| useBackend | bool | 否 | 是否后台点击，默认 false |
| bringToFront | bool | 否 | 是否先切换到前台，默认 false |

> [!TIP]
> 后台点击功能可以在不干扰当前工作的情况下操作其他窗口，非常适合自动化脚本和 AI 助手集成

---

## 点击示例

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # 标签点击
    requests.post(f"{base}/api/click", json={"label": "DJ"})
    
    # 标签右键点击
    requests.post(f"{base}/api/click", json={"label": "DJ", "right": True})
    
    # 坐标点击
    requests.get(f"{base}/api/click/100/200")
    
    # 后台点击
    requests.get(f"{base}/api/click/100/200?useBackend=1")
    
    # 通过标题后台点击
    requests.post(f"{base}/api/clickByTitle", 
        json={"title": "记事本", "x": 100, "y": 200, "useBackend": True})
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // 标签点击
    fetch(`${base}/api/click`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({label: "DJ"})
    });
    
    // 坐标点击
    fetch(`${base}/api/click/100/200`);
    
    // 后台点击
    fetch(`${base}/api/click/100/200?useBackend=1`);
    
    // 通过标题后台点击
    fetch(`${base}/api/clickByTitle`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({title: "记事本", x: 100, y: 200, useBackend: true})
    });
    ```
