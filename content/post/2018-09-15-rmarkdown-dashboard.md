---
title: Rmarkdown中的dashboard
author: ~
date: '2018-09-15'
slug: rmarkdown-dashboard
categories: [R]
tags: [Rmarkdown, Dashboard]
---

# Dashboard
最近因为项目的需求，需要做一个演示的网站。之前对于R语言中的**dashboard**有一些印象，所以准备用**dashboard**做一个。

关于**Dashboard**学习的一些网站：

* [flexdashboard](https://rmarkdown.rstudio.com/flexdashboard/)
* [R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/)

在**dashboard**中，首先将需要的包和内容放在setup里

```{r setup, include=FALSE}
library(dygraphs)
```

在**dashboard**中，每个页面的分级用

`=========================================`

页面中每一栏可以用

```
Column
-----------------------------------------

```

每一节内容可以markdown的三号标题替代，这里要说`tabnet`的性质，如果不想整个页面在Dashboard上铺开，在后面加上这个性质

另外，要在dashboard上增加shiny的组件，可以考虑在目标栏上添加

```
runtime: shiny
```