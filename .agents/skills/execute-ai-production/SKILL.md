---
name: execute-ai-production
description: 记录和管理“打工喵呼噜噜”短视频的 AI 生成、配音、音效和剪辑执行过程。用于脚本/分镜/提示词完成后跟踪生成素材、工具链、失败问题和可复用素材；不替代具体生成工具，不自动发布。
---

# Execute AI Production

## 工作定位

把已经完成的脚本、分镜和提示词推进到实际素材生产阶段，并记录每个工具的输入、输出、问题和可复用素材。本 Skill 不是某个具体 AI 工具的教程，而是生产执行记录和问题沉淀。

## 输入

```yaml
script_file: ""
shot_list_file: ""
prompt_file: ""
asset_briefs:
  - ""
tools:
  image: "待确认"
  video: "待确认"
  voice: "待确认"
  editing: "待确认"
```

## 输出

写入：

```text
outputs/production_runs/YYYYMMDD_栏目_主题.md
```

内容包括：

- 工具链记录。
- 每个环节的输入和输出。
- 生成问题。
- 修复方式。
- 可复用素材。
- 待补资产。

## 执行步骤

1. 读取脚本、分镜、提示词和资产 brief。
2. 按图片、视频、配音、音效/BGM、剪辑拆分生产环节。
3. 为每个环节记录工具、输入文件、输出素材和状态。
4. 遇到角色漂移、动作失败、画面不稳定、配音不贴脸等问题时，记录原因判断。
5. 判断问题应反哺到提示词、资产 brief、角色参考还是剪辑方案。
6. 使用 `templates/production-run-template.md` 输出生产执行记录。

## 检查点

- [ ] 每个素材输出都有来源。
- [ ] 每个失败问题都有修复建议。
- [ ] 新产生的可复用素材已记录。
- [ ] 不自动发布，不自动同步。

## 失败处理

- 工具链未确认：保留工具为 `待确认`，仍输出执行计划。
- 生成失败：记录失败原因，不删除原提示词。
- 角色漂移严重：退回 `develop-ip-assets` 或 `generate-production-prompt`。
- 剪辑节奏弱：退回 `write-short-video-script` 或分镜阶段。

