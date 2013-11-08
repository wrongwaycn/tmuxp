.. _cli:

==================================
命令行接口(Command Line Interface)
==================================

.. _cli_freeze:

冻结会话(Freeze sessions)
"""""""""""""""""""""""""

.. argparse::
    :module: tmuxp.cli
    :func: get_parser
    :prog: tmuxp
    :path: freeze


    您可以通过冻结操作来保存您当前的tmux会话(session)。

    Tmuxp 可以将您的会话(session)保存为 ``.json`` 和 ``.yaml`` 格式。

.. _cli_load:

加载会话(Load session)
""""""""""""""""""""""

.. argparse::
    :module: tmuxp.cli
    :func: get_parser
    :prog: tmuxp
    :path: load

    把配置文件放在 ``$HOME/.tmuxp`` 目录下便于访问，也便于被 :ref:`bash_completion` 探测到。

    当然，文件也可以放在任意路径下。

    .. code-block:: bash

        $ tmuxp load <filename>

    如果在当前工作目录下有 ``.tmuxp.yaml`` 或 ``.tmuxp.json`` 配置文件，可以如下这样加载:

    .. code-block:: bash

        $ tmuxp load .

.. _cli_import:

导入(Import)
""""""""""""

.. _import_teamocil:

从teamocil导入(From teamocil)
'''''''''''''''''''''''''''''

.. argparse::
    :module: tmuxp.cli
    :func: get_parser
    :prog: tmuxp
    :path: import teamocil

.. _import_tmuxinator:

从tmuxinator导入(From tmuxinator)
'''''''''''''''''''''''''''''''''

.. argparse::
    :module: tmuxp.cli
    :func: get_parser
    :prog: tmuxp
    :path: import tmuxinator

.. _convert_config:

在YAML和JSON间转换(Convert between YAML and JSON)
"""""""""""""""""""""""""""""""""""""""""""""""""

.. argparse::
    :module: tmuxp.cli
    :func: get_parser
    :prog: tmuxp
    :path: convert


    tmuxp可以自动地，准确无误地将 ``.yaml`` 转换为 ``.json`` 或是将 ``.json`` 转换为  ``.yaml`` 。

.. _bash_completion:

Bash实现(Bash completion)
"""""""""""""""""""""""""

在bash下， ``.bashrc``:

.. code-block:: bash

    $ source tmuxp.bash

在tcsh下， ``.tcshrc``:

.. code-block:: bash

    $ complete tmuxp 'p/*/`tmuxp.tcsh`/'

在zsh下， ``.zshrc``:

.. code-block:: bash

    $ source tmuxp.zsh

.. _commands:

其他命令(Other commands)
""""""""""""""""""""""""

.. argparse::
    :module: tmuxp.cli
    :func: get_parser
    :prog: tmuxp
    :path: kill-session

.. argparse::
    :module: tmuxp.cli
    :func: get_parser
    :prog: tmuxp
    :path: attach-session
