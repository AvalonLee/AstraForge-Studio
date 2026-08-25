# Changelog

All notable changes to AstraForge Studio（星铸工坊）are documented in this file.

---

## v1.2.0 — 2D Style Expansion

视觉风格扩展：从单一赛璐璐扩展为 7 套 2D base style，同时补齐男性角色主题与角色图 Prompt Gate。

### Added

- **2D 多画风体系**
  - 7 个 base style：`modern-cel` / `retro-cel` / `painterly-anime` / `watercolor-ink` / `vector-flat` / `korean-manhwa` / `western-comic`
  - `core/style-anchor.md` 重写为 2D 风格锚定语模板库，每个 base 含中英锚定与专属禁止项
  - `library/style/style-library.yaml` 新增 5 个 base 组件与 `motion-comic` 呈现层
  - `core/style-engine/style-conflict-rules.yaml` 新增 conflict.004-007，防 2D base 中途互切与跨形态混搭
  - `core/style-engine/style-priority-rules.md` 增加 Base Style 选择规则（按角色美术语言）
  - H3 schema 与 `core/h3-generation-rules.md` 由「赛璐璐硬编码」改为「所选 base 锚定贯穿」
  - PV 模板与角色卡模板参数化：默认 `modern-cel`，可替换为其他 2D base
- **男性角色主题**
  - `library/theme/theme-library.yaml` 新增 `male-suit-release` / `male-samurai-release` / `male-knight-release`
  - 角色路由新增 `male_cool` / `male_hotblooded` / `male_mature`
  - 表情组件 `composed-gaze` / `battle-resolve` / `detached-stare`
  - Benchmark BM-09（Male Suit Elegance 97）、BM-10（Male Samurai Combat 93），BM-04 升级为骑士主题
- **角色图 Prompt Gate**
  - 交互协议 Step0-2 重构：先确认角色与风格、输出角色设定图 Prompt，再锚定 `SESSION_SPEC`
  - `director/character-card-template.md` 支持按 base style 参数化

### Changed

- 默认 `modern-cel` 不变，未指定其他 base 时行为向后兼容
- `core/prompt-structure.md` 与模板的默认禁止项补充欧美卡通反向排除（base = western-comic 时反转）
- `docs/ARCHITECTURE.md`、`docs/USER_GUIDE.md`、`docs/CONFIGURATION.md` 同步多画风说明

### Known Limitations

- 尚未提供 2D 多画风专项 Benchmark 用例
- 3D 形态（三渲二 / 写实 CG / 实拍 VFX）仅列入 roadmap，未进入 P0
- 2D 内 planned 美术细节（fantasy-luxury / sci-fi-anime / urban-neon / historical-anime 等）待后续版本

---

## v1.1.0 — Character Universe Expansion

角色宇宙扩展。核心是把系统从「单角色 PV 导演」扩展为「角色宇宙导演」，
同时补齐可生产性（frontmatter / 模板缺陷 / 校验体系）。

### Added

- **中文品牌名**：星铸工坊。定位语「AI 二次元游戏角色 PV 智能导演系统」
- **Cast Engine（多角色 PV）** — `core/multi-character/`
  - duo / trio / squad 阵容，画面权重 `sum==70` 且 `lead >= second × 1.5`
  - identity_bleed 风险建模、contrast 准入闸门、同框动作等级放大
  - 稳定性按阵容规模封顶 `{1:35, 2:32, 3:28, 4:24}`
  - `templates/cast-duo-15s.md` 双人完整 Prompt 模板
  - 6 个同框镜头组件，均带 `negative_addon` 禁止特征互换
- **Event Engine（活动 PV）**
  - 周年 / 联动 / 季节三类 Theme，CTA 强制且须含活动时间
  - `director/event-director.md`
  - `costume_variant_exception` 受控放行限定造型
- **可生产性修复**
  - `SKILL.md` 补 frontmatter（此前缺失导致 skill 无法被发现与触发）
  - 三个 genre 模板末段补齐机位标注（继承自前身 skill 的缺陷）
  - `examples/walkthrough-frostblade/` 端到端实测样例
- **校验体系**
  - `tools/validate_templates.py`、`tools/validate_benchmarks.py`、`tools/check_links.py`
  - 全部接入 CI，共 5 个校验器
- **工程规范**
  - `docs/BRANCH_POLICY.md`：禁止直接推送 main，经 dev + PR
  - `.githooks/pre-push` 本地守卫 + GitHub Branch Protection 双层强制

### Changed

- `group battle` 由笼统 `level_4 forbidden` 细分：无序混战仍禁止，结构化多角色可控
- Genre 动作等级上限修正（`daily` 1→2）并引入 `genre_ceiling_uplift`
- 全部 61 个组件增加显式 `slug` 字段
- Benchmark 覆盖度 85 → 93（8 例，含首个男性角色 / 多角色 / 活动 PV）

### Known Limitations

- squad（4 人）规则已定义但无用例
- 联动 / 季节 Theme 已定义但无用例
- 男性角色仅有表情组件，尚无专属 Theme

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

### Added (Prompt 生产资产回填)

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

### Known Limitations (v1.0.0 当时)

- Benchmark 覆盖偏女性角色，缺少多角色 / 群像 / 活动 PV 用例
- Theme 库仍在扩展中




