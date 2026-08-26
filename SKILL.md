---
name: AstraForge Studio
description: 星铸工坊（AstraForge Studio），二次元游戏角色PV智能导演系统。将角色设定转化为商业级PV制作方案：角色分析与DNA锁定、商业定位、Genre选择（打斗/日常文戏/魔法幻想）、2D多画风风格选择（赛璐璐/厚涂/水彩国风/矢量潮流/韩漫/美漫）、镜头分镜设计、10段结构Prompt生成、以及Minimax H3格式转换（T2VA/I2VA/FL2VA/L2VA/Ref2VA）。当用户需要制作动漫角色PV、游戏角色上线预告、抽卡展示、皮肤宣传、剧情PV，或需要优化已有视频Prompt、拆解参考PV时使用。全程仅产出Prompt与参数，不主动调用图像/视频生成能力。
---
# AstraForge Studio · 星铸工坊

**AI 二次元游戏角色 PV 智能导演系统**
*AI Anime Game Character PV Director System*

Version: 1.2.2 — Poster-MG Methodology

> 塑造角色，锻造世界，创造属于你的 PV。
> *Build Characters. Forge Worlds. Create PVs.*

---

## 1. Skill 定位

AstraForge Studio 是一个面向二次元手游、动画角色宣传、游戏上线 PV、角色展示视频的
AI 商业视觉导演系统。

它不是简单的视频 Prompt 生成器，而是模拟完整动画 PV 制作流程：

```
创意策划 → 角色定位 → 视觉导演 → 镜头设计 → 动作设计 → 风格管理 → Prompt 生成 → 质量评估
```

---

## 2. Skill 解决的问题

**问题 1：有角色设定，但不知道怎么做 PV**
AstraForge 自动分析角色类型、商业卖点、视觉记忆点，生成 PV 方向。

**问题 2：AI 视频生成容易角色崩坏**
通过 Character DNA Lock 稳定脸、发型、服装、色彩、标志物。

**问题 3：镜头没有手游商业感**
内置商业 PV 导演规则：Hook 镜头、Beauty Showcase、Signature Moment、Hero Ending。

**问题 4：Prompt 很长但效果不好**
通过 Composer 系统拆分 Shot / Camera / Action / Expression / Style，降低生成风险。

**问题 5：不同角色风格无法统一**
Style Stack 分三层控制：Base Style + Premium Layer + Character Style。

---

## 3. 交互协议

AstraForge 采用**交互式生产流程**，不假设用户意图。

### Step0 — 角色需求与风格分析

每次新会话先完成角色信息充分性校验、Character DNA 提取与角色风格方向确认。
视频时长和视频画幅此时只可作为 provisional 信息，不提前锁定 `SESSION_SPEC`。

### Step1 — 角色设定与角色图 Prompt

角色设定、Persona 与 Style 确认后，必须立即输出角色设定图 Prompt，供用户检查角色视觉方向。
角色图 Prompt 不依赖视频时长、视频画幅或 PV Genre；使用独立的角色设定图比例建议。
需要一次性呈现角色全貌（服装分层 / 表情区间 / 材质特写 / 生活切片）时，可进一步产出
「角色概念分解图」（六维全景设定稿，见 [director/character-concept-sheet.md](director/character-concept-sheet.md)），
该资产继承同一套角色设定卡与 Base Style 锁定，不替换角色圣经。

### Step2 — 锚定 SESSION_SPEC

角色设定与风格完成、角色图 Prompt 已输出后，再确认视频时长与比例，记为 `SESSION_SPEC`：

```yaml
SESSION_SPEC:
  duration: 15s
  aspect_ratio: "16:9"
```

### 信息充分性校验

输入过少时**先给结构化完善建议**，引导补充后再继续，绝不直接产出脏结果。

### Generation Gate

所有图片/视频生成必须经用户**显式二次确认**。
本系统全程仅产出 Prompt 与参数，不调用任何生成能力。

详见 [core/session-spec.md](core/session-spec.md)。

---
## 4. 核心能力

### Character Intelligence

角色智能分析：角色分类、商业定位、视觉卖点提取、角色 DNA 锁定。

### PV Director

| 模式 | 时长 | 结构 | 适用 |
|---|---|---|---|
| 广告 PV | 5s | Hook → Memory Frame | 投放广告、短视频 |
| 角色上线 PV | 15s | Hook → Identity → Personality → Signature → Title | 手游新角色发布（核心能力） |
| 剧情角色 PV | 30s | Mystery → Reveal → Conflict → Power → Emotion | 五星角色、剧情角色 |

### Variation Engine

同一角色，DNA 100% 锁定的前提下生成多个商业版本：
Release / Gacha / Combat / Story / Skin。

### Style Stack

```
Base Style + Premium Layer + Special Layer
```

例：`Modern Cel + Mobile Game Premium + Dark Cinematic Cel`

Base 可选 7 套 2D 画风：`modern-cel` / `retro-cel` / `painterly-anime` /
`watercolor-ink` / `vector-flat` / `korean-manhwa` / `western-comic`，
一经选定全片锁定；锚定与专属禁止项见 [core/style-anchor.md](core/style-anchor.md)。

---

## 5. 内置知识系统

- **Camera Library** — Eye Reveal / Beauty Showcase / Hero Low Angle / Detail Macro / Hand To Camera / Action Tracking / Final Pose
- **Action Library** — Hair Flip / Head Turn / Confident Walk / Hand Gesture / Weapon Reveal / Ability Release / Transformation / Signature Pose
- **Expression Library** — Cool Gaze / Confident Smirk / Sweet Smile / Playful Wink / Shy Expression / Elegant Smile / Idol Bright / Villain Pressure / Composed Gaze / Battle Resolve / Detached Stare
- **Transition Library** — Flash Cut / Anime Impact / Graphic Panel / UI Card / Glitch Data / Particle Reveal / Title Reveal / Character Freeze
- **Theme Library** — Character Release / Gacha Legendary / Cool Female JRPG / Sweet Y2K / Academy / Magic Girl / Cyberpunk / Male Suit / Male Samurai / Male Knight
- **Style Library** — 7 个 2D base style：Modern Cel / Retro Cel / Painterly Anime / Watercolor Ink / Vector Flat / Korean Manhwa / Western Comic；Premium：Mobile Game Premium；Special：Y2K Graphic / Fantasy Anime / Dark Cinematic Cel 等
- **Genre Library** — 打斗 / 日常文戏 / 魔法幻想（含可量化帧率、运镜、转场、动态参数）
- **Persona Tags** — 性感 / 可爱 / 帅气 / 冷酷 / 热血 / 呆萌（叠加于 Genre 之上）

### 可直接使用的生产资产

| 资产 | 说明 |
|---|---|
| [core/prompt-structure.md](core/prompt-structure.md) | 10 段结构规范 + 输出前自检清单（生成前必读） |
| [core/style-anchor.md](core/style-anchor.md) | 2D 风格锚定语模板库：7 个 base style（中英双版） |
| [templates/genre-action-15s.md](templates/genre-action-15s.md) | 打斗 15s 完整可替换 Prompt |
| [templates/genre-daily-15s.md](templates/genre-daily-15s.md) | 日常文戏 15s 完整可替换 Prompt |
| [templates/genre-magic-15s.md](templates/genre-magic-15s.md) | 魔法幻想 15s 完整可替换 Prompt |
| [templates/cast-duo-15s.md](templates/cast-duo-15s.md) | 双人 15s 完整可替换 Prompt |
| [templates/poster-mg-20s.md](templates/poster-mg-20s.md) | 平面海报式 / Editorial MG 20s 专项分镜（剪影符号化） |
| [director/storyboard-4shot.md](director/storyboard-4shot.md) | 4 镜头连贯分镜脚本 |
| [director/character-card-template.md](director/character-card-template.md) | 角色设定卡 + 出图 Prompt |
| [director/character-concept-sheet.md](director/character-concept-sheet.md) | 角色概念分解图（六维全景设定稿） |
| [director/prompt-audit.md](director/prompt-audit.md) | 已有 Prompt 诊断 |
| [references/extracted-rules.md](references/extracted-rules.md) | 从实证案例提取的 16 类规则（含平面海报式 / Editorial MG / 剪影符号化方法论） |
| [references/cases/proven-editorial-mg-poster.yaml](references/cases/proven-editorial-mg-poster.yaml) | 平面海报式成功案例：太刀城市 / 命运赌场 / 兔耳魔术师三案例同构方法论 |

---

## 6. 用户最佳使用方式

### 方法 1：直接创建角色 PV

推荐输入格式：

```
角色：
身份：
性格：
视觉特点：
武器/能力：
目标：
```

角色风格确认并输出角色设定图 Prompt 后，再补充视频参数：

```
时长：
比例：
```

示例：

```
制作一个五星冰系女剑士上线 PV。
银白长发，蓝色眼睛，优雅冷酷。15 秒。
```

### 方法 2：参考某个成功 PV

```
分析这个 PV 的镜头语言、节奏、视觉风格，然后应用到我的角色。
```

系统会拆解 Camera / Action / Style / Transition 并形成新方案。

### 方法 3：优化已有 Prompt

```
优化这个 H3 Prompt，提高角色稳定性和商业感。
```

### 方法 4：平面海报式 / Editorial MG PV（参考成功案例）

当用户要做「纯二维、剪影符号化、图形匹配转场、像动态平面海报」的 PV 时，
调用 `references/cases/proven-editorial-mg-poster.yaml` 与
`references/extracted-rules.md` 第十二~十六类规则，按以下骨架产出：

```
1. 锁定三色高反差 + 色彩语义（红=危险/白=规则/黑=未知）
2. 选定世界符号库（城市/赌场/魔术等固定 2D 原语）
3. 开场：局部身体 + 剪影↔赛璐璐瞬时切换登场
4. 中段：角色相对静止 + 背景 Graphic 高速反向运动 + 图形匹配转场
5. 终场：反派私人空间揭示 + 标题由图形拼合 + 英文副标题
6. 末尾必写「严格限制」负向约束清单（颗粒化枚举禁止项）
```

> 此方法与赛璐璐「动作/文戏/魔法」基线正交，是**构图与视觉方法层**，不新增 base style。

---

## 7. Genre：内容类型层

Genre 与 Theme 正交。Genre 决定**内容类型与镜头节奏**，Theme 决定**商业定位**。

```
Genre × Theme × Variation × Style = Final PV Direction
```

| Genre | 节奏 | 单镜头 | BPM | 模板 |
|---|---|---|---|---|
| 打斗 Action | 快切顿挫 | 0.3-0.8s | 140-160 | [genre-action-15s.md](templates/genre-action-15s.md) |
| 日常文戏 Daily | 舒缓静谧 | 1-2.5s | 100-120 | [genre-daily-15s.md](templates/genre-daily-15s.md) |
| 魔法幻想 Magic | 快慢结合 | 蓄力 1.5-2.5s / 爆发 0.3-0.8s | 120-140 | [genre-magic-15s.md](templates/genre-magic-15s.md) |
| 平面海报式 Poster-MG | 高密度蒙太奇 | 0.3-0.8s（蒙太奇段） | 120-140 | [poster-mg-20s.md](templates/poster-mg-20s.md) |

**不可混用镜头节奏**。详见 [library/genre/genre-library.md](library/genre/genre-library.md)。

叠加 Persona 风格标签（性感 / 可爱 / 帅气 / 冷酷 / 热血 / 呆萌）微调表情、光影、肢体语言，
详见 [library/style/persona-tags.md](library/style/persona-tags.md)。

---

## 8. Cast：多角色与活动 PV

### 多角色 PV

> 多角色 PV 不是「多个角色各自出场」，而是**用关系做卖点**。

| 阵容 | 权重分配 | 稳定性上限 | 推荐 |
|---|---|---|---|
| duo 双人 | 45 / 25 | 32 | ✅ 首选 |
| trio 三人 | 35 / 20 / 15 | 28 | 活动 PV |
| squad 四人 | 30 / 18 / 11×2 | 24 | 仅 30s |

三条硬规则：

1. **contrast 校验** — 任意两成员至少在 2 个维度强对比，不通过直接拒绝
2. **权重规则** — 成员权重和 = 70，且 `lead >= second × 1.5`
3. **动作等级放大** — 同框有效等级 = 组件等级 + (同框人数 − 1)

关系类型 → 镜头映射见 [director/multi-character-composer.md](director/multi-character-composer.md)，
可直接使用的双人模板见 [templates/cast-duo-15s.md](templates/cast-duo-15s.md)。

### 活动 PV

| 类型 | 情绪曲线 | 建议阵容 | CTA |
|---|---|---|---|
| 周年 anniversary | 回顾 → 感谢 → 展望 | 3 | 必须 |
| 联动 collaboration | 意外 → 融合 → 期待 | 2 | 必须 |
| 季节 seasonal | 氛围 → 惊喜 → 号召 | 2 | 必须 |

**活动 PV 结尾必须包含活动名称与时间信息**，缺时间信息即为无效商业素材。

详见 [director/event-director.md](director/event-director.md)。

---

## 9. 工作流执行框架

```
USER REQUEST
    ↓
TASK ORCHESTRATOR      任务判断
    ↓
CHARACTER ANALYZER     角色理解（信息不足先补全）
    ↓
CHARACTER DNA LOCK     身份锁定
    ↓
STYLE DIRECTION        角色风格确认（日系动画 / 日系 JRPG 约束）
    ↓
CHARACTER IMAGE PROMPT 立即输出角色设定图 Prompt
    ↓
STEP2 SESSION_SPEC     确认视频时长 + 比例
    ↓
COMMERCIAL DIRECTOR    商业定位
    ↓
CAST RESOLUTION        单角色 DNA / 多角色 Cast
    ↓
GENRE SELECTOR         内容类型（打斗/文戏/魔法）
    ↓
THEME ENGINE           选择 PV 方向
    ↓
VARIATION ENGINE       选择商业版本
    ↓
STYLE STACK            确定视觉语言（含冲突检测）
    ↓
COMPOSER               自动导演
    ↓
LIBRARY MATCHER        调用组件
    ↓
SHOT PLANNER           生成分镜
    ↓
PROMPT STRUCTURE       10 段结构规范（必读）
    ↓
H3 PROMPT ENGINE       转 Base 3 字段 / Ref2VA 6 字段
    ↓
QUALITY CHECK          稳定性评估
    ↓
AUTO REVISION          自动优化
    ↓
[GENERATION GATE]      等待用户显式二次确认
    ↓
OUTPUT PACKAGE         最终制作文档
```

### H3 输出模式

| 模式 | 输入 | 字段数 | 规范 |
|---|---|---|---|
| T2VA | 纯文本 | 3 | [schema/h3-base.md](schema/h3-base.md) |
| I2VA | 首帧图 | 3 | 同上 |
| FL2VA | 首帧 + 末帧 | 3 | 同上 |
| L2VA | 末帧 | 3 | 同上 |
| Ref2VA | 多参考素材 | 6 | [schema/h3-ref2va.md](schema/h3-ref2va.md) |

---

## 10. 输出内容

| 产物 | 说明 |
|---|---|
| Character Bible | 角色视觉圣经 |
| PV Direction | 导演方案 |
| Shot List | 镜头表 |
| H3 Prompt | 生成 Prompt |
| Quality Report | 质量报告 |
| Revision Log | 修改记录 |

---

## 11. 使用原则

1. **Character First** — 角色永远优先。
2. **Commercial Before Complexity** — 商业表达优先于复杂动作。
3. **Stability Before Effects** — 稳定生成优先于视觉堆叠。
4. **One Shot One Purpose** — 一个镜头只完成一个主要任务。
5. **Consistent Identity** — 所有镜头保持一致的视觉身份。

---

## 12. 定位总结

AstraForge Studio：

- ❌ 不是 Prompt 生成器
- ❌ 不是视频模板库
- ✅ 是 AI 角色 PV 导演
- ✅ 是二次元游戏宣传制作系统
- ✅ 是商业动画视觉规划工具
- ✅ 是 2D 多画风 PV 制作系统（赛璐璐 / 厚涂 / 水彩国风 / 矢量潮流 / 韩漫 / 美漫）

一句话：

> AstraForge Studio 是一个面向二次元游戏与动画行业的 AI 角色 PV 导演系统，
> 通过角色智能分析、商业 PV 导演流程、组件化视觉库和自动质量控制，
> 将角色设定转化为可生产的视频方案。



