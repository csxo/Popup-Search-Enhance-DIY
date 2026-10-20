# Popup Search Enhance DIY

> 选中文本弹出快捷搜索、即时翻译与多引擎聚合检索的现代化划词工具箱油猴脚本（Userscript）。  
> 增强定制版本由 [csxo](https://github.com/csxo/) 维护开发，基于 [Lkytal](https://github.com/lkytal/) 的开源脚本 Popup Search 进行现代化重构。

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](https://github.com/csxo/)
[![License](https://img.shields.io/badge/license-AGPL--3.0--or--later%20%7C%20CC%20BY--NC--SA%204.0-green.svg)](http://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Script Handler](https://img.shields.io/badge/support-Tampermonkey%20%7C%20Violentmonkey%20%7C%20ScriptCat-orange.svg)](#-安装与使用)
[![Author](https://img.shields.io/badge/author-csxo%20%26%20lkytal-0078D4.svg)](https://github.com/csxo/)

---

## 🌟 新版特性 / New Features (by [csxo](https://github.com/csxo/))

相比原版，本增强版针对**界面视觉**、**空间布局**、**引擎管理交互**以及**前台划词体验**进行了深度重构与全面优化：

### 1. 极简长方形设置面板（支持自由拖拽调节大小）
- **长方形宽屏视野**：打破原版顶天立地的细长界面，重构为黄金比例的宽屏长方形视窗，界面开阔舒适。
- **手动拖拽缩放窗口**：窗口右下角内置原生平滑拖拽手柄（`#popup_resize_handle`），鼠标按住即可随时自由调整设置窗口的宽和高（支持范围 720px~96vw），自适应不同分辨率与缩放比例的屏幕。
- **现代化视觉重塑**：采用亚克力毛玻璃背景遮罩、微阴影、圆角卡片、平滑的现代切换开关（Toggle Switch）与 Fluent 蓝品牌色，彻底告别老式的粗黑边框与生硬大色块。

### 2. 搜索引擎卡片式多列网格排版 & 卡片内集成添加入口
- **多列网格布局**：告别单列漫长垂直滚动的旧设计，改为**每行 2~3 个卡片的响应式网格布局**，页面空间利用率大幅提升。
- **添加卡片无缝并入网格**：添加自定义搜索引擎的入口直接做成**与上方引擎卡片样式一致的虚线卡片**，作为网格末尾的一项自然排列，无需另起一行，界面整洁统一。

### 3. 原生拖拽排序 (Drag & Drop)
- 每个引擎卡片左侧均配备拖拽手柄（`⋮⋮`）。按住即可在网格内**自由拖拽调整前后顺序**。
- 排序结果实时持久化存储，并**完全同步至前台网页划词悬浮窗的图标顺序**，想把哪个引擎放前面随心所欲。

### 4. 自定义前台快捷操作按钮展示数量 & Fluent 步进器
在设置面板「搜索引擎」顶部提供专用的前台展示控制面板，支持三种模式：
1. **默认模式**：优先展示前 **8** 个已开启的搜索引擎，通过滚轮滑动选择其他引擎；
2. **全部展示模式**：直接展开所有已开启的搜索引擎，不限制悬浮栏宽度；
3. **自定义展示数量模式**：允许用户自由设定前台悬浮窗显示的按钮数量，配备精致的 Fluent 步进器组件 `[ − ]  8  [ + ] 个按钮`（彻底去除浏览器默认的原生黑方块箭头，支持点击加减或键盘直接键入）。

### 5. 精简前台划词悬浮条 & 鼠标滚轮横向丝滑翻页
- **紧凑尺寸**：前台选中文本后弹出的搜索工具栏宽度默认精简至**最多展示 8 个核心引擎图标**（或根据自定义数量展示），避免悬浮栏过长遮挡网页阅读视线。
- **滚轮横向丝滑滑动**：鼠标悬停在悬浮栏上时，**直接滑动鼠标滚轮（上下滚即可转换为横向平滑滚动）**，即可轻松滑出并选用后续的全部引擎及自定义引擎！
- **悬浮条质感升级**：悬浮工具栏升级为微毛玻璃渐变阴影卡片与鼠标悬浮微放大动效，精致不突兀。

### 6. 可视化一键添加自定义引擎
- **移除生硬的 JSON 编辑框**：彻底去掉复杂易出错的代码文本框。
- **点击卡片直接弹出表单**：点击网格中的「➕ 添加自定义引擎」卡片，即可唤起优雅的可视化弹窗。
- **带占位参考样式与快捷动态标签**：输入框内置贴心的参考示例（如 GitHub 搜索等），并提供可一键点击插入的动态参数小药丸标签（`${text}`、`${rawText}`、`${domain}`、`${url}`）。
- **支持快捷删除**：自定义卡片自带删除按钮，随时管理自己专属的引擎库。

### 7. 开源协议严格与原作者保持一致
- 本版本完整保留原作者声明与开源许可类型，现版本同样以 **AGPL-3.0-or-later** 与 **CC BY-NC-SA 4.0** 双协议发布，严格遵从开源社区约定。

---

## ⚡ 原版核心特性 / Original Features (by [Lkytal](https://github.com/lkytal/))

本脚本继承了原作者 [Lkytal](https://github.com/lkytal/) 优秀的架构与经典功能：

- **划词即显与智能物理像素定位**：
  - 网页中选中文本后自动触发，采用临时节点精确定位算法，根据视口和滚动条位置智能调整弹窗在选区上方或下方，并自带防溢出边界检测。
  - 支持普通文本与 `<input>` / `<textarea>` / `contenteditable` 输入框的双轨选区兼容。
- **多引擎聚合检索**：
  - 内置数十种常用检索服务：Google、Bing、百度、维基百科、YouTube、淘宝、京东、豆瓣电影、Amazon、eBay、汉典、站内搜索（`site:${domain}`）、直接打开链接（`Open As Url`）等。
  - 支持 `${text}`、`${domain}` 等多变量模版替换。
- **内置即时划词翻译面板**：
  - 点击翻译按钮直接在悬浮窗下方就地展开翻译面板，支持 Google 翻译（词性、音标、释义拆解）及 DeepL 翻译。
- **剪贴板操作与自动复制**：
  - 一键复制所选文本；支持设置“选中文本后自动复制到剪贴板”。
- **快捷键支持与触发控制**：
  - 支持设置“仅在按住 Ctrl 键时触发划词”，减少普通选词时的打扰。
  - 快捷键 `Ctrl + Alt + P` 强制手动唤出。
  - 快捷键 `Esc` 快速关闭悬浮窗。

---

## 📦 安装与使用

### 1. 前置依赖
在浏览器安装任意一款主流脚本管理器：
- [Tampermonkey (篡改猴)](https://www.tampermonkey.net/)
- [Violentmonkey (暴力猴)](https://violentmonkey.github.io/)
- [ScriptCat (脚本猫)](https://scriptcat.org/)

### 2. 安装脚本
- 打开页面：[https://greasyfork.org/zh-CN/scripts/601177-popup-search-enhance-diy](https://greasyfork.org/zh-CN/scripts/601177-popup-search-enhance-diy)进行安装；
- 或下载或复制 [popsearch-enhance-diy.user.js](popsearch-enhance-diy.user.js)）的代码，在脚本管理器中「新建脚本」粘贴并保存，即可开启使用。

---

## ⌨️ 快捷操作与鼠标手势

| 操作场景 | 操作方式 | 功能说明 |
| :--- | :--- | :--- |
| **划词悬浮窗** | 鼠标左键点击图标 | 触发对应搜索引擎搜索或执行功能 |
| **划词悬浮窗** | 鼠标右键点击工具栏 | **一键复制**选中文本并自动关闭悬浮栏 |
| **划词悬浮窗** | 鼠标中键点击工具栏 | 在新标签页 / 后台直接打开选中的文字（网址直达） |
| **划词悬浮窗** | **鼠标滚轮滑动** | 悬浮栏有宽度限制时，**上下滚动滚轮即可横向翻页**浏览其余引擎 |
| **全局快捷键** | `Ctrl + Alt + P` | 快速重新弹出最近选词的搜索栏 |
| **全局快捷键** | `Esc` | 立即隐藏/关闭弹出的搜索悬浮栏 |
| **设置面板** | **右下角按住拖拽** | **自由缩放**设置窗口大小 |
| **设置面板** | 按住卡片把手拖动 | **实时拖拽排序**搜索引擎 |

---

## ⚙️ 自定义搜索引擎参考示例

在设置面板「搜索引擎」网格中点击 `➕ 添加自定义引擎` 卡片，填写如下格式即可：

### 常用自定义引擎配置示例

- **GitHub 代码搜索**
  - **引擎名称**: `GitHub`
  - **描述**: `搜索 GitHub 代码与仓库`
  - **图标来源**: `https://github.githubassets.com/favicons/favicon.svg`
  - **搜索链接**: `https://github.com/search?q=${text}`

- **Stack Overflow**
  - **引擎名称**: `StackOverflow`
  - **描述**: `技术问答与编程报错检索`
  - **图标来源**: `https://stackoverflow.com/favicon.ico`
  - **搜索链接**: `https://stackoverflow.com/search?q=${text}`

- **MDN Web 技术文档**
  - **引擎名称**: `MDN`
  - **描述**: `MDN Web Docs 权威开发文档`
  - **图标来源**: `https://developer.mozilla.org/favicon-48x48.png`
  - **搜索链接**: `https://developer.mozilla.org/zh-CN/search?q=${text}`

- **Devv AI 编程搜索**
  - **引擎名称**: `Devv`
  - **描述**: `面向开发者的智能 AI 搜索引擎`
  - **图标来源**: `https://devv.ai/favicon.ico`
  - **搜索链接**: `https://devv.ai/search?q=${text}`

### 可用动态变量

| 变量占位符 | 说明 |
| :--- | :--- |
| `${text}` | 经过标准 URL 编码的选中文本（**绝大多数搜索引擎推荐使用此项**） |
| `${rawText}` | 原始未编码的选中文本 |
| `${domain}` | 当前所在网站的域名（例如 `github.com`） |
| `${url}` | 当前网页的完整 URL 地址 |

---

## 🤝 致谢与开源协议

- **当前版本 (Version)**: `0.1.0`
- **现版本增强维护 (Enhanced by)**: [csxo](https://github.com/csxo/) ([GitHub: @csxo](https://github.com/csxo/))
- **原作者 (Original Author)**: [Lkytal](https://github.com/lkytal/) ([GitHub: @lkytal](https://github.com/lkytal/))
- **原项目主页**: [https://github.com/lkytal/GM](https://github.com/lkytal/GM)
- **致谢**: 衷心感谢原作者 [Lkytal](https://github.com/lkytal/) 创造了如此优秀的 Popup Search 基础架构与划词交互设计，为社区提供了稳定可靠的基础。
- **开源协议**: 本项目完全遵从原作者开源协议，基于 [GNU Affero General Public License (AGPL-3.0-or-later)](https://www.gnu.org/licenses/agpl-3.0.html) 与 [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](http://creativecommons.org/licenses/by-nc-sa/4.0/) 双重协议进行开源与二次创作。
