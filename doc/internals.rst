.. _Internals:

===================
内部结构(Internals)
===================

.. seealso:: :ref:`api`

.. module:: tmuxp

tmuxp是一个建立在tmux命令行参数之上的 *抽象层* 。

:class:`util.TmuxRelationalObject` 的角色类似一个容器，用以存放
 :class:`Server`, :class:`Session`, :class:`Window` 以及 :class:`Pane` 之间的关联。

======================== ======================= =========================
对象(object)             子级(child)             父级(parent)                 
======================== ======================= =========================
:class:`Server`          :class:`Session`        None
:class:`Session`         :class:`Window`         :class:`Server`
:class:`Window`          :class:`Pane`           :class:`Session`
:class:`Pane`            None                    :class:`Window`
======================== ======================= =========================

事实上，tmux允许多个服务(server)运行在同一个系统上。每个服务(server)各自使用一个socket。
如果没有指定服务(server)，tmux会自动启动一个默认服务(server)并与其通讯。

一个服务(server)可以拥有多个会话(session)，可以使用 ``Ctrl-a s`` 在会话(session)间切换。

会话(session)，窗口(window)和窗格(pane)都有各自唯一的标识(``session_id``, ``window_id``, ``pane_id`` )，
:class:`util.TmuxMappingObject` 将利用这些标识来查找保存在 :class:`Server` 对象中的数据。

======================== ======================= =========================
对象(Object)             前缀(Prefix)            示例(Example)
======================== ======================= =========================
:class:`Server`          N/A                     N/A, uses ``socket-name``
                                                 and ``socket-path``
:class:`Session`         ``$``                   ``$13``
:class:`Window`          ``@``                   ``@3243``           
:class:`Pane`            ``%``                   ``%5433``
======================== ======================= =========================

Tmux与Pythonics风格的相似性(Similarities to Tmux and Pythonics)
---------------------------------------------------------------

经过对tmux操作的深入理解，以及如何以优雅的方式实现python的API
tmuxp是建立在对tmux操作的深入理解以及对python AP的优雅实现的基础之上。

tmuxp利用tmux中的 ``FORMATTERS`` 来标识 :class:`Session`, :class:`Window` 和 :class:`Pane` 对象。

.. _formatters.c: http://sourceforge.net/p/tmux/tmux-code/ci/master/tree/format.c

Tmuxp如何保留对窗格(pane)，窗口(window)和会话(session)的引用？

    Tmux对每个会话(session)，窗口(window)和窗格(pane)都设有一个唯一的ID。

    窗格(pane)使用 ``%`` 开头，例如 ``%1234``

    窗口(window)使用 ``@`` 开头，例如 ``@2345``

    会话(session)使用 ``$``, 例如 ``$``

Tmuxp如何处理无命名窗口(window)？

    Tmux会给每个窗口分配一个唯一的 ``window_id`` 做为标识。

{pane,window}_index VS a {pane,window,session}_id 的区别是什么?

    Pane是根据屏幕中窗格的排布次序来编排序数。

    window是根据会话中窗格的#来编排序数。

为了检验窗格(pane),窗口(window),会话(session)，
Tmuxp使用 :meth:`Server.list_sessions()`, :meth:`Session.list_windows()`,
:meth:`Window.list_panes()` 来更新数据。


特性(Idiosyncrasies)
--------------------

因为Tmuxp是用python实现的，所以诸如 ``new-window`` 这样的命令都会使用减号(-)而非下划线(_)


引用(Reference)
---------------

- tmux 文档 http://www.openbsd.org/cgi-bin/man.cgi?query=tmux&sektion=1
- tmux 源代码 http://sourceforge.net/p/tmux/tmux-code/ci/master/tree/

.. _abstraction layer: http://en.wikipedia.org/wiki/Abstraction_layer
.. _ORM: http://en.wikipedia.org/wiki/Object-relational_mapping
