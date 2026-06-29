# demo

整个 `source/` 子目录就是这个 harness 的 demo——ECC 不是"装到目标项目里生成文件"的类型,而是把自己整个 repo 作为一份**多目标适配包**:

- 顶层 13+ 个 dotfile 目录(`.claude/`、`.cursor/`、`.codex/`、`.gemini/`、`.zed/` 等)是各家 agent 的入口配置
- `agents/`、`commands/`、`hooks/`、`contexts/`、`skills/` 是**共享内容**,被上面那些 dotfile 目录引用或复制

要看典型文件,推荐入口:

- [source/README.md](../source/README.md) — 项目总览
- [source/AGENTS.md](../source/AGENTS.md) — AGENTS.md spec 入口
- [source/.claude/](../source/.claude/) — Claude Code 适配(`commands/`、`skills/`、`rules/`、`identity.json` 等)
- [source/.cursor/](../source/.cursor/) — Cursor 适配
- [source/agents/](../source/agents/)、[source/commands/](../source/commands/) — 跨 agent 共享的内容池
