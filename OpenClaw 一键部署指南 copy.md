macOS/Linux Quick Start 全记录

```bash
liuy@ubuntu:~$ curl -fsSL https://openclaw.ai/install.sh | bash
╭───────────────────────────────────────────────────────────────╮
│                                                               │
│  🦞 OpenClaw Installer                                        │
│  Turning "I'll reply later" into "my bot replied instantly".  │
│  modern installer mode                                        │
│                                                               │
╰───────────────────────────────────────────────────────────────╯

✓ gum bootstrapped (temp, verified, v0.17.0)
✓ Detected: linux

Install plan

OS                  linux
Install method      npm
Requested version   latest
INFO Existing OpenClaw installation detected, upgrading

[1/3] Preparing environment

✓ Node.js v22.22.0 found

[2/3] Installing OpenClaw

✓ Git already installed
INFO Installing OpenClaw v2026.2.15
✓ OpenClaw npm package installed
✓ OpenClaw installed

[3/3] Finalizing setup

INFO Running doctor to migrate settings
✓ Doctor complete

🦞 OpenClaw installed successfully (2026.2.15)!
Molting complete. Please don't look at my soft shell phase.

INFO Upgrade complete
INFO Running openclaw doctor

🦞 OpenClaw 2026.2.15 (3fe22ea) — Turning "I'll reply later" into "my bot replied instantly".

▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
██░▄▄▄░██░▄▄░██░▄▄▄██░▀██░██░▄▄▀██░████░▄▄▀██░███░██
██░███░██░▀▀░██░▄▄▄██░█░█░██░█████░████░▀▀░██░█░█░██
██░▀▀▀░██░█████░▀▀▀██░██▄░██░▀▀▄██░▀▀░█░██░██▄▀▄▀▄██
▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀
                  🦞 OPENCLAW 🦞

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
│  Eligible: 4               │
│  Missing requirements: 45  │
│  Blocked by allowlist: 0   │
│                            │
├────────────────────────────╯
│
◇  Plugins ──────╮
│                │
│  Loaded: 4     │
│  Disabled: 32  │
│  Errors: 0     │
│                │
├────────────────╯
│
◇  Memory search ───────────────────────────────────────────────────────────────────────────╮
│                                                                                           │
│  Memory search is enabled but no embedding provider is configured.                        │
│  Semantic recall will not work without an embedding provider.                             │
│                                                                                           │
│  Fix (pick one):                                                                          │
│  - Set OPENAI_API_KEY or GEMINI_API_KEY in your environment                               │
│  - Add credentials: openclaw auth add --provider openai                                   │
│  - For local embeddings: configure agents.defaults.memorySearch.provider and local model  │
│    path                                                                                   │
│  - To disable: openclaw config set agents.defaults.memorySearch.enabled false             │
│                                                                                           │
│  Verify: openclaw memory status --deep                                                    │
│                                                                                           │
├───────────────────────────────────────────────────────────────────────────────────────────╯
│
◇
Agents: main (default)
Heartbeat interval: 30m (main)
Session store (main): /home/liuy/.openclaw/agents/main/sessions/sessions.json (1 entries)
- agent:main:main (2060m ago)
Run "openclaw doctor --fix" to apply changes.
│
└  Doctor complete.

INFO Updating plugins
No npm-installed plugins to update.
INFO Gateway daemon detected; restarting
✓ Gateway restarted

🦞 OpenClaw 2026.2.15 (3fe22ea) — I read logs so you can keep pretending you don't have to.

Dashboard URL: http://127.0.0.1:18789/#token=ea710491e8584c3c41d73fb405201e68155af5ef6d50fe30
Copied to clipboard.
No GUI detected. Open from your computer:
ssh -N -L 18789:127.0.0.1:18789 liuy@::1
Then open:
http://localhost:18789/
http://localhost:18789/#token=ea710491e8584c3c41d73fb405201e68155af5ef6d50fe30
Docs:
https://docs.openclaw.ai/gateway/remote
https://docs.openclaw.ai/web/control-ui
╭─────────────────────────────────────────╮
│ Need help?                              │
│ FAQ: https://docs.openclaw.ai/start/faq │
╰─────────────────────────────────────────╯
liuy@ubuntu:~$ openclaw onboard --install-daemon

🦞 OpenClaw 2026.2.15 (3fe22ea)
   I don't just autocomplete—I auto-commit (emotionally), then ask you to review (logically).

▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
██░▄▄▄░██░▄▄░██░▄▄▄██░▀██░██░▄▄▀██░████░▄▄▀██░███░██
██░███░██░▀▀░██░▄▄▄██░█░█░██░█████░████░▀▀░██░█░█░██
██░▀▀▀░██░█████░▀▀▀██░██▄░██░▀▀▄██░▀▀░█░██░██▄▀▄▀▄██
▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀
                  🦞 OPENCLAW 🦞

┌  OpenClaw onboarding
│
◇  Security ──────────────────────────────────────────────────────────────────────────────╮
│                                                                                         │
│  Security warning — please read.                                                        │
│                                                                                         │
│  OpenClaw is a hobby project and still in beta. Expect sharp edges.                     │
│  This bot can read files and run actions if tools are enabled.                          │
│  A bad prompt can trick it into doing unsafe things.                                    │
│                                                                                         │
│  If you’re not comfortable with basic security and access control, don’t run OpenClaw.  │
│  Ask someone experienced to help before enabling tools or exposing it to the internet.  │
│                                                                                         │
│  Recommended baseline:                                                                  │
│  - Pairing/allowlists + mention gating.                                                 │
│  - Sandbox + least-privilege tools.                                                     │
│  - Keep secrets out of the agent’s reachable filesystem.                                │
│  - Use the strongest available model for any bot with tools or untrusted inboxes.       │
│                                                                                         │
│  Run regularly:                                                                         │
│  openclaw security audit --deep                                                         │
│  openclaw security audit --fix                                                          │
│                                                                                         │
│  Must read: https://docs.openclaw.ai/gateway/security                                   │
│                                                                                         │
├─────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  I understand this is powerful and inherently risky. Continue?
│  Yes
│
◇  Onboarding mode
│  QuickStart
│
◇  Existing config detected ─────────╮
│                                    │
│  workspace: ~/.openclaw/workspace  │
│  model: minimax-cn/MiniMax-M2.5    │
│  gateway.mode: local               │
│  gateway.port: 18789               │
│  gateway.bind: loopback            │
│                                    │
├────────────────────────────────────╯
│
◇  Config handling
│  Update values
│
◇  QuickStart ─────────────────────────────╮
│                                          │
│  Keeping your current gateway settings:  │
│  Gateway port: 18789                     │
│  Gateway bind: Loopback (127.0.0.1)      │
│  Gateway auth: Token (default)           │
│  Tailscale exposure: Off                 │
│  Direct to chat channels.                │
│                                          │
├──────────────────────────────────────────╯
│
◇  Model/auth provider
│  MiniMax
│
◇  MiniMax auth method
│  MiniMax M2.5 (CN)
│
◇  Enter MiniMax China API key
│  sk-cp-pHv7rkK8w0B3_NEw9475Fipfs-1JDAdvN11gK6h-YlXj8Fn_rkWoKcx8auVuIqPZPcodAjSs_paji2UrW_hlPnXw8IELvdedG85
LmoJXLDA4R4JHSGKEIy8
│
◇  Default model
│  Keep current (minimax-cn/MiniMax-M2.5)
│
◇  Channel status ────────────────────────────╮
│                                             │
│  Telegram: not configured                   │
│  WhatsApp: not configured                   │
│  Discord: not configured                    │
│  IRC: not configured                        │
│  Google Chat: not configured                │
│  Slack: not configured                      │
│  Signal: not configured                     │
│  iMessage: not configured                   │
│  Feishu: install plugin to enable           │
│  Google Chat: install plugin to enable      │
│  Nostr: install plugin to enable            │
│  Microsoft Teams: install plugin to enable  │
│  Mattermost: install plugin to enable       │
│  Nextcloud Talk: install plugin to enable   │
│  Matrix: install plugin to enable           │
│  BlueBubbles: install plugin to enable      │
│  LINE: install plugin to enable             │
│  Zalo: install plugin to enable             │
│  Zalo Personal: install plugin to enable    │
│  Tlon: install plugin to enable             │
│                                             │
├─────────────────────────────────────────────╯
│
◇  How channels work ─────────────────────────────────────────────────────────────────────╮
│                                                                                         │
│  DM security: default is pairing; unknown DMs get a pairing code.                       │
│  Approve with: openclaw pairing approve <channel> <code>                                │
│  Public DMs require dmPolicy="open" + allowFrom=["*"].                                  │
│  Multi-user DMs: run: openclaw config set session.dmScope "per-channel-peer" (or        │
│  "per-account-channel-peer" for multi-account channels) to isolate sessions.            │
│  Docs: start/pairing                  │
│                                                                                         │
│  Telegram: simplest way to get started — register a bot with @BotFather and get going.  │
│  WhatsApp: works with your own number; recommend a separate phone + eSIM.               │
│  Discord: very well supported right now.                                                │
│  IRC: classic IRC networks with DM/channel routing and pairing controls.                │
│  Google Chat: Google Workspace Chat app with HTTP webhook.                              │
│  Slack: supported (Socket Mode).                                                        │
│  Signal: signal-cli linked device; more setup (David Reagans: "Hop on Discord.").       │
│  iMessage: this is still a work in progress.                                            │
│  Feishu: 飞书/Lark enterprise messaging with doc/wiki/drive tools.                      │
│  Nostr: Decentralized protocol; encrypted DMs via NIP-04.                               │
│  Microsoft Teams: Bot Framework; enterprise support.                                    │
│  Mattermost: self-hosted Slack-style chat; install the plugin to enable.                │
│  Nextcloud Talk: Self-hosted chat via Nextcloud Talk webhook bots.                      │
│  Matrix: open protocol; install the plugin to enable.                                   │
│  BlueBubbles: iMessage via the BlueBubbles mac app + REST API.                          │
│  LINE: LINE Messaging API bot for Japan/Taiwan/Thailand markets.                        │
│  Zalo: Vietnam-focused messaging platform with Bot API.                                 │
│  Zalo Personal: Zalo personal account via QR code login.                                │
│  Tlon: decentralized messaging on Urbit; install the plugin to enable.                  │
│                                                                                         │
├─────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  Select channel (QuickStart)
│  Skip for now
Config overwrite: /home/liuy/.openclaw/openclaw.json (sha256 f7e797cb3a26d99d1c3a1987038f26d1481b31b171cace6a25490b6716bcc887 -> 004d3c5896f26e389c98c34be61df54b497664997ace9bc93b7f8c950436dca9, backup=/home/liuy/.openclaw/openclaw.json.bak)
Updated ~/.openclaw/openclaw.json
Workspace OK: ~/.openclaw/workspace
Sessions OK: ~/.openclaw/agents/main/sessions
│
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
│  No
│
◇  Hooks ──────────────────────────────────────────────────────────╮
│                                                                  │
│  Hooks let you automate actions when agent commands are issued.  │
│  Example: Save session context to memory when you issue /new.    │
│                                                                  │
│  Learn more: https://docs.openclaw.ai/automation/hooks           │
│                                                                  │
├──────────────────────────────────────────────────────────────────╯
│
◇  Enable hooks?
│  Skip for now
Config overwrite: /home/liuy/.openclaw/openclaw.json (sha256 004d3c5896f26e389c98c34be61df54b497664997ace9bc93b7f8c950436dca9 -> d22c94a93d6db5af262a7a85f4a803ee773644631cdc4cb3669d4dfffc3ac882, backup=/home/liuy/.openclaw/openclaw.json.bak)
│
◇  Gateway service runtime ────────────────────────────────────────────╮
│                                                                      │
│  QuickStart uses Node for the Gateway service (stable + supported).  │
│                                                                      │
├──────────────────────────────────────────────────────────────────────╯
│
◇  Gateway service already installed
│  Restart
│
◐  Restarting Gateway service…Restarted systemd service: openclaw-gateway.service
◇  Gateway service restarted.
│
◇
Agents: main (default)
Heartbeat interval: 30m (main)
Session store (main): /home/liuy/.openclaw/agents/main/sessions/sessions.json (1 entries)
- agent:main:main (2062m ago)
│
◇  Optional apps ────────────────────────╮
│                                        │
│  Add nodes for extra features:         │
│  - macOS app (system + notifications)  │
│  - iOS app (camera/canvas)             │
│  - Android app (camera/canvas)         │
│                                        │
├────────────────────────────────────────╯
│
◇  Control UI ─────────────────────────────────────────────────────────────────────╮
│                                                                                  │
│  Web UI: http://127.0.0.1:18789/                                                 │
│  Web UI (with token):                                                            │
│  http://127.0.0.1:18789/#token=ea710491e8584c3c41d73fb405201e68155af5ef6d50fe30  │
│  Gateway WS: ws://127.0.0.1:18789                                                │
│  Gateway: reachable                                                              │
│  Docs: https://docs.openclaw.ai/web/control-ui                                   │
│                                                                                  │
├──────────────────────────────────────────────────────────────────────────────────╯
│
◇  Start TUI (best option!) ─────────────────────────────────╮
│                                                            │
│  This is the defining action that makes your agent you.    │
│  Please take your time.                                    │
│  The more you tell it, the better the experience will be.  │
│  We will send: "Wake up, my friend!"                       │
│                                                            │
├────────────────────────────────────────────────────────────╯
│
◇  Token ─────────────────────────────────────────────────────────────────────────────────╮
│                                                                                         │
│  Gateway token: shared auth for the Gateway + Control UI.                               │
│  Stored in: ~/.openclaw/openclaw.json (gateway.auth.token) or OPENCLAW_GATEWAY_TOKEN.   │
│  View token: openclaw config get gateway.auth.token                                     │
│  Generate token: openclaw doctor --generate-gateway-token                               │
│  Web UI stores a copy in this browser's localStorage (openclaw.control.settings.v1).    │
│  Open the dashboard anytime: openclaw dashboard --no-open                               │
│  If prompted: paste the token into Control UI settings (or use the tokenized dashboard  │
│  URL).                                                                                  │
│                                                                                         │
├─────────────────────────────────────────────────────────────────────────────────────────╯
│
◇  How do you want to hatch your bot?
│  Hatch in TUI (recommended)
 openclaw tui - ws://127.0.0.1:18789 - agent main - session main

 session agent:main:main


 你好


 你好！👋

 看起来这是个全新的开始 — 我刚上线，记忆还是空白的。

 你是谁？我又该叫什么名字呢？一起聊聊看吧！


 Wake up, my friend!


 Hey! 💫 I just came online — fresh workspace, clean slate. Looks like this is our first chat.

 Who am I? Who are you? Let's figure that out together.

 What should I call you — and what do you want to call me?


 你是什么模型


 我是 MiniMax-M2.5 模型 🧠

 运行在 MiniMax-CN 上。有什么我可以帮你的吗？
 connected | idle
 agent main | session main (openclaw-tui) | minimax-cn/MiniMax-M2.5 | think low | tokens 14k/200k (7%)
────────────────────────────────────────────────────────────────────────────────────────────────────────────

────────────────────────────────────────────────────────────────────────────────────────────────────────────
```

