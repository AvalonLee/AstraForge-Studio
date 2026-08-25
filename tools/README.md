# Tools

项目自动化校验脚本，由 `.github/workflows/validate.yml` 在 push / PR 时执行。

## validate_yaml.py

```bash
pip install pyyaml
python tools/validate_yaml.py
```

校验内容：

1. 所有 `*.yaml` / `*.yml` 可正常解析
2. 顶层 `components:` 列表中每个条目声明 `id` 与 `risk`
3. Shot 级组件库（camera / action / expression / transition）额外声明
   `stability_score` 与 `impact_score`
4. 组件 `id` 全局唯一

> Theme 与 Style 属于组合层而非 Shot 级组件，不要求评分字段。

## check_naming.py

```bash
python tools/check_naming.py
```

防止历史项目名 `AnimePV-H3` 回流。`CHANGELOG.md` 与 `docs/DEVELOPER_GUIDE.md`
因需记录更名历史而在允许清单中。

## check_version.py

```bash
python tools/check_version.py
```

以 `skill/manifest.yaml` 的 `version` 为准，校验版本号与中文品牌名在
4 个声明处一致：skill manifest、release manifest、`SKILL.md` 头部、`README.md` 徽章。
同时校验 `git_tag` 与版本号匹配。

## validate_templates.py

```bash
python tools/validate_templates.py
```

校验 `templates/genre-*.md`（单角色）与 `templates/cast-*.md`（多角色）是否达到可生产状态：

1. 存在 `完整可替换模板` 代码块
2. 10 段结构齐全
3. **每个时间分段都有 `机位：` 标注**（原始 skill 三个模板的末段均遗漏）
4. 时间轴连续无缝隙，覆盖完整时长
5. 相邻镜头不复用同一机位
6. 占位符为 `<...>` 形式，可机械替换

## validate_benchmarks.py

```bash
python tools/validate_benchmarks.py
```

校验 `benchmark/test-cases/*.yaml` 与组件库的一致性：

1. 必填字段齐全（`input` / `expected_routing` / `scores` 等）
2. 引用的 genre / variation / template 存在
3. 引用的组件 **slug** 在 `library/` 中存在
4. 声明的风险预算不超过「min(genre 上限, 时长上限) + uplift」
5. 六维评分之和等于 `final_score`
6. 覆盖度断言：三个 Genre 必须各有用例

> 组件引用一律使用显式 `slug` 字段，而非从 `id` 反推。
> 因为 id 分段不可逆（`camera.hero.low_angle.v1` 在全项目被引用为 `hero-low-angle`）。

## check_links.py

```bash
python tools/check_links.py
```

校验所有 Markdown 相对链接指向真实存在的文件。跳过外链、锚点与 mailto。