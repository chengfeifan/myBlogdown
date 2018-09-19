---
title: Jupyter notebook服务器端安装
author: ~
date: '2018-09-19'
slug: jupyter-notebook
categories: [System]
tags: [centos,jupyter]
---
因为之前一直使用团队服务器挂掉了，现在开始用组内的服务器。平常用习惯了 *Jupyter notebook* ，所以也考虑在组内服务器上使用，并在网页端访问。其实整个配置过程非常简单。一般在服务器上安装了`Anaconda`之后，就会自带 *Jupyter notebook* ，因此就只剩下配置了。

# 配置过程
1. 生成配置文件
```
jupyter notebook --generate-config
```

2. 进入 `python` 界面中，使用命令设置 password

```
from notebook.auth import passwd
passwd()
```

或者是

```
$ jupyter notebook password
```

3. 生成ssl证书

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mykey.key -out mycert.pem
```

4. 更改配置文件 `/root/.jupyter/jupyter_notebook_config.py`

```
# Set options for certfile, ip, password, and toggle off
# browser auto-opening
c.NotebookApp.certfile = u'/absolute/path/to/your/certificate/mycert.pem'
c.NotebookApp.keyfile = u'/absolute/path/to/your/certificate/mykey.key'
# Set ip to '*' to bind on all interfaces (ips) for the public server
c.NotebookApp.ip = '*'
c.NotebookApp.password = u'sha1:bcd259ccf...<your hashed password here>'
c.NotebookApp.open_browser = False

# It is a good idea to set a known, fixed port for server access
c.NotebookApp.port = 8888
```

5. 设置根目录，在配置文件 `/root/.jupyter/jupyter_notebook_config.py` 找到 `c.NotebookApp.dir`，更改根目录。可以输入`:\dir`进行查找

6. 运行jupyter notebook 作为后台程序

```
nohup jupyter notebook --allow-root &
```