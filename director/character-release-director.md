# Character Release Director

15 秒角色上线 PV 自动导演器。

Input: Character Profile
Output: 5 Shot Commercial Structure

---

## 固定节奏

```
0-3s    HOOK
3-6s    IDENTITY
6-10s   PERSONALITY
10-13s  SIGNATURE
13-15s  TITLE
```

---

## Shot 01 — Hook

目标：让玩家第一眼记住角色。

| Archetype | Camera | Expression | Action |
|---|---|---|---|
| cool_female | eye-reveal | cool-gaze | head-turn |
| sweet_female | hand-to-camera | playful-wink | hand-gesture |
| fantasy | eye-reveal | elegant-smile | — |
| cyber_female | detail-macro | confident-smirk | hand-gesture |

---

## Shot 02 — Identity

固定调用 `beauty-showcase`。

原因：角色 PV 第一商业目标不是剧情，是**角色识别**。

展示顺序：

```
Face → Hair → Outfit → Signature Item
```

---

## Shot 03 — Personality

| Archetype | Expression | Action |
|---|---|---|
| cool | confident-smirk | weapon-reveal |
| sweet | sweet-smile | hair-flip |
| elegant | elegant-smile | gesture |

---

## Shot 04 — Signature

必须体现角色独有卖点：

```yaml
combat: weapon-reveal
magic: ability-release
fashion: signature-pose
```

规则：不超过 1 角色 / 1 技能 / 1 特效。

---

## Shot 05 — Ending

所有角色固定：

```yaml
camera: hero-low-angle
action: signature-pose
transition: title-reveal
```

---

## 验收标准

- ✓ 第一秒出现角色
- ✓ 15 秒完成角色介绍
- ✓ 有能力展示
- ✓ 有最终记忆画面
- ✓ 角色 DNA 未变化
