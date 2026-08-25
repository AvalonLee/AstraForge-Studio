# Changelog

All notable changes to AstraForge Studio are documented in this file.

---

## v1.0.0 — Foundation Release

**Initial Production Release**

首个正式公开版本。项目前身为内部迭代的 `AnimePV-H3`（迭代至 v2.6），
v1.0.0 起以 AstraForge Studio 名义重新起版，定位为 Production Foundation Release。

### Added

- **Character DNA System** — 角色视觉资产锁定，跨镜头一致性保护，H3 Prompt 自动注入身份锚点
- **Theme Engine** — 商业方向驱动的 PV 主题选择
- **Variation Engine** — 同角色多商业版本（Release / Gacha / Combat / Story / Skin）
- **Style Stack** — Base + Premium + Special 三层视觉语言，含冲突检测与自动收敛
- **Composer** — 5s / 15s / 30s 自动导演，组件评分匹配算法
- **Quality Engine** — 稳定性优先的自动评分、H3 风险分析、自动返修闭环
- **Benchmark Framework** — 回归测试体系（Sweet Y2K / Cool Warrior / Dark Witch）
- **Visual Component Library** — Camera / Action / Expression / Transition / Theme / Style
- **Production Schema** — Character Bible / Shot List / H3 Prompt / Quality Report / Revision Log
- **文档体系** — README / SKILL / User Guide / Architecture / Developer Guide / Installation / Configuration / Contributing

### Changed

- 项目全面从 `AnimePV-H3` 更名迁移为 `AstraForge Studio`
- `composer/` → `director/`，`output-schema/` → `schema/`
- 质量评分权重由「视觉冲击优先」调整为「生成稳定性优先」

### Known Limitations

- Benchmark 覆盖偏女性角色，缺少男性角色 / 多角色 / 群像 PV 用例
- Theme 库仍在扩展中（男性角色上线、联动活动、周年 PV、季节活动）
