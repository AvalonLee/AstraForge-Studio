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
