# 净读API文档

## 概述 - Jingdu (v0.7.2)
净读API提供书籍管理和用户认证服务，支持JSON格式的数据交互。

**基础URL**: `https://jingdu.qzz.io/api`

**默认响应格式**: JSON

## 认证

部分API需要Token认证，Token通过登录接口获取。

## 端点列表

### 1. 根端点

**GET `/api`**

获取API基本信息

**响应示例**:
```json
{
  "about": "Welcome traveler!",
  "time": 1633024000.123456,
  "documentation": "https://js20studio.qzz.io/jingdu-api-docs",
  "name": "jingdu",
  "version": "0.7.2"
}
```

### 2. 获取书籍列表

**GET `/api/get-books`**

获取所有可展示的书籍列表

**响应**:
```json
  {
    "success": true,
    "data": [
      {
        "author": "Janson20",
        "author_id": "068bc0c2-2f09-7789-8000-f672921eed70",
        "book_id": "068bbf8d-9ce0-72e5-8000-124f065499f3",
        "category": "默认",
        "cover": "images/log.jpeg",
        "desc": "这是净读的官方开发日志，记录了净读从无到有的开发过程。",
        "title": "净读开发日志"
      }
    ],
    "count": 1
  }
```

**错误响应**:
```json
{
  "success": false,
  "error": "错误信息"
}
```

### 3. 用户登录

**POST `/api/login`**

用户登录认证

**请求体**:
```json
{
  "username": "用户名",
  "password": "密码"
}
```

**成功响应**:
```json
{
  "success": true,
  "auth": "ok",
  "message": "登录成功",
  "user": "用户名",
  "uuid": "用户UUID",
  "token": "认证令牌"
}
```

**错误响应**:
- 400: 请求数据为空或缺少必要字段
- 401: 用户名或密码错误
- 500: 服务器错误

### 4. 添加章节

**POST `/api/add-chapter`**

为书籍添加新章节（需要认证）

**请求头**:
```
Content-Type: application/json
```

**请求体**:
```json
{
  "token": "用户认证令牌",
  "book_id": "书籍ID",
  "title": "章节标题",
  "content": "章节内容"
}
```

**成功响应**:
```json
{
  "success": true,
  "message": "章节添加成功",
  "chapter_id": "新章节ID"
}
```

**错误响应**:
```json
{
  "success": false,
  "message": "错误信息"
}
```

### 5. 按作者获取书籍

**GET 或 POST `/api/get-books-by-author`**

根据作者名称筛选书籍

**GET请求参数**:
- `author` (query参数): 作者名称

**POST请求体**:
```json
{
  "author": "Janson20"
}
```

**成功响应**:
```json
{
  "count": 1,
  "data": [
    {
      "author": "Janson20",
      "author_id": "068bc0c2-2f09-7789-8000-f672921eed70",
      "book_id": "068bbf8d-9ce0-72e5-8000-124f065499f3",
      "category": "默认",
      "cover": "images/log.jpeg",
      "desc": "这是净读的官方开发日志，记录了净读从无到有的开发过程。",
      "title": "净读开发日志"
    }
  ],
  "success": true
}
```

**无结果响应**:
```json
{
  "success": true,
  "data": [],
  "count": 0,
  "message": "未找到该作者的书籍"
}
```

### 6. 获取书籍详情

**GET 或 POST `/api/get-book-info`**

根据书籍ID获取书籍详细信息

**GET请求参数**:
- `book_id` (query参数): 书籍ID

**POST请求体**:
```json
{
  "book_id": "068bbf8d-9ce0-72e5-8000-124f065499f3"
}
```

**成功响应**:
```json
{
  "data": {
    "author": "Janson20",
    "author_id": "068bc0c2-2f09-7789-8000-f672921eed70",
    "book_id": "068bbf8d-9ce0-72e5-8000-124f065499f3",
    "category": "默认",
    "cover": "images/log.jpeg",
    "desc": "这是净读的官方开发日志，记录了净读从无到有的开发过程。",
    "title": "净读开发日志"
  },
  "success": true
}
```

**错误响应**:
```json
{
  "success": false,
  "message": "未找到书籍"
}
```

### 7. 获取书籍目录

**GET 或 POST `/api/get-book-catalog`**

根据书籍ID获取书籍目录

**GET请求参数**:
- `book_id` (query参数): 书籍ID

**POST请求体**:
```json
{
  "book_id": "068bbf8d-9ce0-72e5-8000-124f065499f3"
}
```

**成功响应**:
```json
{
  "data": [
    "v0.1",
    "v0.2",
    "v0.3",
    "v0.4",
    "v0.5",
    "v0.6",
    "v0.6.1",
    "v0.6.2",
    "上线说明",
    "v0.6.3",
    "v0.7.0-SNAPSHOT",
    "v0.7.1",
    "v0.7.2"
  ],
  "success": true
}
```

## 状态码说明

- `200`: 请求成功
- `400`: 请求参数错误
- `401`: 认证失败
- `500`: 服务器内部错误

## 使用示例

### JavaScript示例
```javascript
// 获取书籍列表
fetch('/api/get-books')
  .then(response => response.json())
  .then(data => console.log(data));

// 用户登录
fetch('/api/login', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    username: 'user123',
    password: 'password123'
  })
})
.then(response => response.json())
.then(data => {
  if (data.success) {
    localStorage.setItem('token', data.token);
  }
});
```

### Python示例
```python
import requests

# 获取书籍列表
response = requests.get('https://your-domain.com/api/get-books')
books = response.json()

# 用户登录
login_data = {
    'username': 'user123',
    'password': 'password123'
}
response = requests.post('https://your-domain.com/api/login', json=login_data)
result = response.json()
if result['success']:
    token = result['token']
```

## 页脚
> © 2025 - 现在 [JS20 Studio](https://js20studio.qzz.io/)
