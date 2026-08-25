# AstraForge Studio User Guide

Version: 1.0.0

---

## 1. 什么是 AstraForge Studio

AstraForge Studio 是一个 AI 驱动的二次元游戏角色 PV 导演系统。

它帮助创作者把：

```
角色设定 → 商业定位 → PV 方案 → 镜头设计 → 视频生成 Prompt
```

转化为完整制作流程。

适用于：

- 二次元手游角色 PV
- 游戏上线宣传
- Gacha 角色展示
- 动画角色宣传
- AI 视频生成前期设计

---

## 2. 能解决什么问题

### 对角色设计师

> 有角色，但不知道如何展示。

解决：自动生成角色卖点、展示方向、镜头语言。

### 对 PV 策划

> 不知道如何规划 15 秒角色 PV。

解决：提供时间轴、Shot Plan、Camera、Action、Emotion。

### 对 AI 视频创作者

> Prompt 复杂但效果不稳定。

解决：通过 Character DNA、Component Library、Quality Check 提高稳定性。

---

## 3. 推荐使用流程

### Step 1 — 输入角色信息

推荐格式：

```
角色名称：
角色类型：
外观：
性格：
能力：
目标：
PV 长度：
参考方向：
```

示例：

```
制作一个 15 秒五星角色上线 PV。
角色：银发冰系女剑士。
性格：冷静、高贵。
能力：冰元素剑技。
目标：手游角色上线宣传。
```

### Step 2 — 选择 PV 模式

| 模式 | 用途 |
|---|---|
| 5 秒广告 | 短广告投放 |
| **15 秒角色 PV** | 新角色上线（推荐模式） |
| 30 秒剧情 PV | 角色故事展示 |

### Step 3 — 系统自动执行

```
角色分析 → 商业定位 → Theme 选择 → Variation 选择 → Style 组合 → 镜头设计 → 质量检查
```

---

## 4. 高级使用方式

### Reference 模式

```
分析这个 PV 的镜头语言，应用到我的角色。
```

系统拆解：节奏、镜头、风格、转场。

### Prompt 优化模式

```
优化这个视频 Prompt，提高角色稳定性、商业感、生成成功率。
```

系统会执行 Prompt Audit：

- **角色一致性** — 发型 / 服装 / 配色是否固定，是否存在互相冲突的描述
- **视频可生成性** — 是否存在不可能镜头
- **AI 风险检测** — 自动标记 3D 倾向词、真人摄影词、复杂物理动作、超大量角色

例：

```
❌ 镜头绕角色 360 度旋转，同时高速推进，同时人物奔跑
✅ 2.5D side parallax movement, slow push-in, character runs across frame
```

---

## 5. 最佳实践

**推荐做**

- ✅ 明确角色身份
- ✅ 明确商业目标
- ✅ 明确 PV 长度

**避免**

- ❌ 只输入「做一个酷炫 PV」
- ❌ 同时要求多个视觉方向
- ❌ 过度复杂动作

### H3 生成约束

单镜头推荐：

```
1 个主要动作 + 1 个镜头运动 + 1 个主要视觉焦点
```

避免：

```
多人物互动 / 复杂打斗连招 / 同时改变服装、发型、环境
```

MiniMax H3 最容易失败的不是风格，而是「一个镜头塞 10 件事情」。

### 动作优先级

| 级别 | 内容 |
|---|---|
| A 级 | look camera / smile / turn / hair movement / hand gesture |
| B 级 | weapon draw / power release |
| C 级 | group battle / destruction / physics simulation |

默认使用 A 级 + B 级组合。

### 动画风格约束

推荐：cel shading、hard shadow、graphic motion、2.5D movement
禁止：realistic photography、PBR material、3D character rendering、live action camera

---

## 6. 输出内容

| 产物 | 说明 |
|---|---|
| Character Bible | 角色视觉定义 |
| PV Direction | 导演方案 |
| Shot List | 镜头表 |
| Prompt Package | 生成 Prompt |
| Quality Report | 质量分析 |
| Revision Log | 修改记录 |

---

## 7. 15 秒角色上线 PV 模板参考

| Shot | 时间 | 目的 | Camera | 内容 |
|---|---|---|---|---|
| 01 | 0-2s | Hook | reveal-closeup | 眼睛、脸、标志特征 |
| 02 | 2-5s | Identity | beauty-showcase | face → hair → outfit → signature item |
| 03 | 5-8s | Personality | medium close | 表情 + 魅力动作 |
| 04 | 8-12s | Signature | action-tracking | ability-release 或 weapon-reveal |
| 05 | 12-15s | Title | final-pose | 角色名 + 称号 + 定格 |

验收标准：

- ✓ 第一秒出现角色
- ✓ 15 秒内完成角色介绍
- ✓ 有能力展示
- ✓ 有最终记忆画面
- ✓ 角色 DNA 未变化

---

## 8. 常见陷阱与规则

### 甜系角色动作冲突

甜妹类角色容易自动叠加 wink + 手伸镜头 + hair flip + 转身，导致手部异常。

```yaml
sweet_character_motion_limit:
  per_shot:
    max: 1 charm_action + 1 expression_change
```

### Y2K 视觉过载

容易 UI 太多、贴纸太多、背景太复杂。

```yaml
y2k_balance_rule:
  character_priority: 70%
  graphic_element: 30%
```

### 站桩问题

角色每次出现都应改变镜头高度、方向、身体姿态和手势，避免 AI 生成时「站桩」。

---

## 9. 系统规则

1. 优先保护 Character DNA。
2. 先确定商业目的，再选视觉风格。
3. 先降低生成风险，再增加特效。
4. 每个镜头只安排一个主要动作。
5. 所有场景保持一致的视觉身份。
