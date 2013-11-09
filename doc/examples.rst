.. _examples:

========
Examples
========

Short hand / inline
-------------------

tmuxp has a short-hand syntax to for those who wish to keep their configs
punctual.

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

Blank panes
-----------

No need to repeat ``pwd`` or a dummy command. A ``null``, ``'blank'``,
``'pane'`` are valid.

Note ``''`` counts as an empty carriage return.

YAML
""""

.. literalinclude:: ../examples/blank-panes.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/blank-panes.json
    :language: json

Start Directory
---------------

Equivalent to ``tmux new-window -c <start-directory>``.

YAML
""""

.. literalinclude:: ../examples/start-directory.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/start-directory.json
    :language: json

2 split panes
-------------

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

YAML - Christmas Tree
"""""""""""""""""""""

.. literalinclude:: ../examples/2-pane-vertical-long.yaml
    :language: yaml

JSON - Christmas Tree
"""""""""""""""""""""

.. literalinclude:: ../examples/2-pane-vertical-long.json
    :language: json

3 panes
-------

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

4 panes
-------

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


Automatic Rename
----------------

YAML
""""

.. literalinclude:: ../examples/automatic-rename.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/automatic-rename.json
    :language: json

Main pane height
----------------

YAML
""""

.. literalinclude:: ../examples/main-pane-height.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../examples/main-pane-height.json
    :language: json

Super-advanced dev environment
------------------------------

.. seealso::
    :ref:`tmuxp developer config` in the :ref:`developing` section.

YAML
""""

.. literalinclude:: ../.tmuxp.yaml
    :language: yaml

JSON
""""

.. literalinclude:: ../.tmuxp.json
    :language: json


Kung fu
-------

.. note::

    tmuxp sessions can be scripted in python. The first way is to use the
    ORM in the :ref:`API`. The second is to pass a :py:obj:`dict` into
    :class:`tmuxp.WorkspaceBuilder` with a correct schema. See:
    :meth:`tmuxp.config.validate_schema`.

Add yours? Submit a pull request to the `github`_ site!

.. _github: https://github.com/tony/tmuxp
