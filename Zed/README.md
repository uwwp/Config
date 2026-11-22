# Zed 配置文件

## 核心适配与优化调整

### 1. 页面布局与侧边栏

* **左侧统一主活动区**：
  * **资源管理器 (`project_panel`)**：停靠在左侧（`"dock": "left"`），开启目录箭头与图标并存（`"folder_indicator": "both"`），显示文件错误/警告气泡（`"diagnostic_badges": true`）及 Git 状态与标记（`"git_status": true`, `"git_status_indicator": true`）。
  * **Git / 源代码管理面板 (`git_panel`)**：Zed 默认停靠于右侧，现将其改为停靠在左侧（`"dock": "left"`），与 VS Code 侧边栏活动栏习惯一致。
  * **大纲视图 (`outline_panel`)**：统一停靠在左侧（`"dock": "left"`）。
* **底部终端 (`terminal`)**：
  * 终端停靠在编辑器底部面板（`"dock": "bottom"`），符合经典底部控制台布局。
* **右侧副侧边栏 (`agent`)**：
  * Zed 内置的 AI Assistant 面板停靠在右侧（`"dock": "right"`），与 VS Code 现代右侧辅助侧边栏（如 Copilot / 聊天助手）一致。
* **顶部标签页 (`tabs`)**：
  * 开启文件类型图标显示（`"file_icons": true`，Zed 默认关闭）；
  * 变动或未保存文件显示 Git 颜色高亮（`"git_status": true`）；
  * 关闭按钮固定在右侧（`"close_position": "right"`）。
* **面包屑与状态栏 (`toolbar`, `status_bar`)**：
  * 开启顶部路径与符号面包屑导航（`"toolbar.breadcrumbs": true`）；
  * 底部状态栏显示光标行列位置 (`cursor_position_button`)、当前语言模式 (`active_language_button`)、换行符 `CRLF`/`LF` (`line_endings_button`)，并常驻显示编码格式如 `UTF-8` (`active_encoding_button: "enabled"`）。

---

### 2. 操作习惯与交互行为

* **函数签名提示 (`"auto_signature_help": true`)**：
  * Zed 默认不自动弹出参数提示。开启后在输入函数调用 `()` 时，会自动弹出参数签名说明，保持与 VS Code IntelliSense 体验一致。
* **代码补全文档浮窗 (`"show_completion_documentation": true`)**：
  * 代码补全候选菜单中并排展示符号的文档注释。
* **预览标签页机制 (`preview_tabs`)**：
  * 开启与 VS Code 完全一致的预览标签机制：单击文件树或从 Quick Open（文件快速打开）进入预览模式（斜体标签），双击或编辑后固定为正式标签，避免快速浏览时打开过多无用标签页。
* **活动作用域缩进参考线 (`"indent_guides.coloring": "indent_aware"`)**：
  * 根据光标当前所在的代码块作用域高亮对应的垂直缩进线。
* **光标与高亮行为**：
  * `"cursor_blink": true`：光标平滑闪烁；
  * `"current_line_highlight": "all"`：当前光标所在行全行高亮（包含行号区域）；
  * `"selection_highlight": true`：双击选中文本时自动高亮全文中相同匹配词。
* **格式化与保存**：
  * 开启保存时自动格式化 (`"format_on_save": "on"`)、输入触发符号时自动格式化 (`"use_on_type_format": true`)、粘贴时自动调整缩进 (`"auto_indent_on_paste": true`)，以及修改后延迟自动保存 (`"autosave": { "after_delay": { "milliseconds": 1000 } }`)。
* **彩虹括号 (`"colorize_brackets": true`)**：
  * 对应 VS Code 的 `editor.guides.bracketPairs: true`，开启成对括号的多彩区分高亮。

---

## 配置文件应用方法

你可以将 [`settings.json`](./settings.json) 的内容直接覆盖或合并至本地 Zed 用户配置中：

### 1. 快捷键直接打开（推荐）
1. 在 Zed 中按下 `Ctrl+Shift+P`（macOS 为 `Cmd+Shift+P`）打开命令面板；
2. 输入并选择 **`zed: open settings file`**；
3. 将 [`settings.json`](./settings.json) 中的配置内容复制粘贴保存即可生效。

### 2. 配置文件默认物理路径
* **Linux**：`~/.config/zed/settings.json`
* **macOS**：`~/.config/zed/settings.json` 或 `~/Library/Application Support/Zed/settings.json`
* **Windows**：`%APPDATA%\Zed\settings.json`