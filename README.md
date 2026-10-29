# 🛠️ Zi's Skills Collection

> 当前 Claude Code 环境的 skills / plugins 清单。
> 这不是一份「收集来但没在用」的列表：按本机 `~/.claude/skills`、`enabledPlugins` 和插件 cache 的实际状态整理。
> 更新：2026-10-29

## 一眼看完

| 类型 | 数量 | 状态 |
|---|---:|---|
| 自建 / 用户 skills | 4 | 启用 |
| 启用中的插件 | 3（3 skills + 5 commands） | 启用 |
| Claude Code 内置 skills | 13 | 随版本 |
| 已安装未启用的插件 | 3（16 skills） | 未启用 |
| 只剩元数据的旧插件 | 5（32 skills） | 不可用 |

当前可用：4 + 3 + 13 = **20 个 skills**（插件命令另算 5 个）。

旧版 README 的 60 个里，有 32 个来自已经不在这台机器上的社区插件；这次按实际状态重写。已安装但没启用的插件、只剩元数据的旧插件，都单独列出来，不再混进「当前可用」。

---

## 1. 自建 / 用户 skills（4）

位置：`~/.claude/skills/`。代码在各自项目或本机，不在本仓库重复分发。

| Skill | 做什么 | 触发场景 |
|---|---|---|
| **et-prj-corpus** | 无头、只读地把一批 ET `.prj` 板片导出成 JSONL，带覆盖率统计；提取规格区 / 尺寸表，判定「完整多尺码表 vs 单码摘要」 | 批量解析 ET 板片资产；问 `.prj` 里到底有没有完整多尺码表 |
| **et-prj-headless** | 无头、只读解析 ET `.prj`，提取 M 码衣长、后中长、裤长等成品尺寸线索 | 要求分析 ET 项目，但禁止打开软件或操作桌面 |
| **jch-recolor** | 金昌 EX9000 JCH 花型换色：参考图反解每层颜色，写回 JCH，输出可交付印染的成品包 | 「这个花型换成这个配色」「JCH 换色」「分色改色」 |
| **reverse-engineer-anything** | REA 的 Claude Code skill：原生 / 托管 / Electron / 固件 / 浏览器目标的逆向调查，170 个工具 | shipped binary / 反编译 / 版本对比 / 运行时证据 |

---

## 2. 启用中的插件（3）

`~/.claude/settings.json` 的 `enabledPlugins` 里为 `true`。每个插件 1 个主 skill；company-background-check 和 customer-acquisition 另带命令。

### 2.1 company-background-check（私有仓库）

> 企业背调 / 新客户调查。**仓库私有，仅协作者可安装。**

- **Skill**：`company-background-check`
- **命令**：`/company-background-check:company-background-check`、`:setup`、`:pdf`、`:help`
- **做什么**：从名片 / 公司名 / 域名出发，先定主体，再查官方登记源（UK Companies House、GLEIF、法国 recherche-entreprises）、自主网页检索、RDAP 域名核验、自审；输出带出处和置信度的公开信息报告。只呈现事实，不做评分。

```bash
# 仅限有仓库权限的协作者
claude plugin marketplace add zisonzishen0415-stack/company-background-check
claude plugin install company-background-check@company-background-check
```

### 2.2 customer-acquisition（私有仓库）

> 获客 / 相似客户发现。**仓库私有，仅协作者可安装。**

- **Skill**：`customer-acquisition`
- **命令**：`/customer-acquisition:customer-acquisition`、`:setup`、`:help`
- **做什么**：把老客户 / 可靠客户名单量化成画像（按 Wilson 95% 下界分铁律 / 多数 / 分化 / 证据不足），再从公开网络、展会名录、B2B 目录、海关提单、社媒找 lookalike 潜客；判重、按相似度 × 证据覆盖排序。

```bash
# 仅限有仓库权限的协作者
claude plugin marketplace add zisonzishen0415-stack/customer-acquisition
claude plugin install customer-acquisition@customer-acquisition
```

### 2.3 weekly-report（公开）

> 从代码证据重建周报。

- **Skill**：`weekly-report`
- **做什么**：从 git history、未提交改动、代码原子和生成物里取证，按功能而不是按 commit 聚类；产出可归档周报、展示版 HTML/PDF、口头汇报版，以及按人拆的清单版。

```bash
claude plugin marketplace add zisonzishen0415-stack/weekly-report
claude plugin install weekly-report@weekly-report
```

---

## 3. Claude Code 内置 skills（13）

无需安装，随 Claude Code 版本变化。

| Skill | 做什么 |
|---|---|
| **dataviz** | 图表 / 图形 / 仪表盘 / 数据可视化 |
| **update-config** | 改 `settings.json`：hooks、权限、环境变量 |
| **keybindings-help** | 自定义键盘快捷键 |
| **code-review** | 审查当前 diff 或 PR 的正确性 / 质量 |
| **simplify** | 审查并应用复用、简化、效率清理 |
| **fewer-permission-prompts** | 扫描记录，把常用只读工具加进允许列表 |
| **loop** | 定时循环运行 prompt 或命令 |
| **claude-api** | Claude API / Anthropic SDK 参考 |
| **workflow-authoring** | 编写 Workflow 脚本、阶段与并行 agent |
| **run** | 启动并驱动项目 app，验证改动 |
| **init** | 初始化 `CLAUDE.md` 代码库文档 |
| **security-review** | 对当前分支变更做安全审查 |
| **plugin-authoring** | 写 Claude Code 插件：面板、状态栏、hook 等 |

---

## 4. 已安装但未启用（3 个插件 / 16 skills）

`installed_plugins.json` 有记录、cache 目录存在，但 `enabledPlugins` 里没有；当前会话不会出现在 Skill 列表。

| 插件 | 版本 | Skills | 说明 |
|---|---|---:|---|
| **superpowers** | 7.0.0 | 15 | 工程工作流：brainstorming → plan → worktree → TDD → review → finish |
| **frontend-design** | 1.1.1 | 1 | UI/UX 实现的前端设计 skill |
| **security-guidance** | 2.0.17 | 0 | 安全 hook / diff review，不是 skill |

启用方式：`/plugin` 里打开，或在 `settings.json` 的 `enabledPlugins` 里加 `"插件名@marketplace": true`。

---

## 5. 只剩元数据的旧插件（5 个 / 32 skills）

`installed_plugins.json` 还留着记录，但 cache 安装目录已经不存在，重装前不可用。

| 插件 | 版本 | Skills |
|---|---|---:|
| **ui-ux-pro-max** | 2.6.2 | 7 |
| **mattpocock-skills** | 1.2.0 | 22 |
| **cc-launch-check** | 1.0.0 | 1 |
| **owasp-security** | unknown | 1 |
| **secure-dev** | unknown | 1 |

旧版 README 里这 32 个的详细条目已移除；需要时按原仓库重装，再加回「当前可用」。

---

## 6. 常用入口

| 想做什么 | 用哪个 |
|---|---|
| 查一家公司 / 新客户 | `/company-background-check:company-background-check` |
| 从老客户名单找潜客 | `/customer-acquisition:customer-acquisition` |
| 整理这一周的成果 | `/weekly-report:weekly-report` |
| 批量解析 ET `.prj` | `et-prj-corpus` |
| 不打开 ET，查 M 码成品尺寸 | `et-prj-headless` |
| JCH 花型换色 | `jch-recolor` |
| 逆向 binary / Electron / 固件 | `reverse-engineer-anything` |
| 图表 / 可视化 | `dataviz` |
| 审查 diff / PR | `code-review` 或 `security-review` |

---

## 7. 维护口径

```bash
# 用户 skills
ls ~/.claude/skills

# 已启用插件
jq '.enabledPlugins' ~/.claude/settings.json

# 已安装插件（含未启用 / 只剩元数据）
jq '.plugins | keys' ~/.claude/plugins/installed_plugins.json

# 数一下每个插件里有多少 SKILL.md
find ~/.claude/plugins/cache -name SKILL.md | wc -l
```

口径：

- **启用**：`~/.claude/skills/<name>/SKILL.md` 存在，或 `enabledPlugins` 为 `true`。
- **已安装未启用**：`installed_plugins.json` 有记录、cache 目录存在，但 `enabledPlugins` 没有。
- **只剩元数据**：`installed_plugins.json` 有记录、cache 目录不存在。
- **内置**：Claude Code 自带，随版本变化；不在 `~/.claude/skills` 里。

本仓库是索引，不是 skill 源码分发。第三方 skill / 插件的版权和许可见各自仓库；自建 skill 的代码留在本机或各自项目里。

---

## 8. 相关链接

| 资源 | URL |
|---|---|
| Claude Code 文档 | <https://docs.anthropic.com/en/docs/claude-code> |
| Claude 官方插件市场 | <https://github.com/anthropics/claude-plugins-official> |
| Superpowers | <https://github.com/obra/superpowers> |
| weekly-report | <https://github.com/zisonzishen0415-stack/weekly-report> |
| 个人网站 | <https://zisonzishen0415-stack.github.io/> |

---

> 维护者：[@zisonzishen0415-stack](https://github.com/zisonzishen0415-stack)
