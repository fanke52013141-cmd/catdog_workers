---
name: develop-ip-assets
description: 为呼噜噜和啊呜呜规划、补齐、审核可复用 IP 视觉/动作/场景/音频资产。
---

# Develop IP Assets

## 目的

把角色圣经和内容需求转化为可复用资产 brief，包括三视图、表情状态、动作姿态、场景、道具、音效和包装。

## 何时使用

- 需要制作新角色资产时。
- 发现视频制作缺少某个表情、动作或场景时。
- 准备训练角色一致性模型或建立 AI 生成参考库时。
- 需要判断某个素材是否值得沉淀为长期资产时。

## 输入

```yaml
character: "呼噜噜 | 啊呜呜 | 双人 | 场景 | 道具"
asset_type: "三视图 | 表情 | 动作 | 场景 | 道具 | 音效 | 包装"
usage_context: "会在哪些视频或栏目中使用"
style_direction: "待确认或具体视觉风格"
priority: "P0 | P1 | P2"
```

## 输出

- 资产 brief。
- 生成提示词草稿。
- 复用场景说明。
- 验收标准。
- 如信息不足，更新缺失项。

## 流程

1. 读取 `references/ip-character-summary.md` 和 `docs/asset-library-plan.md`。
2. 确认资产是否属于 P0 最小可用资产库。
3. 使用 `templates/asset-brief-template.md` 生成 brief。
4. 明确必须保留的识别点，例如呼噜噜发卡、啊呜呜尾巴。
5. 写出负面约束，防止角色漂移。
6. 如缺少视觉风格、工具链或用途，写入 `docs/missing-assets-and-decisions.md`。

## 失败处理

- 角色外观不稳定：退回三视图资产。
- 表情无法区分：增加状态对比图。
- 动作不可复用：改为单条视频临时素材，不进入核心资产库。
- 工具链未知：输出通用提示词，不绑定平台语法。

