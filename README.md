# 个人履历网站

这是一个现代化的个人履历介绍网站，支持暗黑模式、响应式设计，并包含留言板功能。

## 功能特性

- 📄 **个人履历展示**：包含个人信息、工作经历、教育背景、技能和项目经历
- 🖼️ **图片支持**：预留了多个图片位置，可填入图片URL
- 💬 **留言板功能**：访客可以留言，留言保存在本地存储中
- 🌓 **暗黑模式**：支持自动、亮色、暗色三种主题模式
- 📱 **响应式设计**：适配桌面和移动设备
- ✨ **现代化UI**：简洁美观的界面设计

## 如何使用

### 1. 修改个人信息

打开 `index.html` 文件，找到 `<script>` 标签中的 `config` 对象，修改以下内容：

```javascript
const config = {
  // 个人信息
  name: '你的姓名',
  title: '职位/职业',
  bio: '这里填写你的个人简介...',
  avatar: 'https://example.com/avatar.jpg', // 头像图片URL
  
  // 社交媒体链接
  social: {
    github: 'https://github.com/yourusername',
    linkedin: 'https://linkedin.com/in/yourusername',
    email: 'mailto:your.email@example.com'
  },
  
  // 工作经历图片
  experienceImages: [
    'https://example.com/work1.jpg', // 第一份工作的图片
    'https://example.com/work2.jpg'  // 第二份工作的图片
  ],
  
  // 项目图片
  projectImages: [
    'https://example.com/project1.jpg', // 项目1图片
    'https://example.com/project2.jpg', // 项目2图片
    'https://example.com/project3.jpg'  // 项目3图片
  ]
};
```

### 2. 修改工作经历

在HTML中找到 `<section id="experience">` 部分，修改工作经历的内容：
- 职位名称
- 公司名称
- 工作时间
- 工作描述
- 工作图片（在 `config.experienceImages` 中配置）

### 3. 修改教育背景

在HTML中找到 `<section id="education">` 部分，修改教育背景信息。

### 4. 修改技能

在HTML中找到 `<section id="skills">` 部分，修改技能标签。

### 5. 修改项目经历

在HTML中找到 `<section id="projects">` 部分，修改项目信息：
- 项目名称
- 项目描述
- 项目标签
- 项目图片（在 `config.projectImages` 中配置）

### 6. 图片URL说明

所有图片位置都支持填入图片URL，包括：
- 头像图片：`config.avatar`
- 工作经历图片：`config.experienceImages` 数组
- 项目图片：`config.projectImages` 数组

如果不需要显示某张图片，可以留空字符串 `''`，图片位置将显示为占位背景。

### 7. 留言功能

留言功能使用浏览器本地存储（localStorage）保存留言数据。访客可以：
- 填写姓名和留言内容
- 可选填写邮箱
- 提交留言后，留言会显示在留言列表中
- 留言数据保存在浏览器本地，刷新页面不会丢失

**注意**：由于使用本地存储，留言数据只保存在访问者的浏览器中，不同设备/浏览器之间不会共享留言数据。如果需要服务端存储，需要配置后端API。

### 8. 启用 GitHub Issues 留言（可选：Utterances）

本项目支持使用 Utterances（https://utteranc.es/）将留言保存到 GitHub Issues，从而实现所有访客可见的留言板。默认行为（本地开发或未启用 Utterances）仍然回退到 localStorage。

如何启用：
1. 在 `index.html` 中 `<script>` 里的 `config` 对象设置：

```js
utterancesRepo: '你的用户名/你的仓库', // 例如: 'jkhkjlkll/jkhkjlkll.github.io'
```

2. 将代码提交并部署到 GitHub Pages（或其他可通过 HTTPS 访问的域）。
3. 访问页面并使用 GitHub 登录（首次发表评论时会要求授权）。Utterances 会把每条评论存到目标仓库的 Issue 中。

注意事项：
- Utterances 会在目标仓库创建并使用 Issues 来保存评论，评论为公开且存储在 GitHub 上。
- 评论者需要 GitHub 账户并登录后才能发表评论（这是 Utterances 的工作方式）。
- 如果你希望评论与页面一一映射（例如按路径或 URL），可以在 `index.html` 中的 Utterances 注入配置里调整 `issue-term`（默认使用 `pathname`）。

### 9. 编辑提交流程说明

出于安全考虑，页面不会在客户端保存或自动提交 GitHub 仓库的修改（这样可以避免在前端暴露 token）。目前支持两种方式：

- 本地保存（默认）：所有“关于我/工作/教育/技能”等修改会保存到访问者浏览器的 localStorage，仅在本地生效。
- 通过工作流自动化（可选）：如果你需要把编辑内容自动合并到仓库，请使用 GitHub Actions 或后端服务来接收提交请求并安全地使用 GitHub token。该方案需要额外的后端或 CI 配置，不在当前静态页面的实现范围内。

### 10. localStorage 键名（参考）

如果你需要在本地检查或清理数据，这里列出页面使用的 localStorage key：

- 留言：`resume_comments`
- 关于我：`resume_about`
- 工作经历：`resume_experience`
- 教育：`resume_education`
- 技能：`resume_skills`

在浏览器开发者工具中（Application / Storage -> Local Storage）可以查看或删除这些键。

## 部署

这个网站是纯静态的，可以部署到任何静态网站托管服务：

- GitHub Pages
- Netlify
- Vercel
- 任何支持静态文件的服务器

## 浏览器支持

- Chrome (最新版本)
- Firefox (最新版本)
- Safari (最新版本)
- Edge (最新版本)

## 许可证

MIT License