# DailyHotApi 部署与接入说明

## 结论

可以把 DailyHotApi 的部署配置放在本代码仓库里。我们不把第三方源码整包复制进来，而是在 `services/dailyhot-api/` 放 Docker Compose 配置。

这样换电脑后，只要安装 Docker Desktop，就能重新启动热榜 API，项目不会因为本机缺少某个手动部署而跑不通。

## 仓库内位置

```text
services/dailyhot-api/
├── docker-compose.yml
└── README.md
```

## 默认接口地址

```text
http://localhost:6688
```

## 推荐接入 routes

```text
/weibo
/douyin
/toutiao
/zhihu
/bilibili
/baidu
```

## 在项目配置中的对应字段

见 `config/task.yaml`：

```yaml
production:
  hot_topic_sources:
    provider: "DailyHotApi"
    status: "本地 Docker Compose 配置已加入仓库，待安装 Docker 后启动测试"
    base_url: "http://localhost:6688"
    recommended_routes:
      - "weibo"
      - "douyin"
      - "toutiao"
      - "zhihu"
      - "bilibili"
      - "baidu"
```

## 使用方式

启动服务：

```powershell
cd services/dailyhot-api
docker compose up -d
```

测试接口：

```powershell
curl http://localhost:6688/weibo
curl http://localhost:6688/douyin
```

如果接口返回 JSON，就可以让 `collect-hot-topics` Skill 读取这些接口，生成热点池。

## 当前限制

当前机器未检测到 Docker 命令，因此本轮没有完成本地启动测试。配置已经写入仓库，后续在安装 Docker 的电脑上执行上述命令即可。

