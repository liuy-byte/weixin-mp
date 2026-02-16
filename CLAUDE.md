# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个技术文档仓库，记录微信小程序开发相关内容，包括 Claude Code 和 MiniMax 模型的 AI 编程教程和配置。

**技术栈**:
- Claude Code: AI 编程助手
- MiniMax-M2.1: AI 大模型
- cc-switch: 配置切换工具

## 文档架构

本仓库采用主题分类的文档结构：

- **Claude Code 系列**: Claude Code 的安装、配置和命令使用指南
- **AI 模型集成**: MiniMax M2.1 在 Claude Code 中的使用
- **开发工具**: Node.js、JDK 版本管理工具的安装配置
- **镜像配置**: 国内开发环境的加速配置（Homebrew、npm 等）

所有文档使用中文编写，面向国内开发者。

## 常用命令

### Git 操作
```bash
# 提交新文档或更新
git add .
git commit -m "新增文章：[文档标题]"  # 或 "更新文章：[文档标题]"
git push origin main

# 查看状态
git status
git log --oneline -10
```

### 文档编写

本仓库不涉及代码构建、测试或 linting，主要是 Markdown 文档的编写和维护。

## 文档编写规范

1. **文件命名**: 使用中文文件名，清晰描述文档主题
2. **图片管理**: 所有图片统一放在 `images/` 目录下
3. **提交信息**: 使用中文，格式为 "新增文章：" 或 "更新文章：" 前缀
4. **文档结构**:
   - 使用清晰的标题层级
   - 包含必要的代码示例
   - 提供详细的步骤说明
   - 针对国内开发环境提供镜像源配置

## README 维护

当添加新文档时，需要更新 README.md 中的文档链接列表，保持索引的完整性。

## Claude Code 特定内容

本仓库记录了 16 个 Claude Code 命令的详细使用方法：

- `/init` - 初始化项目
- `/clear` - 清除会话历史
- `/compact` - 压缩上下文
- `/memory` - 查看加载的 CLAUDE.md
- `/add-dir` - 扩展工作目录
- `/agents` - 创建/调用子代理
- `/cost` - 显示 token/成本使用情况
- `/doctor` - 诊断环境
- `/export` - 导出对话
- `/model` - 切换 AI 模型
- `/plan` - 任务分解
- `/review` - 代码审查
- `/rewind` - 回滚更改
- `/ide` - IDE 集成

## MCP 服务器配置

本仓库文档中记录了 MCP 服务器的配置方法，配置文件位于 `~/.claude/settings.json`。主要配置包括：

- puppeteer: 浏览器自动化
- fetch: HTTP 请求
- filesystem: 文件系统访问
- sequential-thinking: 深度思考模式

参考文档《在 Claude Code 中使用 MiniMax-M2.1 模型进行 AI 编程.md》了解详细配置。
