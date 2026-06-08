# 打工喵呼噜噜 AI 视频项目

这是一个用于持续制作抖音虚拟 IP 短视频的项目文件夹。它的作用不是存一条视频，而是管理整个账号的资产库、内容生产流程、脚本模板、提示词模板和缺失项。

## 先看这 4 个文件

1. `docs/project-blueprint.md`
   - 项目总蓝图：账号目标、目录结构、工作流、Skill 规划、状态机。

2. `docs/asset-library-plan.md`
   - 可复用资产库规划：三视图、表情、动作、场景、栏目、音频包装。

3. `docs/missing-assets-and-decisions.md`
   - 当前缺失项清单：后续我们就按这里一点点补齐。

4. `references/ip-character-summary.md`
   - 生产版角色摘要：写脚本和提示词时优先参考这里。

5. `references/voice-and-language-style.md`
   - 声音、说话方式和口头禅设定：写台词、配音和做语音包时参考这里。

6. `docs/hot-topic-selection-guide.md`
   - 热点选择、打分和转译规则：做《呼噜噜看热点》时参考这里。

7. `docs/content-production-workflow.md`
   - 内容创作全流程和短视频生存结构：从选题、钩子、脚本、分镜到发布复盘。

8. `docs/workflow-stage-map.md`
   - 每个制作环节对应哪个 Skill、输入是什么、输出写到哪里。

9. `docs/current-project-status.md`
   - 当前已经完成的文件、Skill、模板和输出目录索引。

10. `docs/pending-confirmations.md`
   - 后续需要逐项确认的问题，适合继续沟通时使用。

## 常用模板

- `templates/asset-brief-template.md`：制作三视图、表情、动作、场景时使用。
- `templates/hot-topic-pool-template.md`：收集抖音/微博/微信等热点时使用。
- `templates/topic-brief-template.md`：把热点或灵感转成选题 brief 时使用。
- `templates/short-video-script-template.md`：写 1 分钟以内短视频脚本时使用。
- `templates/shot-list-template.md`：把脚本拆成分镜时使用。
- `templates/production-prompt-template.md`：生成 AI 图像/视频/音频提示词时使用。
- `templates/publish-package-template.md`：整理标题、封面、话题和评论引导时使用。

## 输出目录

- `outputs/hot_topics/`：热点池。
- `outputs/topic_briefs/`：选题 brief。
- `outputs/scripts/`：单条视频脚本。
- `outputs/asset_briefs/`：新增资产 brief。
- `outputs/shot_lists/`：分镜表。
- `outputs/prompts/`：AI 生产提示词。
- `outputs/production_runs/`：AI 生成、配音、音效和剪辑执行记录。
- `outputs/publish_packages/`：发布包装。
- `outputs/reviews/`：成片审核报告。
- `outputs/performance_reviews/`：发布后数据和评论复盘。

所有输出只保存在本地项目内，不自动同步到抖音、微博、微信或其他平台。

## 后续推荐顺序

1. 确认工具链和首月产能。
2. 补齐呼噜噜、啊呜呜的三视图。
3. 建立首批热点池和选题 brief。
4. 写首批 10 条 1 分钟以内测试脚本。
5. 为核心场景建立参考图：工位、出租屋、奶茶/夜宵。
6. 生成分镜、提示词和发布包装。
7. 记录 AI 生产执行过程和成片审核。
8. 用第一批视频数据更新 bad case 和资产优先级。
