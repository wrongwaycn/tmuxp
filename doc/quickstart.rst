.. _quickstart:

====================
快速入门(Quickstart)
====================

命令行(CLI)
-----------

.. seealso:: :ref:`examples`, :ref:`cli`, :ref:`bash_completion`.

tmuxp根据配置文件启动会话(session)。

配置文件保存在``$HOME/.tmuxp`` 或是 ``.tmuxp.py`` ， ``.tmuxp.json`` ， ``.tmuxp.yaml`` 项目目录下。

配置文件必须包括下列内容:

1. ``session_name``
2. ``windows`` 列表
3. 每个 ``windows`` 所包含的``panes`` 列表

创建一个 ``~/.tmuxp/example.yaml`` 文件：

.. literalinclude:: ../examples/2-pane-vertical.yaml
    :language: yaml

运行tmuxp:

.. code-block:: bash

    $ tmuxp load -l

列出当前目录以及 ``$HOME/.tmuxp`` 下可用的配置项，然后tmuxp会检测到 ``example.yaml`` 文件的存在

.. code-block:: bash

    $ tmuxp load example.yaml

创建你的tmuxp会话(session)。


Pythonics
---------

.. seealso::
    :ref:`tmuxp python API 文档 <api>` ， :ref:`developing` ，
    :ref:`internals`.


ORM - `对象关系映射(Object Relational Mapping)`_

AL - `抽象层(Abstration Layer)`_

.. _抽象层(Abstration Layer): http://en.wikipedia.org/wiki/Abstraction_layer
.. _对象关系映射(Object Relational Mapping): http://en.wikipedia.org/wiki/Object-relational_mapping

python抽象层
""""""""""""

.. module:: tmuxp

======================================== =================================
:ref:`tmuxp python api <api>`            :term:`tmux(1)` 指令
======================================== =================================
:class:`Server.new_session()`            ``$ tmux new-session``
:class:`Server.list_sessions()`          ``$ tmux list-sessions``
:class:`Session.list_windows()`          ``$ tmux list-windows``
:class:`Session.new_window()`            ``$ tmux new-window``
:class:`Window.list_panes()`             ``$ tmux list-panes``
:class:`Window.split_window()`           ``$ tmux split-window``
:class:`Pane.send_keys()`                ``$ tmux send-keys``
======================================== =================================

tmux ORM
""""""""

tmuxp的主要内部特性就是tmux服务(类似 `SQLAlchemy`_ 中的 `engine`_ )与会话(session)等对象间的关联和编排。

- :class:`Server` 包含 :class:`Session` 对象。
- :class:`Session` 包含 :class:`Window` 对象。
- :class:`Window` 包含 :class:`Pane` 对象。


tmux对象的实例使用 tmux `1.8`_'s ``pane_id``, ``window_id`` 和
``session_id`` 创建python对象，从而使用最新的数据来构造工作区。

.. _engine: http://docs.sqlalchemy.org/en/rel_0_8/core/engines.html
.. _sqlalchemy: http://www.sqlalchemy.org/
.. _1.8: http://sourceforge.net/projects/tmux/files/tmux/tmux-1.8/
