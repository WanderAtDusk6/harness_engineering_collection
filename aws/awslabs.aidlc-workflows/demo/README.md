# demo

AI-DLC 的「harness 产物」就是 [source/aidlc-rules/](../source/aidlc-rules/) 这个文件夹——release zip 解压后扔进项目里的就是它。

```
aidlc-rules/
├── aws-aidlc-rules/
│   └── core-workflow.md                # 核心工作流规则
└── aws-aidlc-rule-details/             # 按条件加载的细则
    ├── common/
    ├── inception/                      # 阶段一:需求探索
    ├── construction/                   # 阶段二:实现
    ├── operations/                     # 阶段三:运维
    └── extensions/                     # 可选扩展
```

各家 agent 的接入方式在 [source/README.md](../source/README.md) 里:Kiro、Amazon Q Developer、Cursor、Cline、Claude Code 各自的 setup 步骤把 `aidlc-rules/` 链接或拷贝到对应 dotfile 路径。
