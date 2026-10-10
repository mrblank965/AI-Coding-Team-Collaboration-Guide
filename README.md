# AI Coding Team Collaboration Guide

一套面向学生团队和小型项目组的中文协作指南，介绍如何使用 GitHub、VS Code 与 Claude Code、Codex 等 AI 编程助手完成多人开发。

本仓库同时保留：

- 一份可以套用到不同项目的**通用协作指南**；
- 一份来自真实课程项目的 **JobAgent 案例指南**；
- 一份可以直接复制给 AI 编程助手的**通用 Prompt 合集**；
- 配套的 VS Code 操作截图。

## 文档导航

| 文件 | 内容 | 适合谁 |
| --- | --- | --- |
| [AI_CODING_TEAM_COLLABORATION_GUIDE.md](./AI_CODING_TEAM_COLLABORATION_GUIDE.md) | 不依赖具体项目和技术栈的完整协作方法，包括分支设计、成员加入、同步、开发、Commit、Push、PR、冲突处理和发布流程 | 想为自己的团队建立协作规范的人 |
| [JOBAGENT_CASE_COLLABORATION_GUIDE.md](./JOBAGENT_CASE_COLLABORATION_GUIDE.md) | JobAgent 五人课程项目的实际落地案例，包括真实的功能分支划分、职责设计、工作流程和经验说明 | 想参考一个具体项目如何应用这些规则的人 |
| [AI_CODING_TEAM_ESSENTIAL_PROMPTS.md](./AI_CODING_TEAM_ESSENTIAL_PROMPTS.md) | 可以直接复制给 Claude Code、Codex 等代码助手的分阶段 Prompt，包括首次准备、同步、开发、自查、Commit、Push、PR 和集成验收 | 已经开始开发，希望 AI 按规则执行 Git 和编码任务的成员 |
| [`assets/vscode-team-workflow/`](./assets/vscode-team-workflow/) | VS Code 分支切换、同步、源代码管理和 AI 对话示例截图 | 第一次使用 VS Code 和 Git 的成员 |

## 三份文档有什么区别

### 1. 通用协作指南

文件：[`AI_CODING_TEAM_COLLABORATION_GUIDE.md`](./AI_CODING_TEAM_COLLABORATION_GUIDE.md)

它回答的是“团队应该怎样设计流程”：

- 为什么使用 `main → integration → feature` 三层分支；
- 分支、Commit、Push 和 Pull Request 有什么区别；
- 负责人如何搭建仓库和划分职责；
- 成员第一次如何 Clone、切换分支和同步；
- 如何防止覆盖其他成员的提交；
- 如何审核功能 PR 和完成最终发布；
- AI 编程协作中应设置哪些安全边界。

文中的项目名称、仓库地址、分支和负责范围都可以替换，适用于前端、后端、数据分析、课程作业等不同类型项目。

### 2. JobAgent 案例指南

文件：[`JOBAGENT_CASE_COLLABORATION_GUIDE.md`](./JOBAGENT_CASE_COLLABORATION_GUIDE.md)

它回答的是“这些规则在一个真实项目中怎样落地”：

- 如何根据产品页面和功能拆分分支；
- 为什么增加 `feature/integration`；
- 每个功能分支负责什么；
- 成员如何查看完整网站但只修改自己的模块；
- 从功能开发到集成、再到 main 的实际流程；
- 团队讨论过程中遇到的常见误区。

案例中的仓库名、目录和分支来自 JobAgent，只用于演示，不代表其他团队必须采用相同结构。

### 3. 通用 Prompt 合集

文件：[`AI_CODING_TEAM_ESSENTIAL_PROMPTS.md`](./AI_CODING_TEAM_ESSENTIAL_PROMPTS.md)

它回答的是“每一步应该怎样和 AI 说”：

1. 第一次克隆后准备功能分支；
2. 开工前安全同步 integration；
3. 每次新会话发送共同工作规则；
4. 布置具体开发和修复任务；
5. 运行自查和人工验收；
6. 创建本地 Commit；
7. Push 前检查远程分支；
8. 普通 Push 到远程同名功能分支；
9. 创建功能 PR；
10. 审核 PR；
11. 负责人维护 integration；
12. 创建 integration → main 的最终 PR。

使用时将以下占位符替换为团队实际内容：

```text
【项目名称】
【仓库地址】
【角色】
【功能分支】
【负责范围】
【项目约定文档】
```

同一个 AI 会话不需要反复粘贴全部规则。推荐先发送一次“共同工作规则”，后续按任务阶段发送对应的短 Prompt。

## 推荐阅读顺序

### 团队负责人

```text
通用协作指南
→ 根据项目划分分支和职责
→ 参考 JobAgent 案例检查是否遗漏集成层
→ 把 Prompt 合集发给成员
```

### 第一次参与 GitHub 协作的成员

```text
README 文档导航
→ 通用指南中的“成员第一次加入”和“VS Code 六步流程”
→ Prompt 合集第 2～4 节
→ 开始自己的第一个任务
```

### 已经开始开发的成员

可以直接打开 Prompt 合集，根据当前阶段复制：

```text
同步 → 开发 → 自查 → Commit → 远程检查 → Push → PR
```

## 默认分支模型

```text
main（稳定版本）
  ↓
feature/integration（集成和联调版本）
  ↓
feature/*（成员功能分支）
  ↓ Pull Request
feature/integration
  ↓ 最终 Pull Request
main
```

团队如果使用 `develop`、`staging` 或其他名称，可以统一替换。但必须让所有成员清楚：

- 稳定分支是哪一条；
- 集成分支是哪一条；
- 自己在哪条分支开发；
- 功能 PR 和最终 PR 分别指向哪里。

## 核心安全规则

- 不把密码、验证码、API Key、Token 或 Cookie 发给 AI；
- 不提交真实环境变量文件、真实业务数据和个人隐私；
- 不让 AI 编造 Git 作者姓名和邮箱；
- 不在未确认时安装或升级依赖；
- 不使用 reset、强制推送、删除分支或覆盖文件；
- 不让功能成员直接向 `main` 或 integration 推送；
- AI 修改后必须经过差异检查、自动检查和人工验收；
- Pull Request 只创建，不自动合并。

## 仓库结构

```text
AI-Coding-Team-Collaboration-Guide/
├── README.md
├── AI_CODING_TEAM_COLLABORATION_GUIDE.md
├── JOBAGENT_CASE_COLLABORATION_GUIDE.md
├── AI_CODING_TEAM_ESSENTIAL_PROMPTS.md
└── assets/
    └── vscode-team-workflow/
        ├── 01-select-feature-branch.png
        ├── 02-sync-changes-confirmation.png
        ├── 03-common-prompt.png
        ├── 04-sync-integration-prompt.png
        ├── 05-source-control-changes.png
        └── 06-sync-after-commit.png
```

## 图片与 Notion

Markdown 可以使用相对路径插入图片。本仓库的图片统一保存在 `assets/` 中，因此在 GitHub 上可以直接显示。

如果需要导入 Notion，建议同时下载 Markdown 文件和 `assets` 文件夹，并打包成 ZIP 后导入。只导入单独的 `.md` 文件可能导致本地相对路径图片丢失。

## 一句话原则

```text
先同步，后开发；
先分析，后修改；
先验收，后提交；
先检查远程，后推送；
先进入 integration，稳定后再进入 main。
```
