# 我的技术博客

这是使用 [Hugo](https://gohugo.io/) 静态站点生成器和 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 主题搭建的个人技术博客。

## 📋 项目结构

```
blog/
├── .github/workflows/     # GitHub Actions 自动部署配置
│   └── hugo.yml
├── archetypes/            # 内容模板
├── content/               # 博客内容（Markdown 文件）
│   ├── posts/            # 博客文章
│   ├── about.md          # 关于页面
│   ├── archives.md       # 归档页面
│   └── search.md         # 搜索页面
├── static/               # 静态资源（图片、CSS 等）
├── themes/               # 主题文件
│   └── PaperMod/        # PaperMod 主题（Git submodule）
├── hugo.yaml            # Hugo 配置文件
└── README.md            # 本文件
```

## 🚀 快速开始

### 前提条件

- 已安装 Hugo Extended 版本（>= 0.80.0）
- 已安装 Git

### 本地开发

1. **克隆仓库**

```bash
git clone <你的仓库地址>
cd blog
```

2. **初始化主题子模块**

```bash
git submodule update --init --recursive
```

3. **启动本地服务器**

```bash
hugo server -D
```

4. **访问博客**

打开浏览器访问 http://localhost:1313

服务器支持热重载，修改内容后会自动刷新页面。

## ✍️ 写作指南

### 创建新文章

```bash
hugo new content/posts/my-new-post.md
```

这将在 `content/posts/` 目录下创建一个新的 Markdown 文件，包含以下 Front Matter：

```yaml
---
title: "My New Post"
date: 2025-11-21T10:00:00+08:00
draft: true
---
```

### Front Matter 配置

Front Matter 是文章开头的元数据，用于控制文章的显示和行为：

```yaml
---
title: "文章标题"                    # 必填
date: 2025-11-21T10:00:00+08:00    # 必填：发布日期
draft: false                        # true=草稿，false=发布
tags: ["标签1", "标签2"]            # 可选：文章标签
categories: ["分类"]                # 可选：文章分类
summary: "文章摘要"                  # 可选：自定义摘要
showToc: true                       # 可选：显示目录
weight: 1                           # 可选：排序权重（数字越小越靠前）
---
```

### Markdown 语法

支持标准 Markdown 语法，包括：

- **标题**：`# H1`, `## H2`, `### H3`
- **强调**：`**粗体**`, `*斜体*`, `~~删除线~~`
- **列表**：`-` 或 `1.`
- **链接**：`[文本](URL)`
- **图片**：`![描述](图片路径)`
- **代码块**：使用三个反引号，并指定语言

````markdown
```c
#include <stdio.h>
int main() {
    printf("Hello, World!\n");
    return 0;
}
```
````

### 添加图片

1. 将图片放在 `static/images/` 目录下
2. 在文章中引用：`![图片描述](/images/your-image.png)`

## 🌐 部署到 GitHub Pages

### 首次部署

1. **在 GitHub 上创建仓库**

   - 仓库名建议：`blog` 或 `<你的用户名>.github.io`
   - 设置为 Public

2. **修改配置文件**

   编辑 `hugo.yaml`，将 `baseURL` 改为你的 GitHub Pages 地址：

   ```yaml
   # 如果仓库名是 <username>.github.io
   baseURL: https://<username>.github.io/
   
   # 如果仓库名是其他名字（如 blog）
   baseURL: https://<username>.github.io/blog/
   ```

3. **推送到 GitHub**

   ```bash
   # 添加远程仓库
   git remote add origin https://github.com/<username>/<repo-name>.git
   
   # 提交所有文件
   git add .
   git commit -m "Initial commit: Hugo blog setup"
   
   # 推送到 main 分支
   git push -u origin main
   ```

4. **配置 GitHub Pages**

   - 进入仓库的 Settings → Pages
   - Source 选择 "GitHub Actions"
   - 稍等几分钟，GitHub Actions 会自动构建并部署

5. **访问你的博客**

   部署成功后，访问：
   - `https://<username>.github.io/` （如果仓库名是 `<username>.github.io`）
   - `https://<username>.github.io/<repo-name>/` （如果仓库名是其他）

### 日常更新流程

1. 创建或编辑文章
2. 本地预览：`hugo server -D`
3. 确认无误后提交：

```bash
git add .
git commit -m "Add new post: <文章标题>"
git push
```

4. GitHub Actions 会自动构建并部署（约 1-2 分钟）

## ⚙️ 配置说明

### 修改站点信息

编辑 `hugo.yaml`：

```yaml
title: 我的技术博客              # 站点标题
params:
  author: 你的名字                # 作者名
  description: "站点描述"         # 站点描述
  socialIcons:                   # 社交链接
    - name: github
      url: "https://github.com/你的用户名"
```

### 主题自定义

PaperMod 支持丰富的自定义选项，详见 [PaperMod 文档](https://github.com/adityatelange/hugo-PaperMod/wiki)。

常用配置：

- **主题模式**：`defaultTheme: auto/light/dark`
- **代码高亮**：`markup.highlight.style`
- **显示选项**：`ShowReadingTime`, `ShowCodeCopyButtons` 等

## 📚 学习资源

### Hugo 相关

- [Hugo 官方文档](https://gohugo.io/documentation/)
- [Hugo 中文文档](https://hugo.aiaide.com/)
- [PaperMod 主题文档](https://github.com/adityatelange/hugo-PaperMod/wiki)

### Markdown 语法

- [Markdown 基础语法](https://www.markdownguide.org/basic-syntax/)
- [Markdown 扩展语法](https://www.markdownguide.org/extended-syntax/)

### Git 和 GitHub

- [Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [GitHub Pages 文档](https://docs.github.com/en/pages)

## 🛠️ 常用命令

```bash
# 创建新文章
hugo new content/posts/article-name.md

# 启动开发服务器（包含草稿）
hugo server -D

# 启动开发服务器（不包含草稿）
hugo server

# 构建站点（生成静态文件到 public/）
hugo

# 构建并压缩
hugo --minify

# 查看 Hugo 版本
hugo version

# 更新主题
git submodule update --remote --merge
```

## 🐛 故障排除

### 问题：推送后 GitHub Actions 构建失败

**解决方法：**
1. 查看 Actions 标签页的错误日志
2. 确认 `hugo.yaml` 配置正确
3. 确认主题子模块已正确添加

### 问题：本地服务器启动失败

**解决方法：**
1. 确认 Hugo 版本 >= 0.80.0
2. 检查 `hugo.yaml` 语法是否正确
3. 确认主题已正确安装：`git submodule update --init`

### 问题：样式显示不正常

**解决方法：**
1. 清除浏览器缓存
2. 确认 `baseURL` 配置正确（末尾要有 `/`）
3. 重新构建：`hugo --gc`

## 📝 TODO

- [ ] 添加评论系统（Giscus/Disqus）
- [ ] 添加 Google Analytics
- [ ] 自定义域名
- [ ] 添加更多文章分类
- [ ] 优化 SEO

## 📄 许可

本项目内容采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可协议。

---

**Happy Blogging! 🎉**

如有问题，欢迎提交 Issue 或联系我。

