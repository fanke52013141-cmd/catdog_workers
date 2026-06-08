---
name: analyze-publish-performance
description: 复盘“打工喵呼噜噜”视频发布后的数据、评论和用户共鸣。用于记录播放量、3秒留存、完播率、互动、评论关键词，并反哺选题、脚本、资产、提示词和 bad case；不抓取需要授权的平台数据。
---

# Analyze Publish Performance

## 工作定位

把视频发布后的表现转化为下一轮创作改进。重点不是只看播放量，而是判断选题、钩子、完播、IP 记忆点和用户共鸣是否成立。

## 输入

```yaml
publish_package_file: ""
video_topic: ""
metrics:
  views: ""
  three_second_retention: ""
  completion_rate: ""
  average_watch_time: ""
  likes: ""
  comments: ""
  shares: ""
  saves: ""
comment_samples:
  - ""
```

如果用户没有提供数据，只能输出复盘框架或基于评论样本做定性判断。不要承诺自动抓取平台后台数据。

## 输出

写入：

```text
outputs/performance_reviews/YYYYMMDD_栏目_主题.md
```

必要时同步记录：

- `logs/`：阶段复盘记录。
- `bad_cases/bad_case_log.yaml`：重复失败或明显问题。

## 执行步骤

1. 读取发布包、脚本和用户提供的数据。
2. 记录基础指标：播放、3 秒留存、完播、平均播放、点赞、评论、转发、收藏。
3. 提取评论关键词，尤其关注“像我”“打工人”“没电”“周一”“下班”“咖啡”“发卡”等。
4. 判断选题是否有效、钩子是否有效、中段是否掉节奏、IP 记忆点是否被记住。
5. 给出下一步动作：加码、微调、暂停、重做。
6. 使用 `templates/performance-review-template.md` 输出复盘。
7. 如果同类问题重复出现，写入 bad case。

## 检查点

- [ ] 复盘同时看数据和评论，不只看播放量。
- [ ] 明确下一步动作。
- [ ] 能反哺至少一个文件：选题、脚本、资产、提示词或 bad case。
- [ ] 不自动抓取需要授权的数据。

## 失败处理

- 数据不足：输出定性复盘，并列出需要补充的数据。
- 评论样本过少：不做过度结论。
- 播放高但评论弱：判断是否只是热点流量，没有形成 IP 记忆。
- 完播低：优先检查前 3 秒和中段变化。

