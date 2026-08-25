# AstraForge Benchmark Suite

每次重大更新都必须通过回归验证：

```
Skill Update → Benchmark → Quality Check → Regression Test → Release
```

---

## 测试链路

每个用例需完整走通：

```
Task Orchestrator → Character Analyzer → Reference Retrieval
→ Theme Selector → Component Selector → Shot Planner
→ H3 Risk Check → Quality Check
```

每一步单独打分，汇总为 100 分制。

---

## 当前用例

| # | 用例 | 角色方向 | 状态 | 分数 |
|---|---|---|---|---|
| 01 | Sweet Y2K Girl | 甜系 / 时尚 | ✅ PASS | 96 → 98 |
| 02 | Cool Warrior | 冷艳 / 战斗 | ✅ PASS | 99 → 96 |
| 03 | Dark Witch | 幻想 / 黑暗魔女 | ✅ PASS | 99 → 94 |

> 加入生成稳定性权重后，战斗与魔法角色分数下调 —— 视觉强但生成风险更高。

---

## 覆盖情况

| 方向 | 状态 |
|---|---|
| 甜系 | ✅ |
| 冷艳 | ✅ |
| 幻想 | ✅ |
| 男角色 | ⬜ v1.1 待补 |
| 多角色 / 群像 | ⬜ v1.1 待补 |
| 活动 PV | ⬜ v1.1 待补 |

当前评分：**85 / 100**（可发布，但 v1.1 需扩展测试范围）

---

## Benchmark 发现并固化的规则

### Issue-01 — 甜系角色动作冲突

甜妹类角色容易叠加 wink + 手伸镜头 + hair flip + 转身，导致手部异常。

```yaml
sweet_character_motion_limit:
  per_shot:
    max: 1 charm_action + 1 expression_change
```

### Issue-02 — Y2K 视觉过载

```yaml
y2k_balance_rule:
  character_priority: 70%
  graphic_element: 30%
```

---

## 评分构成

| 维度 | 权重 |
|---|---:|
| Generation Stability | 35% |
| Character DNA Consistency | 25% |
| Shot Feasibility | 15% |
| Visual Impact | 10% |
| Commercial Value | 10% |
| Art Direction | 5% |

判定：`>=90 PASS` / `75-89 GOOD` / `60-74 REVISION` / `<60 REBUILD`
