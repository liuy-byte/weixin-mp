# OpenClaw 一键部署指南

> 担心 AI 工具上传敏感数据到云端？希望完全掌控自己的 AI 助手？OpenClaw 提供了一个开源的个人 AI 助手框架，强调数据本地化和完全可控，支持一键部署快速上手。

---

## 一、准备工作

### 系统要求

| 操作系统 | 最低要求 |
|---------|---------|
| macOS | 10.15+ |
| Windows | 10/11 |
| Linux | Ubuntu 20.04+ / Debian 10+ |

### 必需软件

**Node.js 18+**

推荐使用 fnm 管理 Node.js 版本：

```bash
# 安装 LTS 版本
fnm install --lts
fnm use lts-latest
```

> 💡 如需 fnm 详细安装步骤，可参考 [fnm 安装指南](./fnm-安装指南.md)

**API Key（至少一个）**

OpenClaw 支持多个 AI 提供商，选择其中一个获取 API Key：

| 提供商 | 获取地址 | 说明 |
|--------|---------|------|
| Claude | https://console.anthropic.com/ | 推荐，能力强大 |
| OpenAI | https://platform.openai.com/ | 通用选择 |
| MiniMax | https://minimaxi.com | 国内可用 |

---

## 二、一键部署（推荐）⭐

这是最简单的部署方式，适合所有用户。

### macOS / Linux

```bash
# 执行安装脚本
curl -fsSL https://openclaw.ai/install.sh | bash
```

### Windows

```powershell
# PowerShell 中执行
irm https://openclaw.ai/install.ps1 | iex
```

### 初始化配置

安装完成后，运行初始化向导：

```bash
# 启动配置向导
openclaw onboard
```

向导会引导你完成以下配置：
1. **选择 AI 提供商**（Claude / OpenAI / MiniMax 等）
2. **输入 API Key**（粘贴从上述平台获取的密钥）
3. **设置数据存储位置**（默认 `~/.openclaw`）
4. **配置伴侣应用**（macOS 可选，增强系统集成）

### 启动服务

```bash
# 启动 OpenClaw
openclaw start
```

启动成功后，终端会显示：

```
✅ OpenClaw is running on http://localhost:3000
```

### 快速验证

在浏览器打开 `http://localhost:3000`，输入以下测试命令：

```text
帮我创建一个 hello.txt 文件，内容是 "Hello OpenClaw"
```

如果文件创建成功，说明部署完成！🚀

---

## 三、npm 全局安装（备选）

**适合场景**：熟悉 npm 的开发者，国内用户可使用镜像加速

```bash
# 使用国内镜像安装
npm install -g openclaw --registry=https://registry.npmmirror.com

# 安装完成后初始化
openclaw onboard

# 启动服务
openclaw start
```

---

## 四、核心功能使用

### 文件操作

```text
创建一个 todo.md 文件，列出今天的任务清单
```

```text
读取 package.json 的内容并解释依赖项
```

```text
把 config.json 中的端口号改为 8080
```

### 浏览网页

```text
访问 https://news.ycombinator.com 并总结今天的热门话题
```

```text
搜索 "OpenClaw 使用教程" 并整理关键要点
```

### 执行命令

```text
帮我提交代码，commit 信息是 "feat: 添加用户认证模块"
```

```text
运行 npm test 并分析测试失败的原因
```

### 持久化记忆

OpenClaw 会记住对话历史和上下文，重启后仍能继续之前的任务：

```text
帮我分析这个项目的架构
```

重启后继续：

```text
上次你分析的项目，能帮我重构路由模块吗？
```

### 第三方平台集成

OpenClaw 支持 30+ 平台集成：

| 平台类型 | 支持平台 |
|---------|---------|
| 即时通讯 | WhatsApp、Telegram、Slack、Discord |
| 邮件 | Gmail、Outlook |
| 笔记 | Notion、Obsidian、Logseq |
| 项目管理 | Jira、Trello、Asana |
| 代码托管 | GitHub、GitLab |

配置方式：在 Web 界面的 Settings > Integrations 中启用对应平台。

---

## 五、常见问题

### 安装失败

**问题 1**：执行安装脚本时提示网络错误

**解决方案**：改用 npm 安装方式（支持国内镜像）

```bash
npm install -g openclaw --registry=https://registry.npmmirror.com
```

**问题 2**：权限不足（Permission denied）

**解决方案**：

macOS/Linux 系统：
```bash
# 使用 sudo 权限安装
sudo npm install -g openclaw --registry=https://registry.npmmirror.com
```

Windows 系统：以管理员身份运行 PowerShell

### API Key 配置错误

**问题**：启动时提示 "Invalid API Key"

**解决方案**：
1. 检查 API Key 是否正确（去掉多余的空格）
2. 确认提供商选择正确（Claude 的 Key 不能用于 OpenAI）
3. 重新运行配置向导：
```bash
openclaw config --reset
openclaw onboard
```

### macOS 伴侣应用问题

**问题**：macOS 提示"无法打开未经验证的开发者应用"

**解决方案**：

1. 打开**系统设置**
2. 进入**隐私与安全性**
3. 找到"允许从以下位置下载的应用"
4. 选择"App Store 和已认可的开发者"
5. 如仍被拦截，点击"仍要打开"按钮

### 卸载方法

**步骤 1**：停止服务

```bash
openclaw stop
```

**步骤 2**：卸载程序

```bash
npm uninstall -g openclaw
```

**步骤 3**（可选）：删除数据

> ⚠️ 此操作会删除所有配置和对话历史，请谨慎执行

```bash
rm -rf ~/.openclaw
```

---

## 六、为什么选择 OpenClaw

### 云端 AI 工具 vs OpenClaw

| 维度 | 云端工具 | OpenClaw |
|-----|---------|----------|
| 数据隐私 | ❌ 数据上传到云端 | ✅ 完全本地处理 |
| 联网要求 | ✅ 必须联网 | ✅ 可离线（本地模型） |
| 定制能力 | ❌ 功能受限 | ✅ 开源可定制 |
| 成本 | 💰 订阅费（月付/年付） | 💰 API 费用可控 |
| 平台集成 | ❌ 有限平台 | ✅ 30+ 平台支持 |
| 响应速度 | ⚡ 依赖服务器 | ⚡ 本地处理更快 |

### 核心优势

✅ **数据主权**：所有数据存储在本地，不上传到任何云端服务器
✅ **完全透明**：开源代码，可审计每一行逻辑
✅ **灵活集成**：支持多种 AI 模型和第三方平台
✅ **成本可控**：仅支付 API 调用费用，无订阅费
✅ **离线可用**：支持本地模型（Ollama），无需联网

---

## 七、结语

OpenClaw 让 AI 助手回归本质：**你的数据，你做主**。

无论是处理敏感文件、管理项目代码，还是集成个人工作流，OpenClaw 都能提供完全可控的 AI 能力。一键部署，5 分钟上手，开启属于你的本地 AI 助手之旅。

**"AI 不该只存在于云端，你的数据你做主"**

---

## 相关链接

- [官网](https://openclaw.ai/) | [GitHub](https://github.com/openclaw/openclaw)
- [文档](https://openclaw.ai/docs) | [社区](https://openclaw.ai/community)
- [API Key 获取](https://console.anthropic.com/) | [MiniMax（国内）](https://minimaxi.com)
