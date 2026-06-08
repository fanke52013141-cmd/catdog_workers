# 热点来源接口调研

本文件记录适合《呼噜噜看热点》的免费/开源热榜来源方案。

## 1. 推荐方案：DailyHotApi 自部署

项目：

- GitHub: `imsyy/DailyHotApi`
- 地址：https://github.com/imsyy/DailyHotApi
- 说明：一个聚合热门数据的 API 接口，支持 JSON 和 RSS，支持 Docker、自行部署和 Node.js 调用。

适合原因：

- 开源，可自部署，避免依赖不稳定的第三方公开服务。
- 覆盖平台较多，和我们的热点池需求匹配。
- 路由简单，适合接入 `collect-hot-topics` Skill。

从 README 看到的相关平台：

- 微博：`/weibo`
- 抖音：`/douyin`
- 今日头条：`/toutiao`
- 知乎：`/zhihu`
- 百度：`/baidu`
- B站：`/bilibili`
- 快手：`/kuaishou`
- 腾讯新闻：`/qq-news`
- 新浪新闻：`/sina-news`
- 网易新闻：`/netease-news`
- 36氪：`/36kr`
- IT之家：`/ithome`
- 微信读书：`/weread`

## 2. 公开示例接口风险

DailyHotApi README 中给出示例域名：

```text
https://api-hot.imsyy.top/weibo
https://api-hot.imsyy.top/douyin
https://api-hot.imsyy.top/toutiao
```

本地测试时公开示例域名出现 TLS 握手失败。README 也提示示例站点可能因访问量或维护情况异常。

因此建议：

> 公开示例接口只作为临时参考，不作为生产依赖。稳定使用应自部署 DailyHotApi。

## 3. 建议接入方式

### 阶段 1：手动/半自动

- 用户或 Codex 从公开热榜页面、截图、链接、DailyHotApi 结果中收集热点。
- 写入 `outputs/hot_topics/YYYYMMDD_热点池.md`。
- 由 `collect-hot-topics` 进行打工人相关度和 IP 转译初筛。

### 阶段 2：自部署 DailyHotApi

部署方式可选：

- Docker。
- Node.js 本地服务。
- Vercel/服务器部署。

部署后在 `config/task.yaml` 中增加：

```yaml
hot_topic_sources:
  provider: "DailyHotApi"
  base_url: "https://your-domain.example"
  routes:
    - "weibo"
    - "douyin"
    - "toutiao"
    - "zhihu"
    - "bilibili"
    - "baidu"
```

### 阶段 3：自动热点池

未来可以新增脚本或工具：

- 定时拉取指定 routes。
- 合并去重。
- 输出热点池 markdown。
- 只保留打工人相关候选。

当前不建议直接自动发布或自动同步平台。

## 4. 其他备选

搜索 GitHub 时还看到若干 DailyHotApi 分支/重构项目：

- `imsyy/DailyHot`
- `imsyy/DailyHotApi-Vercel`
- `ShellMonster/DailyHotApi-Go`
- `XingYunSK/DailyHotApi`

这些可作为 DailyHotApi 不稳定时的备选，但当前优先研究主项目。

## 5. 待确认

- 是否要自部署 DailyHotApi。
- 部署在哪里：本地、Vercel、服务器。
- 首批拉取哪些 routes。
- 是否需要后续写自动拉取脚本。

