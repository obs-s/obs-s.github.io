---
title: "如何发布新文章"
date: 2026-08-20
draft: false
tags: ["Hugo", "写作"]
categories: ["网站"]
summary: "用 Markdown 在几分钟内发布一篇文章。"
---

在 `content/posts/` 中新建一个 Markdown 文件，例如：

```markdown
---
title: "文章标题"
date: 2026-08-20
tags: ["标签"]
draft: false
---

正文从这里开始。
```

提交并推送到 `main` 分支后，GitHub Actions 会自动构建并发布网站。
