# CISpir 安装与使用指南

**CISpir** 是一款 Chrome 浏览器插件，可以将 YouTube 视频字幕一键保存为 Anki 学习卡片，支持音频抓取、AI 翻译、语法分析等功能，是语言学习者的利器。

---

## 目录

1. [准备工作](#准备工作)
2. [安装 Anki 桌面版](#安装-anki-桌面版)
3. [安装 AnkiConnect 插件](#安装-ankiconnect-插件)
4. [安装 CISpir 浏览器插件](#安装-cispir-浏览器插件)
5. [配置 AI API 密钥](#配置-ai-api-密钥)
6. [使用方法](#使用方法)
7. [常见问题](#常见问题)

---

## 准备工作

在开始之前，请确保你有：

- 一台电脑（Windows / macOS / Linux 均可）
- 一个基于 Chromium 的浏览器（推荐 **Google Chrome** 或 **Microsoft Edge**）
- （可选）一个 AI 服务商的 API 密钥，用于翻译和语法分析功能

---

## 安装 Anki 桌面版

CISpir 依赖于 **Anki** 桌面版来存储和管理学习卡片。Anki 是一款免费、开源的间隔重复记忆（Spaced Repetition）软件，广泛用于语言学习、考试备考等场景。

> ⚠️ **重要**：必须安装 **桌面版** Anki（电脑上的应用程序）。Web 版（ankiweb.net）和手机版（AnkiMobile/AnkiDroid）不支持 AnkiConnect 插件，无法与 CISpir 配合使用。

### 下载与安装

1. 打开 Anki 官方网站：**[https://apps.ankiweb.net/](https://apps.ankiweb.net/)**

2. 根据你的操作系统，选择对应的版本下载：

   | 操作系统 | 操作说明 |
   |---------|---------|
   | **Windows** | 点击 **Download for Windows**（支持 Windows 10 / 11） |
   | **macOS** | 点击 **Download for Mac**（同时支持 Intel 芯片和 Apple Silicon M 系列芯片） |
   | **Linux** | 点击 **Download for Linux**（提供 `.deb`、`.tar.zst` 等格式） |

3. 下载完成后，按照常规方式安装：

   - **Windows**：双击下载的 `.exe` 安装文件，按照安装向导的提示一步步操作即可。
   - **macOS**：双击 `.dmg` 文件，在弹出窗口中把 Anki 图标拖入 **Applications（应用程序）** 文件夹。
   - **Linux**：
     - Debian/Ubuntu 用户：`sudo apt install ./anki-*.deb`
     - 其他发行版：解压 `.tar.zst` 后运行 `./anki`

4. 安装完成后，**打开 Anki**。你会看到 Anki 的主界面，默认已有一个名为「默认」的牌组。

> 💡 **小提示**：建议注册一个免费的 AnkiWeb 账号（在 Anki 中点击 **工具 → 设置 → 同步** 或点击右上角的 **同步** 按钮），这样可以把你电脑上的学习进度同步到手机端（手机端需单独下载 Anki 应用）。

---

## 安装 AnkiConnect 插件

**AnkiConnect** 是 Anki 的一个插件（Add-on），它的作用是在电脑本地开启一个网络接口（`http://localhost:8765`），让 CISpir 这类外部工具能够把卡片写入 Anki。这是 CISpir 能够正常工作的**关键桥梁**，必须安装。

### 安装步骤

1. **打开 Anki 桌面应用**（确保 Anki 正在运行）。

2. 在顶部菜单栏中点击 **工具**（Tools）→ **插件**（Add-ons）。

   > 如果你使用的是英文版 Anki，菜单路径为：**Tools → Add-ons**。

3. 在弹出的「插件」窗口中，点击右上角的 **获取插件…**（Get Add-ons…）按钮。

4. 在弹出的输入框中，输入 AnkiConnect 的插件代码：

   ```
   2055492159
   ```

   > 这个数字是 AnkiConnect 在 Anki 官方插件库中的唯一编号。你也可以在 [ankiweb.net/shared/info/2055492159](https://ankiweb.net/shared/info/2055492159) 查看该插件的详情页面。

5. 点击 **OK**（确定），Anki 会自动下载并安装 AnkiConnect。

6. 安装成功后，插件列表中会显示 **AnkiConnect**。**关闭 Anki 并重新打开**，插件才能生效。

### 验证安装是否成功

重新打开 Anki 后，打开浏览器，在地址栏输入以下地址并回车：

```
http://localhost:8765
```

如果页面显示类似以下内容：

```json
{"result": null, "error": "must be a POST request"}
```

说明 AnkiConnect 已正常运行！CISpir 会自动检测到这个服务，侧边栏顶部将显示绿色的 **Anki ✓** 状态。

> 如果浏览器提示「无法访问此网站」或连接失败，请检查：
> - Anki 是否正在运行
> - AnkiConnect 是否已正确安装（Anki → 工具 → 插件列表中有没有 AnkiConnect）
> - 是否重启了 Anki

---

## 安装 CISpir 浏览器插件

### 方式一：从 Chrome 应用商店安装（推荐，即将上线）

CISpir 即将上架 Google Chrome 应用商店（Chrome Web Store）。上架后，安装将变得非常简单：

1. 打开 [Chrome 应用商店](https://chromewebstore.google.com/)
2. 搜索 **CISpir**
3. 点击 **添加到 Chrome**（Add to Chrome）
4. 在弹出的确认窗口中点击 **添加扩展程序**

安装完成后浏览器工具栏会自动出现 CISpir 图标，无需任何额外配置。后续插件更新也会自动推送，无需手动操作。

> ⏳ 目前商店上架审核流程进行中。在上架完成前，请使用下面的方式二或方式三安装。

---

### 方式二：加载已解压的扩展（推荐当前使用）

直接加载项目中的 `dist` 文件夹，无需安装任何开发工具。

首先你需要获取插件文件：

1. 访问 [github.com/smith0814666/CISpir-anki-extenstion](https://github.com/smith0814666/CISpir-anki-extenstion)
2. 点击绿色的 **Code** 按钮 → 选择 **Download ZIP**
3. 下载完成后，**解压 ZIP 文件**到你电脑上的任意位置（比如桌面）
4. 确认解压后的文件夹里有 `dist` 这个子文件夹。

然后加载到浏览器：

5. 打开 Chrome / Edge 浏览器
6. 在地址栏输入 **`chrome://extensions/`** 并回车
7. 在页面的右上角，打开 **开发者模式**（Developer mode）开关
8. 点击左上角的 **加载已解压的扩展程序**（Load unpacked）
9. 在弹出的文件选择窗口中，找到刚才解压的文件夹，选择里面的 **`dist`** 子文件夹，点击「选择」
10. 加载成功！浏览器工具栏右上角会出现 CISpir 的图标。

### 方式三：从源码构建（需要 Node.js）

如果你熟悉命令行工具，可以从源码构建：

1. 安装 Node.js（如未安装）：
   - 访问 **[https://nodejs.org/](https://nodejs.org/)**
   - 下载 **LTS 版本**（长期支持版）
   - 按照安装向导完成安装

2. 打开终端（Terminal）或命令提示符（CMD），依次运行：

   ```bash
   # 克隆代码仓库
   git clone https://github.com/smith0814666/CISpir-anki-extenstion.git

   # 进入项目目录
   cd CISpir-anki-extenstion

   # 安装项目依赖
   npm install

   # 构建插件
   npm run build
   ```

3. 构建完成后，终端会显示：

   ```
   ✓ manifest.json
   ✓ icons
   ✓ sidepanel/index.html
   ✓ settings/index.html

   ✅ Extension ready at dist/
   → chrome://extensions → Developer mode → Load unpacked → select dist/
   ```

4. 然后按照方式一的第 5~10 步加载 `dist` 文件夹到浏览器。

### 固定图标到工具栏

为了方便以后使用，建议把 CISpir 固定在浏览器工具栏：

1. 点击浏览器右上角的 **🧩 拼图图标**（扩展程序菜单）
2. 在列表中找到 **CISpir**
3. 点击旁边的 **📌 图钉按钮**，CISpir 图标就会常驻在工具栏上

---

## 配置 AI API 密钥

CISpir 的 AI 翻译、语法分析和视频摘要功能，需要你提供一个 AI 服务商的 API 密钥。支持以下四家服务商，**任选一个配置即可**：

| 服务商 | 获取密钥地址 | 推荐模型 | 费用参考 |
|--------|------------|---------|---------|
| **Google AI** | [aistudio.google.com/apikey](https://aistudio.google.com/apikey) | `gemini-2.0-flash` | 🆓 有免费额度 |
| **DeepSeek** | [platform.deepseek.com/api_keys](https://platform.deepseek.com/api_keys) | `deepseek-chat` | 💰 价格低廉 |
| **OpenAI** | [platform.openai.com/api-keys](https://platform.openai.com/api-keys) | `gpt-4o-mini` | 💰 按量付费 |
| **Anthropic** | [console.anthropic.com/keys](https://console.anthropic.com/keys) | `claude-sonnet-5-20251001` | 💰 按量付费 |

> 💰 **省钱建议**：新手推荐从 **Google AI（Gemini）** 开始，其 `gemini-2.0-flash` 模型目前提供免费额度，无需绑定信用卡即可使用。如果需要更好的翻译质量，可以考虑 DeepSeek 或 OpenAI。

### 获取 API 密钥示例（以 Google AI 为例）

1. 打开 [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
2. 登录你的 Google 账号
3. 点击 **Create API Key**（创建 API 密钥）
4. 选择 **Create API key in new project**（在新项目中创建）
5. 复制生成的 API 密钥（一串以 `AIza` 开头的字符）
6. 在 CISpir 设置中填入这个密钥

### 填入 CISpir

1. 点击浏览器工具栏的 **CISpir 图标**，打开侧边栏
2. 点击侧边栏右上角的 ⚙ **齿轮图标**，进入设置页面
3. 找到你申请了密钥的服务商卡片，点击展开
4. 在 **API Key** 输入框中粘贴你的密钥
5. 点击页面右上角的 **Save** 按钮保存

> 🔒 **安全说明**：所有 API 密钥均经过加密（AES-GCM）存储在浏览器本地，不会上传到任何第三方服务器。CISpir 没有后端服务器，所有 AI 请求直接从你的浏览器发送到 AI 服务商。详见[隐私政策](./PRIVACY.md)。

---

## 使用方法

CISpir 的核心使用流程非常简单：

```
① 打开 YouTube 视频 → ② 打开 CISpir 侧边栏 → ③ 加载字幕 → ④ 点击 ☆ 保存句子到 Anki
```

### 第一步：打开 YouTube 视频

用浏览器打开任意一个 **带有字幕** 的 YouTube 视频。大部分 YouTube 视频都有自动生成的字幕（ASR），你也可以选择有人工字幕的视频以获得更好的体验。

### 第二步：确保 Anki 正在运行

在开始之前，请确认 **Anki 桌面应用已经在后台运行**。CISpir 侧边栏顶部会显示 Anki 的连接状态：

| 状态 | 含义 |
|------|------|
| 🟢 **Anki ✓** | 已连接，可以正常使用 |
| 🟡 **Anki …** | 正在检查连接中 |
| 🔴 **Anki ✗** | 未连接——请检查 Anki 是否打开、AnkiConnect 是否安装 |

如果显示未连接，点击它可以重试连接。

### 第三步：打开 CISpir 侧边栏

点击浏览器工具栏上的 **CISpir 图标**，浏览器右侧会弹出一个侧边栏面板。

### 第四步：选择设置并加载字幕

在侧边栏中你会看到：

- **字幕语言选择**：选择你要学习的字幕语言（会自动推荐最佳选项）
- **翻译目标语言**（Translate to）：选择句子翻译的目标语言，支持 15 种语言：
  中文（简体/繁體）、English、日本語、한국어、Français、Deutsch、Español、Português、Русский、العربية、हिन्दी、ไทย、Tiếng Việt、Bahasa Indonesia

设置好后，点击 **Load Captions**（加载字幕）按钮。加载完成后，所有句子会以列表形式显示。

### 第五步：浏览和交互

字幕加载后，你可以进行以下操作：

| 操作 | 怎么做 |
|------|--------|
| **播放某句话** | 点击句子 → 视频自动跳转并播放 |
| **上一句 / 下一句** | 点击底部 ⏮ ⏭ 按钮，或直接按键盘 **← →** 方向键 |
| **单句循环** | 点击底部 🔄 按钮，当前句子反复播放，直到你再次点击关闭 |
| **调整播放速度** | 底部右侧下拉菜单，选择 0.5x ~ 2x 速度 |
| **查单词** | 在字幕文字上**选中（拖蓝）一个单词**，会自动弹出 AI 翻译弹窗，显示释义、读音和词性 |

### 第六步：保存句子到 Anki

每条句子的左侧有一个 **☆（空心星标）** 按钮：

1. 点击 **☆** → 按钮开始旋转（正在保存）→ 变成实心 **★**（保存成功）
2. 每条句子保存时会自动：
   - 📝 保存原文句子
   - 🔊 截取该句的音频片段
   - 🌐 附带 AI 翻译（如果已翻译）
   - 📖 附带语法分析（如果已分析）
   - 🔗 附带 YouTube 视频链接和时间戳

打开 Anki，你就能在 **CISpir** 牌组中看到你保存的卡片了！已保存过的句子会显示为实心 ★，不会重复保存。

### AI 高级功能

以下功能需要先[配置 AI API 密钥](#配置-ai-api-密钥)：

| 功能 | 按钮 | 说明 |
|------|------|------|
| **全文翻译** | 🌐 | AI 批量翻译所有字幕行 |
| **语法分析** | 📖 | 分析句子语法结构、标注假名/拼音、拆解成分 |
| **视频摘要** | 📄 | AI 生成视频内容摘要、提取关键词汇、评估难度级别 |

---

## Anki 卡片说明

CISpir 自动在 Anki 中创建名为 **「CISpir」** 的笔记类型，包含以下信息：

| 字段 | 内容 |
|------|------|
| Text | 源语言句子 |
| Translation | 翻译文本 |
| Reading | 带假名/拼音标注的阅读版本 |
| Audio | 截取的音频片段 |
| TargetWord | 目标学习词汇 |
| WordReading | 词汇发音 |
| Definition | 词汇释义 |
| Explanation | 语法说明 |
| Source | 视频标题、链接和时间戳 |

卡片采用**深色主题设计**，同时兼容 Anki 的日间模式。正面显示音频或句子（供你回忆），背面展示完整信息（翻译、词汇、语法、来源）。

---

## 常见问题

### ❓ Anki 连接失败（显示 Anki ✗）

**按顺序检查：**
1. Anki 桌面应用是否正在运行？
2. AnkiConnect 插件是否已安装？在 Anki 菜单：**工具 → 插件**，列表中应有 "AnkiConnect"
3. 是否在安装 AnkiConnect 后重启了 Anki？
4. 打开浏览器访问 `http://localhost:8765` 看看是否有响应
5. 检查防火墙/安全软件是否阻止了 8765 端口

都确认无误但仍连不上？试试在 CISpir 侧边栏点击红色的 Anki ✗ 按钮手动重连。

### ❓ 点击 Load Captions 后报错或没有字幕

- 确认该视频确实有字幕（YouTube 播放器右下角是否有 CC 按钮）
- 尝试 **刷新 YouTube 页面** 后重试
- 部分视频可能限制了第三方访问字幕数据，这是 YouTube 的限制，无法绕过

### ❓ 保存卡片时提示"重复"

CISpir 会自动检测重复句子，避免同一句保存多次。这是正常行为。如果你确实需要再次保存，可以在 Anki 中手动复制已有卡片。

### ❓ 没有 AI API 密钥能用吗？

**可以！** 即使没有配置 API 密钥，你仍然可以：
- ✅ 加载字幕
- ✅ 截取音频
- ✅ 保存句子到 Anki

但以下功能不可用：
- ❌ 句子翻译
- ❌ 语法分析
- ❌ 视频摘要
- ❌ 选中单词的翻译弹窗

建议申请 Google Gemini 的免费 API 密钥，零成本启用所有 AI 功能。

### ❓ 支持哪些浏览器？

| 浏览器 | 支持情况 |
|--------|---------|
| Google Chrome 114+ | ✅ 完全支持 |
| Microsoft Edge 114+ | ✅ 完全支持 |
| Brave | ✅ 完全支持 |
| Arc | ✅ 完全支持 |
| 其他 Chromium 浏览器 | ✅ 一般可用 |
| Firefox | ❌ 不支持（缺少 sidePanel API） |
| Safari | ❌ 不支持（清单版本不兼容） |

### ❓ 每次打开浏览器都会弹出"开发者模式"警告？

这是 Chrome 对开发者模式加载的扩展程序的例行提示，点击 **×** 关闭即可，不影响插件功能。

### ❓ 如何删除或重命名 Anki 牌组？

在 Anki 桌面应用中直接操作即可：右键点击牌组名称 → **重命名** 或 **删除**。CISpir 会在下次保存时自动创建你指定的牌组。

### ❓ 卡片样式可以自定义吗？

可以！打开 Anki → 工具 → 管理笔记类型 → 找到 **CISpir** → 点击 **卡片…**，在这里你可以编辑卡片的 HTML 模板和 CSS 样式。

---

## 反馈与支持

- 📦 GitHub 仓库：[github.com/smith0814666/CISpir-anki-extenstion](https://github.com/smith0814666/CISpir-anki-extenstion)
- 🐛 遇到 Bug 或有问题？请在 GitHub 提交 [Issue](https://github.com/smith0814666/CISpir-anki-extenstion/issues)

---

**祝学习愉快！🎓**
