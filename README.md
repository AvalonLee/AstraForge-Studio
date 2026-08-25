<div align="center">

# ✨ AstraForge Studio

### AI Anime Game Character PV Director System

**Transform Character Concepts into Commercial Anime PV Production Pipelines**

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![AI Skill](https://img.shields.io/badge/AI-Skill-purple)
![Domain](https://img.shields.io/badge/domain-Anime%20PV-red)
![Status](https://img.shields.io/badge/status-production-green)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

[🚀 Quick Start](docs/INSTALLATION.md) ·
[📖 Documentation](docs/USER_GUIDE.md) ·
[🏗 Architecture](docs/ARCHITECTURE.md) ·
[🧩 Components](library/) ·
[🧪 Benchmark](benchmark/)

</div>

---

## 🌌 Overview

AstraForge Studio 是一个 AI 驱动的二次元游戏角色 PV 导演系统。

它不是一个 Prompt 生成器，而是把完整的动画 PV 制作流程结构化：

```
Character Concept
      ↓
Commercial Direction
      ↓
Visual Design
      ↓
Shot Planning
      ↓
AI Video Generation Workflow
```

面向用户：

- 二次元手游开发者
- 角色设计师
- AI 视频创作者
- 动画工作室与创意团队

---

## 🎬 它解决什么问题

| 典型痛点 | AstraForge 的解法 |
|---|---|
| 有角色设定，但不知道怎么做 PV | Character Intelligence 自动分析角色类型、商业卖点、视觉记忆点 |
| AI 视频生成容易角色崩坏 | Character DNA Lock 锁定脸 / 发型 / 服装 / 配色 / 标志物 |
| 镜头缺乏手游商业感 | 内置商业 PV 导演规则：Hook / Beauty Showcase / Signature / Hero Ending |
| Prompt 很长但效果不好 | Composer 拆分 Shot / Camera / Action / Expression / Style，降低生成风险 |
| 多角色风格不统一 | Style Stack 三层结构 + 冲突检测自动收敛视觉语言 |

---

## ✨ Core Systems

| System | Function |
|---|---|
| 🧬 Character DNA Lock | 保护角色身份，跨镜头零漂移 |
| 🎬 PV Director | 生成商业 PV 结构（5s / 15s / 30s） |
| 🎞 Genre Engine | 打斗 / 日常文戏 / 魔法幻想，含可量化运镜参数 |
| 👥 Cast Engine | 多角色 PV：画面权重、关系锚定、同框风险建模 |
| 🎉 Event Engine | 周年 / 联动 / 季节活动 PV，强制 CTA |
| 🔄 Variation Engine | 同一角色生成多个营销版本 |
| 🎨 Style Stack | 分层控制视觉语言并检测冲突 |
| 📝 Prompt Engine | 10 段结构规范 + H3 格式转换（Base / Ref2VA） |
| 🧪 Quality Engine | 稳定性优先的自动评分与返修 |
| 📚 Component Library | 可复用的镜头 / 动作 / 表情 / 转场组件 |

---

## 🎥 支持的 PV 模式

### 5s Advertisement PV

快速抓取注意力，用于广告投放与短视频平台。

```
Hook → Memory Frame
```

### 15s Character Release PV（主力模式）

手游新角色上线、Gacha Banner、新英雄公告。

```
0-3s    HOOK        角色第一印象
3-6s    IDENTITY    脸 / 发型 / 服装
6-10s   PERSONALITY 情绪与性格
10-13s  SIGNATURE   技能 / 武器 / 标志特征
13-15s  TITLE       最终记忆画面
```

### 30s Story Character PV

五星角色、剧情角色、周年预告。

```
Mystery → Reveal → Conflict → Power → Emotion
```

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
- **Theme** — Character Release / Gacha Legendary / Dark Witch / Sweet Y2K / Cool Warrior
- **Theme（活动）** — Anniversary Celebration / Collaboration Event / Seasonal Event
- **Style** — Modern Cel / Mobile Game Premium / Fantasy Anime / Y2K Graphic / Dark Cinematic Cel
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

覆盖 3 Genre × 4 Theme × 2 性别 × 3 阵容 × 1 活动类型，当前 **93 / 100**。
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

**AstraForge Studio v1.0.0** — 🟢 Production Foundation Release

包含：Character DNA System · PV Director Framework · Genre Engine · **Cast Engine（多角色）** · **Event Engine（活动 PV）** · Variation Engine · Style Engine · Prompt Engine（10 段规范 + H3 转换）· Quality Engine · Benchmark Suite · Visual Component Library

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

**AstraForge Studio**

*Build Characters. Forge Worlds. Create PVs.*

</div>
