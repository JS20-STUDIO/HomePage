### **净读 API 文档**
- 请求地址：`https://jingdu.qzz.io/api`

#### **1. 获取书籍列表 (`/api/get-books`)**
- **描述**：获取系统中的书籍列表，支持分页和分类筛选。
- **请求方法**：`GET`
- **响应示例**：
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
- **错误响应**：
  ```json
  {
    "success": false,
    "message": "分类不存在"
  }
  ```

---

#### **2. 用户登录 (`/api/login`)**
- **描述**：用户通过用户名和密码登录系统。
- **请求方法**：`POST`
- **请求参数**：
  - `username` (必填, str): 用户名。
  - `password` (必填, str): 密码。
- **请求示例**：
  ```json
  {
    "username": "user123",
    "password": "password123"
  }
  ```
- **响应示例**：
  ```json
  {
    "success": true,
    "auth": "ok",
    "message": "登录成功",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "user": "user123",
    "uuid": "00000000-0000-0000-0000-000000000000"
  }
  ```
- **错误响应**：
  ```json
  {
    "success": false,
    "message": "用户名或密码错误"
  }
  ```

---

#### **3. 添加章节 (`/api/add-chapter`)**
- **描述**：为指定书籍添加新章节。
- **请求方法**：`POST`
- **请求参数**：
  - `token` (必填, str): 从`/api/login`获取的登录token。
  - `book_id` (必填, str): 书籍的唯一标识符。
  - `title` (必填, str): 章节标题。
  - `content` (必填, str): 章节内容。
- **请求示例**：
  ```json
  {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "book_id": "00000000-0000-0000-0000-000000000000",
    "title": "第一章",
    "content": "这是第一章的内容..."
  }
  ```
- **响应示例**：
  ```json
  {
    "success": true,
    "message": "章节添加成功",
    "chapter_id": 1
  }
  ```
- **错误响应**：
  ```json
  {
    "success": false,
    "message": "未找到书籍"
  }
  ```

---

### **通用说明**
- **认证**：部分接口（如 `/api/add-chapter`）需要提供有效的 `token`（通过登录接口获取）。
- **响应状态码**：
  - `200`: 请求成功。
  - `400`: 请求参数错误。
  - `401`: 未授权。
  - `404`: 资源不存在。
  - `500`: 服务器内部错误。
