# ⚡ 快速入门指南

你的 Hugo 博客已经搭建完成！本文档提供最简单的部署步骤。

## 📦 当前状态

✅ Hugo 博客已配置完成  
✅ PaperMod 主题已安装  
✅ 示例文章已创建  
✅ GitHub Actions 工作流已配置  
✅ 本地 Git 仓库已初始化  

## 🚀 三步部署到 GitHub Pages

### 步骤 1: 创建 GitHub 仓库

1. 访问 https://github.com/new
2. 输入仓库名：`<你的用户名>.github.io`（例如：`zhangsan.github.io`）
3. 选择 **Public**
4. **不要**勾选任何初始化选项
5. 点击 **Create repository**

### 步骤 2: 修改配置并推送

```bash
# 1. 修改 baseURL（重要！）
nano hugo.yaml
# 将第一行改为: baseURL: https://<你的用户名>.github.io/
# 保存退出（Ctrl+O, Enter, Ctrl+X）

# 2. 提交修改
git add hugo.yaml
git commit -m "Update baseURL"

# 3. 添加远程仓库（替换为你的用户名）
git remote add origin https://github.com/<你的用户名>/<你的用户名>.github.io.git

# 4. 推送代码
git push -u origin main
```

### 步骤 3: 配置 GitHub Pages

1. 进入你的 GitHub 仓库
2. 点击 **Settings** → **Pages**
3. 在 "Build and deployment" 下选择 **Source: GitHub Actions**
4. 等待 1-2 分钟，Actions 会自动构建

### ✨ 完成！

访问 `https://<你的用户名>.github.io/` 查看你的博客！

## 📝 日常写作

```bash
# 创建新文章
hugo new content/posts/my-article.md

# 编辑文章
nano content/posts/my-article.md

# 本地预览
hugo server -D
# 访问 http://localhost:1313

# 发布（设置 draft: false）并推送
git add .
git commit -m "Add new post"
git push
```

## 📚 详细文档

- **完整部署指南**: 查看 [DEPLOYMENT.md](DEPLOYMENT.md)
- **使用说明**: 查看 [README.md](README.md)
- **当前运行的服务器**: http://localhost:1313

## ❓ 遇到问题？

### 推送时需要密码

GitHub 不再支持密码，使用以下方法之一：

**方法 1: Personal Access Token**
1. GitHub Settings → Developer settings → Personal access tokens
2. Generate new token (classic)
3. 勾选 `repo` 和 `workflow`
4. 复制 token
5. 推送时使用 token 作为密码

**方法 2: SSH 密钥**
```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
cat ~/.ssh/id_ed25519.pub
# 将输出添加到 GitHub Settings → SSH and GPG keys
```

### Actions 构建失败

```bash
# 确保主题正确安装
git submodule update --init --recursive
git add .
git commit -m "Fix submodule"
git push
```

### 样式显示不正常

确认 `hugo.yaml` 第一行的 baseURL 正确且以 `/` 结尾。

## 🎯 下一步

- [ ] 修改"关于"页面的个人信息
- [ ] 修改 hugo.yaml 中的社交链接
- [ ] 开始写你的第一篇原创文章
- [ ] 添加你自己的头像图片

---

**Happy Blogging! 开始你的创作之旅吧！** 🎉

