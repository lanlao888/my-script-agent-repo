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

阶段二：资产提取（Extractor）
操作说明：去仓库复制 extractor.md 的 Raw 源码，填入阶段一生成的剧本后发送给 AI。

Plaintext
【系统角色定义】
你现在是短剧资产提取专家。请严格遵循以下规范：
[在此粘贴 github 上 extractor.md 与 SKILL.md 的 Raw 源码]

【输入内容】
以下是刚生成的短剧剧本：
[在此粘贴阶段一生成的短剧剧本]

【任务要求】
请提取出该集剧本中的所有：
1. 核心角色（包含外貌、服装、性格特征）
2. 场景清单（包含时间、地点、氛围）
3. 关键道具清单

阶段三：分镜拆解（Storyboard Director）
操作说明：去仓库复制 storyboard.md 的 Raw 源码，填入剧本和资产清单后发送给 AI。

Plaintext
【系统角色定义】
你现在是短剧分镜导演。请严格遵循以下规范：
[在此粘贴 github 上 storyboard.md 与 SKILL.md 的 Raw 源码]

【输入内容】
剧本：[在此粘贴阶段一生成的剧本]
资产清单：[在此粘贴阶段二提取的资产]

【任务要求】
请将该剧本拆解为逐镜头的分镜脚本，包含：景别（特写/中景/远景）、镜头运动（推拉摇移）、画面描述、音效与台词配音。
阶段四：AI 提示词生成（Prompt Generator）
操作说明：去仓库复制 prompt_generator.md 的 Raw 源码，填入分镜后发送给 AI。

Plaintext
【系统角色定义】
你现在是 AI 视觉提示词专家。请严格遵循以下规范：
[在此粘贴 github 上 prompt_generator.md 及相关 Prompt 规范的 Raw 源码]

【输入内容】
以下是分镜脚本：
[在此粘贴阶段三生成的分镜内容]

【任务要求】
请为镜头 1 至镜头 N 依次生成：
1. Midjourney/SD 生图提示词（包含英文 Prompt、负向词、参数如 --ar 9:16）
2. Sora/Runway/Pika 生视频提示词（包含动态镜头描写、光影风格）

---

粘贴完成后点击 **Commit changes** 保存[cite: 8]，你的 GitHub 首页就会完整显示出阶段一到阶
