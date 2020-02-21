---
layout: mypost
title: Sublime Text配置Python3环境
date:   2020-02-19 22:24:00
categories: [Python]
---

## Sublime Text配置Python3环境

Sublime Text - Tools - Build System - New Build System

会新建一个文本，将内容替换成下面所示，Python路径可能会不一样，自行修改即可

```
{
      "cmd": ["/Library/Frameworks/Python.framework/Versions/3.6/bin/python3", "-u", "$file"],
      "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
      "selector": "source.python",
      "env": {"PYTHONIOENCODING":"utf8"}
}
```

保存的时候命名为**Python3**，然后在.py文件下，选择Tools - Build System - Python3