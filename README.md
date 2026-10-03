# 智能 Agent 开发

这是一个 [mdBook](https://rust-lang.github.io/mdBook/) 站点，框架与 [清华操作系统课 2026](https://oscourse-cn.github.io/Tsinghua-oscourse-OsTrain-2026/index.html) 相同：左侧目录、站内搜索、主题切换、前后翻页。推送到 Gitee 后，由 [Gitee Pages](https://gitee.com/help/articles/4136) 发布网站。

页面正文在 `src/`。侧边目录在 `src/SUMMARY.md`。编好的网页在 `public/`。总体目标在站点根上，某一学期的安排、资料、成果和通知放在该学期目录里，例如 `src/2026fall/`。

## 本地预览

本机若是 Ubuntu 20.04（glibc 2.31），可用 mdBook 0.4.21 预览。在本目录执行：

```bash
mdbook serve --open
```

浏览器打开后，改 Markdown 会自动刷新。只生成页面、不启动服务时执行 `mdbook build`，结果在 `public/`。发布前请先构建，再提交 `public/`。

## 发布到 Gitee Pages

1. 在 [Gitee](https://gitee.com) 注册并完成实名认证（Pages 需要实名）。
2. 新建公开仓库，仓库名与 `book.toml` 里的 `site-url` 一致，例如 `projects-for-students`。不要勾选自动添加 README。
3. 把本目录推到该仓库的 `main` 分支。
4. 打开仓库 **服务 → Gitee Pages**：部署分支选 `main`，部署目录填 `public`，勾选强制 HTTPS 后启动。
5. 之后改了 `src/`，先执行 `mdbook build`，再提交并推送。Gitee Pages 有时要再点一次 **更新**。

站点地址：

`https://用户名.gitee.io/仓库名/`

当前按 `yuzhu-2019/projects-for-students` 配置，地址为 `https://yuzhu-2019.gitee.io/projects-for-students/`。若 Gitee 用户名不同，改 `book.toml` 里的三个地址后再构建。

新增栏目：在 `src/` 增加一个 `.md`，再在 `src/SUMMARY.md` 加一行链接。
