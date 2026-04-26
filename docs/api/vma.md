# VMA 脚本执行

通过 HTTP API 执行 VMA 脚本。

## 执行脚本内容

```bash
curl -X POST http://localhost:51401/api/vma/run \
  -H "Content-Type: application/json" \
  -d '{"script": "click(100, 100)\nsleep(500)\ninput(\"Hello\")"}'
```

**响应：**

```json
{
  "success": true,
  "log": ["完成"],
  "linesExecuted": 3
}
```

---

## 执行脚本文件

```bash
curl -X POST http://localhost:51401/api/vma/runFile \
  -H "Content-Type: application/json" \
  -d '{"file": "C:\\path\\to\\script.vma"}'
```

---

## 参数说明

### /api/vma/run

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| script | string | 是 | VMA 脚本内容 |

### /api/vma/runFile

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| file | string | 是 | VMA 脚本文件路径 |

---

## 获取脚本状态

```bash
curl http://localhost:51401/api/vma/status
```

**响应：**

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

## 停止脚本

```bash
curl -X POST http://localhost:51401/api/vma/stop
```

---

## 执行示例

=== "Python"

    ```python
    import requests
    
    base = "http://localhost:51401"
    
    # 执行脚本内容
    script = """
    // 自动化示例
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
    
    # 执行脚本文件
    response = requests.post(
        f"{base}/api/vma/runFile",
        json={"file": "C:\\scripts\\login.vma"}
    )
    print(response.json())
    
    # 获取脚本状态
    status = requests.get(f"{base}/api/vma/status").json()
    print(status)
    
    # 停止脚本
    requests.post(f"{base}/api/vma/stop")
    ```

=== "JavaScript"

    ```javascript
    const base = "http://localhost:51401";
    
    // 执行脚本内容
    const script = `
    // 自动化示例
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
    
    // 执行脚本文件
    fetch(`${base}/api/vma/runFile`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({file: "C:\\\\scripts\\\\login.vma"})
    })
      .then(r => r.json())
      .then(console.log);
    
    // 获取脚本状态
    fetch(`${base}/api/vma/status`)
      .then(r => r.json())
      .then(console.log);
    
    // 停止脚本
    fetch(`${base}/api/vma/stop`, {method: "POST"});
    ```

---

## 与 AI 助手集成

VMA 脚本非常适合与 AI 助手集成：

```python
import requests

# AI 助手生成脚本并执行
def ai_automate(user_request):
    # AI 理解用户意图，生成 VMA 脚本
    script = ai_generate_script(user_request)
    
    # 执行脚本
    response = requests.post(
        "http://localhost:51401/api/vma/run",
        json={"script": script}
    )
    
    return response.json()

# 示例
ai_automate("打开记事本，输入 Hello World，然后保存到桌面")
```

更多 VMA 语法请参考 [VMA 脚本语法](../vma/index.md)。
