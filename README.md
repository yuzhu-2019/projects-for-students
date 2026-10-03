# 智能 Agent 开发

这是一个 [mdBook](https://rust-lang.github.io/mdBook/) 站点，框架与 [清华操作系统课 2026](https://oscourse-cn.github.io/Tsinghua-oscourse-OsTrain-2026/index.html) 相同：左侧目录、站内搜索、主题切换、前后翻页。推送到 GitHub 后，由 Actions 发布到 GitHub Pages。

页面正文在 `src/`。侧边目录在 `src/SUMMARY.md`。总体目标在站点根上，某一学期的安排、资料、成果和通知放在该学期目录里，例如 `src/2026fall/`。

## 本地预览

课程站和 GitHub Actions 使用 mdBook 0.5.4。本机若是 Ubuntu 20.04（glibc 2.31），0.5.4 的官方二进制无法运行，可改用 0.4.21 做本地预览，页面框架相同。在本目录执行：

```bash
mdbook serve --open
```

浏览器打开后，改 Markdown 会自动刷新。只生成页面、不启动服务时执行 `mdbook build`，结果在 `public/`。

## 发布到 GitHub Pages

1. 把本目录推到 [yuzhu-2019/projects-for-students](https://github.com/yuzhu-2019/projects-for-students) 的 `main` 分支。
2. 打开仓库 Settings → Pages，Source 选 **GitHub Actions**。
3. 之后每次推送，`.github/workflows/mdbook.yml` 会构建并发布。
4. 站点地址：`https://yuzhu-2019.github.io/projects-for-students/`

源码备份同时在 [Gitee y-zhu/projects-for-students](https://gitee.com/y-zhu/projects-for-students)。Gitee 个人仓库没有 Pages，网站只在 GitHub 上发布。

新增栏目：在 `src/` 增加一个 `.md`，再在 `src/SUMMARY.md` 加一行链接。
