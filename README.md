<div align="center">

# ✨ AstraForge Studio

## 星铸工坊

### AI 二次元游戏角色 PV 智能导演系统

**塑造角色，锻造世界，创造属于你的 PV**

*Build Characters. Forge Worlds. Create PVs.*

![Version](https://img.shields.io/badge/version-1.2.2-blue)
![Codename](https://img.shields.io/badge/codename-2D%20Style%20Expansion-8957e5)
![AI Skill](https://img.shields.io/badge/AI-Skill-purple)
![Domain](https://img.shields.io/badge/domain-Anime%20PV-red)
![Status](https://img.shields.io/badge/status-production-green)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

[🚀 Quick Start](docs/INSTALLATION.md) ·
[📖 使用指南](docs/USER_GUIDE.md) ·
[🏗 系统架构](docs/ARCHITECTURE.md) ·
[🧩 组件库](library/) ·
[🧪 Benchmark](benchmark/)

</div>

---

## 1. Skill 简介

星铸工坊是一套面向**二次元游戏、动画角色、AI 视频创作**场景的智能 PV 导演 Skill。

它把角色侧的输入：

| 输入 | |
|---|---|
| 角色设定 | 人物背景 |
| 外观设计 | 技能设定 |
| 世界观信息 | |

转化为可直接投入制作的输出：

| 输出 | |
|---|---|
| 商业角色 PV 方案 | 分镜脚本 |
| 镜头设计 | 动作规划 |
| 表情设计 | 视觉风格方案 |
| AI 生成提示词 | 质量评估报告 |

---

## 2. Skill 解决的问题

### ① 角色不稳定

同一个角色多次生成，会出现脸变化、发型变化、服装变化、武器变化。

星铸工坊通过 **Character DNA Lock**（角色 DNA 锁定系统）保证：

```
角色身份 → 视觉特征 → 核心资产 → 持续一致
```

### ② 缺少商业 PV 导演能力

普通生成只有两步：

```
Prompt → Image
```

星铸工坊走完整导演链路：

```
角色定位 → 商业目标 → PV 结构 → 镜头语言 → 视觉输出
```

### ③ 缺少游戏商业思维

星铸工坊不是单纯生成画面，而是同时模拟**游戏 PV 导演**、**动画演出导演**、**宣发策划**三种角色，
思考的核心问题是：

> 如何让玩家记住这个角色。

---

## 3. 支持内容类型

### 角色上线 PV — 15 秒

适用：五星角色发布、新角色预告、抽卡宣传

```
身份建立 → 魅力展示 → 技能释放 → 终极记忆点
```

### 剧情 PV — 30 秒

适用：主线剧情、角色故事、世界观宣传

```
悬念 → 冲突 → 情绪高潮 → 剧情钩子
```

### 商业广告 PV — 5 秒

适用：游戏广告、社媒短视频

重点：第一眼吸引、强视觉冲击、快速记忆

### 多角色 PV — 15 / 30 秒

适用：双人对手戏、组合角色、阵容展示

用**关系**做卖点，而非多个角色各自出场。详见 [👥 多角色 PV](#-多角色-pv)。

### 活动 PV — 15 / 30 秒

适用：周年庆典、联动活动、季节限定

结尾**必须**包含活动名称与时间信息。详见 [🎉 活动 PV](#-活动-pv)。

---

## 4. 核心工作流程

```
用户需求
   ↓
角色分析
   ↓
Character DNA 锁定
   ↓
商业定位分析
   ↓
主题选择
   ↓
视觉风格匹配
   ↓
镜头 Composer 生成
   ↓
质量检测
   ↓
输出制作方案
```

完整 13 段流水线见 [🏗 Production Workflow](#-production-workflow)。

---

## 5. 核心模块

| 模块 | 职责 |
|---|---|
| 🧠 **Character Intelligence**<br>角色智能系统 | 角色分析、人设提炼、视觉关键词 |
| 🧬 **Character DNA Lock**<br>DNA 锁定系统 | 锁定脸部、发型、服装、武器、标志元素 |
| 🎬 **PV Director**<br>导演系统 | 商业节奏、镜头设计、情绪控制 |
| 🎞 **PV Composer**<br>Composer 系统 | 生成 Shot List / Camera / Action / Expression / Transition |
| 👥 **Cast Engine**<br>多角色引擎 | 画面权重、关系锚定、同框风险建模 |
| 🎉 **Event Engine**<br>活动引擎 | 周年 / 联动 / 季节 PV，强制 CTA |
| 📚 **Component Library**<br>组件库 | Camera / Action / Expression / Transition / Theme / Style |
| 🧪 **Quality Engine**<br>质量引擎 | 角色稳定性、风格一致性、商业冲击力、镜头可执行性 |

---

## 6. 用户最佳使用方式

推荐输入格式：

```
角色名称：
角色定位：
性格：
外观：
技能：
世界观：
目标：
PV 类型：
视觉风格：
```

示例：

```
创建一个 15 秒五星冰系女性角色上线 PV。
定位：高稀有度手游角色
风格：高级二次元商业 PV
要求：突出角色优雅与力量
```

系统会在生成前锚定时长与比例（`SESSION_SPEC`），信息不足时先给出补全建议，
**不会**在信息不充分时直接产出结果。

---

## 7. 适用人群

| 人群 | 场景 |
|---|---|
| **游戏团队** | 角色 PV 策划、宣发团队、美术团队 |
| **AI 创作者** | AI 视频制作、Prompt 工程、角色设计 |
| **独立开发者** | 游戏 Demo 宣传、角色展示 |

---

## 8. Skill 定位总结

> **AstraForge Studio（星铸工坊）是一名 AI 驱动的二次元游戏 PV 导演，
> 将角色设定转化为商业级角色宣传内容。**

它不是：❌ Prompt 生成器 ❌ 视频模板库
它是：✅ AI 角色 PV 导演 ✅ 二次元游戏宣发制作系统 ✅ 商业动画视觉规划工具

---
## 🎞 Genre × Theme

Genre 决定**内容类型与镜头节奏**，Theme 决定**商业定位**，两者正交组合。

| Genre | 节奏 | 单镜头 | 推镜 | BPM | 参考风格 |
|---|---|---|---|---|---|
| 打斗 Action | 快切顿挫 | 0.3-0.8s | 0.4/s | 140-160 | 龙珠Z / 咒术回战 |
| 日常文戏 Daily | 舒缓静谧 | 1-2.5s | 0.2/s | 100-120 | 魔卡少女樱 / 堀与宫村 |
| 魔法幻想 Magic | 快慢结合 | 蓄力 1.5-2.5s / 爆发 0.3-0.8s | 环绕 30-45° | 120-140 | 美少女战士 |

每个 Genre 都提供**完整可替换的 15s Prompt 模板**，以及 5s / 10s 适配方案。

---

## 📝 Prompt Engineering

10 段结构规范确保输出不失控：

```
1 开头总述   2 角色设定   3 主题设定   4 音乐        5 画面风格
6 动态与转场 7 分时间段镜头设计（最核心） 8 表演要求  9 避免项  10 核心目标
```

H3 格式转换：

| 模式 | 输入 | 字段数 |
|---|---|---|
| T2VA / I2VA / FL2VA / L2VA | 文本 / 首帧 / 首末帧 / 末帧 | 3 |
| Ref2VA | 多参考素材（图/视频/音频） | 6 |

每个镜头包含六要素：`composition` / `subjects` / `environment` / `actions` / `camera` / `sound`

---

## 👥 多角色 PV

> 多角色 PV 不是「多个角色各自出场」，而是**用关系做卖点**。

| 阵容 | 权重分配 | 稳定性上限 | 建议 |
|---|---|---|---|
| duo 双人 | 45 / 25 | 32 | ✅ 首选 |
| trio 三人 | 35 / 20 / 15 | 28 | 活动 PV |
| squad 四人 | 30 / 18 / 11×2 | 24 | 仅 30s，禁止同框 |

三道闸门（任一不通过即拒绝）：

1. **contrast 校验** — 任意两成员至少 2 维强对比（发色 / 剪影 / 服装色 / 身形 / 标志物）
2. **权重规则** — 成员权重和 = 70，且 `lead >= second × 1.5`
3. **动作等级放大** — 同框有效等级 = 组件等级 + (同框人数 − 1)

**身份串味（identity_bleed）** 是多角色最致命的失败模式 —— AI 会把 A 的特征混到 B 身上。
风险随同框人数上升：2 人 medium / 3 人 high / 4 人 critical。

关系类型 → 镜头映射：

| 关系 | 推荐镜头 |
|---|---|
| rival 宿敌 | `duo-standoff`、`back-to-back` |
| ally 同伴 | `shoulder-to-shoulder`、`duo-formation` |
| siblings 血亲 | `mirrored-pose` |
| opposing 对立 | `split-frame-duo`（技术上是两个单人镜头，风险最低） |

可直接使用的双人模板：[templates/cast-duo-15s.md](templates/cast-duo-15s.md)
（含 10 段完整 Prompt、关系→构图替换表、5s/30s 适配、风险自检清单）

---

## 🎉 活动 PV

角色 PV 求「记住角色」，活动 PV 求「产生行动」。

| 类型 | 情绪曲线 | 建议阵容 | CTA |
|---|---|---|---|
| 周年 anniversary | 回顾 → 感谢 → 展望 | 3 | 必须含活动时间 |
| 联动 collaboration | 意外 → 融合 → 期待 | 2 | 必须含限时标识 |
| 季节 seasonal | 氛围 → 惊喜 → 号召 | 2 | 必须含活动时间 |

**结尾缺时间信息的活动 PV 是无效商业素材。**

季节 PV 是唯一允许开场弱化角色的类型（0-3s 可降至 30%），全片平均仍须回到 70%。

---

## 🏗 Production Workflow

```
        User Request
             ↓
      Task Orchestrator
             ↓
   Character Intelligence
             ↓
     Character DNA Lock
             ↓
    Commercial Director
             ↓
        Theme Engine
             ↓
      Variation Engine
             ↓
        Style Stack
             ↓
        PV Composer
             ↓
        Shot Planner
             ↓
     Quality Validation
             ↓
     Production Package
```

---

## 🛠 Quick Example

输入：

```
Create a 15 second character release PV.
Character: Silver-haired female knight.
Personality: Elegant and cold.
Ability: Ice sword.
Goal: Five-star mobile game launch.
```

AstraForge 输出：

```
Theme:  Cool Female Release
Style:  Modern Cel + Mobile Game Premium
Shots:  Eye Reveal → Beauty Showcase → Weapon Reveal → Hero Pose → Title Reveal
```

以及完整的 Character Bible、Shot List、H3 Prompt Package、Quality Report。

---

## 📦 Output Package

每次生成都会产出：

| 产物 | 说明 |
|---|---|
| Character Bible | 角色视觉身份文档 |
| PV Direction | 商业创意方向 |
| Style Direction | 视觉语言定义 |
| Shot List | 时间轴与镜头计划 |
| Prompt Package | 可直接用于生成的 Prompt |
| Quality Report | 风险分析与评分 |
| Revision Log | 自动优化记录 |

---

## 📊 Quality First

AstraForge 的评分权重刻意把「能不能稳定生成」放在第一位：

| Metric | Weight |
|---|---:|
| Generation Stability | 35% |
| Character DNA Consistency | 25% |
| Shot Feasibility | 15% |
| Visual Impact | 10% |
| Commercial Value | 10% |
| Art Direction | 5% |

系统自动检测：角色漂移、动作过载、镜头风险、特效堆叠、风格冲突。

---

## 🧩 Component Ecosystem

- **Camera** — Eye Reveal / Beauty Showcase / Hero Low Angle / Detail Macro / Hand To Camera / Environment Reveal
- **Camera（多角色）** — Duo Standoff / Back To Back / Shoulder To Shoulder / Split Frame Duo / Group Formation / Mirrored Pose
- **Action** — Hair Flip / Weapon Reveal / Ability Preparation / Ability Release / Signature Pose
- **Expression** — Cool Gaze / Sweet Smile / Elegant Smile / Playful Wink / Composed Gaze / Battle Resolve / Detached Stare
- **Transition** — Title Reveal / UI Card / Particle Reveal / Character Freeze
- **Theme** — Character Release / Gacha Legendary / Dark Witch / Sweet Y2K / Cool Warrior / Male Suit / Male Samurai / Male Knight
- **Theme（活动）** — Anniversary Celebration / Collaboration Event / Seasonal Event
- **Style（2D Base）** — Modern Cel / Retro Cel / Painterly Anime / Watercolor Ink / Vector Flat / Korean Manhwa / Western Comic
- **Style（Premium / Special）** — Mobile Game Premium / Fantasy Anime / Y2K Graphic / Dark Cinematic Cel
- **Genre** — 打斗 Action / 日常文戏 Daily / 魔法幻想 Magic（可量化参数）
- **Persona** — 性感 / 可爱 / 帅气 / 冷酷 / 热血 / 呆萌（叠加于 Genre 之上）

---

## 📂 Project Structure

```
astraforge-studio/
├── SKILL.md              AI Skill 入口
├── skill/                Skill 部署层
├── core/                 核心规则
│   ├── character-dna/
│   ├── style-engine/
│   ├── quality-engine/
│   └── variation-engine/
├── workflow/             任务调度
├── director/             导演系统
├── library/              视觉组件 + genre
├── templates/            商业模板
├── references/           案例库
├── benchmark/            回归测试
├── schema/               数据协议
├── examples/             示例输出
├── tools/                校验脚本
├── release/              发布信息
└── docs/                 项目文档
```

---

## 🎬 Examples

| Example | Type |
|---|---|
| Sweet Y2K Girl | Character Release PV |
| Cool Warrior | Combat Showcase |
| Dark Witch | Story Character PV |

详见 [examples/](examples/)。

**端到端实测样例**：[examples/walkthrough-frostblade/](examples/walkthrough-frostblade/)
完整走通 Step0 → Quality Report 的真实产出（冷艳冰系女剑士 / 打斗 / 15s），
含 Character DNA、Shot List、成品 Prompt 与质量报告。

---

## 🧪 Benchmark System

每次重大更新都需通过回归验证：

```
Skill Update → Benchmark → Quality Check → Regression Test → Release
```

| # | 用例 | 维度 | Genre | 状态 |
|---:|---|---|---|---|
| 01 | Sweet Y2K Girl | Theme | daily | ✅ 98 |
| 02 | Cool Warrior | Theme | action | ✅ 96 |
| 03 | Dark Witch | Theme | magic | ✅ 94 |
| 04 | Male Knight Combat | Genre + 性别 | action | ✅ 91 |
| 05 | Academy Tsundere Daily | Genre | daily | ✅ 98 |
| 06 | Magic Girl Transform | Genre | magic | ✅ 92 |
| 07 | Duo Rival Showcase | **Cast** | action | ✅ 90 |
| 08 | Anniversary Trio | **Event** | daily | ✅ 84 |
| 09 | Male Suit Elegance | Theme | daily | ✅ 97 |
| 10 | Male Samurai Combat | Theme | action | ✅ 93 |
| 11 | Male Suit Concept Sheet | Concept-Sheet | daily | ✅ 97 |
| 12 | Sweet Y2K Girl Concept Sheet | Concept-Sheet | daily | ✅ 98 |
| 13 | Neutral Character Concept Sheet | Concept-Sheet | daily | ✅ 98 |

覆盖 3 Genre × 2 性别 × 3 阵容 × 1 活动类型，含男性西装 / 武士 / 骑士 Theme、女性甜系 Y2K / 酷飒 JRPG / 学院 / 魔法少女 / 赛博 / 暗黑女巫 Theme、中性 / 非二元 character-release / gacha-legendary Theme 与「角色概念分解图」资产，当前 **93 / 100**（13 例）。
用例以机器可校验 YAML 存放于 [benchmark/test-cases/](benchmark/test-cases/)，
由 `tools/validate_benchmarks.py` 在 CI 中强制校验组件引用、风险预算与评分自洽。

---

## 📚 Documentation

| 文档 | 说明 |
|---|---|
| [User Guide](docs/USER_GUIDE.md) | 使用指南 |
| [Architecture](docs/ARCHITECTURE.md) | 系统架构 |
| [Developer Guide](docs/DEVELOPER_GUIDE.md) | 开发规范 |
| [Installation](docs/INSTALLATION.md) | 安装部署 |
| [Configuration](docs/CONFIGURATION.md) | 配置说明 |
| [Contributing](docs/CONTRIBUTING.md) | 贡献指南 |
| [Prompt Structure](core/prompt-structure.md) | 10 段结构规范（生成前必读） |
| [Genre Library](library/genre/genre-library.md) | 三类内容 Genre 参数 |
| [H3 Base](schema/h3-base.md) / [H3 Ref2VA](schema/h3-ref2va.md) | H3 输出格式规范 |
| [Extracted Rules](references/extracted-rules.md) | 从实证案例提取的规则 |
| [Multi-Character Composer](director/multi-character-composer.md) | 多角色导演逻辑 |
| [Event Director](director/event-director.md) | 活动 PV 导演逻辑 |
| [Branch Policy](docs/BRANCH_POLICY.md) | 分支与推送规范 |
| [Changelog](CHANGELOG.md) | 版本记录 |
| [Roadmap](ROADMAP.md) | 路线规划 |

---

## 🚀 Installation

```bash
git clone https://github.com/AvalonLee/AstraForge-Studio.git
cd AstraForge-Studio
```

详见 [docs/INSTALLATION.md](docs/INSTALLATION.md)。

---

## 📦 Current Release

**AstraForge Studio v1.2.2** — 🟢 Poster-MG Methodology

包含：Character DNA System · PV Director Framework · Genre Engine · **Cast Engine（多角色）** · **Event Engine（活动 PV）** · Variation Engine · Style Engine · Prompt Engine（10 段规范 + H3 转换）· Quality Engine · Benchmark Suite · Visual Component Library · **平面海报式 / Editorial MG 方法**

v1.2 新增：7 套 2D base style（现代赛璐璐 / 复古赛璐璐 / 厚涂动画 / 水彩国风 / 矢量潮流 / 韩漫 / 美漫）、男性角色主题（西装 / 武士 / 骑士）、角色设定图 Prompt Gate、BM-09 / BM-10 基准用例

v1.2.1 新增：角色概念分解图资产（director/character-concept-sheet.md），将「服装分层 / 私密内着 / 表情集 / 材质特写 / 生活切片」六维框架固化为可复用设定稿规范；三套男性主题补充 `concept_sheet` 分解矩阵（服装分层 / 内着 / 表情集 / 材质特写 / 生活切片），新增 BM-11 回归用例。女性向扩展：概念分解图文档补齐性别化背景（羊皮纸纹理）、生活切片三桶统一命名与女性示例、做旧痕迹材质细节；六套女性主题（cool-female-jrpg / sweet-y2k-girl / academy-character / magic-girl / cyberpunk-girl / dark-witch-release）补充 `concept_sheet` 矩阵，新增 BM-12 女性回归用例。中性扩展：为性别中立的 `character-release` / `gacha-legendary` 主题补充 `concept_sheet` 矩阵（跨性别通用示例、背景白底/羊皮纸二选一），新增 BM-13 中性回归用例。

v1.2.2 新增：平面海报式 / Editorial MG / 剪影符号化 PV 方法论。新增实证案例 `references/cases/proven-editorial-mg-poster.yaml`（综合太刀城市 / 命运赌场 / 兔耳魔术师三份成功案例），`references/extracted-rules.md` 由 11 类扩展至 16 类（新增平面海报式视觉、剪影↔赛璐璐切换、反派终场揭示、符号化图形系统、动态负向限制清单范式）。SKILL.md 新增「方法 4：平面海报式 PV」与案例库入口；manifest 新增 `editorial_mg_poster_style` 能力声明与 `visual_approaches`（cel_animation / editorial_mg_poster 双构图模式）。

v1.1 新增：多角色 PV（duo / trio）、活动 PV（周年 / 联动 / 季节）、6 个同框镜头组件、双人 Prompt 模板

---

## 🤝 Contributing

欢迎贡献：Camera / Action 组件、Theme 主题、Style 定义、Benchmark 用例、文档改进。

详见 [docs/CONTRIBUTING.md](docs/CONTRIBUTING.md)。

---

## 🗺 Roadmap

- **v1.x Foundation** — 更多组件、更多模板、更完整的 Benchmark
- **v2.x Advanced Director** — 剧情规划、音频导演、多角色扩展至 squad
- **v3.x Production Platform** — 团队协作、资产管理、云端流水线

---

## 📜 License

MIT License

<div align="center">

**AstraForge Studio · 星铸工坊**

AI 二次元游戏角色 PV 智能导演系统

*Build Characters. Forge Worlds. Create PVs.*

**塑造角色，锻造世界，创造属于你的 PV。**

</div>



