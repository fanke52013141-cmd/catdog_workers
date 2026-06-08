# 当前项目成果索引

本文件用于快速了解目前已经完成的项目文件、内容资产和工作流。

## 1. 已确认的 IP 与账号设定

- 账号名：打工喵呼噜噜。
- 主 IP：呼噜噜 / 胡露露，猫系低电量打工人。
- 副 IP：啊呜呜，呼噜噜的好朋友，不是每条都出现。
- 视觉风格：3D 毛绒动画风。
- 视频时长：1 分钟以内，普通内容建议 15-45 秒。
- 首月节奏：每两天 1 条视频。
- 首批重点：热点和双人互动。
- 工具链：Codex imagegen 生图、即梦生视频、MiniMax AI 配音、剪映剪辑。
- 热点接口调研：已找到开源方案 `imsyy/DailyHotApi`，推荐自部署；公开示例接口不作为稳定依赖。
- 封面方向：建议统一做海报风格，详见 `docs/cover-poster-style-guide.md`。
- 账号核心：用 AI 视频表达打工人的丧感、共鸣和对美好生活的坚持。

## 2. 已完成的核心文档

| 文件 | 用途 |
| --- | --- |
| `README.md` | 项目入口说明 |
| `AGENTS.md` | 项目长期协作规则 |
| `docs/project-blueprint.md` | Codex 任务执行框架总蓝图 |
| `docs/workflow-stage-map.md` | 视频制作阶段、Skill 与输出目录 |
| `docs/content-production-workflow.md` | 内容创作流程与短视频生存法则 |
| `docs/hot-topic-selection-guide.md` | 热点选择、打分和转译规则 |
| `docs/asset-library-plan.md` | 可复用资产库规划 |
| `docs/missing-assets-and-decisions.md` | 缺失资产与待确认决策 |
| `docs/pending-confirmations.md` | 后续需要逐项确认的问题 |

## 3. 已完成的角色参考

| 文件 | 用途 |
| --- | --- |
| `references/ip-character-summary.md` | 生产版角色摘要 |
| `references/voice-and-language-style.md` | 声线、说话方式、口头禅 |

## 4. 已完成的 Skill

| Skill | 作用 |
| --- | --- |
| `produce-short-video` | 单条视频总编排 |
| `collect-hot-topics` | 热点收集与初筛 |
| `select-topic-angle` | 选题角度与 brief |
| `plan-content-calendar` | 内容日历 |
| `write-short-video-script` | 1 分钟以内脚本 |
| `develop-ip-assets` | IP 资产补齐 |
| `generate-production-prompt` | 分镜与 AI 提示词 |
| `execute-ai-production` | AI 生产执行记录 |
| `package-publish-plan` | 发布包装 |
| `review-video-output` | 成片审核 |
| `analyze-publish-performance` | 发布后数据复盘 |

## 5. 已完成的模板

| 模板 | 用途 |
| --- | --- |
| `templates/hot-topic-pool-template.md` | 热点池 |
| `templates/topic-brief-template.md` | 选题 brief |
| `templates/short-video-script-template.md` | 短视频脚本 |
| `templates/asset-brief-template.md` | IP 资产 brief |
| `templates/shot-list-template.md` | 分镜 |
| `templates/production-prompt-template.md` | AI 生产提示词 |
| `templates/production-run-template.md` | AI 生产执行记录 |
| `templates/publish-package-template.md` | 发布包装 |
| `templates/performance-review-template.md` | 发布后复盘 |

## 6. 输出目录

所有生产产物默认写入 `outputs/` 下的对应目录：

- `outputs/hot_topics/`
- `outputs/topic_briefs/`
- `outputs/scripts/`
- `outputs/asset_briefs/`
- `outputs/shot_lists/`
- `outputs/prompts/`
- `outputs/production_runs/`
- `outputs/publish_packages/`
- `outputs/reviews/`
- `outputs/performance_reviews/`

本项目不自动同步到任何外部平台，不自动发布视频。
