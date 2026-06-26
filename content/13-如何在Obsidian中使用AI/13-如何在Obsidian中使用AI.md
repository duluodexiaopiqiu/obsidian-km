# 10. 如何在 Obsidian 中使用 AI

## Obsidian + AI 能做什么？

在 Obsidian 中接入 AI，可以实现：

| 功能 | 说明 |
|-|-|
| **智能写作** | AI 帮你续写、改写、润色笔记内容 |
| **内容总结** | 选中长文，AI 总结核心要点 |
| **翻译** | 选中文本，AI 翻译成指定语言 |
| **知识问答** | 基于你的知识库，AI 回答相关问题 |
| **自动标签** | AI 根据笔记内容推荐标签和链接 |
| **搜索增强** | 用自然语言搜索笔记（"上周关于Python的笔记"） |

## 方案一：使用社区 AI 插件（推荐新手）

### Copilot 插件（最推荐）

这是目前 Obsidian 生态中最成熟的 AI 插件。

**安装方式：**

1. 社区插件搜索 "Copilot"
2. 安装并启用

**支持的 AI 服务：**

| 服务 | 是否免费 | 说明 |
|-|-|-|
| Ollama（本地模型） | ✅ 完全免费 | 需要本地部署，性能取决于你的电脑 |
| OpenAI（GPT） | ❌ 付费 | 需 API Key，质量最高 |
| Anthropic（Claude） | ❌ 付费 | 需 API Key |
| Azure OpenAI | ❌ 付费 | 企业用户 |
| Groq | ✅ 有免费额度 | 速度快，有免费调用次数 |

**推荐路径：**

1. 先试试 **Groq**（免费注册，送额度）
2. 有本地 GPU 可以尝试 **Ollama**
3. 预算充足用 **OpenAI** 或 **Claude**

### Copilot 基础用法

1. 在侧边栏打开 Copilot 聊天面板
2. 选中笔记中的内容
3. 输入指令：`/summarize` 总结、`/explain` 解释、`/rewrite` 改写
4. 或者直接对话提问

### 其他 AI 插件

| 插件 | 特点 |
|-|-|
| **Smart Connections** | 基于 AI 自动推荐相关笔记 |
| **Text Generator** | 用 AI 生成笔记内容，支持模板 |
| **AI Commander** | 多功能 AI 助手 |

## 方案二：连接本地 AI（Ollama）—— 完全免费

### 什么是 Ollama？

Ollama 是一个可以在**你本地电脑**上运行大语言模型的工具。不需要联网，数据不出本机，完全免费。

### 安装步骤

1. 访问 [https://ollama.com](https://ollama.com) 下载安装
2. 安装完成后，打开终端（CMD/Terminal）
3. 下载一个轻量模型：

   ```bash
   ollama pull qwen2:7b
   ```

   ```bash
   ollama pull llama3.2:3b
   ```
4. 运行模型（保持终端开着）：

   ```bash
   ollama serve
   ```

### 在 Obsidian 中配置

1. 安装 Copilot 插件
2. 进入设置 → Copilot
3. 选择模型供应商为 **Ollama**
4. 模型名称填入 `qwen2:7b`（或你下载的模型）
5. 保存即可使用

### 优缺点

- **优点**：完全免费、数据不出本机、离线可用、隐私安全
- **缺点**：需要一定的电脑配置（建议 16GB 内存以上）、模型能力弱于 GPT-4

## 方案三：连接云端 AI（OpenAI / Claude）

### 获取 API Key

1. **OpenAI**：https://platform.openai.com/api-keys
2. **Anthropic Claude**：https://console.anthropic.com

### 在 Copilot 中配置

1. Copilot 设置 → 选择 OpenAI 或 Anthropic
2. 填入 API Key
3. 选择模型（GPT-4o / Claude Sonnet 等）
4. 保存并测试

### 优缺点

- **优点**：模型能力强、速度快、无需本地资源
- **缺点**：需要付费、需要联网、隐私数据上传到第三方

## 实用 AI 指令示例

### 写作助手

```
/rewrite   让这段文字更简洁
/continue  继续写下去
/grammar   检查语法错误
```

### 知识处理

```
/summarize   总结这段内容
/explain     解释这个概念
/translate   翻译成英文
/elaborate   详细展开说明
```

### 笔记整理

```
帮我给这篇笔记生成 3 个标签
这篇笔记应该链接到哪些现有笔记？
帮我提取笔记中的关键信息，生成一个表格
```

## 实战场景

### 场景一：读文章做笔记

1. 把文章复制到 Obsidian
2. 选中全文，输入 `/summarize`
3. AI 生成摘要
4. 把摘要整理成笔记，链接到相关笔记

### 场景二：头脑风暴

1. 新建一篇空白笔记
2. 打开 Copilot，输入你的想法
3. 让 AI 帮你扩展思路、提出反驳、补充细节

### 场景三：知识问答

1. 选中几篇相关笔记
2. 问 AI："根据这些笔记，总结一下 XX 的核心观点"
3. AI 基于你的笔记内容回答

## 小练习

1. 安装 Copilot 插件
2. 注册一个免费的 AI 服务（推荐 Groq 或 本地 Ollama）
3. 在 Copilot 中配置好 AI 服务
4. 选中一段已有的笔记内容，试试 `/summarize`
5. 让 AI 帮你生成一篇日记

## 进阶建议

1. **建立自己的 AI 提示词库** —— 把常用的 AI 指令存成模板
2. **结合 Templater + AI** —— 用模板自动化调用 AI
3. **AI 不是万能的** —— AI 适合辅助和启发，核心知识体系还是靠你自己建立

---

**上一节：**使用 Git 同步到 GitHub  
**📖 回到大纲：**0.大纲