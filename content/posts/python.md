+++
date = '2026-10-29T16:44:48+08:00'
draft = draft
title = 'Python-urllib'
tags=["spider","CS"]
categories=[]
+++

库
-包-模块-类/函数：

函数function 放在 模块（一个.py文件） 里
模块 放在 包 里
包 组成 库lib

```text
Python 标准库（自带）
├── urllib（包）
│   ├── urllib.request（模块）→ urlopen()（函数）
│   ├── urllib.parse（模块）
│   └── urllib.error（模块）
├── json（模块）
├── csv（模块）
└── os（模块）

第三方库（需 pip 安装）
├── requests
├── beautifulsoup4
└── playwright
```

urllib 是 python 标准库的一个包
对象里面有属性（数据）和方法（操作、函数）
 . 表示访问对象的属性、调用对象的方法、访问对象（模块）的东西
 . 表示 从左边的对象(数字int/float、字符串str、列表list、字典、模块module、包package、类type、实例（自定义类型）、函数function、文件、None……)里访问右边的成员(字符串的方法、列表的方法、模块的函数（类）、对象的属性、包的子模块)


