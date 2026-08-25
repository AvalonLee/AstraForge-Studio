# Shot Planner

将 Composer 的决策落为可执行的镜头表。

---

## Shot 字段

```yaml
- id:
  time:
  purpose:
  character_state:
  camera:
  action:
  expression:
  effect:
  transition:
  risk_level:
```

---

## 编排规则

1. **One Shot One Purpose** — 一个镜头只完成一个主要任务
2. **快切优先（默认节奏）** — 15s PV 使用 8-10 个镜头（平均 1.5-2s/镜），
   禁止长镜头拖节奏。5s 4-5 镜 / 10s 6-7 镜 / 15s 8-10 镜 / 30s 14-16 镜
3. **多角度强制** — 连续两个镜头禁止同机位 / 同景别 / 同角度；
   每段动作高潮至少 3 个不同角度快切（正面 / 侧面 / 背面 / 45° / 俯拍 / 仰拍 / 鱼眼 / 荷兰角）
4. **镜头转动高效快速** — 优先快速甩镜、快速部分环绕（90-180°）、急推 / 急拉、
   快切多角度；慢速环绕仅用于蓄力铺垫且不超过 30-45°
5. **英雄镜头配额** — 15s 至少 2 个英雄镜头（开场 Hook / 高潮或结尾定格），
   30s 至少 3 个（开场 / 高潮 / 结尾）；英雄镜头使用低机位仰拍 + 快速部分环绕，
   优先调用 `hero-low-angle` / `hero-orbit` / `final-pose`
6. 同一 Shot 只保留一个高风险动作
7. 每个角色出现时改变镜头高度 / 方向 / 姿态 / 手势，避免站桩
8. 角色展示优先于背景与特效

---

## 风险标注

每个 Shot 必须给出 `risk_level: low / medium / high`。
若单个 Shot 为 high，进入 Auto Revision。
