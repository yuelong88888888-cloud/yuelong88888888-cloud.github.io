# Yuelong Zhang — 个人科研网站

这是 Yuelong Zhang 的个人科研网站，主要展示仿生机器人、柔顺机构、双足运动与机器人学习相关研究。

目标公开地址：[https://yuelong88888888-cloud.github.io](https://yuelong88888888-cloud.github.io)

网站采用轻量的 GitHub Pages + Jekyll 架构，使用 Liquid、HTML、CSS、Markdown 与 YAML，不依赖 JavaScript 框架、CMS 或数据库。网站正文以英文为主；本 README 用中文记录本地开发、内容维护与公开范围。

## 导航与当前公开范围

| 导航项 | 路径 | 说明 |
| --- | --- | --- |
| about | `/` | 首页即 About，不另建 `/about/` 页面 |
| publications | `/publications/` | 内容来自 `_data/publications.yml` |
| projects | `/projects/` | 显示 Jekyll `projects` collection 中公开的项目 |
| CV | `/files/CV.pdf` | 使用稳定 PDF 路径，并在新标签页打开 |

当前版本只公开一个正式项目：**STERS**。

BioArm 暂不公开，目前没有页面、卡片或 publication 条目；后续资料确认适合公开后再加入。

Email 与 LinkedIn 在 `_config.yml` 中集中配置，两个地址均已根据当前确认信息填写。

## STERS 项目页

项目地址：`/projects/sters/`

页面按以下科研叙事组织：

1. Overview
2. Energy Recirculation Across the Stance Phase
3. Dynamics and Stiffness Optimization
4. Contact-Aware Locomotion
5. Reinforcement Learning and Control
6. Experimental Model Validation
7. Real-World Locomotion
8. Disturbance Recovery
9. Walking Performance and Energy Efficiency
10. Project Overview Video
11. Publication / BibTeX

`files/sters-paper.pdf` 保留为本地科研来源文件，但当前版本标记为 under review，不作为公开下载文件输出到网站。只有确认存在适合公开的 clean manuscript 后，才可在 `_projects/sters.md` 或 `_data/publications.yml` 中加入 `paper` 字段。

## 核心源码目录

```text
<仓库根目录>/
├── .gitignore
├── _config.yml
├── Gemfile
├── README.md
├── index.html
├── _data/
│   ├── news.yml
│   └── publications.yml
├── _includes/
│   ├── footer.html
│   └── header.html
├── _layouts/
│   ├── default.html
│   └── project.html
├── _projects/
│   └── sters.md
├── assets/
│   ├── css/
│   │   └── style.css
│   ├── images/
│   │   ├── profile/
│   │   ├── projects/
│   │   │   └── sters/
│   │   └── source/              # 保留的原始图片素材
│   └── videos/
│       ├── source/              # 保留的原始/HEVC 视频素材
│       └── sters/               # 面向浏览器的 STERS 视频
├── files/
│   ├── CV.pdf                    # 稳定公开 CV 路径
│   ├── Zyl.pdf                   # 保留的原始 CV
│   └── sters-paper.pdf           # 保留的 under-review 稿件
├── projects/
│   └── index.html
└── publications/
    └── index.html
```

`_site/`、`.jekyll-cache/`、`.bundle/` 与 `vendor/` 是本地构建或依赖目录，不属于站点源码，已由 `.gitignore` 排除。

本地还可能生成 `Gemfile.lock`，它目前同样被 `.gitignore` 忽略。如果以后决定锁定并提交依赖版本，应同时调整 `.gitignore` 与本节说明。

`_config.yml` 还会把原始素材目录以及不公开的 PDF 排除在生成的 `_site` 之外。

## macOS 本地开发

需要先安装：

- Ruby
- Bundler
- Jekyll（通过 Bundler 安装）

在仓库根目录运行：

```bash
bundle install
bundle exec jekyll serve
```

然后访问：[http://localhost:4000](http://localhost:4000)

当前 `Gemfile` 使用 Jekyll 4；页面模板仅使用 Jekyll/Liquid 核心能力，以保持结构简单。正式发布后仍应检查 GitHub Pages 的构建结果。

如只需生成静态站点而不启动本地服务器：

```bash
bundle exec jekyll build
```

## 日常更新流程

1. 保存修改后的文件。
2. 运行 `bundle exec jekyll serve`。
3. 在 `localhost:4000` 检查受影响页面；涉及布局时同时检查移动端宽度。
4. 运行 `git status` 并检查 diff，确认没有误提交 `_site/`、缓存、依赖目录或 `.DS_Store`。
5. Stage 需要提交的文件并 commit。
6. Push 到 `main`。
7. 检查 GitHub Pages 是否成功部署。

也可以在 VS Code 的 Source Control 中完成 Stage、Commit 和 Sync/Push。

建议每次至少检查：

- `/`
- `/publications/`
- `/projects/`
- `/projects/sters/`
- `/files/CV.pdf`

## 添加新 Project

创建 `_projects/<slug>.md`，并按需加入：

```text
assets/images/projects/<slug>/
assets/videos/<slug>/
```

Front Matter 必须与当前模板使用的字段一致：

```yaml
---
title: Project Name
subtitle: Formal project or paper subtitle
description: One or two concise sentences for listing cards.
short_label: Research area
thumbnail: /assets/images/projects/<slug>/cover.png
thumbnail_alt: Accessible description of the thumbnail
hero: /assets/images/projects/<slug>/cover.png
hero_alt: Accessible description of the project hero
order: 2
selected: false
published: true
paper: /files/public-paper.pdf   # 可选；只指向确认可公开的文件
video: "#project-video"          # 可选；项目页锚点或外部 URL
tags:
  - Robotics
  - Mechanism Design
---
```

字段行为：

- `published: true`：自动出现在 `/projects/`。
- `selected: true`：同时出现在首页 Selected Research。
- `order`：控制项目排序。
- `paper`：可选；没有确认公开 PDF 时不要填写。

未来公开 BioArm 时，再创建：

```text
_projects/bioarm.md
assets/images/projects/bioarm/
assets/videos/bioarm/
```

在公开内容准备好之前，不建立 Coming Soon 占位页。

## 添加 Publication

在 `_data/publications.yml` 中新增条目。当前页面使用以下字段：

```yaml
- id: short-id
  status: Under review
  venue: Confirmed venue or status destination
  title: Formal paper title
  authors: Authors in confirmed order
  image: /assets/images/projects/example/cover.png
  image_alt: Accessible image description
  paper: /files/public-paper.pdf  # 可选；仅用于确认可公开的版本
  project: /projects/example/
  tags:
    - Robotics
```

不要在未核实前添加或猜测 year、DOI、venue、status、作者顺序或 paper URL。事实优先从公开稿件、当前 CV 与已确认资料中核对。

## 更新 News

`_data/news.yml` 当前是空 YAML 列表，因此首页会自动隐藏 News 区域。

新增真实、可确认的动态时，只需编辑 `_data/news.yml`，不需要修改 `index.html`：

```yaml
- date: YYYY-MM-DD
  text: Concise, factual update.
  url: https://example.com/optional-link
```

`url` 可省略。不要为了填充页面而编造新闻。

## 更新 CV

直接替换：

```text
files/CV.pdf
```

保持文件名不变，长期稳定地址为：

```text
https://yuelong88888888-cloud.github.io/files/CV.pdf
```

替换后应在本地和构建产物中确认 PDF 能正常打开。

## 素材命名与媒体规范

网站发布版文件名使用小写英文、数字和短横线，例如：

- `sters-overview.png`
- `sters-real-walking-1.mp4`
- `public-paper.pdf`

避免使用空格、中文文件名、特殊符号，以及 `final-final-v2` 一类难以维护的版本名。

- 照片优先使用 JPG。
- 技术 figure、diagram 与 plot 优先使用 PNG。
- 浏览器视频使用 H.264 MP4、`yuv420p`，并写入 fast-start metadata。
- 短的无声演示可使用 `muted autoplay loop playsinline`，但不得自动播放声音。
- 长视频必须提供 controls，且不得 autoplay；按需使用 `preload="metadata"` 或 `preload="none"`。
- 技术图不要使用会裁掉内容的 `object-fit: cover`。
- 高信息密度图应提供原尺寸打开方式，方便检查小字。
- 转码生成网页版本时保留原始视频。

原始科研素材可以保留在 `assets/images/source/` 或 `assets/videos/source/`；网页使用规范命名的派生版本，不要覆盖或删除唯一的原始文件。

## 公开仓库安全

不要提交：

- 密码、token、private API key 或 credential
- 私人地址
- 未公开科研数据
- 不适合公开的论文内部信息
- 与站点无关的本地缓存、依赖与系统文件

## TODO

- 获得可公开的 STERS clean manuscript 后，再添加 `paper` 字段与 Paper 链接；当前 `files/sters-paper.pdf` 继续排除出站点。
- 只有出现真实、可验证的动态时才填写 `_data/news.yml`。
- BioArm 资料适合公开后再添加项目文件、媒体与对应 publication；此前不显示占位内容。
