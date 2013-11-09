.. _quickstart:

==========
Quickstart
==========

CLI
---

.. seealso:: :ref:`examples`, :ref:`cli`, :ref:`bash_completion`.

tmuxp launches sessions from a configuration file.

Configuration files can be stored in ``$HOME/.tmuxp`` or in project
directories as ``.tmuxp.py``, ``.tmuxp.json`` or ``.tmuxp.yaml``.

Every configuration is required to have:

1. ``session_name``
2. list of ``windows``
3. list of ``panes`` for every window in ``windows``

Create a file, ``~/.tmuxp/example.yaml``:

.. literalinclude:: ../examples/2-pane-vertical.yaml
    :language: yaml

with tmuxp:

.. code-block:: bash

    $ tmuxp load -l

It will list configs available in the current directory and
``$HOME/.tmuxp``. ``example.yaml`` is detected by tmuxp. 

.. code-block:: bash

    $ tmuxp load example.yaml

This creates your tmuxp session.


Pythonics
---------

.. seealso::
    :ref:`tmuxp python API documentation <api>` and :ref:`developing`,
    :ref:`internals`.


ORM - `Object Relational Mapper`_

AL - `Abstraction Layer`_

.. _Abstraction Layer: http://en.wikipedia.org/wiki/Abstraction_layer
.. _Object Relational Mapper: http://en.wikipedia.org/wiki/Object-relational_mapping

python abstraction layer
""""""""""""""""""""""""

.. module:: tmuxp

======================================== =================================
:ref:`tmuxp python api <api>`            :term:`tmux(1)` equivalent
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

tmuxp's core internal feature is the object relation and orchestration of
the tmux server (think an `engine`_ in `SQLAlchemy`_) and the server's
sessions, so on...

- :class:`Server` holds :class:`Session` objects.
- :class:`Session` holds :class:`Window` objects.
- :class:`Window` holds :class:`Pane` objects.

instances of tmux objects use tmux `1.8`_'s ``pane_id``, ``window_id`` and
``session_id`` to build create python objects to build workspaces with the
freshest data.

.. _engine: http://docs.sqlalchemy.org/en/rel_0_8/core/engines.html
.. _sqlalchemy: http://www.sqlalchemy.org/
.. _1.8: http://sourceforge.net/projects/tmux/files/tmux/tmux-1.8/
