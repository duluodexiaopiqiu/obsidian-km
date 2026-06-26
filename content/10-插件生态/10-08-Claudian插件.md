# 5. Claudian插件

## 注意

作者推荐node安装



```YAML
type: tutorial
status: 草稿
```

## 一句话理解 Claudian

**Claudian 是 Obsidian 里的 Claude AI 助手。** 它把你的 Obsidian 知识库变成 Claude 的"工作区"，你可以在笔记右侧直接和 Claude 对话，让它帮你读笔记、写笔记、改笔记、整理文件，甚至用自然语言命令它管理整个知识库。

本文教你：**从零开始，在 Obsidian 里安装并使用 Claudian 插件，让它成为你的 AI 知识库助手。**

---

## 重要前提： Claudian 适合你吗？

在动手之前，先确认自己是否符合以下条件。 Claudian 对新手**有一定门槛**，如果条件不满足，后面会卡壳。

### 必须具备的条件

<sheet sheet-id="jMv33o" token="DIcXsUVAPhnhePtCw5HcPUgMnbd"></sheet>

> ⚠️ **核心门槛**：Claudian 不是一个独立的 AI 聊天插件，它必须依赖电脑上安装的 **Claude Code CLI** 才能工作。装插件之前，必须先装好 CLI。这一点和别的 AI 插件（比如直接填 API key 就能用的插件）不一样。

### 如果你是以下情况，建议先用其他 AI 插件

<sheet sheet-id="bKugDH" token="DIcXsUVAPhnhePtCw5HcPUgMnbd"></sheet>

> 💡 **一句话判断**：如果你愿意为了"让 AI 自动管理整个 Obsidian 知识库"而付出一点学习成本，Claudian 值得折腾；如果你只是想"在 Obsidian 里偶尔问问 AI"，用普通 AI 插件更简单。

---

## Claudian 能做什么

Claudian 的核心能力可以分成四类：

### 侧边栏 AI 对话

在 Obsidian 右侧打开一个聊天窗口，和 Claude 实时对话。可以中途打断、多标签页、历史会话、分支会话。

### 直接读写你的笔记

Claudian 可以读取你的 `.md` 文件、搜索内容、创建新笔记、修改现有笔记。你的整个知识库就是它的"上下文"。

### 行内编辑（Inline Edit）

选中笔记里的一段文字，按快捷键，Claudian 会直接在原地帮你润色、翻译、扩写、缩写，并显示修改对比。

### 斜杠命令和技能（Slash Commands / Skills）

输入 `/` 或 `$` 调用预设的 Prompt 模板，或加载你自定义的"技能"，让重复任务一键完成。

### @ 引用任意内容

输入 `@` 可以引用知识库文件、子代理、MCP 服务器、外部目录文件，让 AI 基于指定内容作答。

### 计划模式（Plan Mode）

按 `Shift + Tab` 切换到计划模式，Claudian 会先分析需求、给出执行计划，等你确认后再动手改文件。

---

## 安装前准备：安装 Claude Code CLI

这是 Claudian 最让新手头疼的一步。请按顺序操作，不要跳过。

安装 Claude Code CLI 有两条路：

<sheet sheet-id="1MXtyK" token="DIcXsUVAPhnhePtCw5HcPUgMnbd"></sheet>

> 💡 **新手建议**：如果不知道怎么选，直接走**方案 A 原生安装**，不用装 Node.js，步骤最少。

### 方案 A：原生安装（推荐，不需要 Node.js）

1. 访问 Anthropic 官方文档：[code.claude.com](https://code.claude.com/docs/en/overview)
2. 找到对应你系统（Windows / macOS / Linux）的安装包
3. 下载并运行安装程序
4. 按提示完成安装（通常一路"下一步"即可）

**原生安装完成后，直接跳到下方「验证 Claude Code」**，不需要安装 Node.js。

---

### 方案 B：通过 npm 安装（需要先装 Node.js）

如果你选择用 npm 安装，必须先装 Node.js。以下是 Node.js 的安装步骤：

#### 第一步：下载并安装 Node.js

1. 访问 Node.js 官网：[nodejs.org](https://nodejs.org/)
2. 你会看到两个版本： 

   - **LTS（长期支持版）**—— 推荐选这个，更稳定
   - Current（最新版）—— 不推荐新手选
3. 点击 LTS 版本下载按钮（Windows 用户选择 `.msi` 安装包）
4. 运行下载的安装程序，一路点"下一步"
5. 安装程序会帮你把 Node.js 添加到系统 PATH 中（默认勾选，不要取消）

> ⚠️ **注意**：安装过程中有一个步骤叫"Add to PATH"，**务必保持勾选**，否则后面终端里找不到 `npm` 命令。

#### 第二步：验证 Node.js 安装成功

打开终端（Windows 按 `Win + R` → 输入 `cmd` → 回车），分别输入：

```Bash
node --version
npm --version
```

如果显示版本号（例如 `v22.10.0` 和 `10.x.x`），说明安装成功。

> ⚠️ **如果提示 'node' 不是内部或外部命令**：说明安装时没勾选"Add to PATH"，需要重启电脑，或者重新运行安装程序并勾上。

#### 第三步：用 npm 安装 Claude Code CLI

确认 Node.js 装好后，在终端执行：

```Bash
npm install -g @anthropic-ai/claude-code
```

等待安装完成（可能需要几分钟）。安装成功后，验证一下：

```Bash
claude --version
```

如果显示版本号，说明 Claude Code CLI 安装成功。

### 验证 Claude Code 能正常工作

在终端输入：

```Bash
claude
```

如果能进入 Claude 交互界面，说明 CLI 安装成功。

> ⚠️ **注意**：Claude Code 需要登录 Anthropic 账号并处于订阅状态。如果提示未登录或没有权限，先解决账号问题，再回头装 Claudian。

---

## 在 Obsidian 里安装 Claudian 插件

### 第一步：打开社区插件

1. 打开 Obsidian
2. 点击左下角 **设置**（齿轮图标）
3. 左侧选择 **社区插件**
4. 确保右上角 **安全模式** 已关闭（按钮显示为灰色/已关闭）

> 如果安全模式是开启的，点击按钮关闭它。关闭后会提示你风险，点击确认即可。

### 第二步：搜索并安装 Claudian

1. 在社区插件页面，点击 **浏览**
2. 搜索框输入：`Claudian`
3. 找到 **Claudian**（作者 YishenTu，插件 ID 为 `realclaudian`）
4. 点击 **安装**
5. 安装完成后，点击 **启用**

### 第三步：确认侧边栏出现 Claudian 图标

启用后，Obsidian 左侧功能区会出现一个 Claudian 图标（通常是一个对话气泡或机器人图标）。点击它会在右侧打开 Claudian 侧边栏。

如果没有图标，可以按 `Ctrl + P` 打开命令面板，搜索 `Claudian` 查看相关命令。

---

## 配置 Claudian

### 基础配置

1. 打开 Obsidian 设置
2. 左侧找到 **Claudian**（在社区插件分类下）
3. 点击打开设置面板

### 关键设置项说明

<sheet sheet-id="Rcnxme" token="DIcXsUVAPhnhePtCw5HcPUgMnbd"></sheet>

### 自动检测失败怎么办？

如果插件提示 "Claude CLI not found" 或 `spawn claude ENOENT`，说明插件没找到你的 Claude Code CLI。需要手动指定路径。

#### 如何找到 Claude CLI 路径

**Windows（原生安装）：**

```PowerShell
where.exe claude
```

典型路径示例：

```Plain Text
C:\Users\你的用户名\AppData\Local\Claude\claude.exe
```

**Windows（npm 安装）：**

```PowerShell
npm root -g
```

然后找到：

```Plain Text
全局 node_modules\@anthropic-ai\claude-code\cli-wrapper.cjs
```

**macOS / Linux：**

```Bash
which claude
```

典型路径：

```Plain Text
/Users/你的用户名/.volta/bin/claude
```

找到路径后，复制到 Claudian 设置的 **Claude CLI 路径** 中。

> ⚠️ **Windows 特别注意**：不要填 `.cmd` 或 `.ps1` 文件。优先用 `claude.exe`（原生安装）或 `cli-wrapper.cjs`（npm 安装）。

### 配置环境变量（进阶）

如果你用 nvm、fnm、volta 等 Node 版本管理器，Obsidian 可能找不到 Node。需要在 Claudian 设置的环境变量中添加：

```Plain Text
PATH=/path/to/node/bin
```

把 `/path/to/node/bin` 换成你电脑上 Node.js 的实际 `bin` 目录。

---

## 基础使用：和 Claude 对话

### 打开侧边栏

1. 点击左侧功能区 Claudian 图标
2. 或者按 `Ctrl + P`，输入 `Claudian`，选择打开侧边栏

### 发送第一条消息

1. 在右侧 Claudian 面板的输入框中输入问题
2. 按回车发送
3. 等待 Claude 回复（回复会实时流式显示）

示例问题：

```Plain Text
请帮我总结这篇笔记的核心观点。
```

> 如果当前笔记处于打开状态，Claudian 通常会自动获取上下文。你也可以手动用 `@` 引用文件。

### 打断回复

如果 Claude 的回复不是你想要的，可以点击面板上的 **停止** 按钮，或者继续发送新指令覆盖。

---

## 常用功能详解

### 引用文件（@ 功能）

在输入框中输入 `@`，会弹出可引用的内容列表：

- **知识库文件**：指定某个 `.md` 文件作为上下文
- **子代理**：调用你预设的 AI 工作流
- **MCP 服务器**：连接外部工具（如浏览器、数据库等）
- **外部目录文件**：引用 Vault 外的文件

示例：

```Plain Text
请阅读 @读书笔记.md，然后帮我写一份读后感。
```

### 行内编辑（Inline Edit）

1. 在笔记中选中一段文字
2. 使用快捷键（需要在 Claudian 设置中查看或自定义）
3. 输入你的编辑指令，比如： 

   - "润色这段文字"
   - "翻译成英文"
   - "精简到 100 字"
4. 确认后，Claudian 会直接修改选中的文字，并显示修改前后的差异

> 💡 行内编辑是 Claudian 最方便的功能之一，适合改错字、润色、翻译、缩写等场景。

### 斜杠命令（/ 功能）

在输入框中输入 `/`，可以调用预设 Prompt 模板。例如：

- `/summarize`：总结当前笔记
- `/translate`：翻译内容
- `/tags`：给笔记推荐标签
- `/links`：推荐双链

> 你也可以自定义自己的斜杠命令，把重复工作变成一键操作。

### 计划模式（Plan Mode）

按 `Shift + Tab` 切换到计划模式。此时 Claudian 会先：

1. 分析你的需求
2. 列出它打算执行的操作
3. 等待你确认或修改

确认后，它才会真正修改文件。这个模式**强烈建议新手开启**，因为它能避免 AI 乱改你的笔记。

### 自定义指令（# 功能）

在输入框中输入 `#`，可以添加临时自定义指令，让 Claude 在单次对话中按你的偏好工作。

例如：

```Plain Text
# 请用中文回答，语气专业但易懂
请帮我整理这篇会议记录。
```

---

## 新手推荐的三个工作流

### 工作流 1：让 AI 帮你读笔记并写总结

1. 打开一篇笔记
2. 打开 Claudian 侧边栏
3. 输入： 

```Plain Text
请总结这篇笔记的核心观点，并列出 3 个可执行的行动建议。
```

1. 将回复复制到笔记底部，或让 Claudian 直接帮你写入新文件

### 工作流 2：批量整理笔记标签

1. 选中多篇笔记（或告诉 Claudian 某个文件夹）
2. 输入： 

```Plain Text
请阅读这些笔记，给每篇推荐 3 个标签，并解释原因。
```

1. 审阅推荐结果，手动修改标签

### 工作流 3：用自然语言管理文件

1. 输入： 

```Plain Text
请帮我把所有标题包含"待办"的笔记移动到一个新文件夹"待处理"。
```

1. 如果开启了计划模式，先确认计划
2. 让 Claudian 执行，你在旁边检查结果

> ⚠️ **重要**：任何涉及文件移动、删除、修改的操作，都建议先开启计划模式，确认无误后再执行。AI 操作不可逆，一旦文件被改错，需要你自己恢复。

---

## 新手必须知道的注意事项

### 先备份，再折腾

Claudian 有能力直接修改、删除你的笔记。在正式使用之前，**务必先做好备份**。

推荐做法：

- 使用 Git 版本控制（可以精确回退到任何一次提交）
- 或使用坚果云 / Obsidian Sync 等同步服务
- 至少先复制一份 Vault 到别处

> 如果你还没做好备份，先去看 5.obsidian如何备份，再回来装 Claudian。

### 开启计划模式，避免 AI 误操作

默认情况下，Claudian 可能会直接执行你的命令。新手强烈建议：

- 每次使用前按 `Shift + Tab` 开启计划模式
- 在设置中开启"需要确认"相关选项（如果有）
- 不要一次性让 AI 处理大量文件

### 注意 API 费用

Claudian 调用 Claude 会产生费用。虽然单次对话通常不贵，但以下情况会快速消耗额度：

- 一次性处理大量长笔记
- 反复让 AI 生成大量内容
- 开启 Agent 模式做复杂任务

> 💡 建议：新手先用少量、短笔记测试，熟悉后再处理大量内容。

### 不要给 AI 敏感信息

虽然你的笔记本地存储，但 Claudian 会把你引用的内容发送给 Claude 的 API。因此：

- 不要把包含密码、身份证、银行卡等敏感信息的笔记发给 AI
- 不要上传涉密文件
- 在团队中使用时，注意公司数据保密政策

### 网络要稳定

Claudian 依赖 Claude 的在线服务。如果网络不稳定，会出现：

- 回复中断
- 命令执行失败
- 插件报错

> 如果你在国内使用，可能需要稳定的网络环境。否则响应速度和稳定性都会受影响。

### 插件只支持桌面端

Claudian **不支持 iOS 和 Android**。手机和平板上无法使用。

### Claude Code 和 Claudian 是两个东西

- **Claude Code**：Anthropic 官方的命令行 AI 工具，在终端运行
- **Claudian**：Obsidian 的插件，把 Claude Code 嵌入到 Obsidian 里

很多人混淆这两个。记住：装 Claudian 之前必须先装好 Claude Code CLI。

---

## 常见问题排查

### 问题 1：提示 "Claude CLI not found"

**原因**：Claudian 找不到你的 Claude Code CLI。

**解决**：

1. 先在终端确认 `claude` 命令能运行
2. 如果终端能运行，但 Obsidian 里找不到，说明 PATH 问题
3. 在 Claudian 设置中手动填写 Claude CLI 的完整路径
4. 如果用了 Node 版本管理器，在环境变量中添加 Node 的 bin 目录

### 问题 2：发送消息后没有回复

**原因**：可能是网络问题、账号权限问题，或 Claude Code 没有正确启动。

**解决**：

1. 检查网络是否能访问 Claude 服务
2. 检查 Claude Code 账号是否有效、是否有额度
3. 重启 Obsidian
4. 在终端单独运行 `claude`，确认 CLI 本身正常

### 问题 3： Claudian 乱改了我的笔记

**原因**：可能你没有开启计划模式，或误发了修改命令。

**解决**：

1. 立刻用备份恢复（这就是为什么必须先备份）
2. 以后开启计划模式
3. 对不确定的命令，先让 Claude 描述它会做什么，确认后再执行

### 问题 4：行内编辑没有反应

**原因**：可能没有正确选中文字，或快捷键未生效。

**解决**：

1. 确保先选中一段文字，再调用命令
2. 检查 Claudian 快捷键设置是否冲突
3. 用命令面板（Ctrl + P）搜索 Claudian 行内编辑命令手动执行

### 问题 5：侧边栏显示空白或卡住

**原因**：可能是插件加载异常。

**解决**：

1. 关闭并重新打开侧边栏
2. 在设置中禁用再重新启用 Claudian
3. 重启 Obsidian
4. 如果问题持续，考虑重新安装插件

---

## Claudian 和其他 AI 插件的对比

<sheet sheet-id="tEJ5Nv" token="DIcXsUVAPhnhePtCw5HcPUgMnbd"></sheet>

> 如果你只是想在 Obsidian 里偶尔调用 AI 润色文字，普通 AI 插件可能更简单；如果你想要一个能帮你整理、管理、改写整个知识库的 AI 助手，Claudian 更值得投入。

---

## 给新手的建议

1. **不要一上来就让它操作大量文件**。先用 1-2 篇笔记测试，熟悉它的行为模式。
2. **备份是底线**。任何 AI 插件都有误操作风险，备份不是可选项，是必选项。
3. **多用计划模式**。尤其是涉及文件增删改的操作，一定要让 AI 先给计划，你确认后再执行。
4. **从小任务开始**。比如："总结这篇笔记"、"给这篇笔记推荐 3 个标签"、"翻译这段文字"。等熟练后再尝试复杂任务。
5. **学会用 @ 引用**。明确告诉 AI 它要处理哪些文件，能大幅提升结果质量。
6. **关注 API 费用**。不要让它无限制地处理大量长文档，先估算一下消耗。

---

## 小练习

1. 确认你的 Obsidian 版本是否在 v1.7.2 以上，且是桌面版。
2. 在终端输入 `claude --version`，确认 Claude Code CLI 已安装。
3. 在 Obsidian 社区插件中安装并启用 Claudian。
4. 打开一篇你最熟悉的笔记，对 Claudian 说："请总结这篇笔记的核心内容。"
5. 尝试用 `@` 引用一篇文件，然后让它基于该文件回答一个问题。
6. 选中一段文字，尝试一次行内编辑（如润色或翻译）。
7. 测试一次计划模式：让 Claudian 计划如何整理你的一个文件夹，但不要执行，只看它的计划是否合理。

---

**上一节：**5.obsidian如何备份 **下一节：**7.Obsidian多设备同步指南