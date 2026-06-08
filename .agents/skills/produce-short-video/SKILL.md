---
name: produce-short-video
description: 编排“打工喵呼噜噜”单条短视频从热点/灵感到本地发布包的完整生产流程。用于用户要求做一条视频、从热点生成脚本、把灵感落成选题 brief/脚本/分镜/提示词/发布包装；不执行自动发布或平台同步。
---

# Produce Short Video

## 工作定位

编排单条 1 分钟以内短视频的完整生产链路。本 Skill 负责决定调用顺序和检查输出，不把所有细节写在一个文件里。

## 输入

```yaml
source_type: "热点 | 日常灵感 | 魔幻设定 | 双人关系 | 用户指定"
topic: ""
column: "呼噜噜看热点 | 呼噜噜的怪早晨 | 打工喵生存报告 | 呼噜噜与啊呜呜 | 待判断"
target_duration: "1 分钟以内，建议 15-45 秒"
available_assets:
  - ""
need_outputs:
  - "topic_brief"
  - "script"
  - "shot_list"
  - "prompt"
  - "publish_package"
```

## 输出

按阶段写入：

- `outputs/hot_topics/`：热点池，仅热点任务需要。
- `outputs/topic_briefs/`：选题 brief。
- `outputs/scripts/`：短视频脚本。
- `outputs/asset_briefs/`：新增资产 brief，可选。
- `outputs/shot_lists/`：分镜表。
- `outputs/prompts/`：生产提示词。
- `outputs/production_runs/`：AI 生产执行记录。
- `outputs/publish_packages/`：发布包装。
- `outputs/reviews/`：成片审核报告，初版视频生成后使用。
- `outputs/performance_reviews/`：发布后数据复盘，用户提供数据后使用。

## 编排流程

1. 如果输入是热点或用户要求看热点，先调用 `collect-hot-topics`。
2. 调用 `select-topic-angle`，把热点或灵感转成选题 brief。
3. 调用 `write-short-video-script`，产出 1 分钟以内脚本。
4. 检查脚本是否需要新资产；如需要，调用 `develop-ip-assets`。
5. 调用 `generate-production-prompt`，产出分镜和 AI 生产提示词。
6. 调用 `execute-ai-production`，记录 AI 生成、配音、音效和剪辑执行过程。
7. 调用 `package-publish-plan`，产出标题、封面文案、简介、标签和评论引导。
8. 如果用户提供初版视频、截图或视频说明，调用 `review-video-output`。
9. 如果用户提供发布后数据或评论样本，调用 `analyze-publish-performance`。

## 检查点

- [ ] 每个阶段都有本地输出文件。
- [ ] 脚本时长不超过 1 分钟。
- [ ] 前 3 秒有钩子。
- [ ] 至少强化一个 IP 记忆点。
- [ ] 不自动发布，不自动同步。

## 失败处理

- 缺热点数据：跳过热点池，直接把用户提供内容作为选题输入。
- 缺资产：进入资产 brief，不阻断脚本输出。
- 工具链未确认：提示词输出通用版。
- 用户只要某一阶段：只执行对应 Skill，不强制跑完整流程。
