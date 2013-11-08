.. _examples:

==============
示例(Examples)
==============

简短参数/命令行参数(Short hand / inline)
----------------------------------------

.. sidebar:: short hand

    .. aafig::
       :textual:

        +-------------------+
        | 'did you know'    |
        | 'you can inline'  |
        +-------------------+
        | 'single commands' |
        |                   |
        +-------------------+
        | 'for panes'       |
        |                   |
        +-------------------+

YAML
""""

.. literalinclude:: ../examples/shorthands.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/shorthands.json
    :language: json

分割出两个面板(2 split panes)
-----------------------------

.. sidebar:: 2 pane

    .. aafig::

        +-----------------+
        | $ pwd           |
        |                 |
        |                 |
        +-----------------+
        | $ pwd           |
        |                 |
        |                 |
        +-----------------+

YAML - Short form
"""""""""""""""""

.. literalinclude:: ../examples/2-pane-vertical.yaml
    :language: yaml

JSON - Short form
"""""""""""""""""

.. literalinclude:: ../examples/2-pane-vertical.json
    :language: json

YAML - 圣诞树结构(Christmas Tree)
"""""""""""""""""""""""""""""""""

.. literalinclude:: ../examples/2-pane-vertical-long.yaml
    :language: yaml

JSON - 圣诞树结构(Christmas Tree)
"""""""""""""""""""""""""""""""""

.. literalinclude:: ../examples/2-pane-vertical-long.json
    :language: json

三个面板(3 panes)
-----------------

.. sidebar:: 3 panes

    .. aafig::

        +-----------------+
        | $ pwd           |
        |                 |
        |                 |
        +--------+--------+
        | $ pwd  | $ pwd  |
        |        |        |
        |        |        |
        +--------+--------+

YAML
""""

.. literalinclude:: ../examples/3-pane.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/3-pane.json
    :language: json

四个面板(4 panes)
-----------------

.. sidebar:: 4 panes

    .. aafig::

        +--------+--------+
        | $ pwd  | $ pwd  |
        |        |        |
        |        |        |
        +--------+--------+
        | $ pwd  | $ pwd  |
        |        |        |
        |        |        |
        +--------+--------+

YAML
""""

.. literalinclude:: ../examples/4-pane.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/4-pane.json
    :language: json


自动重命名(Automatic Rename)
----------------------------

YAML
""""

.. literalinclude:: ../examples/automatic-rename.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/automatic-rename.json
    :language: json

定制主面板高度(Main pane height)
--------------------------------

YAML
""""

.. literalinclude:: ../examples/main-pane-height.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/main-pane-height.json
    :language: json

定制启动目录(Start Directory)
-----------------------------

等同于 ``tmux new-window -c <start-directory>``.

YAML
""""

.. literalinclude:: ../examples/start_directory.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/start_directory.json
    :language: json


定制高级开发环境(Super-advanced dev environment)
------------------------------------------------

.. seealso::
    详见 :ref:`developing` 中的 :ref:`tmuxp developer config`

YAML
""""

.. literalinclude:: ../.tmuxp.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../.tmuxp.json
    :language: json



功夫(Kung fu)
-------------

.. note::

    tmuxp的会话(session)是可以用python脚本进行定制的。第一个方法是使用 :ref:`API` 中的方法
    第二个方法是给 :class:`tmuxp.WorkspaceBuilder` 传递一个符合规格的 :py:obj:`dict` 字典。
    详见 :meth:`tmuxp.config.check_consistency` 。

tmuxp需要您的指点，欢迎您在 `github`_ 上赐教。

.. _github: https://github.com/tony/tmuxp
