# 🧠 DeepSeek for Paper
### _(Published on Hangar, Modrinth & BBSMC!)_
[![DeepSeekForPaper](https://img.shields.io/hangar/dt/DeepSeekForPaper?link=https%3A%2F%2Fhangar.papermc.io%2Fjanson20%2FDeepSeekForPaper&style=for-the-badge)](https://hangar.papermc.io/janson20/DeepSeekForPaper)
[![DeepSeekForPaper](https://img.shields.io/hangar/stars/DeepSeekForPaper?link=https%3A%2F%2Fhangar.papermc.io%2Fjanson20%2FDeepSeekForPaper&style=for-the-badge)](https://hangar.papermc.io/janson20/DeepSeekForPaper)
[![DeepSeekForPaper](https://img.shields.io/hangar/views/DeepSeekForPaper?link=https%3A%2F%2Fhangar.papermc.io%2Fjanson20%2FDeepSeekForPaper&style=for-the-badge)](https://hangar.papermc.io/janson20/DeepSeekForPaper)
[![PaperMC](https://img.shields.io/badge/Server-Paper%201.20--1.21-brightgreen?style=for-the-badge)](https://papermc.io)
[![Java](https://img.shields.io/badge/Java-17%2B-blue?style=for-the-badge)](https://adoptium.net/)
# English
> 💬 Integrate DeepSeek AI into Your Minecraft Server — Ask questions, generate commands, and execute with a click, directly in chat!

---

## ✨ Introduction

**DeepSeek for Paper** is an intelligent chat and command generation plugin that integrates the **DeepSeek AI model**. It allows players to ask the AI questions directly in the game or request it to generate Minecraft commands, which can then be executed with **a single click on the chat message**.

* 💬 AI Q&A: Use `/askai` to chat with DeepSeek
* 🧠 Command Generation: Use `/askcmd` to generate operational commands
* ⚙️ One-Click Execution: Run commands directly by clicking the chat message
* 🧩 No external libraries required, works out-of-the-box

---

## 🪄 Feature Demo

> Player input:

```
/askcmd Give me a diamond sword
```

> AI response:

```
💡 AI Suggested Command: /give @p diamond_sword 1
✨ [Click to Execute this Command]
```

After the player clicks the green prompt, the command will be executed with the current permissions.

---

## ⚙️ Installation Guide

1. Place `DeepSeekForPaper.jar` into your server's `plugins/` folder
2. Start the server once to generate the configuration file
3. Edit `plugins/DeepSeekForPaper/config.yml`:

   ```yaml
   api-key: "Your DeepSeek API Key"
   api-url: "https://api.deepseek.com/chat/completions"
   ```
4. Restart the server and it's ready to use!

---

## 🧩 Available Commands

| Command               | Description                 |
| --------------------- | --------------------------- |
| `/askai <question>`   | Ask a question to DeepSeek |
| `/askcmd <command description>` | Let AI generate corresponding commands |
| `/acceptcmd`          | Execute the last generated command (current player only) |

---

## 🛡️ Permissions

| Permission Node       | Description           | Default     |
| --------------------- | --------------------- | ----------- |
| `deepseek.ask`        | Use `/askai`          | ✅ All players |
| `deepseek.cmd`        | Use `/askcmd`         | ✅ All players |
| `deepseek.accept`     | Execute AI-generated commands | ✅ All players |

---

## ⚙️ Technical Features

* Asynchronous API calls (non-blocking main thread)
* Uses Adventure API to build clickable messages
* Automatically packages DeepSeek JSON communication

---

## 👨💻 Developer Information

* **Author:** Janson20
* **Plugin ID:** `DeepSeekForPaper`
* **Package:** `net.jason.dfp`

---

## 💬 Feedback Welcome

* 🐛 Report bugs or suggest features
* ❤️ Make your server smarter!

---
# 简体中文
> 💬 让你的 Minecraft 服务器接入 DeepSeek AI —— 直接在聊天中提问、生成命令、点击执行！

---

## ✨ 简介

**DeepSeek for Paper** 是一款集成 **DeepSeek AI 模型** 的智能聊天与命令生成插件。
它让玩家可以直接在游戏中向 AI 提问，或请求 AI 生成 Minecraft 指令，并通过 **点击消息** 一键执行。

* 💬 AI 问答：输入 `/askai` 即可与 DeepSeek 对话
* 🧠 命令生成：输入 `/askcmd` 生成操作指令
* ⚙️ 一键执行：点击聊天消息直接运行
* 🧩 无需外部库，开箱即用

---

## 🪄 功能演示

> 玩家输入：

```
/askcmd 给我一把钻石剑
```

> AI 回复：

```
💡 AI 建议的命令：/give @p diamond_sword 1
✨ [点击执行此命令]
```

玩家点击绿色提示后，命令会自动以当前权限执行。

---

## ⚙️ 安装指南

1. 将 `DeepSeekForPaper.jar` 放入服务器的 `plugins/` 文件夹
2. 启动服务器一次，生成配置文件
3. 编辑 `plugins/DeepSeekForPaper/config.yml`：

   ```yaml
   api-key: "你的DeepSeek API密钥"
   api-url: "https://api.deepseek.com/chat/completions"
   ```
4. 重启服务器即可使用！

---

## 🧩 可用指令

| 指令               | 说明                 |
| ---------------- | ------------------ |
| `/askai <问题>`    | 向 DeepSeek 提问      |
| `/askcmd <命令描述>` | 让 AI 生成对应命令        |
| `/acceptcmd`     | 执行上一次生成的命令（仅限当前玩家） |

---

## 🛡️ 权限

| 权限节点              | 说明           | 默认     |
| ----------------- | ------------ | ------ |
| `deepseek.ask`    | 使用 `/askai`  | ✅ 所有玩家 |
| `deepseek.cmd`    | 使用 `/askcmd` | ✅ 所有玩家 |
| `deepseek.accept` | 执行 AI 生成的命令  | ✅ 所有玩家 |

---

## ⚙️ 技术特性

* 异步 API 调用（不阻塞主线程）
* 使用 Adventure API 构建点击消息
* 自动封装 DeepSeek JSON 通信

---


## 👨‍💻 开发者信息

* **作者:** Janson20
* **插件 ID:** `DeepSeekForPaper`
* **包名:** `net.jason.dfp`

---

## 💬 欢迎反馈

* 🐛 提交 Bug 或功能建议
* ❤️ 让你的服务器更智能！
