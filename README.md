# obs-s.github.io

`obs-s` 的纯博客网站，基于 Hugo + PaperMod，由 Johnny-son.github.io 移植。

- 网站地址：https://obs-s.github.io/
- GitHub：https://github.com/obs-s
- 邮箱：qx1289@gmail.com
- Hugo Extended：0.165.0（与 GitHub Actions 一致）

## 本地预览

```bash
git clone --recurse-submodules git@github-obs-s:obs-s/obs-s.github.io.git
cd obs-s.github.io
hugo server --bind 127.0.0.1 --port 1313 --baseURL http://127.0.0.1:1313/
```

浏览器打开 http://127.0.0.1:1313/ 。如已克隆仓库，运行 `git submodule update --init --recursive` 获取主题。

生产构建：

```bash
hugo --minify
```

## 内容与站点配置

- `hugo.yaml`：站点名称、地址、Posts 栏目头像和评论配置。
- `config/development/server.yaml`：本地预览禁用页面缓存，避免首页显示旧版。
- `content/_index.md`：首页直接展示 Posts；旧 `/archives/` 和 `/posts/` 列表地址跳转到首页。
- `layouts/archives.html`：右侧使用 PaperMod 原有年份 → 月份归档样式，显示文章标题、日期及文章 front matter 中的 summary；未填写 summary 时仅显示日期。
- `layouts/baseof.html`：双栏布局，覆盖文章页及归档页。
- `layouts/_partials/blog_sidebar.html`：左侧头像、年份归档及 RSS 订阅。
- `assets/css/extended/blog.css`：浅色双栏样式及深色/手机适配；窄屏时头像栏移至文章列表上方。
- `content/posts/`：文章。目前仅保留「学生思维与硕博阶段」，旧站迁移的三篇文章已删除。
- `themes/PaperMod`：Git 子模块，固定为原站主题版本。

顶部移除 Posts 导航；全站只有首页一个文章列表入口，文章仍可单独阅读。

## GitHub Pages

部署工作流保留在 `.github/workflows/deploy.yml`。仓库已公开，Settings → Pages 的 Source 已设为 GitHub Actions；推送到 `main` 后会自动构建和部署。

发布文章：在 `content/posts/` 新建 Markdown 文件，填写 `title`、`date`、`draft: false` 和可选的 `summary`，正文放在 front matter 下方。本地预览确认后，提交并推送：

```bash
git add content/posts/
git commit -m "Publish new post"
git push origin main
```

部署进度可在仓库 Actions 页面查看。

## 评论

文章页已启用 Giscus 中文评论区，并跟随网站切换浅色/深色主题。访客登录 GitHub 后即可评论或回应。

评论存放在 `obs-s/obs-s.github.io` 仓库 Discussions 的 Announcements 分类，按文章 URL 路径匹配；首次评论或回应后自动创建对应讨论。文章发布后尽量保持路径不变，以免评论分散到新讨论。

`hugo.yaml` 中的 `params.comments` 控制全站评论开关；单篇文章可在 front matter 中添加 `comments: false` 关闭评论。Giscus App 仅授权访问此博客仓库。
