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

### Added (第二批 — 从原始 skill 与实证案例回填)

从 `animepv-h3` 原始 skill 与三份已验证成片案例中提炼补齐，
让项目从「架构规范」变为「可直接产出 Prompt 的生产系统」：

- **Prompt Engineering 层**
  - `core/prompt-structure.md` — 10 段结构规范 + 输出前自检清单（生成前必读）
  - `core/style-anchor.md` — 赛璐璐风格锚定语（中英双版）
  - `core/session-spec.md` — SESSION_SPEC 锚定、信息充分性校验、Generation Gate
- **H3 输出格式规范**
  - `schema/h3-base.md` — T2VA / I2VA / FL2VA / L2VA 三字段格式
  - `schema/h3-ref2va.md` — Ref2VA 六字段格式
  - 镜头六要素：composition / subjects / environment / actions / camera / sound
- **Genre 内容类型层**（与 Theme 正交）
  - `library/genre/genre-library.md` — 打斗 / 日常文戏 / 魔法幻想，含可量化帧率、运镜、震动、BPM 参数
  - `library/style/persona-tags.md` — 6 种 Persona 风格标签与叠加规则
  - `library/camera/camera-motion-spec.md` — 运镜速度、机位变化 6 维强制规则、转场清单
- **完整可用 Prompt 模板**
  - `templates/genre-action-15s.md` — 打斗 15s（含 10 段完整 Prompt + 5s/10s 适配 + 精简版）
  - `templates/genre-daily-15s.md` — 日常文戏 15s
  - `templates/genre-magic-15s.md` — 魔法幻想 15s
- **导演资产**
  - `director/storyboard-4shot.md` — 4 镜头连贯分镜脚本
  - `director/character-card-template.md` — 角色设定卡 + 出图 Prompt
- **实证案例库**
  - `references/cases/proven-pink-signal.yaml` — 御姐甜妹 PINK SIGNAL（H3 实测直出）
  - `references/cases/proven-academy-file.yaml` — 学院傲娇 ACADEMY FILE（H3 实测直出）
  - `references/cases/proven-cel-baseline.yaml` — 赛璐璐三套可量化参数基线
  - `references/extracted-rules.md` — 从实证案例提取的 11 类规则

### Known Limitations

- Benchmark 覆盖偏女性角色，缺少男性角色 / 多角色 / 群像 PV 用例
- Theme 库仍在扩展中（男性角色上线、联动活动、周年 PV、季节活动）
