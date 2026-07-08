# 周报汇总

> 每周日更新，按老师要求的格式：
> 1. 本周目标是什么
> 2. 我实际完成了什么
> 3. 遇到哪些问题，我自己尝试了哪些解决办法
> 4. 我对这个问题现在的理解是什么
> 5. 下周准备做什么
> 6. 需要老师判断或建议的问题是什么

---

## 第1周：工具环境搭建（2026-06-25 至 2026-07-01）

### 1. 本周目标是什么

本周是实习的第一周，核心目标是按照老师要求，把"工作台"搭起来，建立学习和做事的基础操作系统。具体目标包括：

- 注册 GitHub 账号，创建仓库 `ai-summer-2026`
- 安装并配置终端环境（Windows Terminal + PowerShell 7）
- 安装 Git 并完成基础配置（user.name、user.email、默认分支）
- 安装 Python 和 uv（Python 项目管理工具）
- 安装 VS Code 编辑器及必要插件（Python、Markdown All in One、GitLens）
- 安装 Obsidian 用于阅读和管理 Markdown 文档
- 安装 Rust 工具链（cargo）及现代命令行工具（starship、zoxide、dufs、rg、fd、bat、eza）
- 安装 TypeScript 工具链（bun）
- 创建仓库基础文件：README.md、tools.md、ai-usage-log.md、weekly-log.md
- 完成第一次 Git 提交并推送到 GitHub
- 理解"仓库里放什么 vs 系统里装什么"的区别

---

### 2. 我实际完成了什么

#### ✅ 核心工具安装（全部验证通过）

| 工具 | 验证命令 | 状态 |
|------|----------|------|
| Git | `git --version` | ✅ 已安装 |
| Python | `python --version` | ✅ 已安装 |
| uv | `uv --version` | ✅ 已安装 |
| VS Code | `code --version` | ✅ 已安装 |
| Windows Terminal | 开始菜单打开 | ✅ 已安装 |
| PowerShell 7 | `pwsh --version` | ✅ 已安装 |
| Obsidian | 应用程序打开 | ✅ 已安装 |

#### ✅ 现代命令行工具安装（Rust 工具链）

| 工具 | 验证命令 | 安装方式 | 状态 |
|------|----------|----------|------|
| Rust (rustc) | `rustc --version` | rustup.rs | ✅ |
| cargo | `cargo --version` | rustup.rs 自带 | ✅ |
| starship | `starship --version` | `cargo install starship` | ✅ |
| zoxide | `zoxide --version` | `cargo install zoxide` | ✅ |
| dufs | `dufs --version` | `cargo install dufs` | ✅ |
| rg (ripgrep) | `rg --version` | `cargo install ripgrep` | ✅ |
| fd | `fd --version` | `cargo install fd-find` | ✅ |
| bat | `bat --version` | `cargo install bat` | ✅ |
| eza | `eza --version` | `cargo install eza` | ✅ |

#### ✅ TypeScript 工具链

| 工具 | 验证命令 | 状态 |
|------|----------|------|
| bun | `bun --version` | ✅ 已安装 |

#### ✅ 仓库创建与文件产出

| 文件 | 作用 | 状态 |
|------|------|------|
| `README.md` | 项目介绍与仓库结构说明 | ✅ 已创建并推送 |
| `tools.md` | 记录所有安装的工具、版本、安装方式、使用体验 | ✅ 已创建并推送 |
| `ai-usage-log.md` | 记录本周与 AI 协作的 2 次典型对话 | ✅ 已创建并推送 |
| `weekly-log.md` | 本周周报（本文件） | ✅ 已创建并推送 |
| `.gitignore` | 忽略虚拟环境、缓存等不该上传的文件 | ✅ 已创建并推送 |
| `版本检查命令速查表.md` | 汇总所有工具的版本检查命令 | ✅ 已创建并推送 |

#### ✅ Git 基础操作实践

- 完成 Git 全局配置（user.name、user.email、defaultBranch）
- 创建 GitHub 仓库并 clone 到本地
- 完成 `git add` → `git commit` → `git push` 完整流程
- 理解 commit message 的写法（"第一周：搭建基础工具环境"）

---

### 3. 遇到哪些问题，我自己尝试了哪些解决办法

#### 问题 1：Rust 工具链通过 cargo 安装时编译失败

- **现象**：执行 `cargo install starship` 时报错，提示缺少 C++ 构建工具
- **尝试**：
  1. 阅读错误信息，发现是 Windows 缺少 MSVC 编译器
  2. 搜索"cargo install 失败 Windows C++ build tools"
  3. 尝试从 GitHub releases 直接下载预编译的 `.exe` 文件
- **解决**：
  - starship、zoxide 通过 GitHub releases 下载预编译版
  - 其余工具（rg、fd、bat、eza、dufs）安装 Visual Studio Build Tools（约 2GB）后通过 cargo 成功安装
- **耗时**：约 1 小时

#### 问题 2：uv 安装后终端识别不到

- **现象**：安装 uv 后，终端输入 `uv --version` 显示 "command not found"
- **尝试**：
  1. 重新打开终端（让环境变量刷新）
  2. 在 PowerShell 中输入 `$env:PATH` 查看环境变量
  3. 发现 uv 安装在 `C:\Users\用户名\.local\bin`，但 PATH 未自动添加
- **解决**：手动将该路径添加到系统环境变量，重新打开终端后验证成功
- **耗时**：约 20 分钟

#### 问题 3：分不清"哪些工具装在系统里"和"哪些放进仓库里"

- **现象**：担心把 Git、Python 等可执行文件误放进仓库，导致仓库混乱
- **尝试**：
  1. 打开仓库文件夹查看是否有 `.exe` 文件
  2. 确认仓库里只有 `.md` 文件和项目文件夹
  3. 查阅 AI 给出的"仓库里放什么 vs 系统里装什么"说明
- **解决**：理解了"仓库 = 食谱本（记录文件），系统 = 厨房（安装软件）"的类比；创建了 `.gitignore` 文件排除虚拟环境和缓存文件
- **耗时**：约 15 分钟

#### 问题 4：对大量陌生技术术语感到困惑

- **现象**：老师 PDF 中出现 repo、commit、push、shell、uv、cargo 等数十个术语，一开始完全不知道在说什么
- **尝试**：
  1. 把每个术语列出来，逐个搜索含义
  2. 向 AI 请求"所有英文词的解释"，获得了一份术语速查表
- **解决**：建立了自己的术语速查表，每个词用一句话解释，降低了认知门槛
- **耗时**：约 30 分钟（阅读 + 整理）

---

### 4. 我对这个问题现在的理解是什么

#### 对"工具链"的理解

以前我以为"学编程就是学写代码"，现在理解了：写代码只是很小一部分。**真正影响效率的是工具链**——你怎么管理文件、怎么记录历史、怎么安装依赖、怎么写文档。工具链顺了，写代码只是水到渠成的事情。

#### 对 Git 的理解

Git 不是备份工具，而是"时间线工具"。它让我可以：
- 记录每次修改的"为什么"（commit message）
- 随时回到之前的任意状态
- 在 GitHub 上展示我的工作，让别人能复现

老师说的"别人 clone 之后按 README 能跑起来"——我现在明白这意味着我的仓库要足够"自解释"。

#### 对"仓库 vs 系统"的理解

- **系统安装**：Git、Python、uv、VS Code、Rust 等软件程序——装在电脑里，所有项目共享
- **仓库文件**：README、tools.md、代码、配置——放在 GitHub 上，是这个项目的专属记录
- **不该放仓库的**：虚拟环境、缓存、安装包、个人密码——用 `.gitignore` 排除

#### 对 AI 使用的理解

老师要求"从问问题变成共同工作"，我本周实践后发现：
- **有效提问**：给完整背景（我在做什么、为什么做、卡在哪、希望输出什么格式）
- **无效提问**：只发一句"这个怎么弄"
- **关键改进**：记录 AI 的"有用之处"和"不可靠之处"，训练自己判断信息质量的能力

#### 对"持续推进"的理解

老师不期待我做复杂成果，但要求"每周有清楚产出"。我本周最大的产出不是"装了多少软件"，而是：
- 建立了一套可复用的记录系统（tools.md、ai-usage-log.md、weekly-log）
- 理解了每个工具"为什么装"，而不是盲目安装
- 完成了第一次完整的 Git 工作流（add → commit → push）

---

### 5. 下周准备做什么

#### 学习任务：Missing Semester（MIT 免费课程）

- **重点章节**：Shell 工具与脚本、Git 进阶、SSH 与远程服务器、编辑器（Vim/VS Code）、tmux
- **产出目标**：写一份"我的命令行工作流"文档，记录我自己常用的命令组合，不是照抄课程
- **时间安排**：每天 1-2 小时，预计 5-6 天完成

#### 实践目标

- 学会用 tmux 分屏操作（终端复用）
- 学会用 SSH 连接远程服务器（基础操作）
- 练习 Git 进阶操作：branch、merge、冲突处理
- 用命令行完成日常文件操作（创建、移动、复制、查找），而不是用鼠标

#### 补充工具（如需）

- 如果 Missing Semester 提到某个我还没装的工具，按需补充
- 继续完善 tools.md，把实际使用的体验写进去（而不是只列安装记录）

---

### 6. 需要老师判断或建议的问题是什么

#### 问题 1：关于 Rust 工具链的安装范围

老师提到"至少装好 cargo，了解一些常见工具"，我本周把提到的 8 个工具（starship、zoxide、dufs、rg、fd、bat、eza）全部安装了。请问：
- 这个数量是否合适，还是说我应该"了解即可"，不需要全部装完？
- 有些工具（如 dufs）目前还用不上，是否有必要现在就装？

#### 问题 2：关于 AI 使用日志的深度

我本周记录了 2 次 AI 对话，但感觉还不够深入。老师要求"每周选 2-3 次比较有代表性的 AI 对话"——请问：
- 代表性是指"技术问题"还是"思维问题"？比如我纠结"要不要全装 Rust 工具"这个决策过程，是否值得记录？
- AI 使用日志的格式是否需要更结构化，还是目前这个模板就够了？

#### 问题 3：关于 tools.md 的颗粒度

目前的 tools.md 记录了每个工具的版本、安装方式、用途、使用体验。请问：
- 是否需要加入"为什么选这个工具而不是替代品"（比如为什么用 uv 而不是 conda）？
- 是否需要记录"安装失败的尝试"，还是只写最终成功的路径？

#### 问题 4：关于下周 Missing Semester 的学习策略

Missing Semester 内容很多（Shell、Git、Vim、SSH、tmux 等），请问：
- 是否需要全部看完，还是重点看我目前最缺的（Shell 和 Git 进阶）？
- "我的命令行工作流"文档应该写到什么深度？是罗列常用命令，还是写成一个可复用的操作手册？

---

## 本周产出附件清单

| 文件 | 路径 | 说明 |
|------|------|------|
| README.md | `ai-summer-2026/README.md` | 项目介绍与仓库结构 |
| tools.md | `ai-summer-2026/tools.md` | 工具安装与使用记录 |
| ai-usage-log.md | `ai-summer-2026/ai-usage-log.md` | AI 协作使用日志 |
| weekly-log.md | `ai-summer-2026/weekly-log.md` | 本周周报（本文件） |
| .gitignore | `ai-summer-2026/.gitignore` | 忽略规则 |
| 版本检查命令速查表.md | `ai-summer-2026/版本检查命令速查表.md` | 所有工具版本检查命令汇总 |

---

*第 1 周报完*
