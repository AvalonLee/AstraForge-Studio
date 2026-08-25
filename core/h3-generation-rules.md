# H3 Generation Rules

## Core Principle

H3 不是动画制作软件。需要：简单动作、明确镜头、单一视觉重点。

---

## Shot Complexity Rule

每个镜头最多：

```
1 个角色主体 + 1 个主要动作 + 1 个镜头运动 + 1 个主要特效
```

推荐结构：

```
Shot / Duration / Character / Action / Camera / Effect
```

### Good Example

> 角色走向镜头，镜头缓慢推进，背景出现 UI。

### Bad Example

> 角色奔跑、拔剑、释放魔法、城市爆炸、天气变化、镜头 360 度旋转。

---

## Camera Rules

**Recommended**：push in / pull out / pan / zoom / 2.5D parallax

**High Risk**：360 orbit / complex tracking / realistic camera movement

---

## Motion Priority

| 级别 | 内容 |
|---|---|
| A 级 | look camera / smile / turn / hair movement / hand gesture |
| B 级 | weapon draw / power release |
| C 级 | group battle / destruction / physics simulation |

默认使用 A 级 + B 级组合。

---

## Animation Style Rule

默认：Pure 2D anime animation

推荐：cel shading / hard shadow / graphic motion / 2.5D movement / 12fps 有限动画

禁止：realistic photography / PBR material / 3D character rendering / live action camera /
现代运动模糊

---

## Prompt Base 结构

Base 模式必须包含：

```
composition / subjects / environment / actions / camera / sound
```

---

## Negative Prompt 建议

```
realistic, 3D CGI, live action, PBR material,
character drift, extra weapons, different hairstyle, different outfit
```
