# AstraForge Studio

**AI Anime Game Character PV Director System**

Version: 1.0.0 — Production Foundation Release

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

## 3. 核心能力

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

---

## 4. 内置知识系统

- **Camera Library** — Eye Reveal / Beauty Showcase / Hero Low Angle / Detail Macro / Hand To Camera / Action Tracking / Final Pose
- **Action Library** — Hair Flip / Head Turn / Confident Walk / Hand Gesture / Weapon Reveal / Ability Release / Transformation / Signature Pose
- **Expression Library** — Cool Gaze / Confident Smirk / Sweet Smile / Playful Wink / Shy Expression / Elegant Smile / Idol Bright / Villain Pressure
- **Transition Library** — Flash Cut / Anime Impact / Graphic Panel / UI Card / Glitch Data / Particle Reveal / Title Reveal / Character Freeze
- **Theme Library** — Character Release / Gacha Legendary / Cool Female JRPG / Sweet Y2K / Academy / Magic Girl / Cyberpunk
- **Style Library** — Modern Cel / Retro Cel / Y2K Graphic / Fantasy Anime / Mobile Game Premium / Dark Cinematic Cel

---

## 5. 用户最佳使用方式

### 方法 1：直接创建角色 PV

推荐输入格式：

```
角色：
身份：
性格：
视觉特点：
武器/能力：
目标：
时长：
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

---

## 6. 工作流执行框架

```
USER REQUEST
    ↓
TASK ORCHESTRATOR      任务判断
    ↓
CHARACTER ANALYZER     角色理解
    ↓
CHARACTER DNA LOCK     身份锁定
    ↓
COMMERCIAL DIRECTOR    商业定位
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
H3 PROMPT ENGINE       生成视频 Prompt
    ↓
QUALITY CHECK          稳定性评估
    ↓
AUTO REVISION          自动优化
    ↓
OUTPUT PACKAGE         最终制作文档
```

---

## 7. 输出内容

| 产物 | 说明 |
|---|---|
| Character Bible | 角色视觉圣经 |
| PV Direction | 导演方案 |
| Shot List | 镜头表 |
| H3 Prompt | 生成 Prompt |
| Quality Report | 质量报告 |
| Revision Log | 修改记录 |

---

## 8. 使用原则

1. **Character First** — 角色永远优先。
2. **Commercial Before Complexity** — 商业表达优先于复杂动作。
3. **Stability Before Effects** — 稳定生成优先于视觉堆叠。
4. **One Shot One Purpose** — 一个镜头只完成一个主要任务。
5. **Consistent Identity** — 所有镜头保持一致的视觉身份。

---

## 9. 定位总结

AstraForge Studio：

- ❌ 不是 Prompt 生成器
- ❌ 不是视频模板库
- ✅ 是 AI 角色 PV 导演
- ✅ 是二次元游戏宣传制作系统
- ✅ 是商业动画视觉规划工具

一句话：

> AstraForge Studio 是一个面向二次元游戏与动画行业的 AI 角色 PV 导演系统，
> 通过角色智能分析、商业 PV 导演流程、组件化视觉库和自动质量控制，
> 将角色设定转化为可生产的视频方案。
