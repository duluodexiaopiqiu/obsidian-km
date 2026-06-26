# 6.claudian插件

<title>6.claudian插件</title>

我是醒醒，AI共学社主理人，30岁程序员转型一人公司践行者。闲鱼+小红书变现五位数，已帮300+人用AI为工作提效。不教你追工具，只帮你用AI解决问题、赋能业务。长期主义者，专注让AI真正落地到你的工作里。

---

# 把你的AI助手直接塞进Obsidian里

你平时用Obsidian记笔记对吧。

那你有没有想过：能不能在Obsidian里直接跟AI说「帮我写一篇关于XX的笔记」，然后AI就真的在你的笔记库里帮你写？

不是复制粘贴到ChatGPT再贴回来。是AI直接在你的Obsidian里读写文件，像你的私人助手一样。

今天要介绍的 **Claudian** 插件，做的就是这件事。

---

## Claudian是做什么的

一句话说清楚：

**Claudian是一个Obsidian插件，它把AI编程代理直接嵌入到你的Obsidian里。**

你的整个笔记库，就是AI的工作目录。它可以直接读你的笔记、写新笔记、修改现有笔记、搜索文件，甚至执行一些命令。

支持的AI后端有：

- **Claude Code（主力推荐）** — Anthropic出品，写代码、写文章都很强
- **Codex** — OpenAI出品
- **Opencode** — 开源
- **Pi** — 开源

你可以选一个用，最推荐的是Claude Code。

**但注意**：Claudian本身只是一个「壳」，真正干活的是Claude Code。所以第一步，你得先把Claude Code装上。

---

## 前置准备：安装Claude Code

这一步是**整个教程最关键的地方**，也是最容易卡住小白的地方。

千万别跳过，跟着一步步来。

### 什么是Claude Code？

Claude Code是Anthropic（Claude的公司）出的一个「命令行AI编程工具」。

简单理解：它是在终端里跟你聊天的AI，能读写文件、执行命令。

Claudian插件就是调用它来干活。

### 安装前的系统要求

- **操作系统**：Windows / macOS / Linux 都可以（但Claudian只支持桌面版）
- **需要安装 Node.js**（16+版本）

### 第一步：安装Node.js

如果你电脑上已经有Node.js了，可以跳过这一步。

**怎么检查有没有Node.js？**

打开终端（Windows操作如下）：

1. 按键盘 `Win + R`
2. 输入 `powershell` 然后回车
3. 在弹出的黑窗口中输入以下命令：

```Plain Text
node --version
```

如果显示 `v18.x.x` 或 `v20.x.x` 之类的版本号，说明已经有了。

如果提示「node不是可识别的命令」，说明还没装。

**下载Node.js：**

1. 打开 [https://nodejs.org/](https://nodejs.org/)
2. 下载 LTS 版本（左边那个，推荐大多数用户）
3. 双击安装包，一路点「下一步」就行
4. 装完后重新打开powershell，输入 `node --version` 验证

### 第二步：安装Claude Code

在刚才的powershell里，输入以下命令：

```Plain Text
npm install -g @anthropic-ai/claude-code
```

这一步要联网下载，可能需要1-3分钟。

看到类似下面的输出，就说明装好了：

```Plain Text
added xxx packages in xxx seconds
```

### 第三步：验证安装

在powershell里输入：

```Plain Text
claude --version
```

如果显示版本号（比如 `0.x.x`），说明安装成功。

**如果提示「claude不是可识别的命令」：**

别慌，这是常见问题。试试下面的解决方案：

**方案A：关闭powershell重新打开**

有时候重启终端就好了。

**方案B：用npx运行**

```Plain Text
npx @anthropic-ai/claude-code --version
```

**方案C：检查npm全局安装路径**

```Plain Text
npm root -g
```

会显示一个路径，比如 `C:\Users\你的用户名\AppData\Roaming\npm\node_modules`

然后检查这个路径是不是在系统PATH里。

---

### 第四步：配置Claude API Key或订阅

Claude Code是需要付费的。目前有两种方式：

**方式1：Claude Pro订阅（推荐小白）**

1. 打开 [https://claude.ai/](https://claude.ai/)
2. 注册账号
3. 订阅Claude Pro（\$20/月）
4. 在Claude Code里登录你的Claude账号

然后在终端运行：

```Plain Text
claude
```

如果是第一次运行，会提示你登录认证。按提示操作就行。

**方式2：使用API Key（适合有开发经验的用户）**

1. 打开 [https://console.anthropic.com/](https://console.anthropic.com/)
2. 注册并充值
3. 创建一个API Key
4. 设置环境变量：

```Plain Text
set ANTHROPIC_API_KEY=你的APIKey
```

注意：每次重启终端都要重新设置，或者你把它加到系统环境变量里。

---

### 验证Claude Code能正常工作

在终端里输入：

```Plain Text
claude
```

看到Claude的欢迎界面和输入提示（`>`），就说明一切正常了。

输入 `/exit` 退出。

好了，最难的部分已经过去了。

---

## 安装Claudian插件

### 方法1：从社区插件市场安装（推荐）

这是最简单的方法：

1. 打开Obsidian
2. 点击左下角 ⚙️ **设置**
3. 在左侧找到 **第三方插件**
4. **关闭安全模式**
5. 点击 **浏览** 按钮
6. 在搜索框输入 **Claudian**
7. 找到插件后点击 **安装**
8. 安装完成后点击 **启用**

搞定了。

### 方法2：从GitHub手动安装

如果因为网络原因在插件市场搜不到，可以手动装：

1. 打开 [https://github.com/YishenTu/claudian/releases/latest](https://github.com/YishenTu/claudian/releases/latest)
2. 下载 `main.js`、`manifest.json` 和 `styles.css` 三个文件
3. 在你的Obsidian笔记库文件夹里，找到 `.obsidian/plugins/` 目录

```Plain Text
你的笔记库文件夹/
└── .obsidian/
    └── plugins/  ← 在这里创建一个 claudian 文件夹
```

1. 在 `plugins/` 下创建一个 `claudian` 文件夹
2. 把下载的三个文件复制进去
3. 结构长这样：

```Plain Text
.obsidian/plugins/claudian/
├── main.js
├── manifest.json
└── styles.css
```

1. 回到Obsidian → 设置 → 第三方插件 → 启用 **Claudian**

---

## 首次使用：跟Claude打个招呼

插件启用后，Obsidian的界面会多出几个东西：

### 打开聊天面板

方法一：看Obsidian左侧的工具栏（功能区），有一个新的图标，鼠标悬停会显示「Claudian Chat」，点击它。

方法二：按 `Ctrl + P` 打开命令面板，输入「Claudian」，选择「Open Claudian Chat」。

聊天面板会在右侧打开，这就是你跟AI聊天的地方。

### 你的第一条指令

在聊天输入框里输入：

```Plain Text
帮我看看我最近一周写了哪些笔记
```

Claude会开始工作：读取你的笔记库、搜索文件、然后给你一个总结。

你会看到它思考的过程——它在读哪些文件、做了哪些操作。

**⚠️ 第一次使用的时候，会弹出一个确认窗口，问你是否允许Claude执行操作。** 这是安全机制，点击「允许」就行。

### 写一篇新笔记

试试这个：

```Plain Text
帮我写一篇关于「如何养成好习惯」的笔记，放在 Habits/ 文件夹下
```

Claude会直接在你的笔记库里创建文件。

你切换到Obsidian的文件管理器，就能看到新生成的笔记。

---

## 核心功能详解

### 聊天面板（Chat Sidebar）

这是你用得最多的功能。

- 可以开**多个聊天标签**，同时处理不同任务
- 对话会自动保存，关掉再打开还能接着聊
- 支持 `Shift+Tab` 切换到**Plan模式**——AI会先给你出方案，等你批准了再执行。适合复杂的任务。

### 内联编辑（Inline Edit）

这是最神奇的功能。

在笔记里**选中一段文字**，然后按快捷键（默认是某个键，你可以在设置里配置），会弹出一个编辑窗口。

告诉AI你想怎么改——比如「把这段说得更简单点」「改成英文」「补充更多细节」。

AI会给出修改建议，用**单词级别的差异对比**（diff）显示哪些地方改了，你可以选择接受还是拒绝。

**不需要离开当前笔记页面，不需要复制粘贴到别的地方。**

### @引用（Mention）

在聊天输入框里输入 `@`，会自动弹出提醒，你可以：

- `@文件名` — 引用笔记库里的某个文件
- `@子代理` — 引用你配置的子AI代理
- `@MCP服务器` — 引用外部工具

比如你写：

```Plain Text
帮我检查一下 @我的周报.md 里的语法错误
```

Claude就会自动找到 `我的周报.md` 这个文件来处理。

### Slash命令（斜杠命令）

在输入框输入 `/`，会弹出模板列表。

比如可能有：

- `/翻译` — 把当前笔记翻译成英文
- `/总结` — 总结一篇笔记
- `/润色` — 润色文字

这些模板是可以自己配置的。

### 多标签对话

Claudian支持多个聊天标签，你可以：

- 一个标签在写文章
- 一个标签在查资料
- 一个标签在改代码

相互独立，互不干扰。

而且对话历史可以**导出、分叉（fork）、压缩**。

### MCP服务器

这是进阶功能。简单说，你可以通过MCP协议把外部工具接进来。

比如接一个联网搜索工具，Claude就能上网查资料。

对于新手可以暂时不管这个，以后需要了再研究。

---

## Claudian的设置说明

点击设置 → Claudian，你会看到几个配置项：

**Provider（AI提供商）**

- 默认选了 Claude
- 你也可以换 Codex、Opencode、Pi

**Claude CLI路径**

- 如果Claudian找不到你装的Claude Code，需要手动填路径
- Windows默认路径签收：`where.exe claude`
- 常见路径：`C:\Users\你的用户名\AppData\Roaming\npm\node_modules\@anthropic-ai\claude-code\cli-wrapper.cjs`

**语言**

- 支持中文界面
- 在设置里找 Language 切换

---

## 新手常见问题与注意事项

### Q1：安装Claude Code时提示权限错误

```Plain Text
Error: EACCES: permission denied
```

**原因**：npm全局安装需要管理员权限。

**解决**：

- Windows：用「管理员身份运行」powershell再试
- macOS/Linux：在命令前加 `sudo`

```Plain Text
sudo npm install -g @anthropic-ai/claude-code
```

### Q2：Claudian提示「Claude CLI not found」

**原因**：插件找不到Claude Code。

**解决**：

1. 在终端输入 `where.exe claude`（Windows）或 `which claude`（Mac/Linux）
2. 把输出的路径，填到 Claudian 设置 → Advanced → Claude CLI path

常见路径参考：

<sheet sheet-id="1jc6b5" token="GtunsL7RWhNo5FtSlKncvGWdnXg"></sheet>

**⚠️ Windows用户注意**：不要用 `.cmd` 或 `.ps1` 结尾的文件，要用 `.exe` 或 `.cjs`。

### Q3：聊天面板打不开

**检查**：

1. 插件启用了没有
2. Obsidian版本是不是 1.7.2 以上
3. 试试重启Obsidian
4. 查看开发者工具有没有报错（`Ctrl + Shift + I`）

### Q4：中文显示乱码

**原因**：终端编码问题。

**解决**：在powershell里先运行：

```Plain Text
chcp 65001
```

然后再启动Obsidian。或者在系统区域设置里勾选「Beta版：使用Unicode UTF-8提供全球语言支持」。

### Q5：AI说「我没有权限操作文件」

这是Claudian的安全机制，第一次使用会弹窗问你允不允许。

**注意**：一定要点「允许」，不然AI读不了你的笔记也写不了。

### Q6：费用问题

**这是新手最容易忽略的问题。**

Claudian本身是**免费开源**的。但调用Claude Code需要付费：

- **Claude Pro**：\$20/月，普通使用够用
- **API按量付费**：用得越多越贵，适合重度用户

新手建议先订一个月Pro试试水，觉得好用再考虑API。

### Q7：隐私安全

- 你的笔记内容会发送到Anthropic（或你选的AI提供商）的服务器
- 如果你对隐私很敏感，不要往笔记里放密码、密钥等敏感信息
- Claudian不开Telemetry（不会上报你的使用数据）
- 本地存储的文件都在你的笔记库里，不会外传

### Q8：不要在编辑模式大量使用AI改内容

内联编辑功能很香，但注意：AI修改是直接操作文件的。

建议先在阅读模式下让AI生成内容，确认没问题了再切换到编辑模式微调。

养成 **先审后存** 的习惯。

---

## 适合用Claudian的场景

### 场景1：日常笔记助手

你写笔记卡壳了，直接让AI帮你接下去写，不用切到浏览器。

### 场景2：整理知识库

让AI帮你把散落在各个文件夹的笔记归类、打标签、建立链接。

```Plain Text
帮我找出所有关于「AI」的笔记，给它们加上 #AI 标签
```

### 场景3：写周报/日报

```Plain Text
根据我这周写的笔记，帮我写一份周报总结
```

### 场景4：学习笔记生成

你在学一个新东西，让AI帮你整理学习大纲，生成笔记框架。

### 场景5：翻译笔记

```Plain Text
把这篇笔记翻译成英文，保持Markdown格式不变
```

---

## 最后

Claudian这个插件，本质上是**把AI的能力直接嵌入到了你每天用的笔记工具里**。

以前你想让AI帮你写东西，流程是这样的：

> 写提示词 → 复制到ChatGPT → 等回复 → 复制回来 → 贴到笔记里 → 调整格式

现在流程变成了：

> 在Obsidian里直接说「帮我写」

就是这么简单。

如果你已经在用Obsidian做知识管理，Claudian值得一试。

唯一需要注意的就是：**第一步装Claude Code的时候别放弃**，跨过那个坎，后面就很顺畅了。

**觉得有用的话，收藏转发，让更多人看到。**

---

**作者信息**

- 作者：醒醒
- 网站：[https://xingxing.aigongxue.cfd/](https://xingxing.aigongxue.cfd/)
- 邮箱：[2430486030@qq.com](mailto:2430486030@qq.com)

---

AI这东西，不怕你不会，就怕你学错了方向。

很多人一上来就追热点、囤工具，结果越学越懵。

其实搞懂底层逻辑，比收藏100个工具有用得多。

关注我，少走弯路，用正确的方式拥抱AI。

👇👇👇

【此处插入公众号账号卡片】

---

*觉得有用就点个赞、在看吧，下次被AI概念绕晕的时候回来看看。*