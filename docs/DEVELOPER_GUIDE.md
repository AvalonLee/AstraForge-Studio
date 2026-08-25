# Developer Guide

**AstraForge Studio v1.0.0**

---

## Project Philosophy

AstraForge Studio 被设计为一个模块化的 AI 导演框架（modular AI directing framework）。

每一项能力都应该是：

- reusable（可复用）
- testable（可测试）
- configurable（可配置）

---

## 目录规范

| 目录 | 职责 |
|---|---|
| `core/` | 核心规则 |
| `director/` | 导演逻辑 |
| `library/` | 视觉组件 |
| `templates/` | 商业模板 |
| `benchmark/` | 测试系统 |
| `schema/` | 数据协议 |
| `workflow/` | 任务调度 |
| `references/` | 案例库 |

---

## 新增组件流程

以新增一个 Camera 组件为例：

1. 创建文件 `library/camera/new-camera.yaml`
2. 填写 Schema：`metadata` / `parameters` / `prompt` / `composer` / `quality`
3. 加入 `compatibility` 规则
4. 加入 Benchmark 测试

---

## YAML 组件规范

每个组件必须包含：

```yaml
component:
  id:
  metadata:
  usage:
  parameters:
  prompt:
  composer:
  quality:
```

组件评分字段必填：

```yaml
stability_score:
impact_score:
```

### 组件示例

```yaml
id: camera.eye.reveal.v1
name: Eye Reveal Shot
category: camera
purpose: instant character recognition
focus:
  - eye design
  - emotion
shot: macro close-up
movement: slow reveal from shadow
prompt_block: >
  anime female character eye reveal,
  sharp detailed eyes,
  dramatic lighting,
  slow cinematic reveal
best_for:
  - cool female
  - mysterious female
risk: low
```

---

## 开发原则

### 1. 不直接修改核心规则

新增能力优先通过「增加模块」实现，而非改动既有核心规则。

### 2. 所有组件必须可评分

必须包含 `stability_score` 与 `impact_score`。

### 3. 所有重大更新必须通过 Benchmark

```
Modify → Benchmark → Quality Check → Release
```

---

## GitHub 开发流程

> ⚠️ **红线：禁止直接推送到 `main`。** 所有推送先进 `dev`，再通过 PR 合入 `main`。
> 详见 [BRANCH_POLICY.md](BRANCH_POLICY.md)。

| 分支 | 用途 | 可否直接推送 |
|---|---|---|
| `main` | 稳定版本 | ❌ 仅通过 PR |
| `dev` | 集成开发分支，日常推送目标 | ✅ |
| `feature/*` | 功能分支 | ✅ |
| `hotfix/*` | 紧急修复 | ✅ |

克隆后需启用本地推送守卫：

```bash
git config core.hooksPath .githooks
```

发布流程：

```
Development
    ↓
Feature Branch
    ↓
Pull Request
    ↓
GitHub Actions
  ├── YAML Check
  ├── Documentation Check
  └── Benchmark
    ↓
Release Candidate
    ↓
Tag v1.0.0
    ↓
GitHub Release
    ↓
Archive Package
```

---

## 版本规范

| Tag | 含义 |
|---|---|
| `v1.0.0` | Initial Production Release |
| `v1.1.0` | 新增组件 |
| `v1.2.0` | 新增 PV 模板 |
| `v2.0.0` | 重大架构升级 |

---

## Benchmark 编写规范

每个 Benchmark 用例需覆盖完整链路：

```
Task Orchestrator → Character Analyzer → Reference Retrieval
→ Theme Selector → Component Selector → Shot Planner
→ H3 Risk Check → Quality Check
```

每一步单独打分，最终汇总为 100 分制评分，并记录发现的问题（Issue）与对应新增规则。

---

## 命名迁移历史

项目前身为 `AnimePV-H3`，v1.0.0 起统一迁移：

| 旧名称 | 新名称 |
|---|---|
| AnimePV-H3 Skill | AstraForge Studio |
| animepv-h3 | astraforge-studio |
| H3 规则层 | H3 Prompt Engine |
| Composer | Director Composer |
| Library | Visual Component Library |
| Benchmark | AstraForge Benchmark Suite |
| Output Schema | Production Schema |

发布前由 CI 自动校验，也可本地执行：

```bash
pip install pyyaml
python tools/validate_yaml.py   # YAML 解析 + 组件字段 + id 唯一性
python tools/check_naming.py    # 历史名称回流检查
```

详见 [tools/README.md](../tools/README.md)。
