---
icon: material/api
---

# HTTP API

Vimina 提供完整的 HTTP API 接口，默认监听 `http://localhost:51401`。

## 概述

API 采用 RESTful 风格设计，支持以下功能：

- **基础操作** - 控件扫描、截图、窗口列表等
- **点击操作** - 坐标点击、标签点击、后台点击等
- **窗口管理** - 激活、关闭、最小化、最大化窗口
- **鼠标键盘** - 鼠标移动、键盘输入、快捷键等
- **VMA 脚本** - 执行 VMA 脚本

## 基础信息

| 项目 | 值 |
|------|-----|
| 基础 URL | `http://localhost:51401` |
| 数据格式 | JSON |
| 字符编码 | UTF-8 |
| CORS | 支持 |

## 响应格式

所有 API 响应均为 JSON 格式：

```json
{
  "success": true,
  "data": { ... },
  "message": "操作成功"
}
```

错误响应：

```json
{
  "success": false,
  "error": "错误信息"
}
```

## 快速示例

=== "curl"

    ```bash
    # 显示标签并扫描
    curl -X POST http://localhost:51401/api/show
    
    # 获取扫描结果（仅可交互控件）
    curl http://localhost:51401/api/scan
    
    # 扫描所有控件（包括文本、图片等）
    curl http://localhost:51401/api/scanAll
    
    # 通过窗口标题扫描
    curl "http://localhost:51401/api/scanByTitle?title=记事本"
    
    # 点击坐标
    curl http://localhost:51401/api/click/100/200
    
    # 发送文本
    curl -X POST http://localhost:51401/api/input \
      -H "Content-Type: application/json" \
      -d '{"text": "Hello World"}'
    ```

=== "Python"

    ```python
    import requests
    
    base_url = "http://localhost:51401"
    
    # 显示标签并扫描
    requests.post(f"{base_url}/api/show")
    
    # 获取扫描结果（仅可交互控件）
    result = requests.get(f"{base_url}/api/scan").json()
    
    # 扫描所有控件（适合AI理解窗口内容）
    result = requests.get(f"{base_url}/api/scanAll").json()
    
    # 点击坐标
    requests.get(f"{base_url}/api/click/100/200")
    
    # 发送文本
    requests.post(f"{base_url}/api/input", json={"text": "Hello World"})
    ```

=== "JavaScript"

    ```javascript
    const baseUrl = "http://localhost:51401";
    
    // 显示标签并扫描
    fetch(`${baseUrl}/api/show`, {method: "POST"});
    
    // 获取扫描结果
    fetch(`${baseUrl}/api/scan`)
      .then(r => r.json())
      .then(console.log);
    
    // 扫描所有控件
    fetch(`${baseUrl}/api/scanAll`)
      .then(r => r.json())
      .then(console.log);
    
    // 点击坐标
    fetch(`${baseUrl}/api/click/100/200`);
    
    // 发送文本
    fetch(`${baseUrl}/api/input`, {
      method: "POST",
      headers: {"Content-Type": "application/json"},
      body: JSON.stringify({text: "Hello World"})
    });
    ```

## 详细文档

请查看以下章节了解详细的 API 文档：

- [基础操作](basic.md) - 控件扫描、截图、窗口列表
- [点击操作](click.md) - 各种点击方式
- [窗口管理](window.md) - 窗口操作
- [鼠标键盘](input.md) - 输入控制
- [VMA 脚本](vma.md) - 脚本执行
