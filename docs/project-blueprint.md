# Codex 任务执行框架：打工喵呼噜噜 AI 视频项目

## 1. 任务本质定义

- 用户原始目标：为抖音 AI 虚拟 IP 视频账号搭建一个可持续的视频制作项目文件，缺失内容单独记录，后续逐步构建。
- 任务类型：长期内容生产项目管理 + IP 资产库建设 + 短视频批量创作流程。
- State A / 初始状态：已有两份角色圣经，已有账号方向想法，但还缺少统一项目目录、资产清单、制作流程、模板和缺失项管理。
- State B / 终结状态：形成一个可复用项目框架，可以持续补资产、写脚本、生成提示词、审核成片、沉淀 bad case。
- 核心转化路径：角色设定提炼 -> 资产库规划 -> 热点收集 -> 选题 brief -> 1 分钟以内脚本 -> 分镜/提示词 -> 发布包装 -> 成片审核 -> 复盘迭代。
- 关键约束：不能把账号做成纯 AI 炫技；必须强化角色记忆点；资产必须可复用；未知信息标记为 `待确认`。
- 待确认：视觉风格、工具链、更新频率、配音方式、商业禁区。

## 2. Codex 承载面映射

| 内容 | Codex 承载面 | 文件/位置 | 原因 |
| --- | --- | --- | --- |
| 项目长期协作规则 | `AGENTS.md` | `AGENTS.md` | 保持后续每次协作的角色和内容原则一致 |
| 业务参数 | config | `config/task.yaml` | 账号定位、角色、栏目、工具链可以持续调整 |
| 角色参考 | references | `references/ip-character-summary.md` | 作为脚本和提示词生成的稳定上下文 |
| 缺失资产与决策 | docs | `docs/missing-assets-and-decisions.md` | 明确还缺什么，避免脑内管理 |
| 资产生产能力 | Skill | `.agents/skills/develop-ip-assets/SKILL.md` | 用于持续补齐三视图、表情、动作、场景 |
| 内容日历能力 | Skill | `.agents/skills/plan-content-calendar/SKILL.md` | 用于把四大栏目和热点优先策略拆成发布计划 |
| 热点选择规则 | docs | `docs/hot-topic-selection-guide.md` | 用于判断哪些热点值得做，以及如何转译成打工人情绪 |
| 内容生产流程 | docs | `docs/content-production-workflow.md` | 固化短视频创作流程、完播结构和发布复盘方法 |
| 阶段输出映射 | docs | `docs/workflow-stage-map.md` | 明确每个环节的 Skill、输入、输出和目录 |
| 热点收集能力 | Skill | `.agents/skills/collect-hot-topics/SKILL.md` | 用于建立抖音/微博/微信/小红书/B站等热点池 |
| 选题角度能力 | Skill | `.agents/skills/select-topic-angle/SKILL.md` | 用于把热点或灵感转成可拍摄 brief |
| 脚本创作能力 | Skill | `.agents/skills/write-short-video-script/SKILL.md` | 用于稳定产出 1 分钟以内脚本 |
| 提示词生成能力 | Skill | `.agents/skills/generate-production-prompt/SKILL.md` | 用于把脚本转成图像/视频/音频提示词 |
| AI 生产执行能力 | Skill | `.agents/skills/execute-ai-production/SKILL.md` | 用于记录 AI 生成、配音、音效和剪辑执行过程 |
| 发布包装能力 | Skill | `.agents/skills/package-publish-plan/SKILL.md` | 用于生成标题、封面文案、话题和评论引导 |
| 成片审核能力 | Skill | `.agents/skills/review-video-output/SKILL.md` | 用于审核角色一致性、节奏和复用性 |
| 发布后复盘能力 | Skill | `.agents/skills/analyze-publish-performance/SKILL.md` | 用于复盘发布后的数据、评论和用户共鸣 |
| 模板 | templates | `templates/` | 标准化脚本、分镜、资产 brief |
| 迭代复盘 | bad_cases | `bad_cases/bad_case_log.yaml` | 记录失败案例并反哺框架 |

## 3. 项目目录树

```text
hululu-awuwu-ai-video-project/
├── AGENTS.md
├── .codex/
│   └── config.toml
├── .agents/
│   └── skills/
│       ├── collect-hot-topics/
│       ├── select-topic-angle/
│       ├── develop-ip-assets/
│       ├── plan-content-calendar/
│       ├── write-short-video-script/
│       ├── generate-production-prompt/
│       ├── execute-ai-production/
│       ├── package-publish-plan/
│       ├── review-video-output/
│       └── analyze-publish-performance/
├── config/
│   └── task.yaml
├── references/
│   └── ip-character-summary.md
├── docs/
│   ├── project-blueprint.md
│   ├── asset-library-plan.md
│   ├── content-production-workflow.md
│   ├── hot-topic-selection-guide.md
│   ├── workflow-stage-map.md
│   └── missing-assets-and-decisions.md
├── templates/
│   ├── asset-brief-template.md
│   ├── hot-topic-pool-template.md
│   ├── topic-brief-template.md
│   ├── short-video-script-template.md
│   ├── shot-list-template.md
│   ├── production-prompt-template.md
│   └── publish-package-template.md
├── checks/
│   └── consistency-checklist.md
├── schemas/
│   └── short-video-script.schema.json
├── outputs/
├── logs/
└── bad_cases/
    └── bad_case_log.yaml
```

## 4. AGENTS.md 蓝图

见项目根目录 `AGENTS.md`。

## 5. .codex/config.toml 蓝图

见 `.codex/config.toml`。

## 6. config/task.yaml 蓝图

见 `config/task.yaml`。

## 7. Skills 规划表

| Skill | 原子能力 | 输入 | 输出 | 调用时机 | 依赖 | 失败处理 | 必需性 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| produce-short-video | 编排单条视频全流程 | `source_type`, `topic`, `column`, `need_outputs` | 阶段输出集合 | 用户要求做一条完整视频包时 | 全部阶段 Skill、流程表 | 用户只要某阶段则不强制跑全流程 | 必需 |
| collect-hot-topics | 收集和初筛热点池 | `date`, `sources`, `raw_topics` | 热点池 | 做热点内容前/每日选题前 | 热点选择规则、用户提供或公开来源 | 数据不足则标记待用户提供 | 必需 |
| select-topic-angle | 生成选题 brief | `topic`, `source`, `column`, `assets` | 一句话表达、打分、钩子、结尾回收 | 热点池或灵感确定后 | 内容流程、热点规则、角色摘要 | 角度太散则收束为一个情绪 | 必需 |
| develop-ip-assets | 规划和补齐可复用 IP 资产 | `character`, `asset_type`, `usage_context` | 资产 brief、缺失项、提示词方向 | 新增角色素材或补资产时 | 角色摘要、资产计划 | 不确定项写入缺失文档 | 必需 |
| plan-content-calendar | 规划栏目和发布批次 | `period`, `columns`, `capacity` | 内容选题表、优先级 | 做周/月计划时 | task.yaml、栏目库 | 产能未知时按 MVP 估算 | 必需 |
| write-short-video-script | 写短视频脚本 | `topic_brief`, `column`, `characters`, `emotion` | 1 分钟以内脚本 | 每条视频制作前 | 角色摘要、声音设定、脚本模板 | 人设漂移则重写 | 必需 |
| generate-production-prompt | 生成图像/视频/音频提示词 | `script`, `shot_list`, `tool` | 分镜提示词、音频提示词 | 脚本确认后 | 分镜模板、工具参数 | 工具未知时输出通用提示词 | 必需 |
| execute-ai-production | 记录 AI 生产执行 | `script`, `shot_list`, `prompt`, `tools` | 生产执行记录、问题记录、可复用素材 | 提示词完成后/生成素材时 | 生产执行模板、工具链 | 工具未定则输出执行计划 | 必需 |
| package-publish-plan | 生成发布包装 | `script`, `shot_list`, `topic`, `goal` | 标题、封面、简介、标签、评论引导 | 脚本/分镜完成后 | 发布包装模板 | 不自动发布，只输出本地发布包 | 必需 |
| review-video-output | 审核成片/素材 | `script`, `asset_refs`, `video_notes` | 问题清单、修改建议、可复用资产记录 | 生成初版后 | 审核清单 | 严重漂移时退回资产或提示词阶段 | 必需 |
| analyze-publish-performance | 发布后数据复盘 | `publish_package`, `metrics`, `comment_samples` | 数据复盘、评论关键词、改进项 | 视频发布后 | 复盘模板、用户提供数据 | 数据不足则输出定性复盘框架 | 必需 |

## 8. Skill 文件蓝图

实际 Skill 文件已放入 `.agents/skills/`。

## 9. 业务状态机

```text
[热点/日常灵感/栏目计划]
  -> collect-hot-topics
[热点池]
  -> select-topic-angle
[选题 brief]
  -> write-short-video-script
[1 分钟以内脚本]
  -> develop-ip-assets
[必要资产 brief]
  -> generate-production-prompt
[分镜和生成提示词]
  -> execute-ai-production
[AI 生产记录 + 初版视频]
  -> package-publish-plan
[发布包装]
  -> review-video-output
[可发布版本]
  -> analyze-publish-performance
[复盘记录]
  -> bad case / asset library update
```

## 10. 数据流映射

| 上游节点 | 输出数据 | 下游节点 | 输入数据 | 兼容性 | 转换规则 |
| --- | --- | --- | --- | --- | --- |
| 角色圣经 | 角色设定、口头禅、关系 | 资产规划 | 角色参考 | 直接兼容 | 提炼为生产摘要 |
| 资产规划 | 三视图、表情、动作、场景清单 | 脚本创作 | 可调用素材 | 部分待补 | 缺失素材标记 `待制作` |
| 热点收集 | 热点池、初筛评分 | 选题角度 | 候选热点 | 兼容 | 删除不适合热点 |
| 选题角度 | 一句话表达、钩子、结尾回收 | 脚本创作 | 选题 brief | 兼容 | 每条选题只聚焦一个冲突 |
| 脚本 | 台词、动作、场景 | 分镜提示词 | 镜头、画面、音效需求 | 兼容 | 每 3-6 秒拆一镜 |
| 分镜提示词 | 画面/视频/音频生成描述 | AI 生产执行 | 生成输入和工具链记录 | 兼容 | 记录每个生成输出 |
| AI 生产执行 | 初版素材、问题、可复用资产 | 成片审核 | 初版视频和生产问题 | 兼容 | 检查角色一致性和节奏 |
| 脚本/分镜 | 共鸣点、画面、IP 记忆点 | 发布包装 | 标题、封面、话题 | 兼容 | 提炼成 1 秒可读封面 |
| 审核记录 | 问题、修复建议 | bad case/资产库 | 失败原因 | 兼容 | 重复问题更新模板或 Skill |
| 发布数据 | 指标、评论、关键词 | 发布后复盘 | 完播、留存、评论样本 | 用户提供 | 形成加码/微调/暂停判断 |

## 11. 输出产物规划

| 产物 | 路径 | 格式 | 来源 | 命名规则 |
| --- | --- | --- | --- | --- |
| 热点池 | `outputs/hot_topics/` | `.md` | collect-hot-topics | `YYYYMMDD_热点池.md` |
| 选题 brief | `outputs/topic_briefs/` | `.md` | select-topic-angle | `YYYYMMDD_栏目_主题.md` |
| 单条视频脚本 | `outputs/scripts/` | `.md` | write-short-video-script | `YYYYMMDD_栏目_主题.md` |
| 分镜表 | `outputs/shot_lists/` | `.md` | generate-production-prompt | `YYYYMMDD_主题_分镜.md` |
| 生产提示词 | `outputs/prompts/` | `.md` | generate-production-prompt | `YYYYMMDD_主题_提示词.md` |
| 资产 brief | `outputs/asset_briefs/` | `.md` | develop-ip-assets | `角色_资产类型_版本.md` |
| AI 生产执行记录 | `outputs/production_runs/` | `.md` | execute-ai-production | `YYYYMMDD_栏目_主题.md` |
| 发布包装 | `outputs/publish_packages/` | `.md` | package-publish-plan | `YYYYMMDD_栏目_主题.md` |
| 审核报告 | `outputs/reviews/` | `.md` | review-video-output | `YYYYMMDD_主题_审核.md` |
| 发布后复盘 | `outputs/performance_reviews/` | `.md` | analyze-publish-performance | `YYYYMMDD_栏目_主题.md` |

## 12. Bad Case 与迭代机制

- bad case 记录位置：`bad_cases/bad_case_log.yaml`
- 触发标签：`character-drift`, `weak-hook`, `unclear-conflict`, `asset-missing`, `tool-limit`, `brand-risk`, `low-reuse`
- 复盘节奏：每 10 条视频或每周复盘一次。
- 反哺方式：角色漂移更新 `references/`；提示词问题更新 `templates/production-prompt-template.md`；栏目问题更新 `config/task.yaml`；重复缺失更新 `docs/missing-assets-and-decisions.md`。

## 13. 一致性校验 Checklist

- [ ] 每条内容都能说清使用了哪个角色记忆点。
- [ ] 每条内容只讲一个核心冲突。
- [ ] 角色台词符合语言风格。
- [ ] 生成提示词包含角色外观、状态、场景、动作。
- [ ] 新素材标记是否可复用。
- [ ] 缺失项已记录。
- [ ] 如果失败，已写入 bad case。

## 14. 最小可复用版本

MVP 只保留这些文件也可以工作：

- `AGENTS.md`
- `config/task.yaml`
- `references/ip-character-summary.md`
- `docs/asset-library-plan.md`
- `docs/missing-assets-and-decisions.md`
- `templates/short-video-script-template.md`
- `templates/production-prompt-template.md`
- `.agents/skills/write-short-video-script/SKILL.md`
- `.agents/skills/generate-production-prompt/SKILL.md`
- `.agents/skills/collect-hot-topics/SKILL.md`
- `.agents/skills/select-topic-angle/SKILL.md`

## 15. 待用户确认的问题

- 账号外显名称已定为“打工喵呼噜噜”，人物档案名保留“胡露露”。
- 栏目方向已收束为四大项目：《呼噜噜看热点》《呼噜噜的怪早晨》《打工喵生存报告》《呼噜噜与啊呜呜》。
- 视觉风格已定为 3D 毛绒动画风。
- 主要工具链使用哪些：即梦、可灵、Runway、Pika、Midjourney、剪映、其他？
- 两人声线已确认；最终使用 AI 配音还是真人配音待确认。
- 首月目标是测试 10 条、30 条，还是按日更节奏推进？
- 商业合作是否有不能接的品类？
