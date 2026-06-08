# 视频制作环节、Skill 与输出目录

本文件定义整个项目的生产链路。原则是：每个关键环节都有对应 Skill，每个环节都有本地输出文件；输出不自动同步到抖音、微博、微信或任何外部平台。

## 1. 总原则

- 内容创作可以灵活，生产流程必须稳定。
- 每个环节都要产出可检查的文件。
- 每个下游环节只读取上游的明确输出，不依赖口头记忆。
- 所有输出默认写入项目内 `outputs/`。
- 不做自动发布，不做自动同步；发布动作由用户或后续明确工具链执行。

## 2. 环节总表

| 阶段 | 对应 Skill | 输入 | 输出 | 输出目录 |
| --- | --- | --- | --- | --- |
| 单条视频总编排 | `produce-short-video` | 热点 / 日常灵感 / 魔幻设定 / 用户指定主题 | 阶段输出集合 | 按下列阶段分别输出 |
| 热点收集 | `collect-hot-topics` | 用户给的热点 / 热榜来源 / 手动搜索结果 | 热点池 | `outputs/hot_topics/` |
| 选题角度 | `select-topic-angle` | 热点池 / 日常选题 / 栏目方向 | 选题 brief | `outputs/topic_briefs/` |
| 内容日历 | `plan-content-calendar` | 选题 brief / 栏目比例 / 产能 | 周/月内容计划 | `outputs/topic_briefs/` |
| 脚本创作 | `write-short-video-script` | 选题 brief / 角色参考 / 声音设定 | 1 分钟以内脚本 | `outputs/scripts/` |
| 资产补齐 | `develop-ip-assets` | 脚本 / 缺失镜头 / 缺失道具 | 资产 brief | `outputs/asset_briefs/` |
| 分镜提示词 | `generate-production-prompt` | 脚本 / 资产 brief / 工具链 | 分镜与 AI 提示词 | `outputs/shot_lists/`, `outputs/prompts/` |
| AI 生产执行 | `execute-ai-production` | 脚本 / 分镜 / 提示词 / 资产 brief | 生产执行记录、问题记录、可复用素材 | `outputs/production_runs/` |
| 发布包装 | `package-publish-plan` | 脚本 / 分镜 / 视频说明 | 标题、封面文案、话题、评论引导 | `outputs/publish_packages/` |
| 成片审核 | `review-video-output` | 初版视频 / 脚本 / 分镜 / 发布包 | 审核报告 | `outputs/reviews/` |
| 发布后复盘 | `analyze-publish-performance` | 数据 / 评论 / 发布包 | 数据复盘、评论分析、改进项 | `outputs/performance_reviews/`, `logs/`, `bad_cases/` |

## 3. 单条视频文件命名

推荐命名：

```text
YYYYMMDD_栏目_主题.md
```

示例：

```text
20260608_呼噜噜看热点_班味实体化.md
20260608_呼噜噜的怪早晨_醒来只剩3%电量.md
```

## 4. 单条视频最小生产包

一条视频至少应有：

- `outputs/topic_briefs/YYYYMMDD_栏目_主题.md`
- `outputs/scripts/YYYYMMDD_栏目_主题.md`
- `outputs/shot_lists/YYYYMMDD_栏目_主题.md`
- `outputs/prompts/YYYYMMDD_栏目_主题.md`
- `outputs/production_runs/YYYYMMDD_栏目_主题.md`
- `outputs/publish_packages/YYYYMMDD_栏目_主题.md`

如果涉及新增角色、表情、动作或场景，还要有：

- `outputs/asset_briefs/角色_资产类型_主题.md`

如果已有初版成片，还要有：

- `outputs/reviews/YYYYMMDD_栏目_主题.md`

## 5. 输出不同步说明

本项目只管理生产过程和本地文件。以下动作默认不执行：

- 不自动发布到抖音。
- 不自动同步到微博、微信、小红书或其他平台。
- 不自动抓取需要登录、授权或绕过限制的数据。
- 不自动保存用户未确认的外部平台账号信息。

如果未来需要自动同步或定时发布，应新增独立 Skill 或工具链，并单独确认权限、账号、安全边界和失败处理。
