--- 
title: "Advanced R学习笔记"
subtitle: "优雅的 Bookdown 书籍模版"
author: 
  - Lee
date: "2022-04-12"
site: bookdown::bookdown_site
documentclass: elegantbook
bibliography: 
 - book.bib
 - packages.bib
lot: yes
lof: yes
colorlinks: yes
toccolor: Maroon
link-citations: yes
nocite: '@*'    # 将正文未引用的参考文献也列在书中
mathspec: yes
graphics: yes
subject: "基于 elegantbook 文类的 bookdown 模版"
keywords:
  - elegantbook
  - bookdown
  - pandoc
  - R
hyperrefoptions:
- linktoc=all
- pdfstartview=FitH
github-repo: XiangyunHuang/ElegantBookdown
classoption: 
 - lang=cn
 - 11pt
 - scheme=chinese
 - chinesefont=nofont
 - citestyle=gb7714-2015
 - bibstyle=gb7714-2015
description: "最初看到 elegantbook 做的书籍样式很漂亮，就想把它引入到 bookdown 中，遂定制了此模版。在此基础上，做了迁移和扩展的工作，融合了 LaTeX (精美)、Pandoc (简洁) 和 R (强大) 的特性。This is a bookdown template based on ElegantBook. The output format for this template is bookdown::gitbook and bookdown::pdf_book."
---

\mainmatter

# 自定义 block {-}

基于 Pandoc 自定义 block 是一件很有意思的事情，目前不想让模版过于复杂，仅给出几个最常用的例子。如何自定义可以去看谢益辉的新书 <https://bookdown.org/yihui/rmarkdown-cookbook/custom-blocks.html>。

[要做的还有很多]{.todo}

::: {.rmdwarn data-latex="{警告}"}
这是警告
:::

::: {.rmdtip data-latex="{提示}"}
这是提示
:::

:::: {.rmdnote data-latex="{注意}"}
这是注意
::::

::: {.rmdinfo}
普通说明
:::



[为什么选择R语言]{.todo}
