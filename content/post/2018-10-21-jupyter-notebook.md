---
title: jupyter notebook的目录
author: ~
date: '2018-10-21'
slug: jupyter-notebook
categories: [python]
tags: [jupyter-notebook]
---
# 问题
最近一直用 *jupyter notebook* 写代码，因为要跑的代码比较长，所以导致整个页面都比较长，导致找到之前写的代码比较困难，这个时候就想着能不能有个目录来显示整个页面的内容，结果发现其实是可以的，就是用的 [Jupyter Nbextensions Configurator](https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator)，里面有许多扩展功能。

# 安装扩展
对于使用 *Anaconda* 的用户，直接使用下面的指令

```
conda install -c conda-forge jupyter_nbextensions_configurator
```

对于使用 *pip* 的用户，需要用到下面两个指令
```
pip install jupyter_nbextensions_configurator
```

针对特定用户

```
jupyter nbextensions_configurator enable --user
```

# 访问设置
访问 `http://localhost:8888/tree`，你就可以看到`nbextensions`, 看到`Table of contents`，就可以进行设置了