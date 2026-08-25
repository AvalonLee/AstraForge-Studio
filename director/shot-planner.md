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
2. 15s PV 最多 4 次镜头切换
3. 同一 Shot 只保留一个高风险动作
4. 每个角色出现时改变镜头高度 / 方向 / 姿态 / 手势，避免站桩
5. 角色展示优先于背景与特效

---

## 风险标注

每个 Shot 必须给出 `risk_level: low / medium / high`。
若单个 Shot 为 high，进入 Auto Revision。
