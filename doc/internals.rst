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

tmuxp is was built in the spirit of understanding how tmux operates
and how python objects and tools can abstract the API's in a pleasant way.

tmuxp uses ``FORMATTERS`` in tmux to give identity attributes to
:class:`Session`, :class:`Window` and :class:`Pane` objects. See
`formatters.c`_.

.. _formatters.c: http://sourceforge.net/p/tmux/tmux-code/ci/master/tree/format.c

How is tmuxp able to keep references to panes, windows and sessions?

    Tmux has unique ID's for sessions, windows and panes.

    panes use ``%``, such as ``%1234``

    windows use ``@``, such as ``@2345``

    sessions use ``$``, for money, such as ``$``

How is tmuxp able to handle windows with no names?

    Tmux provides ``window_id`` as a unique identifier.

What is a {pane,window}_index vs a {pane,window,session}_id?

    Pane index refers to the order of a pane on the screen.

    Window index refers to the # of the pane in the session.

To assert pane, window and session data, tmuxp will use
:meth:`Server.list_sessions()`, :meth:`Session.list_windows()`,
:meth:`Window.list_panes()` to update objects.

Idiosyncrasies
--------------

Because this is a python abstraction and commands like ``new-window``
have dashes (-) replaced with underscores (_).

Reference
---------

- tmux docs http://www.openbsd.org/cgi-bin/man.cgi?query=tmux&sektion=1
- tmux source code http://sourceforge.net/p/tmux/tmux-code/ci/master/tree/

.. _abstraction layer: http://en.wikipedia.org/wiki/Abstraction_layer
.. _ORM: http://en.wikipedia.org/wiki/Object-relational_mapping
