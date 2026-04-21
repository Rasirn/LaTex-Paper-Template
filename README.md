# latex-paper-template

一个基于 XeLaTeX + ctex 的中文学术论文 LaTeX 模板，适用于毕业论文、期刊投稿等场景。

## 目录结构

```
.
├── paper.tex              # 主文件（入口）
├── .latexmkrc             # latexmk 配置（使用 XeLaTeX，产物输出到 build/）
├── .gitignore
├── build/                 # 编译产物（自动生成，不提交）
├── chapters/              # 各章节内容
│   ├── abstract.tex       # 摘要
│   ├── introduction.tex   # 引言
│   ├── method.tex         # 方法
│   ├── experiment.tex     # 实验
│   └── conclusion.tex     # 结论
├── figures/               # 图片资源
├── tables/                # 表格文件
├── references/
│   └── refs.bib           # 参考文献
└── styles/                # 自定义样式文件
```

## 环境要求

- [TeX Live](https://tug.org/texlive/) 2022 或以上（推荐最新版）
- 编译引擎：**XeLaTeX**（必须，ctex 在 macOS 下依赖系统字体）
- 构建工具：`latexmk`（TeX Live 已内置）

## 快速开始

```bash
# 克隆模板
git clone https://github.com/<你的用户名>/latex-paper-template.git
cd latex-paper-template

# 编译（自动调用 XeLaTeX）
latexmk paper.tex

# 清理编译产物
latexmk -C paper.tex
```

编译完成后，PDF 输出在 `build/paper.pdf`。

## 使用说明

### 写作

- 在 `chapters/` 下对应文件中编写各章节内容
- 主文件 `paper.tex` 通过 `\input{}` 自动引入，无需修改主文件结构

### 插入图片

将图片放入 `figures/`，正文中直接引用文件名：

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics{example.png}  % 不需要写路径前缀
    \caption{图片标题}
    \label{fig:example}
\end{figure}
```

### 添加参考文献

在 `references/refs.bib` 中添加 BibTeX 条目，正文中使用 `\cite{key}` 引用。

### 自定义样式

将自定义 `.sty` 文件放入 `styles/`，在 `paper.tex` 中通过 `\usepackage{styles/yourpackage}` 引入。

## 许可证

MIT License
