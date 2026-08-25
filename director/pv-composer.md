# AstraForge Composer

核心导演模块，负责生成 Shot / Camera / Action / Expression / Transition。

---

## 导演链

```
Character DNA → Theme → Variation Engine → Style Stack
→ Style Validation Gate → Composer → Shot Planner → H3 Prompt
```

任何 Shot 生成前必须读取 `character_dna`。

---

## Component 自动选择算法

```
Component Score = Character Fit + Theme Match + Commercial Value - Risk
```

示例（银发女剑士）：

| 组件 | Fit | Theme | Commercial | Risk | Total | 结果 |
|---|---:|---:|---:|---:|---:|---|
| weapon-reveal | 10 | 10 | 10 | -2 | **28** | 选择 |
| 普通挥剑 | 7 | 5 | 6 | -5 | 13 | 舍弃 |

---

## Quality Feedback Loop

```
Composer → Shot Plan → Quality Check → Risk Analyzer → Revision → Final Shot Plan
```

### 自动修正示例

输入：黑暗魔女五星 PV

初版：

```yaml
action: huge magic explosion
camera: 360 rotation
effect: level 4
```

检测：action=high / camera=high / effect=critical

自动修正：

```yaml
action: controlled magic
camera: hero low angle
effect: purple energy particles (level 2)
```

风险：HIGH → LOW

---

## 最终输出模板

1. **Character Direction** — 角色定位 / 视觉卖点 / 商业目标
2. **Style Direction** — Base Style / Premium Layer / Special Layer
3. **Shot Plan** — 表格（Shot / Time / Camera / Action / Purpose）
4. **H3 Prompt** — 逐 Shot 输出
5. **Quality Report** — Stability / Risk / Score / Revision
