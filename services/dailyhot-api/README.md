# DailyHotApi 热榜服务

本目录用于部署《打工喵呼噜噜》项目的热榜数据源。它不保存第三方项目源码，只保存可复现的 Docker 部署配置。

## 作用

部署后可以通过 API 获取微博、抖音、今日头条、知乎、B站、百度等热榜，用于 `collect-hot-topics` Skill 生成热点池。

默认本地地址：

```text
http://localhost:6688
```

常用接口：

```text
http://localhost:6688/weibo
http://localhost:6688/douyin
http://localhost:6688/toutiao
http://localhost:6688/zhihu
http://localhost:6688/bilibili
http://localhost:6688/baidu
```

## 启动

先安装 Docker Desktop，然后在本目录执行：

```powershell
docker compose up -d
```

查看运行状态：

```powershell
docker compose ps
```

测试接口：

```powershell
curl http://localhost:6688/weibo
curl http://localhost:6688/douyin
```

停止服务：

```powershell
docker compose down
```

更新镜像：

```powershell
docker compose pull
docker compose up -d
```

## 换电脑后的恢复方式

1. 克隆本仓库。
2. 安装 Docker Desktop。
3. 进入 `services/dailyhot-api/`。
4. 执行 `docker compose up -d`。
5. 用 `http://localhost:6688/weibo` 测试是否返回 JSON。

## 注意

- 当前仓库只负责部署配置，不维护 `DailyHotApi` 源码。
- 若公开平台接口变化，DailyHotApi 可能需要更新镜像。
- 不建议依赖公开示例域名作为长期生产源，优先使用本地或自有服务器部署。
- 本机如果没有 Docker，就无法直接启动，但配置文件仍可在有 Docker 的电脑上复现。

