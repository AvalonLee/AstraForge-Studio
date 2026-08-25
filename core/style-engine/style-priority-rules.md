# Style Priority Rules

当多个 Style 竞争时，优先级为：

```
角色商业定位 > Theme > Premium Layer > Base Style > Special Style
```

---

## 系统不做平均融合

例：角色为甜酷少女，输入 `Y2K + Dark + Cyber`。

系统不会平均融合，而是：

```yaml
primary: y2k-graphic
secondary: modern-cel
remove: dark-cinematic-cel
```

---

## Style Validation Gate

Composer 调用前必须通过验证：

```
Theme Engine → Style Stack → Conflict Detection → Resolve → Composer
```

---

## Style Stack 结构

```yaml
style_stack:
  base_style:      # 负责动画表现
  premium_layer:   # 负责商业质感
  special_layer:   # 负责角色个性
```

## 自动组合规则

```yaml
style_composition:
  default_base: modern-cel
  commercial_upgrade:
    character_release:    add mobile-game-premium
    legendary_character:  add cinematic-lighting
    dark_character:       add dark-cinematic-cel
    fashion_character:    add y2k-graphic
```

---

## Style Lock

生成过程中允许 camera change / pose change，
禁止 style change（例：开始 2D cel anime，禁止中途变 realistic 3D CGI）。

---

## 商业风格优先级

```
Character clarity > Visual impact > Background complexity
```
