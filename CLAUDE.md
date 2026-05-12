Skills 按分类文件夹组织在 `skills/` 目录下：

- `engineering/` — 日常编码工作
- `productivity/` — 日常非编码工作流工具
- `misc/` — 保留但很少使用
- `personal/` — 与我个人设置相关，不做推广
- `in-progress/` — 尚未准备好发布的草稿
- `deprecated/` — 不再使用

每个 `engineering/`、`productivity/` 或 `misc/` 中的 skill 必须在顶层 `README.md` 中有引用，并在 `.claude-plugin/plugin.json` 中有条目。`personal/`、`in-progress/` 和 `deprecated/` 中的 skill 不能出现在这两者中。

顶层 `README.md` 中的每个 skill 条目必须将 skill 名称链接到其 `SKILL.md`。

每个分类文件夹都有一个 `README.md`，列出该分类中的每个 skill 及其单行描述，skill 名称链接到其 `SKILL.md`。