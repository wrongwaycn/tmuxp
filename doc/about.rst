.. module:: tmuxp

.. _about:

====
介绍
====

tmuxp帮助您管理您的文本工作区，遵守BSD许可。

事实上，tmuxp也是一个构建于tmux之上的对象关系映射(ORM)。
终端用户可以使用YAML, JSON以及 :py:obj:`dict` 字典配置项来启动工作区
（就如同 `tmuxinator`_ 和 `teamocil`_ 所做的那样）。

您可以跳过本章，直接查看 :ref:`quickstart` 和 :ref:`examples` 。

想深入了解更多或参与其中，不妨看看 :ref:`api` 和 :ref:`developing` 。

该开源软件遵守 `BSD-licensed`_ 许可，代码托管在 http://github.com/tony/tmuxp.


与 tmuxinator / teamocil 的异同
-------------------------------

.. note::

    如果您是 teamocil / tmuxinator 的用户，想更加详细地比较异同，
    不妨在github上 `编辑该页面`_ 。

相似之处
""""""""

**加载会话** 都是根据配置文件中加载tmux会话

**YAML** 支持YAML格式

**支持命令行参数/简短参数配置** 都支持在单独的命令中使用简短标记。

不足之处
""""""""

**稳定性Stability** 现阶段，tmuxinator 和 teamocil 相比于tmuxp要更加稳定，也更易于对其扩展开发。

**ERB / 模板支持** teamocil 支持 `ERB`_ 标记。

**版本支持** tmuxp 只支持 ``tmux >= 1.8`` ，Teamocil 和
tmuxinator 可以支持更早期版本。

不同之处
""""""""

**开发所用语言** tmuxp 使用 python。而 teamocil 和 tmuxinator 则使用 ruby。

**工作区搭建过程Workspace building process** teamocil 和 tmuxinator 直接通过shell命令行处理配置项。
而 tmuxp 则是通过ORM层来处理配置项。

其他特性
--------

**CLI** tmuxp的命令行接口支持tab补全，可以杀死和附加到会话。
详见 :ref:`commands` 。

**Import config导入配置文件** 可以从 Teamocil / Tmuxinator [1]_ 导入配置文件。 
详见 :ref:`cli_import` 。

**冻结会话** 支持将会话冻结为YAML和JSON格式 [1]_ 。 详见 :ref:`cli_freeze` 。

**JSON配置** 支持JSON配置。 详见 :ref:`Examples` 。

**基于ORM的API** - 利用 tmux(>=1.8) 的唯一ID来标识面板，窗口和会话，
以创建关联视图的tumx对象：
:class:`Server` , :class:`Session` , :class:`Window` , :class:`Pane` 。
详见 :ref:`Internals` 。

**转换** ``$ tmuxp convert <filename>`` 可以将JSON/YAML内容与文件互相转换。

.. [1] 冻结或导入会话是一个保存当前进度的好方法，有时可能要微调一下 - 没什么能代替一个用心制作的配置文件。

细微改动
--------

- 编写最新版本tmux下的单元测试，以测试tmux的会话，窗口和面板的有效性。详见 :ref:`travis` 。
- 在tmux下可以加载或切换到新会话。
- 加载配置文件可以恢复会话。
- 可在 virtualenv / rvm / 其他命令下使用。
- 使用 ``$ tmuxp load /full/file/path.json`` 可以从任何位置加载配置文件。
- 使用 ``$ tmuxp load .`` 可以在当前目录下载入配置文件 ``.tmuxp.yaml`` 和 ``.tmuxp.json`` 。
- ``$ tmuxp -2``, ``$ tmuxp -8`` 强行指定 :term:`tmux(1)` 的配色。
-  ``$ tmuxp -L<socket-name>``, ``$ tmuxp -S<socket-path>`` 可支持socket，
  ``$ tmuxp -f<config-file>`` 可加载配置文件

.. _attempt at 1.7 test: https://travis-ci.org/tony/tmuxp/jobs/12348263
.. _kaptan: https://github.com/emre/kaptan
.. _unittest: http://docs.python.org/2/library/unittest.html
.. _BSD-licensed: http://opensource.org/licenses/BSD-2-Clause
.. _tmuxinator: https://github.com/aziz/tmuxinator
.. _teamocil: https://github.com/remiprev/teamocil
.. _ERB: http://ruby-doc.org/stdlib-2.0.0/libdoc/erb/rdoc/ERB.html
.. _编辑该页面: https://github.com/tony/tmuxp/edit/master/doc/about.rst
