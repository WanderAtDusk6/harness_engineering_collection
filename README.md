# Harness Engineering Collection

面向 coding agent 的代码仓库结构与约定合集。

> ⚠️ **粗略版本,未经人工逐条核验**。当前内容(尤其分类、对比表格里的描述)由 AI 协助生成,只做了初步整理,还没有逐项查证。请按 WIP 看待,链接和归类可能有误,欢迎纠正。

## 目录约定

每个 harness 一个文件夹,包含两个子目录:

- `source/` — 上游 repo(git submodule);若无开源 repo,放一个指向原始来源的说明文件
- `demo/` — 该 harness 的示例文件结构

## 已收录

排序:基础约定 / 事实标准 → 官方厂商 harness → 社区项目。

### 基础约定 / 事实标准

单文件约定,丢进 repo 即用。性质:`开放`=中立组织维护,`事实`=单厂发起、社区广泛采用。

| Spec                                                                                                                                                                                                                                                                       | 来源/相关                                                                                                                                                                                                                                     | 性质 | 示例                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- | --------------------------------------------------------------------------- |
| **AGENTS.md** ([source](https://github.com/agentsmd/agents.md) · [demo](specs/agents.md/demo/))                                                                                                                                                                            | https://agents.md/                                                                                                                                                                                                                            | 开放 | 项目根 `AGENTS.md` — 怎么 build/test/跑                                     |
| **SKILL.md** ([source](https://github.com/agentskills/agentskills) · [demo](specs/skill.md/demo/))                                                                                                                                                                         | [agentskills.io](https://agentskills.io) · [Anthropic 原文](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [博客](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | 开放 | skill 目录根 `SKILL.md`,YAML frontmatter                                    |
| **DESIGN.md** ([source](https://github.com/google-labs-code/design.md) · [demo](google/google-labs-code.design-md/demo/) · [spec](https://github.com/google-labs-code/design.md/blob/main/docs/spec.md) · [design.md合集](https://github.com/VoltAgent/awesome-design-md)) | Google Labs 提出                                                                                                                                                                                                                              | 事实 | 项目根 `DESIGN.md`,设计 token + 说明;`npx @google/design.md lint DESIGN.md` |

### 官方厂商

| Harness                                                                                                                                                                          | 实现                                                                                                                                                                                                             | 文件结构                                                                                                                                                | Agent 入口                                                               | 状态存储                                                            | 接入方式                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------- | --------------------------------- |
| **Anthropic · autonomous-coding** ([source](https://github.com/anthropics/claude-quickstarts/tree/main/autonomous-coding) · [demo](anthropic/anthropic.autonomous-coding/demo/)) | Python + Claude Agent SDK,[博客](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) + [quickstart](https://github.com/anthropics/claude-quickstarts/tree/main/autonomous-coding) | `autonomous_agent_demo.py` + `agent.py` / `client.py` / `security.py` / `progress.py` + `prompts/{app_spec.txt,initializer_prompt.md,coding_prompt.md}` | Python 入口脚本                                                          | 运行时文件(`feature_list.json` / `claude-progress.txt` / `init.sh`) | `pip install -r requirements.txt` |
| **OpenAI · harness engineering** ([source](https://openai.com/zh-Hans-CN/index/harness-engineering/) · [demo](openai/openai.harness-engineering/demo/))                          | 无公开 repo,[博客](https://openai.com/zh-Hans-CN/index/harness-engineering/) + 示例布局                                                                                                                          | `AGENTS.md` + `ARCHITECTURE.md` + `docs/{design-docs,exec-plans,product-specs,references,generated}/`                                                   | `AGENTS.md`                                                              | 文件                                                                | 手动                              |
| **AWS Labs · AI-DLC Workflows** ([source](https://github.com/awslabs/aidlc-workflows) · [demo](aws/awslabs.aidlc-workflows/demo/))                                               | Markdown 规则包 + release zip,[博客](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/)                                                                                                      | `aidlc-rules/{aws-aidlc-rules,aws-aidlc-rule-details}/`(三阶段:inception/construction/operations + extensions)                                          | 各家 agent 的 dotfile(Kiro / Q Developer / Cursor / Cline / Claude Code) | 文件                                                                | 解压 release zip + 按 agent 配置  |

### 社区项目

| Harness                                                                                                                                             | 实现                                                                        | 文件结构                                                                                                                                       | Agent 入口                           | 状态存储 | 接入方式                                |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ | -------- | --------------------------------------- |
| **hoangnb24/repository-harness** ([source](https://github.com/hoangnb24/repository-harness) · [demo](community/hoangnb24.repository-harness/demo/)) | Rust CLI + 安装脚本                                                         | `AGENTS.md` + `docs/`(16 文档 + 7 ADR + 模板)+ `scripts/schema/*.sql` + CLI 二进制                                                             | `AGENTS.md`                          | SQLite   | `irm \| iex` / `curl \| bash`           |
| **affaan-m/ECC** ([source](https://github.com/affaan-m/ECC) · [demo](community/affaan-m.ECC/demo/))                                                 | TypeScript + Shell + npm 包(`ecc-universal`、`ecc-agentshield`)+ GitHub App | 13+ 个 dotfile 目录(`.claude/`、`.cursor/`、`.codex/`、`.gemini/`、`.zed/` 等)共享 `agents/` `commands/` `hooks/` `contexts/` `skills/` 内容池 | 各家 agent 的 dotfile(如 `.claude/`) | 文件     | `npx ecc-universal` / GitHub App / 手动 |

## 常用命令

```bash
# 首次克隆
git clone --recurse-submodules <repo-url>

# 已克隆,初始化 submodule
git submodule update --init --recursive

# 更新所有 submodule 到上游 HEAD
git submodule update --remote --merge
```

Submodule 自动更新由 [`.github/workflows/update-submodules.yml`](.github/workflows/update-submodules.yml) 每周一执行。

## 添加新 harness

```bash
# 有开源 repo
git submodule add -b main <repo-url> <category>/<author>.<repo>/source

# 无开源 repo:在 source/ 内放一个 README.md 说明来源链接
```

`<category>` 取 `specs/`、`anthropic/`、`openai/`、`aws/`、`google/`,均不适用则用 `community/`。
