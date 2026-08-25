# Architecture

**AstraForge Studio · 星铸工坊 v1.1.0 — 系统架构文档**

---

## Overview

AstraForge Studio 采用分层 AI 生产架构（Layered AI Production Architecture）。

```
User
 ↓
Task Orchestrator
 ↓
Character Intelligence Layer
 ↓
Commercial Direction Layer
 ↓
Creative Planning Layer
 ↓
Prompt Engineering Layer
 ↓
Generation Layer
 ↓
Quality Layer
 ↓
Production Output
```

设计原则：

```
决策层 → 导演层 → 组件层 → 生成层 → 验证层
```

明确避免早期 Skill 的常见问题：Prompt 堆积、知识混杂、案例替代规则、组件不可复用。

---

## Layer 1 — Task Orchestrator

职责：理解用户需求，判断 PV 类型、工作模式、输出目标。

### 支持的任务类型

| Task | 用途 | 调用 |
|---|---|---|
| TASK_CREATE_PV | 从零制作角色 PV | `create-pv` |
| TASK_OPTIMIZE | 优化已有 Prompt | `optimize-prompt` |
| TASK_CONVERT_H3 | 描述转 H3 结构 | `convert-h3` |
| TASK_ANALYZE_REFERENCE | 拆解优秀 PV | `analyze-reference` |
| TASK_CHARACTER_PROFILE | 角色设计分析 | `analyze-character` |

### 混合任务优先级

多任务同时出现时的执行顺序：

```
1. Analyze Reference
2. Character Analysis
3. Create PV
4. Optimize
5. Convert H3
```

原因：前置理解影响后续质量。不要合并任务，应拆分串行。

### 任务置信度

```yaml
task: CREATE_PV
confidence: 0.92
```

---

## Layer 2 — Character Intelligence

### Character Analyzer

将角色描述转换为 Character Archetype：

| Archetype | 关键词 |
|---|---|
| cool_female | 冷酷 / 御姐 / 战士 / 剑士 / 女王 / 高冷 |
| sweet_female | 可爱 / 甜 / 少女 / 偶像 / 粉色 |
| academy_female | 学园 / 学生 / 制服 / 青春 / 傲娇 |
| fantasy_female | 魔法 / 贵族 / 精灵 / 圣女 |
| cyber_female | 赛博 / 科技 / 黑客 / neon |
| boss | Boss / 反派 / 敌人 |

**混合标签规则**：计算权重，选择主类型 + 辅助 Style，不强制二选一。
例：银发 + 剑士 + 科技服装 → `cool_female 60% / cyber 40%`。

输出：

```yaml
character_analysis:
  main_type:
  secondary_style:
  confidence:
  recommended_theme:
```

### Character DNA Lock

**核心原则**：角色不是一个 Prompt 描述，而是一套不可破坏的视觉资产。

生成优先级从：

```
Character Description → Prompt → Video
```

升级为：

```
Character Input → Character DNA Extraction → DNA Lock → Theme → Style → Composer → H3 Prompt
```

#### 稳定优先级

```
Face > Hair > Costume > Signature Item > Color > Personality > Action
```

#### Lock Level System

| Level | 说明 | 范围 |
|---|---|---|
| Level 0 | 绝对禁止变化 | 发色、眼睛颜色、核心服装、标志配饰、年龄感 |
| Level 1 | 允许动态变化 | 发丝摆动、表情、姿势、光影 |
| Level 2 | 自由变化 | 背景、特效、镜头、UI 元素 |

#### Forbidden Changes

```yaml
forbidden_changes:
  critical:
    - face_change
    - hair_color_change
    - costume_change
    - eye_color_change
  high:
    - weapon_change
    - body_shape_change
  medium:
    - expression_shift
    - personality_shift
```

#### Identity Validator

```yaml
identity_score:
  face: 25
  hair: 20
  costume: 20
  color: 15
  signature_item: 10
  personality: 10

result:
  ">=90": PASS
  "70-90": REVISION
  "<70": FAIL
```

---

### Cast Resolution（多角色）

单角色用 `character_dna`（单一 identity）；多角色必须改用 `cast`，
因为需要表达「角色间关系」与「画面权重」，这两者单角色 schema 无法承载。

```
character_dna  → 1 人
cast           → 2-4 人 + relationship + screen_weight
```

三道闸门（任一不通过即拒绝进入 Composer）：

| 闸门 | 规则 |
|---|---|
| contrast_requirement | 任意两成员至少 2 维强对比（发色/剪影/服装色/身形/标志物） |
| weight_rule | `sum(screen_weight) == 70` 且 `lead >= second × 1.5` |
| action_amplification | 同框有效等级 = 组件等级 + (同框人数 − 1) |

稳定性上限按阵容规模封顶，避免多角色方案获得虚高评分：

```yaml
stability_cap: { 1: 35, 2: 32, 3: 28, 4: 24 }
```

**身份串味（identity_bleed）** 是多角色最致命的失败模式：AI 会把 A 的特征
混到 B 身上，或生成介于两人之间的第三张脸。风险随同框人数与外观相似度上升。
详见 `core/multi-character/cast-risk-rules.yaml`。

---

## Layer 3 — Commercial Director

负责商业目标定位：

```yaml
commercial_goal:
  - banner_conversion      # 上线 PV
  - character_attachment   # 剧情 PV
  - story_interest
  - brand_memory
  - rarity_conversion      # 抽卡 PV
  - power_demonstration    # 战斗 PV
  - cosmetic_conversion    # 皮肤 PV
```

同一个角色在不同商业目标下会得到不同的 Theme。

### 商业 PV 规则（Premium Character PV Rules）

**Rule 01 — 角色永远第一视觉主体**

```yaml
character: 70%
effect: 20%
environment: 10%
```

**Rule 02 — 技能展示不是战斗展示**

```
❌ 连续战斗 / 多人混战 / 大爆炸
✅ 角色 → 技能准备 → 标志动作 → 英雄定格
```

**Rule 03 — 每个角色必须有三个记忆点**：face / signature_item / signature_pose

**Rule 04 — 五星角色增加 Rarity Layer**：光效、premium UI、title 动画、特殊转场

---

## Layer 4 — Creative Engine

### Theme Engine

决定 PV 商业方向。Theme 定义包含结构、推荐 Camera / Action / Expression / Transition 与风险等级。

### Variation Engine

在 Character DNA 完全不变的前提下改变展示角度、镜头语言、情绪方向、商业目标。

| Variation | ID | Commercial Goal |
|---|---|---|
| New Character Release | `release.standard.v1` | character_acquisition |
| Legendary Gacha Showcase | `gacha.legendary.v1` | rarity_conversion |
| Combat Showcase | `combat.showcase.v1` | power_demonstration |
| Story Emotional PV | `story.emotional.v1` | character_attachment |
| Skin / Fashion Showcase | `skin.showcase.v1` | cosmetic_conversion |

Theme 与 Variation 的关系：

```
Theme → Variation → Style Stack → Composer
```

例：`dark-witch + gacha.legendary` = 华丽稀有；`dark-witch + story.emotional` = 神秘悲伤。
角色不变，商业表达变化。

#### Variation Validator

- Rule 01 — Character DNA 必须 100% 保持
- Rule 02 — Variation 必须符合角色（如「黑暗魔女 + 甜偶像皮肤 PV」→ compatibility LOW，自动调整）
- Rule 03 — 商业目标一致（抽卡转化不能输出纯剧情慢镜头）

### Genre Engine

Genre 与 Theme 正交：Genre 决定**内容类型与镜头节奏**，Theme 决定**商业定位**。

```
Genre × Theme × Variation × Style = Final PV Direction
```

| Genre | 单镜头 | 推镜速度 | 震动 | BPM |
|---|---|---|---|---|
| 打斗 | 0.3-0.8s | 0.4/s | 8-12px / 0.2-0.5s（仅命中） | 140-160 |
| 日常文戏 | 1-2.5s | 0.2/s | 无 | 100-120 |
| 魔法幻想 | 蓄力 1.5-2.5s / 爆发 0.3-0.8s | 匀速环绕 30-45° | 5-8px（爆发） | 120-140 |

**不可混用镜头节奏**。详见 `library/genre/genre-library.md`。

### Event Engine（活动 PV）

活动 PV 与角色 PV 的成功标准不同：角色 PV 求「记住角色」，活动 PV 求「产生行动」。

| 类型 | 情绪曲线 | CTA |
|---|---|---|
| anniversary | 回顾 → 感谢 → 展望 | 必须含活动时间 |
| collaboration | 意外 → 融合 → 期待 | 必须含限时标识 |
| seasonal | 氛围 → 惊喜 → 号召 | 必须含活动时间 |

季节 PV 是**唯一**允许开场弱化角色的类型（0-3s 角色占比可降至 30%），
但全片平均仍须回到 Rule 01 的 70%。这是受控例外。

限定造型（季节/联动）本质是换装，与 DNA Lock 的 `costume_change: critical`
冲突，通过 `costume_variant_exception` 受控放行。

---

### Style Stack

Style 不是单层选择，而是三层结构：

```yaml
style_stack:
  base_style:      # 负责动画表现
  premium_layer:   # 负责商业质感
  special_layer:   # 负责角色个性
```

自动组合规则：

```yaml
style_composition:
  default_base: modern-cel
  commercial_upgrade:
    character_release:    add mobile-game-premium
    legendary_character:  add cinematic-lighting
    dark_character:       add dark-cinematic-cel
    fashion_character:    add y2k-graphic
```

#### Style Conflict Detection

| Rule | 冲突 | Level | 处理 |
|---|---|---|---|
| 001 | y2k-graphic × dark-cinematic-cel | C | 保留角色身份，移除 y2k，加 fantasy-anime |
| 002 | retro-cel × mobile-game-premium | B | 依目标二选一（怀旧 vs 商业精致） |
| 003 | sweet-y2k × heavy-battle | B | 降低战斗强度，保留角色魅力 |

#### Style Priority

```
角色商业定位 > Theme > Premium Layer > Base Style > Special Style
```

系统不做平均融合，而是通过 Style Resolver 主动移除冲突项，并在进入 Composer 前经过
**Style Validation Gate**。

---

## Layer 5 — Composer

核心导演模块，负责生成 Shot / Camera / Action / Expression / Transition。

### 15s 固定节奏

```
0-3s    HOOK
3-6s    IDENTITY
6-10s   PERSONALITY
10-13s  SIGNATURE
13-15s  TITLE
```

### Shot 自动生成规则（Hook 镜头示例）

| Archetype | Camera | Expression | Action |
|---|---|---|---|
| cool_female | eye-reveal | cool-gaze | head-turn |
| sweet_female | hand-to-camera | playful-wink | hand-gesture |
| fantasy | eye-reveal | elegant-smile | — |

Shot 02 固定调用 `beauty-showcase`，展示顺序：Face → Hair → Outfit → Signature Item。
原因：角色 PV 第一商业目标不是剧情，是角色识别。

Shot 05 所有角色固定：`hero-low-angle` + `signature-pose` + `title-reveal`。

### Component 自动选择算法

```
Component Score = Character Fit + Theme Match + Commercial Value - Risk
```

例：银发女剑士 + `weapon-reveal` → 10 + 10 + 10 - 2 = **28**（选择）；
普通挥剑 → 7 + 5 + 6 - 5 = 13（舍弃）。

### Quality Feedback Loop

```
Composer → Shot Plan → Quality Check → Risk Analyzer → Revision → Final Shot Plan
```

---

## Layer 5.5 — Prompt Engineering

Composer 产出 Shot Plan 后，进入 Prompt 工程层。

### 10 段结构规范

生成任何 Prompt 前**必读** `core/prompt-structure.md`。缺段会导致视频输出失控。

```
1 开头总述   2 角色设定   3 主题设定   4 音乐        5 画面风格
6 动态与转场 7 分时间段镜头设计（最核心） 8 表演要求  9 避免项  10 核心目标
```

### 风格锚定

`core/style-anchor.md` 提供赛璐璐锚定语（中英双版），必须贯穿所有镜头。

### H3 输出格式

| 模式 | 字段数 | 规范 |
|---|---|---|
| T2VA / I2VA / FL2VA / L2VA | 3（integrated_multimodal_description / overall_soundscape / non_diegetic_music） | `schema/h3-base.md` |
| Ref2VA | 6（+ subject_definitions / summary / retention_analysis） | `schema/h3-ref2va.md` |

每个镜头必须包含六要素：composition / subjects / environment / actions / camera / sound

---

## Layer 6 — Quality Engine

### 评分权重

| Metric | Weight |
|---|---:|
| Generation Stability | 35% |
| Character DNA Consistency | 25% |
| Shot Feasibility | 15% |
| Visual Impact | 10% |
| Commercial Value | 10% |
| Art Direction | 5% |

**为什么稳定性最高？** 一个视觉上很强但无法稳定生成的方案，商业价值低于一个稳定可复现的方案。

### H3 Risk Analyzer

**Risk 01 — 角色漂移**

```yaml
character_drift:
  low:    单角色固定镜头
  medium: 角色运动
  high:   变身 / 换装
```

**Risk 02 — 动作复杂度**

| Level | 说明 | 示例 |
|---|---|---|
| 1 | 稳定 | 站立、转头、微笑、挥手 |
| 2 | 可接受 | 拔武器、释放技能、走向镜头 |
| 3 | 高风险 | 连续战斗、高速移动、翻转飞行 |
| 4 | 禁止 | 多人战斗、复杂变身、大规模破坏 |

```yaml
max_action_level:
  15s: Level 2
  30s: Level 3
```

**Risk 03 — Camera 复杂度**

稳定：slow push / pan / closeup / hero shot / 2.5D parallax
风险：360 orbit / 高速追踪 / 复杂运镜
15s PV 最多 4 次镜头切换。

**Risk 04 — Effect 复杂度**

```yaml
effect_level:
  0: 无特效
  1: 光效
  2: 粒子
  3: 技能爆发
  4: 环境毁灭

限制:
  15s_character_pv: max effect_level 2
  legendary:        max effect_level 3
```

### Stability Rules

- **Rule 01** — 优先降低动作，不降低角色展示
- **Rule 02** — 优先减少特效，不减少技能表达
- **Rule 03** — 优先固定镜头，不增加镜头数量

### Auto Revision

| 触发条件 | 自动执行 |
|---|---|
| 稳定性 < 40 | 减少 Action 复杂度 / Effect / Camera 运动 |
| 角色一致性 < 20 | 增加 character lock、appearance anchor、negative prompt |
| 商业感低 | 增加 beauty-showcase、hero-pose、title-reveal |

---

## Layer 7 — Production Schema

输出协议目录：

```
schema/
├── character-bible.schema.yaml
├── pv-production.schema.yaml
├── shot-list.schema.yaml
├── h3-prompt.schema.yaml
├── quality-report.schema.yaml
└── revision-log.schema.yaml
```

### 生产状态机

```yaml
production_state:
  - ANALYSIS
  - THEME_SELECTED
  - STYLE_LOCKED
  - SHOT_DESIGNED
  - PROMPT_GENERATED
  - QUALITY_CHECKED
  - FINALIZED
```

作用：防止未完成分析就直接生成 Prompt。

---

## Fallback Rules

| 场景 | 处理 |
|---|---|
| 角色信息缺失 | 不生成，进入 Character Clarification（询问年龄感 / 性格 / 风格 / 用途） |
| 混合原型 | 保留 primary + secondary，不强制二选一 |
| 需求过多 | 保留角色卖点，删除低价值复杂元素 |
| 缺少 Style | 默认 `modern-cel` |
| 缺少时长 | 默认 15s Character Release PV |
| 生成失败 | 降低复杂度，保留角色 / 镜头 / 表情 |

冲突优先级：

```
Character Identity > Commercial Goal > Visual Effect > Complex Action
```

---

## 一级目录职责

| 目录 | 职责 |
|---|---|
| `docs/` | 项目文档 |
| `skill/` | AI Skill 加载层 |
| `core/` | 核心规则（DNA / Style / Quality / Variation / Prompt 结构 / 风格锚定 / 会话协议） |
| `workflow/` | 任务调度 |
| `director/` | 导演系统 |
| `library/` | 视觉组件（含 genre 内容类型层） |
| `templates/` | 商业模板 |
| `references/` | 案例库 |
| `benchmark/` | 回归测试 |
| `schema/` | 数据协议 + H3 输出格式规范 |
| `examples/` | 示例输出 |
| `release/` | 发布信息 |
