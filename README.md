# Notion → PDF 转换器 Pro V3 📄✨

一个纯浏览器端的 Notion Markdown 导出解析与 PDF 打印排版工具。完美解决 Notion 原生导出 PDF 排版受限，以及普通 Markdown 转 PDF 时图片丢失、代码块/表格截断等痛点。

## 🌟 核心特性

- **📦 极速 ZIP 解析**：无需手动解压，直接拖拽 Notion 导出的 `.zip` 压缩包，自动读取 Markdown 文本并映射本地关联图片。
- **🖨️ 专为打印优化的排版**：
  - **防截断机制**：代码块与表格强制自动换行，彻底告别 PDF 右侧内容溢出或截断。
  - **Notion 语法还原**：完美兼容并渲染 Notion 的 `<aside>` 标注块（Callout），且打印时智能防分页。
  - **LaTeX 支持**：内置 KaTeX，高清渲染数学公式。
- **🎨 高自由度定制**：
  - **字体切换**：内置 Noto Serif（默认衬线）、Apple 苹方、微软雅黑，以及全局引用的 **霞鹜文楷 (手写体)**。
  - **排版微调**：支持全局字号无极缩放，支持自定义标注块（Callout）底色及“填充/线框”模式。
- **📝 实时编辑预览**：左侧内置 CodeMirror 编辑器，支持手动修改 Markdown 源码，右侧所见即所得。
- **🔒 绝对隐私安全**：纯前端（HTML/CSS/JS）实现，所有文件解析与渲染均在本地浏览器中完成，**零服务端上传**，保护你的笔记隐私。

## 🚀 如何使用

1. **导出 Notion 笔记**：
   - 在 Notion 页面点击右上角的 `...`
   - 选择 `Export`
   - `Export format` 选择 **Markdown & CSV**，点击导出并下载 `.zip` 文件。
2. **导入本工具**：
   - 使用浏览器打开 `index.html`（或访问部署好的网页）。
   - 将下载好的 `.zip` 文件直接 **拖拽** 到左侧的「MARKDOWN 源码」区域（或点击顶部工具栏的“📁 上传 ZIP”）。
3. **定制与微调**：
   - 可以在左侧源码区做最后的文字修改。
   - 使用顶部工具栏调整最适合的字体、字号和高亮颜色。
4. **导出为 PDF**：
   - 点击右上角 **🖨️ 导出 PDF** 按钮。
   - 在浏览器的打印弹窗中，将目标打印机设置为“另存为 PDF”即可（建议纸张尺寸设为 A4，边距设为默认或无）。

## 🛠️ 技术栈

本项目为单文件免构建工具，开箱即用。核心依赖均通过 CDN 引入：

- **Markdown 解析**: [marked.js](https://marked.js.org/)
- **ZIP 提取**: [JSZip](https://stuk.github.io/jszip/)
- **代码高亮**: [highlight.js](https://highlightjs.org/)
- **源码编辑**: [CodeMirror 5](https://codemirror.net/5/)
- **公式渲染**: [KaTeX](https://katex.org/)
- **中文字体**: [霞鹜文楷 Lite (WebFont)](https://github.com/lxgw/LxgwWenKai-Lite)

## 💡 开发说明

如果你想基于此项目进行二次开发，可以直接修改 `index.html`：
- `processMarkdown(src)`：包含对 Notion 特有 `<aside>` 标签及图片相对路径的正则预处理逻辑。
- `@media print` 样式块：包含了核心的打印排版保护规则（如 `page-break-inside: avoid` 和 `word-break: break-all`）。

## 📄 许可证

MIT License
