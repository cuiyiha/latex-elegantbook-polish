# latex-elegantbook-polish

一个用于 Codex 的个人技能：在尽量保留正文和数学语义的前提下，将中文 LaTeX 书籍、讲义和长篇数学文档优化为 ElegantBook 风格，并完成编译与视觉检查。

## 功能

- 识别 LaTeX 主文件及项目结构
- 优化中文书籍的章节层级、主题配色、字体、间距和页眉页脚
- 为定义、定理、推论、例题和习题建立一致的视觉样式
- 使用 XeLaTeX 和 `latexmk` 编译并检查错误、缺字及警告
- 抽查封面、章节页和正文页的 PDF 渲染效果
- 按需在编辑器中打开项目和主 `.tex` 文件

## 安装

下载本仓库，将整个 `latex-elegantbook-polish` 文件夹放入个人 Codex 技能目录：

```text
$CODEX_HOME/skills/latex-elegantbook-polish
```

如果未设置 `CODEX_HOME`，通常使用：

```text
~/.codex/skills/latex-elegantbook-polish
```

重新打开 Codex 任务后即可使用。

## 使用

显式调用：

```text
使用 $latex-elegantbook-polish 优化当前中文 LaTeX 文档，并完成编译与视觉检查。
```

也可以直接描述需求，例如：

```text
请把这份中文数学讲义优化成 ElegantBook 风格，并用 XeLaTeX 编译。
```

## 设计原则

该技能把 ElegantBook 作为视觉方向，而不是强制依赖 `elegantbook.cls`。它会优先采用对现有项目改动较小、可维护且可移植的实现方式，并避免在没有明确请求时改写公式、定理内容或数学符号。

## 许可证

[MIT](LICENSE)
