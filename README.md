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
| 🔄 Variation Engine | 同一角色生成多个营销版本 |
| 🎨 Style Stack | 分层控制视觉语言并检测冲突 |
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

- **Camera** — Eye Reveal / Beauty Showcase / Hero Low Angle / Detail Macro / Hand To Camera
- **Action** — Hair Flip / Weapon Reveal / Ability Release / Signature Pose
- **Expression** — Cool Gaze / Sweet Smile / Elegant Smile / Playful Wink
- **Transition** — Title Reveal / UI Card / Particle Reveal / Character Freeze
- **Theme** — Character Release / Gacha Legendary / Dark Witch / Sweet Y2K / Cool Warrior
- **Style** — Modern Cel / Mobile Game Premium / Fantasy Anime / Y2K Graphic / Dark Cinematic Cel

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
├── library/              视觉组件
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

---

## 🧪 Benchmark System

每次重大更新都需通过回归验证：

```
Skill Update → Benchmark → Quality Check → Regression Test → Release
```

当前基准用例：Sweet Y2K ✅ · Cool Warrior ✅ · Dark Witch ✅

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

包含：Character DNA System · PV Director Framework · Variation Engine · Style Engine · Quality Engine · Benchmark Suite · Visual Component Library

---

## 🤝 Contributing

欢迎贡献：Camera / Action 组件、Theme 主题、Style 定义、Benchmark 用例、文档改进。

详见 [docs/CONTRIBUTING.md](docs/CONTRIBUTING.md)。

---

## 🗺 Roadmap

- **v1.x Foundation** — 更多组件、更多模板、更完整的 Benchmark
- **v2.x Advanced Director** — 多角色 PV、剧情规划、音频导演
- **v3.x Production Platform** — 团队协作、资产管理、云端流水线

---

## 📜 License

MIT License

<div align="center">

**AstraForge Studio**

*Build Characters. Forge Worlds. Create PVs.*

</div>
