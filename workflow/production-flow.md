# Character PV Production Workflow

## Phase 1 — Character Understanding

Load: `character-analyzer`
Output: Character Profile

## Phase 2 — Commercial Decision

Load: `pv-mode-selector`, `variation-selector`
Output: PV Type + Variation

## Phase 3 — Experience Retrieval

Load: Reference Case / Theme / Style

## Phase 4 — Composition

Load: `component-selector`, `shot-planner`, `rhythm-controller`

## Phase 5 — Generation

Create: H3 Prompt

## Phase 6 — Evaluation

Run: `quality-check` → `risk-analyzer` → `auto-revision`

---

## Final Delivery

```
Character Direction
PV Concept
Shot List
H3 Prompt
Quality Score
```

---

## Character Classifier

| Archetype | 关键词 | 加载 |
|---|---|---|
| cool_female | 冷酷 / 御姐 / 战士 / 剑士 / 女王 / 高冷 | theme.cool-female-jrpg |
| sweet_female | 可爱 / 甜 / 少女 / 偶像 / 粉色 | theme.sweet-y2k-girl |
| academy_female | 学园 / 学生 / 制服 / 青春 | theme.academy-character |
| fantasy_female | 魔法 / 贵族 / 精灵 / 圣女 | theme.magic-girl |
| cyber_female | 赛博 / 科技 / 黑客 / neon | theme.cyberpunk-girl |
| boss | Boss / 反派 / 敌人 | theme.boss-intro |

**混合规则**：计算权重，选择主类型 + 辅助 Style，不强制二选一。

---

## PV Mode Selector

| 条件 | 模式 |
|---|---|
| 新角色 / 角色介绍 / 游戏上线 | 15s Character Release（默认） |
| 明确要求短视频广告投放 | 5s Mobile Ad |
| 限定 / 五星 / 稀有 | Gacha Showcase |
| 剧情 / 背景 / 世界观 | 30s Story PV |

未指定时默认：15s New Character Release。

---

## Fallback Rules

| 场景 | 处理 |
|---|---|
| 角色信息缺失 | 不生成，询问年龄感 / 性格 / 风格 / PV 用途 |
| 混合原型（如甜美机械少女） | Primary: sweet_female / Secondary: cyber_style |
| 需求过多（少女+战斗+变身+城市毁灭+多人战争） | 保留角色卖点，删除低价值复杂元素 |
| 缺少 Style | 默认 modern-cel |
| 缺少时长 | 默认 15s |
| H3 风险过高 | 降低 Action Level，保留 Camera + Expression + Identity |

冲突优先级：

```
Character Identity > Commercial Goal > Visual Effect > Complex Action
```
