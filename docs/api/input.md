# 鼠标键盘

## 鼠标操作

### 移动鼠标

移动鼠标到指定坐标。

```bash
curl http://localhost:51401/api/move/500/300
```

---

### 获取鼠标位置

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

### 拖拽操作

从起点拖拽到终点。

```bash
# 从 100,100 拖到 500,300
curl http://localhost:51401/api/drag/100/100/500/300
```

---

## 键盘操作

### 发送文本

模拟键盘输入文本。

```bash
curl -X POST http://localhost:51401/api/input \
  -H "Content-Type: application/json" \
  -d '{"text": "Hello World"}'
```

---

## 输入示例

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # 移动鼠标
    requests.get(f"{base}/api/move/100/100")
    
    # 获取鼠标位置
    pos = requests.get(f"{base}/api/mouse").json()
    
    # 拖拽操作
    requests.get(f"{base}/api/drag/100/100/500/300")
    
    # 输入文本
    requests.post(f"{base}/api/input", json={"text": "Hello"})
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // 移动鼠标
    fetch(`${base}/api/move/100/100`);
    
    // 获取鼠标位置
    fetch(`${base}/api/mouse`)
      .then(r => r.json())
      .then(console.log);
    
    // 拖拽操作
    fetch(`${base}/api/drag/100/100/500/300`);
    
    // 输入文本
    fetch(`${base}/api/input`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({text: "Hello"})
    });
    ```
