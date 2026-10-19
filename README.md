# 刘垭畅 · Yachang Liu

基于 PRISM 的响应式学术主页，支持中文 / English、浅色 / 深色主题。当前已按本人最近提供的项目与竞赛信息整理，已补齐中英文姓名、公开邮箱和 GitHub；暂不使用真人头像，奖项年份和完整名称仍待补充。

## 日常维护

```sh
npm ci
npm run dev
```

在终端显示的本地地址预览。修改内容后会自动刷新；按 Ctrl+C 停止。

| 要改的内容 | 中文文件 | 英文文件 |
| --- | --- | --- |
| 姓名、简介、邮箱、GitHub、导航 | `content_zh/config.toml` | `content/config.toml` |
| 首页自我介绍 | `content_zh/bio.md` | `content/bio.md` |
| 首页项目摘要 | `content_zh/research.md` | `content/research.md` |
| 首页竞赛摘要 | `content_zh/highlights.md` | `content/highlights.md` |
| 首页区块顺序、研究兴趣 | `content_zh/about.toml` | `content/about.toml` |
| 项目详情 | `content_zh/projects.toml` | `content/projects.toml` |
| 获奖记录 | `content_zh/awards.toml` | `content/awards.toml` |
| 近期动态 | `content_zh/news.toml` | `content/news.toml` |
| 在线简历 | `content_zh/cv.md` | `content/cv.md` |

两种语言分别维护：更新一份不会自动翻译另一份。中文为默认语言，浏览器会记住手动选择。

### 补齐个人身份

在两份 `config.toml` 中分别修改 `[site]` 的 `title`、`description` 和 `[author]` 的 `name`、`title`、`institution`。

头像放入 `public/avatar.jpg`，然后把两份配置中的 `avatar` 改为 `/avatar.jpg`。目前使用抽象机器人图标，没有使用参考站人物照片。

在 `[social]` 下按需添加：

```toml
email = "你的公开邮箱"
github = "https://github.com/你的账号"
```

未配置的联系方式会自动隐藏。不要把学号、成绩单、身份证、私人电话或密钥放进 `public/`。

### 新增项目或奖项

在对应 TOML 文件末尾增加一个条目；`date` 不确定时直接省略。

```toml
[[items]]
title = "项目名称"
subtitle = "个人贡献或项目状态"
date = "2026"
content = "说明做了什么、你的贡献和已经验证的结果。支持 **加粗** 和 [链接](https://example.org)。"
tags = ["具身智能", "机器人"]
```

奖项条目也使用 `[[items]]`。不要把参赛计划或预期奖牌写成获奖。项目描述、首页摘要与简历要一起同步。

### 新增动态

在 `news.toml` 顶部添加：

```toml
[[news]]
date = "2026-10"
content = "具体进展，使用已经发生并可确认的事实。"
```

同时更新两份 `config.toml` 中的 `last_updated`。

### 论文

当前没有确认的论文，已移除论文导航并清空原站论文。将来有正式论文时：

1. 把 BibTeX 写入 `content/publications.bib`（中文可共用，或维护 `content_zh/publications.bib`）。
2. 在两份配置中添加指向 `/publications`、target 为 `publications` 的导航。
3. 如需首页代表作，在 `about.toml` 添加 `publications` 区块。

## 验证与上线

```sh
npm run build
npm run preview
```

构建会进行类型与编译检查，结果输出到 `out/`。打开预览后检查首页、项目、荣誉、简历、语言切换与深色模式。

## GitHub Pages 发布

正式网址：https://yatechance.github.io/

源码仓库：https://github.com/YateChance/YateChance.github.io

当前本地维护目录：`/Users/wens/Work/YateChance.github.io`。

内容更新并通过本地构建后运行：

```sh
git add content content_zh public
git commit -m "Update homepage content"
git push origin main
```

推送到 `main` 后，GitHub Actions 会自动安装依赖、构建并发布。通常需要几分钟；在仓库的 Actions 页面查看 `Deploy personal homepage` 的状态。成功后刷新正式网址。

也可以直接在 GitHub 网页编辑对应文件并提交到 `main`，同样会触发自动发布。不要把私人材料、密码或 API 密钥提交到仓库；该仓库和网站均公开。

原 ChatGPT Sites 链接作为旧版本保留，不会随 GitHub 推送自动更新。以后请优先维护本仓库。

## 样式与组件

- `src/app/globals.css`：颜色、字体、排版。
- `src/components/`：导航、主页、项目卡片与主题切换。
- `public/`：部署后可直接访问的头像、字体和下载文件。

维护文字通常只需要修改 `content/` 和 `content_zh/`，无需修改组件代码。

## 来源与授权

视觉结构基于 https://github.com/wayaairon/wayaairon.github.io 的 PRISM 实现，遵循 MIT License 并保留 `LICENSE` 和页脚署名。原作者照片、简历 PDF、二维码、论文和个人经历已移除。公开内容来自本人确认的个人资料。
