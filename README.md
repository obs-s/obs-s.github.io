# Johnny Son 的个人网站

基于 [Hugo](https://gohugo.io/) 与 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 构建，部署到 GitHub Pages。

## 写文章

在 `content/posts/` 添加 Markdown 文件，推送到 `main` 分支即可自动发布。

本地预览：

```bash
git submodule update --init --recursive
hugo server -D
```

首次发布前，请在 GitHub 仓库的 **Settings → Pages → Build and deployment** 中选择 **GitHub Actions**。
