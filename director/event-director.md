# Event Director

活动 PV 导演器（周年 / 联动 / 季节）。

> **与角色 PV 的根本差异**：角色 PV 卖「认识一个新角色」，
> 活动 PV 卖「参与一个限时事件」。
> 前者的成功标准是**记住角色**，后者是**产生行动**（回流 / 参与 / 付费）。

---

## 三条硬性差异

### 1. 必须有 CTA（Call To Action）

角色 PV 可以只留标题。活动 PV 结尾**必须**包含：

```
活动名称 + 时间信息（限时标识 / 开启日期）
```

缺少时间信息的活动 PV 是无效的商业素材。

### 2. 情绪曲线不同

| 类型 | 曲线 |
|---|---|
| 角色 PV | 好奇 → 认识 → 想要 |
| 周年 PV | 回顾 → 感谢 → 展望 |
| 联动 PV | 意外 → 融合 → 期待 |
| 季节 PV | 氛围 → 惊喜 → 号召 |

### 3. 季节 PV 是唯一允许弱化角色开场的类型

`core/commercial-pv-principles.md` 的 Rule 01 要求角色占 70%。
季节 PV 的开场（0-3s）可用环境建立节日氛围，此处角色占比可降至 30%，
但**全片平均仍须回到 70%**。这是明确的受控例外，不是放宽规则。

---

## 15s 周年 PV 结构

```
0-2s     MILESTONE     里程碑数字 / 周年标识
2-5s     LEAD          主打角色单人
5-9s     ROTATION      阵容轮换（老角色回归感）
9-12s    ENSEMBLE      全阵容列队同框
12-15s   CTA           周年标题 + 活动时间
```

阵容规模建议 3 人。`ENSEMBLE` 段必须使用 `action_level 1` 组件。

## 15s 联动 PV 结构

```
0-2s     COLLISION     双方视觉符号碰撞
2-5s     SIDE A        本作角色
5-8s     SIDE B        联动方角色
8-12s    CROSSOVER     跨阵营同框（关系是卖点）
12-15s   CTA           联动标题 + 限时标识
```

## 15s 季节 PV 结构

```
0-3s     ATMOSPHERE    季节环境（允许角色占比 30%）
3-7s     COSTUME       限定造型展示
7-11s    INTERACTION   角色互动 / 节日动作
11-15s   CTA           活动标题 + 限时标识
```

---

## 30s 周年 PV

```
0-6s     里程碑 + 世界回顾
6-14s    阵容轮换（4-6 人，靠出场顺序而非同框）
14-21s   高光集锦（快切）
21-27s   全阵容列队
27-30s   CTA
```

> 4 人以上**禁止同框**，须靠出场顺序建立群体感。见 `cast-risk-rules.yaml`。

---

## 活动 PV 的风险特征

活动 PV 天然比角色 PV 风险高，原因：阵容规模大 + 需要同框。

| 类型 | 建议阵容 | 稳定性上限 | 主要风险 |
|---|---|---|---|
| 季节 | 2 | 32 | 限定造型与原 DNA 的冲突 |
| 联动 | 2 | 32 | 跨风格视觉不统一 |
| 周年 | 3 | 28 | 身份串味、阵容色彩打架 |

### 限定造型与 DNA Lock

季节/联动限定造型本质是换装，与 DNA Lock 的 `costume_change: critical` 冲突。
处理方式同 `transformation_exception`：

```yaml
costume_variant_exception:
  must_remain_identical: [face, hair_color, eye_color, signature_asset]
  may_change: [costume_form, accessory_theme]
  constraint: 造型变化须全片一致，不得在片中切换回原造型
```

---

## IP 安全边界（联动 PV 专属）

本系统**仅产出原创设计描述**。联动 PV 中：

- ❌ 不得在 Prompt 中描述现有 IP 的具体角色外观
- ❌ 不得生成他方 IP 的 Logo / 标识
- ✅ 可描述「跨作品碰撞」的构图与氛围
- ✅ 对方角色素材须由用户自行提供并确保已获授权

---

## 自检

1. 结尾是否有活动名称 **与时间信息**？
2. 情绪曲线是否匹配活动类型（而非套用角色 PV 的「好奇→想要」）？
3. 阵容是否满足 contrast_requirement（任意两人 2 维强对比）？
4. 同框段落是否只用了 `action_level 1` 组件？
5. 限定造型是否保持了 face / hair_color / eye_color / signature_asset？
