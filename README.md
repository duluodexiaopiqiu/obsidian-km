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
| 8 | Chat 和 Agent 的区别 | 理解 AI 交互模式 |
| 9 | 模板 | 让笔记录入事半功倍 |
| 10 | 插件生态介绍与推荐安装 | 扩展 Obsidian 能力 |
| 10.1 | 必备插件推荐 | 精选实用插件 |
| 10.2 | 使用 Git 同步到 GitHub | 数据备份与多端同步 |
| 11 | 如何在 Obsidian 中使用 AI | AI 辅助知识管理 |
| 12 | 常见问题 | 常见问题汇总 |

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
│   ├── 00-大纲.md
│   ├── 01-Obsidian介绍.md
│   ├── 02-安装下载与界面熟悉.md
│   ├── 03-知识库/             ← 第3章子文档
│   │   ├── 03-什么是知识库Vault.md
│   │   └── 03-01-知识库的设计.md
│   ├── 04-Markdown语法/       ← 第4章子文档
│   │   ├── 04-Markdown语法.md
│   │   ├── 04-01-设置面板说明.md
│   │   ├── 04-02-通过官方文档学习.md
│   │   └── 04-03-obsidian的钥匙串.md
│   ├── 05-创建第一篇笔记与双向链接.md
│   ├── 06-知识组织文件夹标签链接.md
│   ├── 07-图谱视图.md
│   ├── 08-chat和agent的区别/  ← 第8章子文档
│   │   ├── 08-chat和agent的区别.md
│   │   └── 08-01-chat和agent的区别.md
│   ├── 09-模板/               ← 第9章子文档
│   │   ├── 09-模板.md
│   │   └── 09-01-读书模版.md
│   ├── 10-插件生态/           ← 第10章子文档
│   │   ├── 10-插件生态介绍与推荐安装.md
│   │   ├── 10-01-插件下载教程.md
│   │   ├── 10-02-挑选插件指南.md
│   │   ├── 10-03-WebClipper收录.md
│   │   ├── 10-04-AI补全插件.md
│   │   ├── 10-05-calender插件.md
│   │   ├── 10-06-终端插件.md
│   │   ├── 10-07-copilot插件.md
│   │   ├── 10-08-Claudian插件.md
│   │   └── 10-09-claudian插件.md
│   ├── 11-必备插件推荐.md
│   ├── 12-使用Git同步到GitHub/ ← 第12章子文档
│   │   ├── 12-使用Git同步到GitHub.md
│   │   └── 12-01-备份.md
│   ├── 13-如何在Obsidian中使用AI/ ← 第13章子文档
│   │   ├── 13-如何在Obsidian中使用AI.md
│   │   └── 13-01-node安装.md
│   └── 14-常见问题/           ← 第14章子文档
│       ├── 14-常见问题.md
│       └── 14-01-解决新建按钮问题.md
├── docs/                      ← 项目文档（使用文档、同步方案等）
│   ├── 使用文档.md
│   └── 飞书知识库同步方案.md
├── quartz/                    ← Quartz 框架源码（一般不用动）
├── quartz.config.ts           ← 站点配置（标题、主题、baseUrl 等）
├── quartz.layout.ts           ← 页面布局配置
├── .github/workflows/
│   └── deploy.yml              ← 自动部署流水线
├── package.json               ← 依赖声明
└── .gitignore                 ← 排除 node_modules、public 等
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
