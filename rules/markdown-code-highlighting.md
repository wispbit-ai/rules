---
include: "*.md"
title: Use code highlighting in Markdown
tags: markdown
---

Specify the appropriate language for code blocks to enable proper syntax highlighting. For CLI commands use `bash`, and for Python code use `py` or `python`.

Bad:

```markdown
transformers chat Qwen/Model-Name --torch_dtype auto
```

Good:

````markdown
```bash
transformers chat Qwen/Model-Name --torch_dtype auto
```
````

```

```
