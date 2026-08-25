# Session Protocol (SESSION_SPEC)

## 核心原则

AstraForge Studio 采用**交互式生产流程**，不假设用户意图。
每步需要用户确认后才进入下一步。

---

## Step0 — 时长与比例锚定（全局锚定）

每次新会话**必须首先确认**两个参数，记为 `SESSION_SPEC`：

```yaml
SESSION_SPEC:
  duration: 15s            # 5s / 10s / 15s / 30s / custom
  aspect_ratio: "16:9"     # 16:9 / 9:16 / 1:1 / custom
```

后续所有步骤直接引用此值，不再重复确认。

用户未指定时给出可选示例：

| 参数 | 建议 |
|---|---|
| 时长 | 5s（短广告）/ 15s（标准角色PV）/ 30s（剧情PV） |
| 比例 | 16:9（横版推荐）/ 9:16（竖版短视频） |

---

## 信息充分性校验

**任何时候用户输入过少，必须先完善再继续，绝不直接产出脏结果。**

| 场景 | 处理 |
|---|---|
| Step0 时长/比例未指定 | 给出可选示例，引导选择 |
| Step1 角色描述过简 | 补全设定维度（发型/瞳色/服装/气质），附优化方向 |
| Step2 画面诉求模糊 | 先给运镜、构图、光影、节奏优化方向供选择 |

---

## Generation Gate — 生成闸门

**所有图片/视频生成必须经用户显式二次确认。**
本系统全程仅产出 Prompt 与参数，不调用任何生成能力。

---

## 输出语言

- 重写/技术章节：**英文**
- 对话、歌词、可见场景文本：保留原始语言
- 与用户的交流：始终用中文

---

## 文件按需加载（避免上下文污染）

| 阶段 | 加载文件 |
|---|---|
| 入口 | SKILL.md |
| Step0 | core/session-spec.md |
| Step1 角色设定 | core/character-dna/ + director/character-card-template.md |
| Step1 风格标签 | library/style/persona-tags.md |
| Step2 生成 Prompt 前 | core/prompt-structure.md（必读） |
| Step2 主题模板 | library/genre/ 对应文件 |
| Step2 分镜脚本 | director/storyboard-4shot.md |
| Step3 H3 转换 | schema/h3-base.md 或 schema/h3-ref2va.md |
| Step3 质量检查 | core/quality-engine/ |
