# 知识管理 · Obsidian 实战

> 面向零基础或初学者的 Obsidian 入门到实战系列教程，帮助你建立一套属于自己的个人知识管理体系。

🌐 **在线访问**：[duluodexiaopiqiu.github.io/obsidian-km](https://duluodexiaopiqiu.github.io/obsidian-km/)

---

## 课程目录

| 章节 | 标题 | 说明 |
|------|------|------|
| 1 | Obsidian 介绍 | 它是什么、能解决什么问题 |
| 2 | 什么是知识库（Vault） | Obsidian 的核心概念 |
| 3 | 安装下载与界面熟悉 | 从零开始搭建环境 |
| 4 | 掌握 Markdown 语法 | Obsidian 的内容基础 |
| 5 | 创建第一篇笔记与双向链接 | 核心功能详解 |
| 6 | 知识组织：文件夹、标签、链接 | 怎么选、怎么用 |
| 7 | 图谱视图 | 看见你的知识网络 |
| 8 | 模板 | 让笔记录入事半功倍 |
| 9 | 插件生态介绍与推荐安装 | 扩展 Obsidian 能力 |
| 9.1 | 必备插件推荐 | 精选实用插件 |
| 9.2 | 使用 Git 同步到 GitHub | 数据备份与多端同步 |
| 10 | 如何在 Obsidian 中使用 AI | AI 辅助知识管理 |

---

## 技术栈

- **内容格式**：Markdown（Obsidian 风格，支持 `[[双向链接]]`）
- **网站框架**：[Quartz 4.5.2](https://quartz.jzhao.xyz/) — 专为 Obsidian vault 设计的静态站点生成器
- **部署平台**：GitHub Pages（推送代码自动构建发布）
- **CI/CD**：GitHub Actions（`.github/workflows/deploy.yml`）

## 项目结构

```
obsidian-km/
├── content/                  ← 📝 所有 Markdown 内容放这里
│   ├── index.md              ← 首页（课程导航）
│   ├── 0.大纲.md
│   ├── 1.Obsidian介绍.md
│   └── ...
├── quartz/                   ← Quartz 框架源码（一般不用动）
├── quartz.config.ts          ← 站点配置（标题、主题、baseUrl 等）
├── quartz.layout.ts          ← 页面布局配置
├── .github/workflows/
│   └── deploy.yml            ← 自动部署流水线
├── package.json              ← 依赖声明
└── .gitignore                ← 排除 node_modules、public 等
```

## 本地预览

```bash
# 1. 安装依赖（首次或 node 版本变更后需要）
npm install

# 2. 启动本地预览服务器
node quartz/bootstrap-cli.mjs build --serve

# 3. 打开浏览器访问
# http://localhost:8080
```

## 贡献 / 更新内容

详见 → [使用文档（如何新增内容并发布）](docs/使用文档.md)

## License

MIT
