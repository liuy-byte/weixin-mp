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
      "im:message",
      "im:message:send_as_bot",
      "im:message:readonly",
      "im:message.p2p_msg:readonly",
      "im:message.group_at_msg:readonly",
      "im:chat.access_event.bot_p2p_chat:read",
      "im:chat.members:bot_access",
      "im:resource",
      "contact:user.employee_id:readonly",
      "application:bot.menu:write"
    ],
    "user": [
      "im:chat.access_event.bot_p2p_chat:read"
    ]
  }
}
```

保留完整权限列表，避免后续补权报错。

---

## 三、获取凭证

在「凭证与基础信息」页面复制：

- **App ID**：形如 `cli_xxxxxxxxxxxxx`
- **App Secret**：一串加密字符

两个值后续配置 OpenClaw 时需要用到。

---

## 四、OpenClaw 端安装并配置飞书插件

```bash
# 安装飞书通道插件
openclaw skills install feishu

# 填入凭证
openclaw config set plugins.feishu.appId "你的AppID"
openclaw config set plugins.feishu.appSecret "你的AppSecret"

# 重启网关使配置生效
openclaw gateway restart
```

---

## 五、飞书开放平台发布机器人

回到飞书开放平台，创建版本：

- 填写版本号和更新日志
- 选择可用范围（自己 / 特定群组 / 全员）
- 点击发布

个人版自建应用提交后直接上线，无需审核。

---

## 六、完成配对审批

在飞书中找到刚发布的机器人，发送任意消息，终端会出现配对码（Pairing Code），执行：

```bash
openclaw pairing approve feishu 配对码
```

---

## 七、验证对话

飞书内再次向机器人发消息，收到 AI 回复即表示对接成功。

---

## 常见问题

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
| 安装飞书插件 | `openclaw skills install feishu` |
| 配置 App ID | `openclaw config set plugins.feishu.appId "xxx"` |
| 配置 App Secret | `openclaw config set plugins.feishu.appSecret "xxx"` |
| 配对审批 | `openclaw pairing approve feishu 配对码` |
| 重启网关 | `openclaw gateway restart` |

---

飞书接入最容易卡在事件订阅和插件配置两处，按上面步骤走一遍，基本不会绕路。

---

## 相关链接

微信内长按复制链接到浏览器打开。

**OpenClaw**
```
官网：https://openclaw.ai/
飞书开放平台：https://open.feishu.cn/app
```
