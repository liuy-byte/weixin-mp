# Sisyphus 深度解析与 UltraWork Mode 补充实施计划

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** 在《Oh-My-OpenCode Agent 使用完全指南.md》的 1.1 Sisyphus 章节中补充深度解析和 UltraWork Mode 内容

**Architecture:** 采用渐进式扩充方案，在现有 1.1 节后追加两个新子节（🔧 深度解析 和 ⚡ UltraWork Mode），保持原有内容不变

**Tech Stack:** Markdown 文档编辑

---

## Task 1: 添加深度解析部分

**Files:**
- Modify: `Oh-My-OpenCode Agent 使用完全指南.md:44` (在 1.1 节使用命令后)

**Step 1: 在 1.1 节末尾添加分隔符和深度解析标题**

定位到第 44 行（使用命令代码块后），添加：

```markdown

---

#### 🔧 Sisyphus 深度解析
```

**Step 2: 验证插入位置正确**

运行: `head -50 "Oh-My-OpenCode Agent 使用完全指南.md" | tail -10`
预期: 看到新添加的分隔符和标题

**Step 3: 添加工作流程五阶段表格**

在深度解析标题后添加：

```markdown

##### 工作流程：五阶段智能编排

Sisyphus 不是简单的任务分配器,而是像资深工程师一样思考和执行。每个任务都经过 5 个严格阶段:

| 阶段 | 名称 | 核心工作 | 关键约束 |
|-----|------|---------|---------|
| 1️⃣ | **意图门槛** | 分类用户意图,判断任务类型 | 非平凡任务**必须创建 TODO** |
| 2️⃣ | **代码库评估** | 理解项目结构、技术栈、代码模式 | 必须理解现有代码再动手 |
| 3️⃣ | **探索与研究** | 并行后台调用专家 Agent 调研 | 后台任务**必须并行**执行 |
| 4️⃣ | **实现** | 代码编写、Bug 修复、功能开发 | 委托给专业 Agent,不自己写 |
| 5️⃣ | **完成** | 运行诊断、构建验证、测试套件 | **必须验证**,有证据才算完成 |

> **核心理念**: Sisyphus 负责"想清楚怎么做",专业 Agent 负责"做具体的事"。职责分离是效率的关键。
```

**Step 4: 添加推荐配置参数表格**

继续添加：

```markdown

---

##### 推荐配置参数

要发挥 Sisyphus 的最大威力,配置很关键:

| 配置项 | 推荐值 | 说明 |
|--------|--------|------|
| **模型** | Claude Opus 4.5 | 🔥 强烈推荐,其他模型体验显著下降 |
| **思考预算** | 32k tokens | 深度思考的保障,不要降低 |
| **温度** | 0.1 | 代码 Agent 固定值,保证稳定性 |
| **最大令牌** | 64000 | 处理大型项目必需 |

⚠️ **重要提示**: 使用 Claude Sonnet 或其他模型会导致任务拆解质量下降、并行调度混乱。
```

**Step 5: 添加并行执行优势部分**

继续添加：

```markdown

---

##### 并行执行优势：时间节省 33%

传统 AI 编程工具是串行执行,Sisyphus 的并行调度能显著提速:

| 执行方式 | 典型任务耗时 | 效率对比 |
|---------|-------------|---------|
| **串行执行**(传统) | 6 分钟 | 基准 100% |
| **并行执行**(Sisyphus) | 4 分钟 | ⚡ 节省 33% 时间 |

**工作原理**:
- ✅ 探索阶段:代码库分析、文档查询、最佳实践搜索**同时进行**
- ✅ 实现阶段:前端、后端、测试 Agent **并行开发**
- ✅ 验证阶段:LSP 诊断、构建检查、测试运行**同步执行**

> **实战案例**: 开发带测试的 REST API,传统方式需串行完成(设计→实现→测试→文档),Sisyphus 让实现和测试编写并行,文档生成同步进行,总耗时从 30 分钟降到 20 分钟。
```

**Step 6: 添加验证机制与核心原则部分**

继续添加：

```markdown

---

##### 验证机制与核心原则

**三重验证,确保质量**:
- ✅ **LSP 诊断**: 实时语法检查,类型错误不过关
- ✅ **构建检查**: 编译/打包必须成功
- ✅ **测试套件**: 所有测试必须通过才算完成

**委托优先原则**:

Sisyphus 默认**不自己写代码**,而是:
1. 判断任务需要哪个专家(Oracle/Explore/Visual Engineering 等)
2. 委托给最合适的 Agent 执行
3. 验证结果并整合

> 💡 **为什么这样设计?** 专业的人做专业的事。Sisyphus 擅长编排和验证,写代码交给专业 Agent 质量更高。

**何时 Sisyphus 自己动手?**
- 仅当任务极其简单(单文件、已知位置、简单修改)
- 其他情况一律委托或使用 Category + Skill 机制
```

**Step 7: 验证深度解析部分格式**

运行: `grep -A 5 "🔧 Sisyphus 深度解析" "Oh-My-OpenCode Agent 使用完全指南.md"`
预期: 看到深度解析标题和工作流程部分

**Step 8: 提交深度解析部分**

```bash
git add "Oh-My-OpenCode Agent 使用完全指南.md"
git commit -m "更新文章：补充 Sisyphus 深度解析（工作流程、配置、并行优势、验证机制）"
```

---

## Task 2: 添加 UltraWork Mode 部分

**Files:**
- Modify: `Oh-My-OpenCode Agent 使用完全指南.md` (在深度解析部分后)

**Step 1: 添加 UltraWork Mode 标题**

在验证机制部分后添加：

```markdown

---

#### ⚡ UltraWork Mode：一键全员激活

##### 什么是 UltraWork Mode

UltraWork 是 Sisyphus 的"超级加速模式",通过一个关键词**激活所有高级功能**:

- ⚡ 自动并行后台任务
- 🔍 深度探索代码库
- 🤖 强制多 Agent 协作
- ✅ 严格质量验证

**工作原理**:
当你在提示词中包含 `ultrawork` 或缩写 `ulw` 时,系统自动:
1. 设置最大精度模式(`variant = "max"`)
2. 注入 200+ 行完整指令集
3. 激活所有专业 Agent
4. 启用并行调度引擎
```

**Step 2: 添加使用方法部分**

继续添加：

```markdown

---

##### 使用方法

**基础触发**:
```bash
opencode "ultrawork 开发一个用户认证模块"
```

**简化写法**(推荐):
```bash
opencode "ulw 为项目添加 JWT 登录功能"
```

**激活确认**:
成功激活后会看到:
- 🎯 Toast 通知: "Ultrawork Mode Activated - Maximum precision engaged"
- 💬 回复开头: "ULTRAWORK MODE ENABLED!"
- 🔄 并行后台任务开始运行
```

**Step 3: 添加四大设计原则表格**

继续添加：

```markdown

---

##### 四大设计原则

UltraWork Mode 的威力源自这些核心理念:

| 原则 | 含义 | 实际体现 |
|-----|------|---------|
| 🚫 **人类干预是失败信号** | 系统应自动处理,无需人工纠正 | 自动探索→规划→实现→验证,全流程自动化 |
| 💎 **代码应不可区分** | AI 产出应达资深工程师水准 | 严格验证、强制测试、代码审查 |
| 🧠 **最小化认知负担** | 用户仅表达意图,代理负责执行 | 仅需一句话需求,剩下的交给系统 |
| 🎯 **可预测且可委托** | 运作应如编译器般稳定可靠 | 固定流程、强制验证、结果可复现 |

> **设计哲学**: "告诉我要什么,而不是怎么做"。你负责提需求,Sisyphus 负责想明白并协调专家完成。
```

**Step 4: 添加适用场景对比表格**

继续添加：

```markdown

---

##### 适用场景对比

并非所有任务都适合 UltraWork Mode:

| 场景类型 | 是否使用 | 原因 |
|---------|---------|------|
| 🏗️ **复杂新功能**(3+ 文件) | ✅ 强烈推荐 | 需多 Agent 协作、深度规划 |
| 🔥 **紧急 Bug 排查** | ✅ 推荐 | 需快速诊断、并行验证 |
| 📦 **系统重构** | ✅ 推荐 | 需全局分析、分步实施 |
| 🔧 **简单修改**(单文件) | ❌ 不推荐 | 过度使用资源,直接用对应 Agent 更快 |
| ⚡ **快速验证想法** | ❌ 不推荐 | 注入大量指令反而降低效率 |

**判断标准**:
- 任务涉及 **3 个以上文件/模块** → 用 `ulw`
- 需要 **多个 Agent 协作** → 用 `ulw`
- **单文件简单修改** → 直接用对应 Agent(如 `用 Explore 帮我...`)
```

**Step 5: 添加重要注意事项部分**

继续添加：

```markdown

---

##### ⚠️ 重要注意事项

**1. 避免过度使用**

❌ **错误做法**:
```bash
opencode "ulw 修改一个变量名"
opencode "ulw 添加一行注释"
```

✅ **正确做法**:
```bash
opencode "ulw 重构整个认证系统"  # 复杂任务才用
opencode "用 Explore 帮我找到变量定义位置"  # 简单任务直接指定 Agent
```

**2. 资源消耗提醒**

UltraWork Mode 会注入 200+ 行指令,每次对话成本更高。仅在真正需要深度分析和多 Agent 协作时使用。

**3. Provider 配置要求**

UltraWork 依赖多个 AI 模型并行工作,确保:
- ✅ 配置了 Claude Opus 4.5(必需)
- ✅ 所有专业 Agent 的 Provider 可用
- ✅ API 配额充足

**4. 后台任务限制**

UltraWork Mode **仅在主会话中有效**,后台子 Agent 会话不会自动激活该模式(避免递归注入)。
```

**Step 6: 添加验证清单**

继续添加：

```markdown

---

##### 验证清单

使用 UltraWork Mode 后,确认以下各项:

- [ ] 输入 `ulw` 后看到 Toast 通知
- [ ] 代理回复以 "ULTRAWORK MODE ENABLED!" 开头
- [ ] 观察到并行后台任务运行
- [ ] 代理使用 Category + Skills 系统
- [ ] 任务完成后有验证证据(测试结果、构建成功等)

如果以上任意一项未出现,说明 UltraWork Mode 可能未正确激活,检查命令是否包含 `ulw` 或 `ultrawork` 关键词。
```

**Step 7: 验证 UltraWork Mode 部分格式**

运行: `grep -A 3 "⚡ UltraWork Mode" "Oh-My-OpenCode Agent 使用完全指南.md"`
预期: 看到 UltraWork Mode 标题和简介

**Step 8: 提交 UltraWork Mode 部分**

```bash
git add "Oh-My-OpenCode Agent 使用完全指南.md"
git commit -m "更新文章：补充 UltraWork Mode 使用指南（激活方法、设计原则、适用场景）"
```

---

## Task 3: 验证整体内容

**Files:**
- Read: `Oh-My-OpenCode Agent 使用完全指南.md`

**Step 1: 验证 1.1 节结构完整性**

运行: `grep "^###" "Oh-My-OpenCode Agent 使用完全指南.md" | head -10`
预期: 看到 1.1-1.6 六个 Agent 标题，结构未改变

**Step 2: 验证深度解析部分标题层次**

运行: `grep "^####" "Oh-My-OpenCode Agent 使用完全指南.md"`
预期: 看到 🔧 和 ⚡ 两个四级标题

**Step 3: 验证所有表格格式正确**

运行: `grep -c "^|" "Oh-My-OpenCode Agent 使用完全指南.md"`
预期: 表格行数显著增加（原文基础上增加约 30+ 行）

**Step 4: 验证代码块格式正确**

运行: `grep -c '```' "Oh-My-OpenCode Agent 使用完全指南.md"`
预期: 代码块标记成对出现（偶数）

**Step 5: 人工阅读 1.1 节完整内容**

运行: `sed -n '/### 1.1 Sisyphus/,/### 1.2 Oracle/p' "Oh-My-OpenCode Agent 使用完全指南.md" | less`
预期:
- 原有内容未被修改
- 深度解析部分格式正确
- UltraWork Mode 部分格式正确
- 分隔符 `---` 正确放置
- emoji 使用适度

**Step 6: 检查是否有重复内容**

运行: `grep -i "sisyphus" "Oh-My-OpenCode Agent 使用完全指南.md" | sort | uniq -c | sort -rn | head`
预期: 无明显重复段落

**Step 7: 验证文档总体可读性**

使用 Markdown 预览工具查看完整文档
预期:
- 层次分明
- 表格正确渲染
- 代码块正确高亮
- emoji 正确显示

---

## Task 4: 最终提交

**Files:**
- Modify: `Oh-My-OpenCode Agent 使用完全指南.md`

**Step 1: 检查 git 状态**

运行: `git status`
预期: 看到文章文件已修改

**Step 2: 查看完整 diff**

运行: `git diff "Oh-My-OpenCode Agent 使用完全指南.md" | head -100`
预期: 仅在 1.1 节后有新增内容，无删除

**Step 3: 最终提交**

```bash
git add "Oh-My-OpenCode Agent 使用完全指南.md"
git commit -m "$(cat <<'EOF'
更新文章：补充 Sisyphus 深度解析和 UltraWork Mode 完整指南

新增内容:
- Sisyphus 五阶段工作流程（意图门槛→代码库评估→探索研究→实现→完成）
- 推荐配置参数（Claude Opus 4.5、32k thinking、温度 0.1）
- 并行执行优势数据对比（串行 6 分钟 vs 并行 4 分钟，节省 33%）
- 三重验证机制（LSP 诊断、构建检查、测试套件）
- 委托优先核心原则
- UltraWork Mode 激活机制和使用方法
- 四大设计原则（人类干预是失败信号等）
- 适用场景对比表格
- 避坑指南和验证清单

参考官方文档完整补充，保持原文结构和风格
EOF
)"
```

**Step 4: 推送到远程仓库**

运行: `git push origin main`
预期: 成功推送

**Step 5: 验证推送成功**

运行: `git log --oneline -1`
预期: 看到最新提交记录

---

## 预期结果

完成后，1.1 Sisyphus 章节将包含：

1. **基础介绍**（原有，未改动）
   - 定位、核心能力
   - 适用场景
   - 实战案例
   - 使用命令

2. **深度解析**（新增）
   - 五阶段工作流程表格
   - 推荐配置参数表格
   - 并行执行优势数据对比
   - 验证机制与委托原则

3. **UltraWork Mode**（新增）
   - 激活机制和使用方法
   - 四大设计原则表格
   - 适用场景对比表格
   - 避坑指南和验证清单

总新增内容约 150-200 行，全部在 1.1 节内部扩充，不影响其他章节结构。

---

## 注意事项

1. **保持原文不变**: 所有修改都是在原有内容后追加，绝不删除或修改现有内容
2. **格式一致性**: 使用与原文相同的 Markdown 格式、表格风格、emoji 使用习惯
3. **数据准确性**: 所有数字（33%、6分钟、4分钟、32k tokens 等）必须与官方文档一致
4. **代码块语法**: 确保所有代码块使用正确的语言标识（bash、markdown 等）
5. **分隔符使用**: 用 `---` 清晰分隔不同层次，便于阅读
6. **链接完整性**: 确保文档末尾的相关链接部分不受影响
