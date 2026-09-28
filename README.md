# Personal Website — Hugo + Blowfish + GitHub Pages

基于 **Hugo (Extended)** 与 **[Blowfish](https://blowfish.page/)** 主题的个人主页：
Personal Homepage / Portfolio / Projects / Blog / Academic Profile。
纯静态站点，无后端、无额外前端框架，托管在 GitHub Pages，由 GitHub Actions 自动构建部署。

## 技术栈

| 层 | 技术 |
| --- | --- |
| 静态网站生成器 | Hugo Extended (≥ 0.158) |
| 主题 | Blowfish v3.8.0（git submodule，未修改主题源码） |
| 内容 | Markdown |
| 版本管理 | Git |
| 托管 | GitHub Pages |
| CI / CD | GitHub Actions |

## 本地开发

```bash
# 1. 安装 Hugo Extended（macOS）
brew install hugo
#    其他系统见 https://gohugo.io/installation/

# 2. 克隆（包含主题 submodule）
git clone --recurse-submodules <你的仓库地址>
cd <仓库名>
#    若已克隆但忘记 submodule，执行：
git submodule update --init --recursive

# 3. 本地预览（http://localhost:1313）
hugo server -D

# 4. 生产构建（产物在 public/）
hugo --minify
```

## 双语支持（中文 / English）

站点为中英双语：**英文版在根路径 `/`，中文版在 `/zh-cn/`**。
两套内容按"同文件名配对"互相链接（如 `hello-world.md` ↔ `hello-world.zh-cn.md`），
有翻译的页面会自动在导航栏出现 🌐 语言切换下拉菜单。

| 文件 | 说明 |
| --- | --- |
| `config/_default/languages.en.toml` / `languages.zh-cn.toml` | 各语言的站点标题、作者信息（占位符两份都要改） |
| `config/_default/menus.en.toml` / `menus.zh-cn.toml` | 各语言的导航菜单 |
| `i18n/en.yaml` / `i18n/zh-cn.yaml` | 自定义界面文案（论文按钮、"最新文章"等） |
| `data/interests/{en,zh-cn}.toml`、`data/skills/{en,zh-cn}.toml` | 研究方向 / 技能数据 |
| `content/**/xxx.md` ↔ `xxx.zh-cn.md` | 正文翻译对 |

**添加双语文章**：先 `hugo new posts/my-post.md` 写英文版，再复制一份
`my-post.zh-cn.md` 写中文版（front matter 的 date 保持一致），推送即可。
只想发单语也没问题——没有翻译的页面不显示切换按钮。

## ⚠️ 启动后必改的个人信息

所有个人信息集中在配置文件中，**不需要改任何 HTML 模板**：

| 需要修改 | 位置 |
| --- | --- |
| GitHub 用户名（baseURL） | `config/_default/hugo.toml` → `baseURL = "https://USERNAME.github.io/"` |
| 姓名 / 站点标题 | `config/_default/languages.en.toml` → `title` 与 `[params.author] name` |
| 头像 | 替换 `assets/img/avatar.png` |
| Hero 简介（headline / bio） | `config/_default/languages.en.toml` → `[params.author]` |
| 社交链接（当前为 GitHub / Email） | 同上文件的 `links` 列表 |
| 导航栏右侧图标链接 | `config/_default/menus.en.toml` 底部"右侧社交图标"部分 |
| 研究方向标签 | `data/interests/en.toml` 与 `data/interests/zh-cn.toml` |
| 技能清单 | `data/skills/en.toml` 与 `data/skills/zh-cn.toml` |
| 简介正文 | `content/about/index.md` |
| CV 文件 | 替换 `static/cv/cv.pdf` |

所有示例内容（2 个项目、2 篇论文、3 篇博客）均带 ⚠️ **Placeholder** 标记，直接替换即可。

## 目录结构

```
.
├── .github/workflows/hugo.yaml   # GitHub Actions 自动部署
├── archetypes/                   # 新建内容的 front matter 模板
├── assets/
│   ├── css/custom.css            # 自定义样式（主题官方扩展点）
│   └── img/avatar.png            # 头像
├── config/_default/
│   ├── hugo.toml                 # 站点基础配置（baseURL / permalinks / taxonomies）
│   ├── languages.en.toml         # 语言 + 作者个人信息（集中管理）
│   ├── markup.toml               # Markdown / KaTeX passthrough / TOC
│   ├── menus.en.toml             # 导航栏与社交图标
│   └── params.toml               # 主题外观与功能参数
├── content/
│   ├── _index.md                 # 首页（Hero 下方各区块）
│   ├── about/                    # About 页面
│   ├── projects/                 # 项目（Page Bundle，卡片布局）
│   ├── research/                 # Research 页面
│   ├── publications/             # 论文（按年份自动分组）
│   ├── posts/                    # 博客
│   └── cv/                       # CV 入口页
├── data/
│   ├── interests.toml            # 研究方向标签
│   └── skills.toml               # 技能（按类别）
├── i18n/en.yaml                  # 主题文案覆盖（如 "Recent Posts"）
├── layouts/                      # 布局覆盖（不修改主题）
│   ├── partials/publication-item.html
│   ├── partials/favicons.html
│   ├── publications/{list,single}.html
│   └── shortcodes/               # interests / skills / featured-projects / recent-publications
├── static/
│   ├── cv/cv.pdf                 # CV PDF（导航栏 CV 页的下载目标）
│   ├── files/papers/             # 论文 PDF
│   └── images/                   # favicon 等
└── themes/blowfish/              # 主题（git submodule，勿手动修改）
```

## 内容管理

### 添加博客文章

```bash
hugo new posts/my-new-post.md
# 编辑 content/posts/my-new-post.md，完成后把 front matter 中 draft 改为 false
```

支持 Markdown、KaTeX 数学公式（front matter 加 `math: true`，文章任意位置加 `{{< katex >}}`）、
代码高亮 + 复制按钮、目录（TOC）、tags / categories、阅读时间、RSS。

### 添加项目

```bash
hugo new projects/my-project/index.md
# 项目图片放到同目录 feature.png
```

front matter 关键字段：`title` / `description` / `tags` / `github` / `demo` / `featured`（true 时上首页）。
Projects 页面自动使用卡片布局。

### 添加论文

```bash
hugo new publications/my-paper-2026.md
```

front matter：`title` / `authors` / `date`（决定年份分组）/ `venue` / `doi` / `pdf` / `code` / `project` / `bibtex`（可选，详情页自动展示）。
PDF 文件放 `static/files/papers/`，front matter 里 `pdf = "/files/papers/xxx.pdf"`。
列表页与首页"Recent Publications"自动更新，按年份自动分组。

### 部署到 GitHub Pages

1. 在 GitHub 创建名为 **`USERNAME.github.io`** 的空仓库（公开）
2. 修改 `config/_default/hugo.toml` 中的 `baseURL` 为 `https://USERNAME.github.io/`
3. 推送：

   ```bash
   git remote add origin git@github.com:USERNAME/USERNAME.github.io.git
   git push -u origin main
   ```

4. 仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**
5. 之后每次 `git push` 自动构建部署，访问 `https://USERNAME.github.io`

### 更新主题

```bash
git submodule update --remote --merge themes/blowfish   # 升级到最新
# 或固定到某个版本：
cd themes/blowfish && git checkout v3.8.0 && cd ../..
git add themes/blowfish && git commit -m "pin blowfish vX.Y.Z"
```

## 常用命令

| 命令 | 作用 |
| --- | --- |
| `hugo server -D` | 本地开发服务器（含草稿） |
| `hugo --minify` | 生产构建 |
| `hugo new posts/foo.md` | 新建文章（使用 archetype） |
| `hugo mod verify` / `hugo config` | 排查配置 |
