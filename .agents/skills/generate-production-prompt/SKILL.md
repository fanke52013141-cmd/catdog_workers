---
name: generate-production-prompt
description: 将短视频脚本拆成分镜，并生成图像、视频、音频生产提示词。
---

# Generate Production Prompt

## 目的

把确认后的脚本转成可供 AI 图像、AI 视频、配音和剪辑使用的生产提示词。

## 何时使用

- 脚本确认后。
- 需要为单个镜头生成图片或视频时。
- 需要把角色一致性要求写入提示词时。

## 输入

```yaml
script_file: "脚本路径或脚本文本"
target_tool: "待确认 | 即梦 | 可灵 | Runway | Pika | Midjourney | 其他"
visual_style: "待确认或指定风格"
asset_refs:
  - "三视图/表情/场景参考"
duration_seconds: 15-35
```

## 输出

- 分镜表。
- 每个镜头的画面提示词。
- 负面提示词。
- 音频/配音提示。
- 缺失资产记录。

## 流程

1. 按 3-6 秒一镜拆解脚本。
2. 每个镜头都写清角色外观、状态、场景、动作、道具。
3. 角色一致性提示词必须包含发卡/尾巴等识别点。
4. 使用 `templates/shot-list-template.md` 和 `templates/production-prompt-template.md`。
5. 工具链未知时输出通用提示词。

## 失败处理

- 如果镜头太复杂，拆成多个简单镜头。
- 如果角色漂移，强化参考图和负面提示词。
- 如果动作难生成，改为静态表情 + 剪辑节奏实现。

