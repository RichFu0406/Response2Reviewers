# Response2Reviewers

论文审稿回复模板，提供 Word 和 LaTeX 两种格式。[查看原版 PDF](latex/reviewresponse_example.pdf)。

## Word

[下载 Word 模板](reviewresponse_template.docx?raw=true)，打开后替换示例内容。完成编辑后，右键目录选择“更新域 → 更新整个目录”。

## LaTeX

### 1. 导入 Overleaf

1. 下载 [latex](latex) 中的 `.tex`、`.cls`、`.sty` 三个文件。GitHub 文件页面的 **Download raw file** 按钮可用于下载。
2. 在 [Overleaf](https://www.overleaf.com/) 新建空白项目，删除默认的 `main.tex`，将三个文件上传到同一目录。原版 `.pdf` 仅供预览，无需上传。
3. 在项目设置中，将主文件设为 `reviewresponse_example.tex`，编译器选 **pdfLaTeX**，点击 **Recompile**。

### 2. 修改内容

**只需编辑 `reviewresponse_example.tex`，另外两个源码文件保留原样。**

先找到 `% 2. Complete the paper data`，修改下面的稿件信息：

| 命令 | 修改内容 |
| --- | --- |
| `\myTitle` | 稿件标题 |
| `\myJournal` | 期刊名称 |
| `\myAuthors` | 作者姓名及单位上标 |
| `\myAuthorsShort` | 简短作者名，如 `Alice Smith et al.` |
| `\myEmail` | 通讯作者邮箱 |
| `\myDept` | 单位名称及地址 |
| `\myShortTitle` | 页眉短标题，通常保留 `Response to reviewers` |

修改时只替换花括号里的内容，不改命令名。例如：

```latex
\newcommand{\myTitle}{Your manuscript title}
\newcommand{\myJournal}{Journal Name}
```

作者后的 `$^{1}$` 是单位上标，需与单位编号对应；`\\` 表示换行。首页的 `\today` 会显示编译日期，也可直接替换为固定日期。

接着，替换 `abstract` 环境中的开头致谢，以及下方的审稿意见和回复：

```latex
\section{Reviewer 1}

\rcomment{Paste the reviewer's comment here.}

\textbf{Response}

Write your response here, including the manuscript location.

\begin{quotation}\noindent
Paste the revised passage here. Use \newtext{blue text} for changes.
\end{quotation}
```

- **增加意见**：复制一组评论和回复，评论编号会自动递增。
- **增加审稿人**：复制整个章节，将标题依次改为 `Reviewer 2`、`Reviewer 3`；新章节的评论编号从 1 开始。
- **另起一页**：在新章节前添加 `\clearpage`。
- **展示修订**：`\newtext{...}` 将文字标蓝；不需要修订摘录时，删除 `quotation` 整块。

需要参考文献时，上传自己的 `responsereferences.bib`，取消文件末尾 `\bibliographystyle` 和 `\bibliography` 两行前的 `%`，在回复中用 `\citep{文献键}` 引用。

### 3. 编译与下载

点击 **Recompile**，检查目录、页码和正文，再下载 PDF。目录未刷新时，再编译一次。导出前替换所有示例信息，包括作者、单位、审稿意见、回复和 `Lorem Ipsum` 段落。

普通正文中的 `%`、`&`、`_`、`#`、`$` 需写成 `\%`、`\&`、`\_`、`\#`、`\$`。模板默认用于英文回复。

## 文件结构

```text
├── README.md
├── reviewresponse_template.docx
└── latex/
    ├── reviewresponse_example.tex
    ├── reviewresponse_example.pdf
    ├── reviewresponse.cls
    └── tcolorbox.sty
```

原版模板由 Javier Sánchez-Monedero 编写，采用 [CC BY-SA 3.0](http://creativecommons.org/licenses/by-sa/3.0/) 许可；Word 改编沿用相同许可。`tcolorbox.sty` 保留原有作者与 LPPL 许可声明。
