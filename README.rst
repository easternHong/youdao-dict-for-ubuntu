有道词典的Linux客户端. 视频演示:

- http://v.youku.com/v_show/id_XNTI2ODQ1MjY4.html
- http://v.youku.com/v_show/id_XNTI2ODYyMzUy.html

截图:

.. image:: https://raw.github.com/idning/youdao-dict-for-ubuntu/master/imgs/youdao-dict.png
    :height: 355px

特点
====

1. 自动取词, 鼠标跟随
2. 发音.
3. 单词白名单
4. 用chrome 浏览器跳转到youdao查词.

5. 基于web版youdao , 而不是API(http://fanyi.youdao.com/openapi.do?keyfrom=tinxing&key=1312427901&type=data&doctype=json&version=1.1&q=hello)
   因为API 通常有鉴权而比较慢.

6. 界面简洁, 用最大字体显示默认翻译, 屏幕占用面积小, 真正做到无缝阅读体验.
7. 代码简洁清晰, 总共250行, 如果不爽，自己改吧改吧~

install
=======

安装deb包
---------

::

    wget http://idning.github.io/imgs/res/youdao-dict-0.1.0_all.deb
    sudo dpkg -i youdao-dict-0.1.0_all.deb

直接运行 ``youdao-dict`` 即可.

启动图标会安装在office分组下, 可以参考这里增加自动启动项:  http://jingyan.baidu.com/article/7c6fb428632c3980642c90ce.html

手动安装(适合于需要hack的同学)
------------------------------

::

    apt-get install mplayer python-gtk2 python-webkit
    pip install -e git://github.com/idning/youdao-dict-for-ubuntu.git#egg=youdao-dict
    运行:
    dict.py

    开机自动启动: 在/etc/xdg/autostart下, 增加一个.desktop文件::

        root@ning-laptop:/etc/xdg/autostart# cat youdao-dict-for-ubuntu.desktop
        [Desktop Entry]
        Name=youdao-dict-for-ubuntu
        Comment=youdao-dict-for-ubuntu
        Exec=dict.py
        Terminal=false
        Type=Application
        OnlyShowIn=GNOME;

    请自行修改路径~

配置
----

单词白名单: ~/.youdao-dict/common_words.txt, 例子:

https://github.com/idning/youdao-dict-for-ubuntu/blob/master/common_words.txt

日志
----

~/.youdao-dict/dict.log

可以从日志中抽取常用词加入到白名单去


实现原理
========

获取当前选中的单词, 可以使用 ``xclip -o``, 我这里用的是 监听 ``selection_received`` 消息

其它词典
========

:stardict:
   StarDict hasn't seen any active development for many years
   推荐 GoldenDict
:GoldenDict:
   确实不错, 但是占CPU. 常年占20%
:youdao:
    网页版而且有广告.
    chrome 插件不错.

stardict, GoldenDict 的一个共同问题是, 查询结果的 **字体都是一样大小** . 很不好看.

:一个QT版的:
     https://github.com/lvzongting/youdao-qt

:openyoudao:
     界面比较复杂, python 实现(不错, 不过讨厌留在网页上的广告.):
    - https://github.com/justzx2011/openyoudao
    - http://v.youku.com/v_show/id_XNDAzMDUxNDk2.html

此外还有emacs 插件, vim 插件, 命令行版.

`@idning`_

.. _`@idning`: http://weibo.com/idning


