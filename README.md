# 🎬 AI Short Video Workflow Agent (短剧自动化创作流水线)

本项目是一套专为短剧创作打造的 **AI Agent 与提示词规范库**。通过结构化的 Prompt 编排，实现从“小说原文 ➔ 格式化剧本 ➔ 资产提取 ➔ 分镜拆解 ➔ 生图/生视频提示词”的全流程纯文本协作。

---

## 📁 项目文件路径速查

| 创作阶段 | 核心角色 Prompt 路径 (必选) | 细节规则 Skill 路径 (可选补充) |
| :--- | :--- | :--- |
| **阶段 1：剧本改编** | `workspace/prompts/script_rewriter.md` | `skills/script-rewriter/SKILL.md` |
| **阶段 2：资产提取** | `workspace/prompts/extractor.md` | `skills/extractor/SKILL.md` |
| **阶段 3：分镜拆解** | `workspace/prompts/storyboard.md` | `skills/storyboard/SKILL.md` |
| **阶段 4：提示词生成** | `workspace/prompts/prompt_generator.md` | `skills/prompt-generator/` (对应子文件) |

---

## 🚀 GitHub 网页端调用指南（3 步快速使用）

无需安装任何本地环境，在浏览器打开本仓库即可快速使用：

1. **获取规范源码**：根据上方表格，点击进入对应的 `.md` 文件，点击右上角的 **`Raw`** 按钮（或复制图标 📋）复制代码全文。
2. **组合提示词**：参照下方对应的【调用模版】，将复制的内容粘贴到 `[在此粘贴...]` 位置。
3. **发送给大模型**：打开 ChatGPT / Claude / DeepSeek，将组合好的完整文本一次性发送给 AI。

---

## 📖 4 阶段工作流调用模版

### 阶段一：剧本改编（Script Rewriter）
> **操作说明**：先去仓库复制 `script_rewriter.md` 的 Raw 源码，替换下方方括号内容，填入小说原文后发送给 AI。

```text
【系统角色定义】
你现在是短剧改编大师。请严格遵循以下规范：
[在此粘贴 github 上 script_rewriter.md 与 SKILL.md 的 Raw 源码]

【输入内容】
以下是我的原始小说/故事大纲：
[在此粘贴你的小说或故事原文]

【任务要求】
请按照规范，将其改写为符合短剧节奏（前3秒抓客、高频打脸/爽点、集末留钩子）的标准短剧剧本。
