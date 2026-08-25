# Director Task Orchestrator

所有请求先进入 Task Orchestrator。Router 只负责任务入口，不负责具体生成。

```
User Input
    ↓
Task Understanding
    ↓
Task Classification
    ↓
Workflow Selection
    ↓
Module Loading
    ↓
Execution
    ↓
Quality Check
    ↓
Final Output
```

---

## Supported Tasks

| Task | 用途 | 调用 |
|---|---|---|
| TASK_CREATE_PV | 从零制作角色 PV | `create-pv` |
| TASK_OPTIMIZE | 优化已有 Prompt | `optimize-prompt` |
| TASK_CONVERT_H3 | 普通描述转 H3 结构 | `convert-h3` |
| TASK_ANALYZE_REFERENCE | 拆解优秀 PV | `analyze-reference` |
| TASK_CHARACTER_PROFILE | 角色设计分析 | `analyze-character` |

---

## Task Classifier

| Task | 关键词 |
|---|---|
| CREATE_PV | 做 PV / 角色宣传 / 动漫短片 / 新角色 |
| OPTIMIZE | 优化 / 改进 / 提升效果 / 跑不好 |
| CONVERT_H3 | H3 / 转换格式 / 视频 Prompt |
| ANALYZE_REFERENCE | 分析这个 PV / 拆解 / 学习风格 |
| CHARACTER_PROFILE | 设计角色 / 角色设定 / 人设 |

输出：

```yaml
task: CREATE_PV
confidence: 0.92
```

---

## Execution Rule

不要直接生成。必须：

```
理解任务 → 选择路径 → 加载必要能力
```

---

## 混合任务优先级

```
1. Analyze Reference
2. Character Analysis
3. Create PV
4. Optimize
5. Convert H3
```

原因：前置理解影响后续质量。任务应拆分串行，不要合并。

例："分析这个 PV，然后帮我做类似角色 PV"
→ Task1: Analyze Reference → Task2: Create PV

---

## Execution Planner

### CREATE_PV

```
1. Character Analyzer
2. Character DNA Lock
3. PV Template Selector
4. Reference Retrieval
5. Component Selection
6. Shot Planner
7. H3 Conversion
8. Quality Check
```

### OPTIMIZE_PROMPT

```
1. Prompt Audit
2. Detect Risk
3. Rewrite Structure
4. H3 Check
5. Quality Score
```

### CONVERT_H3

```
1. Parse Scene
2. Extract Character
3. Define Action
4. Add Camera
5. Add Style
6. Generate H3 Format
```

### ANALYZE_REFERENCE

```
1. Visual Analysis
2. Camera Extraction
3. Transition Extraction
4. Style Extraction
5. Reusable Components
```
