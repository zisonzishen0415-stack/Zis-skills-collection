# 🛠️ Claude Code Skills Collection

> 一套精心挑选的 Claude Code Skills 合集，覆盖工程开发、UI/UX 设计、代码审查、TDD、调试等工作流。共 **57 个 Skills**，来自 3 个社区插件 + 14 个内置技能。

---

## 📦 快速安装

### 一键安装所有插件

```bash
# 1. Superpowers — 工程开发工作流（14 skills）
/plugin marketplace add anthropics/claude-plugins-official
/plugin install superpowers@claude-plugins-official

# 2. UI-UX-Pro-Max — 设计智能引擎（7 skills）
git clone https://github.com/nextlevelbuilder/ui-ux-pro-max-skill.git
# 放入 ~/.claude/plugins/cache/ui-ux-pro-max-skill/

# 3. Matt Pocock Skills — 专业工程实践（22 skills）
git clone https://github.com/mattpocock/skills.git
# 放入 ~/.claude/plugins/cache/mattpocock/
```

### 手动安装

在 Claude Code 中输入：
```
/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill
/plugin marketplace add mattpocock/skills
```

---

## 📊 总览

| # | 插件/来源 | 版本 | Skills 数 | 类型 |
|---|----------|------|-----------|------|
| 1 | **superpowers** | 6.1.1 | 14 | 工程工作流 |
| 2 | **ui-ux-pro-max** | 2.6.2 | 7 | UI/UX 设计 |
| 3 | **mattpocock-skills** | 1.2.0 | 22 | 专业工程实践 |
| 4 | **Built-in** | — | 14 | Claude Code 内置 |
| | **合计** | | **57** | |

---

## 🔗 1. Superpowers — 工程开发工作流

> **仓库**: [github.com/obra/superpowers](https://github.com/obra/superpowers)
> **作者**: Jesse Vincent
> **安装**: `/plugin install superpowers@claude-plugins-official`

一个覆盖完整开发管线的技能体系：从头脑风暴 → 计划 → 编写 → 测试 → 审查 → 完成。

### 完整 Workflow

```
using-superpowers (入口)
  → brainstorming (设计)
    → writing-plans (计划)
      → using-git-worktrees (隔离工作区)
        → subagent-driven-development / executing-plans (执行)
          → test-driven-development (TDD)
          → systematic-debugging (调试)
          → requesting-code-review / receiving-code-review (审查)
          → dispatching-parallel-agents (并行任务)
          → verification-before-completion (验证)
            → finishing-a-development-branch (合并/PR)
```

### 技能清单

| Skill | 描述 | 使用方式 |
|-------|------|----------|
| **brainstorming** | 在编写代码前，将想法转化为完整设计和规格 | `/brainstorming` |
| **dispatching-parallel-agents** | 为独立任务分派子代理并行工作 | `/dispatching-parallel-agents` |
| **executing-plans** | 在单独会话中执行已有的实现计划 | `/executing-plans` |
| **finishing-a-development-branch** | 结构化处理分支合并：本地合并/PR/保持/丢弃 | `/finishing-a-development-branch` |
| **receiving-code-review** | 处理代码审查反馈，强调技术严谨性 | `/receiving-code-review` |
| **requesting-code-review** | 分派代码审查子代理在问题扩散前捕获 | `/requesting-code-review` |
| **subagent-driven-development** | 在当前会话中为每个任务分派实现子代理 | `/subagent-driven-development` |
| **systematic-debugging** | 四阶段查错法：根因调查→模式分析→假设检验→实施 | `/systematic-debugging` |
| **test-driven-development** | 红-绿-重构循环：先写失败测试再看它失败再写代码 | `/test-driven-development` |
| **using-git-worktrees** | 用 git worktree 隔离功能开发工作区 | `/using-git-worktrees` |
| **using-superpowers** | 入口技能，确保所有技能在适当时被正确调用 | `/using-superpowers` |
| **verification-before-completion** | 在声称完成前运行验证命令 — 证据先于断言 | `/verification-before-completion` |
| **writing-plans** | 编写包含精确文件路径和代码的综合实现计划 | `/writing-plans` |
| **writing-skills** | 用 TDD 方法论创建和验证新技能 | `/writing-skills` |

---

## 🎨 2. UI-UX-Pro-Max — 设计智能引擎

> **仓库**: [github.com/nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
> **版本**: 2.6.2
> **安装**: `git clone` 到 `~/.claude/plugins/cache/ui-ux-pro-max-skill/`

一个可搜索的本地设计知识库，含 **84 种 UI 风格、161 种配色、73 组字体搭配、99 条 UX 指南、25 种图表类型**，覆盖 17 个技术栈。

### 依赖关系

```
ui-ux-pro-max (设计智能引擎 — 搜索、规则、推荐)
  ├── design (统一入口 — 路由至所有子技能)
  │   ├── brand (品牌声音、身份、资源)
  │   ├── design-system (Token 架构 + 幻灯片引擎)
  │   ├── ui-styling (shadcn/ui + Tailwind 实现)
  │   └── banner-design (社交媒体/广告横幅 + AI 视觉)
  └── slides (演示文稿创建)
```

### 技能清单

| Skill | 描述 | 使用方式 |
|-------|------|----------|
| **ui-ux-pro-max** | 核心设计智能引擎，基于优先级的多类规则系统 | `/ui-ux-pro-max` + `python scripts/search.py "<query>" --design-system` |
| **design** | 统一设计入口：品牌、Token、UI、Logo、幻灯片、横幅、图标 | `/design [design-type] [context]` |
| **brand** | 品牌声音、视觉识别、信息框架、资源管理 | `/brand [update\|review\|create] [args]` |
| **design-system** | 三层 Token 架构：primitive → semantic → component | `/design-system [component or token]` |
| **ui-styling** | shadcn/ui + Tailwind CSS 组件化 UI 构建 | `/ui-styling [component or layout]` |
| **banner-design** | 多平台横幅设计，22 种风格，AI 生成视觉元素 | `/banner-design [platform] [style] [dimensions]` |
| **slides** | HTML 演示文稿 + Chart.js + 设计 Token | `/slides [topic] [slide-count]` |

### 技术栈支持

React · Next.js · Vue · Nuxt.js · Nuxt UI · Svelte · Astro · SwiftUI · React Native · Flutter · Tailwind · shadcn/ui · Jetpack Compose · Angular · Laravel · JavaFX · Three.js

---

## ⚙️ 3. Matt Pocock Skills — 专业工程实践

> **仓库**: [github.com/mattpocock/skills](https://github.com/mattpocock/skills)
> **作者**: [Matt Pocock](https://www.aihero.dev)
> **安装**: `git clone` 到 `~/.claude/plugins/cache/mattpocock/`

一套由 Matt Pocock 打造的"真正工程"技能集合，强调烧烤式访谈（grilling）、规格驱动、TDD、领域建模和代码审查。

### 主流程

```
setup-matt-pocock-skills (首次配置)
  → grill-with-docs (访谈 + 文档)
    → to-spec (生成规格 PRD)
      → to-tickets (分解为工单)
        → implement (实现)
          → code-review (审查)
```

### 工程技能 (Engineering)

| Skill | 描述 | 触发方式 |
|-------|------|----------|
| **ask-matt** | 路由器 — 根据当前情况推荐合适的技能 | 手动 `/ask-matt` |
| **code-review** | 双轴审查：编码标准 + 规格合规 | 自动触发 |
| **codebase-design** | 深层模块设计词汇：接口、接缝、适配器 | 自动触发 |
| **diagnosing-bugs** | 多阶段诊断循环：复现→假设→仪器化→修复 | 自动触发 |
| **domain-modeling** | 构建和完善项目的领域模型 + ADR | 自动触发 |
| **grill-with-docs** | 持续访谈流程，同时创建 ADR 和词汇表 | 手动 `/grill-with-docs` |
| **implement** | 按规格实现，内部驱动 TDD + 代码审查 | 手动 `/implement` |
| **improve-codebase-architecture** | 扫描热点，发现深化机会，生成 HTML 报告 | 手动 `/improve-codebase-architecture` |
| **prototype** | 构建抛弃式原型：逻辑型（终端）/ UI 型（多变体） | 自动触发 |
| **research** | 委托后台代理调查文档/源码/规范，返回引用文件 | 自动触发 |
| **resolving-merge-conflicts** | 按冲突块来源、合并目标解决 git 合并冲突 | 自动触发 |
| **setup-matt-pocock-skills** | 首次使用前配置仓库：跟踪器、标签、文档布局 | 手动 `/setup-matt-pocock-skills` |
| **tdd** | TDD 参考：好测试、接缝、反模式、红-绿循环 | 自动触发 |
| **to-spec** | 将访谈上下文转化为规格说明（PRD） | 手动 `/to-spec` |
| **to-tickets** | 将规格分解为垂直切片工单并发布到跟踪器 | 手动 `/to-tickets` |
| **triage** | 五角色状态机对 issue 进行分类：needs-triage→ready/wontfix | 手动 `/triage` |
| **wayfinder** | 为超大工作块规划路线 → 决策工单 → 移交给 `/to-spec` | 手动 `/wayfinder` |

### 生产力技能 (Productivity)

| Skill | 描述 | 触发方式 |
|-------|------|----------|
| **grill-me** | 无状态访谈 — 无代码库，不保存本地内容 | 手动 `/grill-me` |
| **grilling** | 持续访谈原语 — `/grill-with-docs` 和 `/grill-me` 的基础 | 自动触发 |
| **handoff** | 将当前对话压缩为交接文档（Markdown） | 手动 `/handoff [focus]` |
| **teach** | 多会话渐进式教学，构建课程和参考资料 | 手动 `/teach [topic]` |
| **writing-great-skills** | 编写技能的参考指南：词汇表、信息层次、反模式 | 手动 `/writing-great-skills` |

---

## 🏗️ 4. Claude Code 内置技能

Claude Code 自带的 14 个技能，无需安装。

| Skill | 描述 | 使用方式 |
|-------|------|----------|
| **deep-research** | 深度研究：多源搜索 → 获取 → 验证 → 合成引用报告 | `/deep-research [topic]` |
| **dataviz** | 创建图表/图形/仪表盘/数据可视化 | `/dataviz`（触发词：chart, graph, plot, dashboard） |
| **update-config** | 配置 settings.json：hooks, 权限, 环境变量 | `/update-config` |
| **keybindings-help** | 自定义键盘快捷键和组合键 | `/keybindings-help` |
| **verify** | 端到端验证代码变更是否按预期工作 | `/verify` |
| **code-review** | 审查当前 diff 的正确性和质量 | `/code-review`（可选 `--fix`） |
| **simplify** | 审查代码的重用/简化/效率改进并应用 | `/simplify` |
| **fewer-permission-prompts** | 扫描记录，添加常用工具到允许列表减少权限提示 | `/fewer-permission-prompts` |
| **loop** | 定时循环运行 prompt 或命令 | `/loop [interval] [command]` |
| **claude-api** | Claude API / Anthropic SDK 参考 | `/claude-api` |
| **run** | 启动并驱动项目应用验证变更 | `/run` |
| **init** | 初始化 CLAUDE.md 代码库文档 | `/init` |
| **review** | 审查 GitHub Pull Request | `/review` |
| **security-review** | 完成当前分支变更的安全审查 | `/security-review` |

---

## 🚀 使用场景

### 新功能开发
```
/brainstorming → /writing-plans → /implement (Matt Pocock) 或 /subagent-driven-development (Superpowers)
```

### Bug 修复
```
/systematic-debugging 或 /diagnosing-bugs
```

### 代码审查
```
/code-review (built-in) 或 /code-review (Matt Pocock) 或 /requesting-code-review (Superpowers)
```

### UI 设计
```
/ui-ux-pro-max → /design → /ui-styling
```

### 项目启动
```
/setup-matt-pocock-skills → /grill-with-docs → /to-spec → /to-tickets
```

---

## 📚 相关资源

| 资源 | URL |
|------|-----|
| Superpowers 仓库 | [github.com/obra/superpowers](https://github.com/obra/superpowers) |
| UI-UX-Pro-Max 仓库 | [github.com/nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) |
| UI-UX-Pro-Max 官网 | [uupm.cc](https://uupm.cc) |
| Matt Pocock Skills 仓库 | [github.com/mattpocock/skills](https://github.com/mattpocock/skills) |
| Matt Pocock 官网 | [aihero.dev](https://www.aihero.dev) |
| Claude Code 官方文档 | [docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code) |
| Claude Plugins 官方市场 | [github.com/anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) |

---

## 🤝 贡献

欢迎提交 PR 添加更多优质的 Claude Code Skills！

每个 Skill 条目应包含：
- 名称和简短描述
- 来源仓库 URL
- 安装方式
- 使用示例

---

> 维护者: [@zisonzishen0415](https://github.com/zisonzishen0415-stack)
