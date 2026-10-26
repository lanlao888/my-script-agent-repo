# 🎬 AI Short Video Workflow Agent (短剧自动化创作流水线)

本项目是一套专为短剧创作打造的 **AI Agent 与提示词规范库**。通过结构化的 Prompt 编排，实现从“小说/原文 ➔ 格式化剧本 ➔ 资产提取 ➔ 分镜拆解 ➔ 生图/生视频提示词”的全流程本地/云端纯文本协作。

---

## 📁 目录结构

```text
├── workspace/
│   └── prompts/            # 4 大 Agent 核心系统角色 Prompt
│       ├── script_rewriter.md
│       ├── extractor.md
│       ├── storyboard.md
│       └── prompt_generator.md
└── skills/                 # 4 大 Skill 细化规则与参数规范
    ├── script-rewriter/
    ├── extractor/
    ├── storyboard/
    └── prompt-generator/
