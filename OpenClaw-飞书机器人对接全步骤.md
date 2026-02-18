# OpenClaw｜飞书机器人对接全步骤，7步跑通

> 装好了 OpenClaw，飞书接入却卡在权限配置和事件订阅？这里是从建应用到机器人响应的完整路径，照着做不绕弯。

## 前置条件

| 条件 | 说明 |
|------|------|
| OpenClaw 已安装并可正常启动 | 执行 `openclaw --version` 能返回版本号 |
| 飞书企业管理员权限 | 或有权限在飞书开放平台创建自建应用 |

---

## 一、飞书开放平台创建自建应用

访问 open.feishu.cn，登录飞书账号，点击「创建自建应用」，按下表填写：

| 配置项 | 推荐值 |
|--------|--------|
| 应用名称 | OpenClaw |
| 应用描述 | 个人专属 AI 智能助手 |
| 应用类型 | 机器人应用 |

---

## 二、配置应用权限（批量导入）

侧边栏「权限管理」→「批量导入」，粘贴以下 JSON 后确认开通：

```json
{
  "scopes": {
    "tenant": [
      "aily:file:read", "aily:file:write",
      "application:application.app_message_stats.overview:readonly",
      "application:application:self_manage",
      "application:bot.menu:write", "cardkit:card:write",
      "contact:user.employee_id:readonly",
      "corehr:file:download", "docs:document.content:read",
      "event:ip_list", "im:chat",
      "im:chat.access_event.bot_p2p_chat:read",
      "im:chat.members:bot_access", "im:message",
      "im:message.group_at_msg:readonly",
      "im:message.group_msg",
      "im:message.p2p_msg:readonly",
      "im:message:readonly", "im:message:send_as_bot",
      "im:resource", "sheets:spreadsheet",
      "wiki:wiki:readonly"
    ],
    "user": [
      "aily:file:read", "aily:file:write",
      "im:chat.access_event.bot_p2p_chat:read"
    ]
  }
}
```

---

## 三、配置事件订阅

侧边栏「事件与回调」→「事件订阅」：

- 加密策略：**长连接模式**
- 订阅事件：搜索并添加 `im.message.receive_v1`（接收消息）

事件订阅缺失是飞书机器人无响应最常见的原因之一。

---

## 四、获取凭证

在「凭证与基础信息」页面复制：

- **App ID**：形如 `cli_xxxxxxxxxxxxx`
- **App Secret**：一串加密字符

---

## 五、OpenClaw 端安装并配置飞书插件

```bash
# 安装飞书通道插件
openclaw plugins install @openclaw/feishu

# 交互式添加飞书频道，按提示输入 App ID 和 App Secret
openclaw channels add

# 重启网关使配置生效
openclaw gateway restart
```

---

## 六、飞书开放平台发布机器人

回到飞书开放平台，创建版本：

- 填写版本号和更新日志
- 选择可用范围（自己 / 特定群组 / 全员）
- 点击发布

个人版自建应用提交后直接上线，无需审核。

---

## 七、完成配对并验证

在飞书中找到刚发布的机器人，发送任意消息，终端会出现配对码（Pairing Code），执行：

```bash
openclaw pairing approve feishu 配对码
```

再次向机器人发消息，收到 AI 回复即表示对接成功。

---

## 常见问题

**❌ 机器人无响应（无报错）**

检查事件订阅是否已添加 `im.message.receive_v1`，以及是否选择了**长连接模式**。

**❌ duplicate plugin id detected（插件重复加载）**

原因：飞书插件同时存在于全局路径和用户配置路径。

```bash
# 删除重复插件，重启服务
rm -rf ~/.openclaw/extensions/feishu
openclaw gateway restart
```

**❌ Cannot find module 'zod'（Zod 依赖缺失）**

```bash
npm install -g zod
openclaw gateway restart
```

---

## 命令速查

| 操作 | 命令 |
|------|------|
| 安装飞书插件 | `openclaw plugins install @openclaw/feishu` |
| 添加飞书频道 | `openclaw channels add` |
| 配对审批 | `openclaw pairing approve feishu 配对码` |
| 重启网关 | `openclaw gateway restart` |
| 查看网关状态 | `openclaw gateway status` |
| 实时日志 | `openclaw logs --follow` |

---

飞书接入最容易卡在事件订阅和插件配置两处，按上面步骤走一遍，基本不会绕路。

---

## 相关链接

微信内长按复制链接到浏览器打开。

**OpenClaw**
```
官网：https://openclaw.ai/
飞书对接文档：https://docs.openclaw.ai/zh-CN/channels/feishu
飞书开放平台：https://open.feishu.cn/app
```
