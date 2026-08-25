# Premium Character PV Rules

米哈游式高级手游 PV 的商业规则层。

---

## Rule 01 — 角色永远第一视觉主体

```yaml
character: 70%
effect: 20%
environment: 10%
```

---

## Rule 02 — 技能展示不是战斗展示

错误：

```
连续战斗 / 多人混战 / 大爆炸
```

正确：

```
角色 → 技能准备 → 标志动作 → 英雄定格
```

---

## Rule 03 — 每个角色必须有三个记忆点

```yaml
memory_points:
  - face
  - signature_item
  - signature_pose
```

---

## Rule 04 — 五星角色增加 Rarity Layer

```yaml
rarity:
  - light_effect
  - premium_ui
  - title_animation
  - special_transition
```

---

## Rule 05 — 商业目标优先于视觉复杂度

```
Character Identity > Commercial Goal > Visual Effect > Complex Action
```

---

## Rule 06 — 避免站桩

角色每次出现都应改变镜头高度、方向、身体姿态和手势。

---

## Rule 07 — 类型专项限制

```yaml
sweet_character_motion_limit:
  per_shot:
    max: 1 charm_action + 1 expression_change

y2k_balance_rule:
  character_priority: 70%
  graphic_element: 30%
```
