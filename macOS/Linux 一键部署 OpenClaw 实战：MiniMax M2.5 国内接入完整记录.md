# macOS/Linux 一键部署 OpenClaw 实战：MiniMax M2.5 国内接入完整记录

> 从零开始，15 分钟搭建本地 AI 助手。Ubuntu 真实部署过程 + MiniMax CN API Key 配置全记录。

---

## 前言

担心 AI 工具上传代码到云端？想在服务器上部署自己的 AI 助手？

本文记录我在 Ubuntu 服务器上一键部署 OpenClaw 的完整过程，从安装到配置 MiniMax M2.5 国内模型，全程 15 分钟搞定。

**本文价值**:
- ✅ 真实环境实操（Ubuntu 20.04 + MiniMax CN）
- ✅ 完整命令行输出（可直接复制）
- ✅ 国内优化方案（API Key + CN endpoint）
- ✅ 常见问题预案（提前避坑）

---

## 一、准备工作

### 系统要求

| 配置项 | 我的环境 | 兼容范围 |
|--------|---------|---------|
| 操作系统 | Ubuntu 20.04 | macOS 10.15+ / Linux 各发行版 |
| 网络环境 | 国内直连 | 可访问 openclaw.ai |

**依赖说明**:
- ✅ Node.js（v18+）和 Git 会由安装脚本自动检测和安装
- ✅ 无需提前安装任何依赖，脚本会自动处理

### 获取 MiniMax API Key

这是**唯一需要提前准备**的内容：

1. 访问 https://platform.minimaxi.com/
2. 注册/登录账号
3. 进入 **API Keys** 页面
4. 点击"创建新密钥"
5. 复制并保存 API Key（格式：`sk-cp-...`）

> 💡 **提示**: 也可以不提前准备，在配置时再注册获取，但提前准备可以加快部署速度

---

## 二、一键部署全过程

### 执行安装命令

在终端执行：

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

### 安装过程实录

以下是完整的安装输出（我添加了关键步骤注释）：

```bash
╭───────────────────────────────────────────────────────────────╮
│                                                               │
│  🦞 OpenClaw Installer                                        │
│  Turning "I'll reply later" into "my bot replied instantly".  │
│  modern installer mode                                        │
│                                                               │
╰───────────────────────────────────────────────────────────────╯

✓ gum bootstrapped (temp, verified, v0.17.0)
✓ Detected: linux  # 👉 自动检测操作系统

Install plan

OS                  linux
Install method      npm
Requested version   latest
INFO Existing OpenClaw installation detected, upgrading  # 👉 检测到旧版本，自动升级

[1/3] Preparing environment

✓ Node.js v22.22.0 found  # 👉 确认 Node.js 版本符合要求

[2/3] Installing OpenClaw

✓ Git already installed
INFO Installing OpenClaw v2026.2.15  # 👉 当前最新版本
✓ OpenClaw npm package installed
✓ OpenClaw installed

[3/3] Finalizing setup

INFO Running doctor to migrate settings  # 👉 自动迁移旧配置
✓ Doctor complete

🦞 OpenClaw installed successfully (2026.2.15)!
Molting complete. Please don't look at my soft shell phase.
```

### 关键步骤解读

**1. 环境检测与自动配置**
- 自动检测 Node.js（v18+），如未安装会自动安装
- 自动检测 Git，如未安装会自动安装
- 无需手动干预，脚本全自动处理依赖

**2. 版本管理**
- 检测到旧版 OpenClaw 会自动升级
- 保留原有配置文件（自动备份）

**3. Doctor 诊断**
- 自动运行健康检查
- 迁移配置到新版本格式
- 检测系统环境和插件状态

### 安装后诊断

安装完成后会自动运行 `openclaw doctor`，输出系统状态：

```bash
INFO Running openclaw doctor

🦞 OpenClaw 2026.2.15 (3fe22ea) — Turning "I'll reply later" into "my bot replied instantly".

┌  OpenClaw doctor
│
◇  Security ─────────────────────────────────╮
│                                            │
│  - No channel security warnings detected.  │
│  - Run: openclaw security audit --deep     │
│                                            │
├────────────────────────────────────────────╯
│
◇  Skills status ────────────╮
│                            │
│  Eligible: 4               │  # 👉 可用的功能模块
│  Missing requirements: 45  │
│  Blocked by allowlist: 0   │
│                            │
├────────────────────────────╯
│
◇  Plugins ──────╮
│                │
│  Loaded: 4     │  # 👉 已加载插件数量
│  Disabled: 32  │
│  Errors: 0     │
│                │
├────────────────╯
│
└  Doctor complete.
```

**诊断信息说明**:
- **Security**: 安全状态检查
- **Skills**: 功能模块状态（部分需要额外依赖）
- **Plugins**: 插件加载情况

### Gateway 自动启动

诊断完成后，系统会自动重启 Gateway 服务：

```bash
INFO Gateway daemon detected; restarting
✓ Gateway restarted

🦞 OpenClaw 2026.2.15 (3fe22ea) — I read logs so you can keep pretending you don't have to.

Dashboard URL: http://127.0.0.1:18789/#token=ea710491e8584c3c41d73fb405201e68155af5ef6d50fe30
Copied to clipboard.
```

**远程访问提示**（如果在服务器上部署）:

```bash
No GUI detected. Open from your computer:
ssh -N -L 18789:127.0.0.1:18789 liuy@your-server-ip

Then open:
http://localhost:18789/
http://localhost:18789/#token=ea710491e8584c3c41d73fb405201e68155af5ef6d50fe30
```

> 💡 **提示**: 如果在远程服务器部署，可以通过 SSH 隧道访问 Web 界面

---

## 三、MiniMax M2.5 国内接入实战 🔥

### 初始化配置

运行配置向导：

```bash
openclaw onboard --install-daemon
```

### 配置流程实录

**第一步：安全声明确认**

```bash
◇  Security ──────────────────────────────────────────────────────────────────────────────╮
│                                                                                         │
│  Security warning — please read.                                                        │
│                                                                                         │
│  OpenClaw is a hobby project and still in beta. Expect sharp edges.                     │
│  This bot can read files and run actions if tools are enabled.                          │
│  A bad prompt can trick it into doing unsafe things.                                    │
│                                                                                         │
│  If you're not comfortable with basic security and access control, don't run OpenClaw.  │
│  Ask someone experienced to help before enabling tools or exposing it to the internet.  │
│                                                                                         │
├─────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  I understand this is powerful and inherently risky. Continue?
│  Yes  # 👉 选择 Yes 继续
```

**第二步：选择配置模式**

```bash
◇  Onboarding mode
│  QuickStart  # 👉 快速配置模式，推荐新手
```

**第三步：检测现有配置**

```bash
◇  Existing config detected ─────────╮
│                                    │
│  workspace: ~/.openclaw/workspace  │
│  model: minimax-cn/MiniMax-M2.5    │  # 👉 我之前配置过
│  gateway.mode: local               │
│  gateway.port: 18789               │
│  gateway.bind: loopback            │
│                                    │
├────────────────────────────────────╯
│
◇  Config handling
│  Update values  # 👉 更新配置（首次安装会跳过此步）
```

**第四步：Gateway 设置确认**

```bash
◇  QuickStart ─────────────────────────────╮
│                                          │
│  Keeping your current gateway settings:  │
│  Gateway port: 18789                     │
│  Gateway bind: Loopback (127.0.0.1)      │  # 👉 只允许本机访问
│  Gateway auth: Token (default)           │
│  Tailscale exposure: Off                 │
│  Direct to chat channels.                │
│                                          │
├──────────────────────────────────────────╯
```

**第五步：选择模型提供商** 🔥

```bash
◇  Model/auth provider
│  MiniMax  # 👉 选择 MiniMax（国内推荐）
```

### MiniMax API Key 配置 ⭐

**选择认证方式**:

```bash
◇  MiniMax auth method
│  MiniMax M2.5 (CN)  # 👉 选择国内节点 + API Key 方式
```

**输入 API Key**:

```bash
◇  Enter MiniMax China API key
│  sk-cp-pHv7rkK8w0B3_NEw9475Fipfs-1JDAdvN11gK6h-YlXj8Fn_rkWoKcx8auVuIqPZPcodAjSs_paji2UrW_hlPnXw8IELvdedG85LmoJXLDA4R4JHSGKEIy8
```

> 📌 **重要**: 粘贴 API Key 后按 Enter，不要手动输入（容易出错）

**确认默认模型**:

```bash
◇  Default model
│  Keep current (minimax-cn/MiniMax-M2.5)  # 👉 保持当前配置
```

### CN Endpoint 配置要点

**方式一：通过选择 "MiniMax M2.5 (CN)" 自动配置**（推荐）

如果在配置时选择了 "MiniMax M2.5 (CN)"，系统会自动设置正确的 CN endpoint，无需手动修改。

**方式二：手动配置**（高级用户）

如果需要手动修改配置文件 `~/.openclaw/openclaw.json`：

```json
{
  "models": {
    "providers": {
      "minimax": {
        "baseUrl": "https://api.minimaxi.com/anthropic"
      }
    }
  }
}
```

> 📌 **注意**: 是 `api.minimaxi.com`（有个 i），不是 `api.minimax.io`

### 跳过可选配置

**Channel 配置**（第三方平台集成）:

```bash
◇  Channel status ────────────────────────────╮
│                                             │
│  Telegram: not configured                   │
│  WhatsApp: not configured                   │
│  Discord: not configured                    │
│  ... (更多平台)                             │
│                                             │
├─────────────────────────────────────────────╯
│
◇  Select channel (QuickStart)
│  Skip for now  # 👉 暂时跳过，稍后可配置
```

**Skills 配置**:

```bash
◇  Skills status ─────────────╮
│                             │
│  Eligible: 4                │
│  Missing requirements: 38   │
│  Unsupported on this OS: 7  │
│  Blocked by allowlist: 0    │
│                             │
├─────────────────────────────╯
│
◇  Configure skills now? (recommended)
│  No  # 👉 暂时跳过，基础功能先跑通
```

**Hooks 配置**:

```bash
◇  Hooks ──────────────────────────────────────────────────────────╮
│                                                                  │
│  Hooks let you automate actions when agent commands are issued.  │
│  Example: Save session context to memory when you issue /new.    │
│                                                                  │
├──────────────────────────────────────────────────────────────────╯
│
◇  Enable hooks?
│  Skip for now  # 👉 稍后配置
```

### Gateway 服务启动

```bash
◇  Gateway service already installed
│  Restart  # 👉 重启服务应用新配置
│
◐  Restarting Gateway service…
Restarted systemd service: openclaw-gateway.service
◇  Gateway service restarted.
```

### 配置完成

```bash
◇  Control UI ─────────────────────────────────────────────────────────────────────╮
│                                                                                  │
│  Web UI: http://127.0.0.1:18789/                                                 │
│  Web UI (with token):                                                            │
│  http://127.0.0.1:18789/#token=ea710491e8584c3c41d73fb405201e68155af5ef6d50fe30  │
│  Gateway WS: ws://127.0.0.1:18789                                                │
│  Gateway: reachable                                                              │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────╯
```

---

## 四、首次启动与验证

### 启动 TUI 交互界面

配置完成后，系统会提示：

```bash
◇  How do you want to hatch your bot?
│  Hatch in TUI (recommended)  # 👉 选择在 TUI 中启动
```

自动进入 TUI 界面：

```bash
openclaw tui - ws://127.0.0.1:18789 - agent main - session main

session agent:main:main
```

界面底部会显示连接状态：

```text
connected | idle
agent main | session main (openclaw-tui) | minimax-cn/MiniMax-M2.5 | think low | tokens 0k/200k (0%)
```

**状态栏说明**:
- **connected**: 与 Gateway 连接状态
- **idle**: 当前状态（空闲）
- **minimax-cn/MiniMax-M2.5**: 正在使用的模型
- **tokens 0k/200k**: Token 使用情况

### 基础对话测试

从我的实际测试记录：

**测试 1：中文对话**

```text
你好
```

**AI 回复**:
```text
你好！👋

看起来这是个全新的开始 — 我刚上线，记忆还是空白的。

你是谁？我又该叫什么名字呢？一起聊聊看吧！
```

**测试 2：英文对话**

```text
Wake up, my friend!
```

**AI 回复**:
```text
Hey! 💫 I just came online — fresh workspace, clean slate. Looks like this is our first chat.

Who am I? Who are you? Let's figure that out together.

What should I call you — and what do you want to call me?
```

**测试 3：模型识别**

```text
你是什么模型
```

**AI 回复**:
```text
我是 MiniMax-M2.5 模型 🧠

运行在 MiniMax-CN 上。有什么我可以帮你的吗？
```

### 验证成功标志

看到状态栏显示以下信息，说明配置成功：

```text
connected | idle
agent main | session main (openclaw-tui) | minimax-cn/MiniMax-M2.5 | think low | tokens 14k/200k (7%)
```

**验证清单**:

| 验证项 | 测试命令 | 预期结果 | 状态 |
|--------|---------|---------|------|
| 连接状态 | 查看状态栏左侧 | `connected` | ✅ |
| 模型识别 | `你是什么模型` | 回复 MiniMax-M2.5 | ✅ |
| 中文对话 | `你好` | 正常中文回复 | ✅ |
| 英文对话 | `Hello` | 正常英文回复 | ✅ |
| Token 统计 | 查看状态栏右侧 | 显示使用量 | ✅ |

**退出 TUI**：按 `Ctrl+C` 或输入 `/exit`

---

## 五、国内环境优化建议

### npm 镜像配置

如果使用 npm 安装方式，建议配置国内镜像：

```bash
# 安装时指定镜像
npm install -g openclaw --registry=https://registry.npmmirror.com

# 或全局配置镜像
npm config set registry https://registry.npmmirror.com
```

### Gateway 后台运行

**使用 systemd 管理**（推荐，Linux 系统）:

配置向导会自动设置 systemd 服务：

```bash
# 查看服务状态
systemctl --user status openclaw-gateway

# 启动服务
systemctl --user start openclaw-gateway

# 停止服务
systemctl --user stop openclaw-gateway

# 开机自启
systemctl --user enable openclaw-gateway
```

**使用 pm2 管理**（跨平台）:

```bash
# 安装 pm2
npm install -g pm2

# 启动 Gateway
pm2 start "openclaw gateway run" --name openclaw-gateway

# 查看状态
pm2 status

# 查看日志
pm2 logs openclaw-gateway

# 开机自启
pm2 startup
pm2 save
```

### 网络问题处理

**问题 1**: 安装脚本下载失败

**解决方案**:
```bash
# 改用 npm 安装
npm install -g openclaw --registry=https://registry.npmmirror.com
```

**问题 2**: Gateway 启动失败

**排查步骤**:
```bash
# 检查端口占用
lsof -i :18789

# 查看日志
openclaw gateway run --verbose

# 重新生成配置
openclaw onboard --install-daemon
```

---

## 六、可能遇到的问题

### 安装失败

**问题 1**: 执行安装脚本时提示网络错误

**原因**: 脚本服务器访问受限

**解决方案**:
```bash
# 方案 1：使用 npm 安装
npm install -g openclaw --registry=https://registry.npmmirror.com

# 方案 2：使用代理
export http_proxy=http://your-proxy:port
export https_proxy=http://your-proxy:port
curl -fsSL https://openclaw.ai/install.sh | bash
```

**问题 2**: 权限不足（Permission denied）

**解决方案**:

```bash
# 使用 sudo 权限安装
sudo npm install -g openclaw --registry=https://registry.npmmirror.com
```

### 配置错误

**问题 1**: API Key 无效

**现象**:
```bash
Error: Invalid API key
```

**解决方案**:
1. 检查 API Key 是否正确（去掉多余的空格、换行）
2. 确认选择了 "MiniMax M2.5 (CN)" 而非其他选项
3. 重新运行配置：
   ```bash
   openclaw onboard --install-daemon
   ```

**问题 2**: CN endpoint 配置错误

**现象**: 调用 API 时提示 404 或网络错误

**解决方案**:

检查配置文件 `~/.openclaw/openclaw.json`：

```bash
# 查看配置
cat ~/.openclaw/openclaw.json | grep baseUrl
```

确认是：
```json
"baseUrl": "https://api.minimaxi.com/anthropic"
```

如果不对，手动修改：
```bash
nano ~/.openclaw/openclaw.json
```

或通过 Web 界面修改（推荐）:
1. 访问 `http://127.0.0.1:18789`
2. 进入 **Config** → **models** 栏目
3. 修改 `baseUrl` 为 `https://api.minimaxi.com/anthropic`
4. 点击 **Save**，然后点击 **Update**

### 运行错误

**问题 1**: 端口占用

**现象**:
```bash
Error: Port 18789 already in use
```

**解决方案**:
```bash
# 查找占用端口的进程
lsof -i :18789

# 杀掉进程（替换 PID）
kill -9 <PID>

# 或修改端口
openclaw config set gateway.port 18790
```

**问题 2**: TUI 无法连接

**现象**: TUI 启动后显示 `disconnected`

**排查步骤**:
```bash
# 1. 检查 Gateway 是否运行
ps aux | grep openclaw

# 2. 手动启动 Gateway
openclaw gateway run

# 3. 检查防火墙
# Linux
sudo ufw status
sudo ufw allow 18789

# macOS
# 系统设置 → 安全性与隐私 → 防火墙
```

### 配置文件位置

如需手动编辑配置：

```bash
# 配置文件路径
~/.openclaw/openclaw.json

# 工作空间
~/.openclaw/workspace

# 会话存储
~/.openclaw/agents/main/sessions/sessions.json
```

编辑配置文件：
```bash
nano ~/.openclaw/openclaw.json
```

### 卸载方法

**步骤 1**: 停止服务

```bash
# 停止 systemd 服务（Linux）
systemctl --user stop openclaw-gateway

# 或停止 pm2 服务
pm2 stop openclaw-gateway
pm2 delete openclaw-gateway
```

**步骤 2**: 卸载程序

```bash
npm uninstall -g openclaw
```

**步骤 3**（可选）: 删除数据

> ⚠️ 此操作会删除所有配置和对话历史，请谨慎执行

```bash
rm -rf ~/.openclaw
```

---

## 七、进阶使用技巧

### Hooks 自动化配置

Hooks 可以在执行特定命令时自动触发操作。

**示例：保存会话记忆**

编辑配置文件 `~/.openclaw/openclaw.json`，添加：

```json
{
  "hooks": {
    "session-memory": {
      "enabled": true,
      "events": ["session:new"],
      "actions": ["memory:save"]
    }
  }
}
```

**效果**: 执行 `/new` 创建新会话时，自动保存当前会话上下文到记忆。

**示例：命令日志记录**

```json
{
  "hooks": {
    "command-logger": {
      "enabled": true,
      "events": ["command:*"],
      "actions": ["log:file"]
    }
  }
}
```

**效果**: 所有命令都会记录到日志文件。

### Skills 功能启用

Skills 是 OpenClaw 的功能扩展模块。

**查看可用 Skills**:

```bash
openclaw doctor
```

在输出中找到 **Skills status** 部分：

```text
◇  Skills status ────────────╮
│                            │
│  Eligible: 4               │  # 可直接使用
│  Missing requirements: 38  │  # 需要安装依赖
│  Blocked by allowlist: 0   │
│                            │
├────────────────────────────╯
```

**启用 Skill**（以 `web-search` 为例）:

```bash
# 查看 Skill 详情
openclaw skill info web-search

# 启用 Skill
openclaw skill enable web-search
```

**常用 Skills**:
- `web-search`: 网页搜索
- `code-review`: 代码审查
- `file-ops`: 文件操作
- `terminal`: 终端命令执行

### 多 Agent 配置

OpenClaw 支持多个独立的 Agent，每个有独立的配置和记忆。

**创建新 Agent**:

```bash
openclaw agent create coding --model minimax-cn/MiniMax-M2.5
```

**切换 Agent**:

```bash
openclaw tui --agent coding
```

**使用场景**:
- **main**: 日常对话
- **coding**: 代码开发
- **writing**: 文档写作
- **research**: 资料研究

每个 Agent 独立记忆，互不干扰。

---

## 八、结语

OpenClaw 让 AI 助手回归本质：**你的数据，你做主**。

通过本文的实战记录，你应该已经成功部署了 OpenClaw + MiniMax M2.5 的本地 AI 助手。无论是处理敏感文件、管理项目代码，还是集成个人工作流，OpenClaw 都能提供完全可控的 AI 能力。

**"AI 不该只存在于云端，你的数据你做主"**

---

## 🎁 免费体验福利

想快速体验 OpenClaw + MiniMax 的强大功能？

**关注本公众号，回复「MiniMax API Key」，即可获取临时测试密钥！**

使用临时 API Key 可以：
- ✅ 快速体验 OpenClaw 的核心功能
- ✅ 测试 MiniMax M2.5 模型能力
- ✅ 无需立即注册 MiniMax 账号

> 💡 临时密钥有效期 7 天，每日有调用次数限制。如需长期使用，建议前往 [MiniMax 平台](https://platform.minimaxi.com/) 注册账号获取正式 API Key。

---

## 相关链接

> 💡 微信内无法直接点击链接，请长按复制到浏览器打开

**OpenClaw 官方资源**
```
官网：https://openclaw.ai/
文档：https://docs.openclaw.ai/
```

**MiniMax 平台**
```
配置指南：https://platform.minimaxi.com/document/OpenClaw
获取 API Key：https://platform.minimaxi.com/
```

**其他 AI 平台**
```
Claude API Key：https://console.claude.com/
OpenAI API Key：https://platform.openai.com/
```
