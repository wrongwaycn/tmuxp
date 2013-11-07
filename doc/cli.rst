.. _cli:

==========
命令行接口
==========

.. _cli_freeze:

冻结会话(Freeze Session)
""""""""""""""""""""""""

您可以通过冻结操作来保存您当前的tmux会话。

.. code-block:: bash

    $ tmuxp freeze <session-name>

Tmuxp 可以将您的会话保存为 ``.json`` 和 ``.yaml`` 格式。

``v0.0.37`` 支持冻结 `virtualenv`_ ，

.. _virtualenv: http://www.virtualenv.org/

.. _cli_load:

加载会话(Load Session)
""""""""""""""""""""""

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


.. code-block:: bash

    $ tmuxp import teamocil <filename>

.. _import_tmuxinator:

从tmuxinator导入(From tmuxinator)
'''''''''''''''''''''''''''''''''

.. code-block:: bash

    $ tmuxp import tmuxinator <filename>

.. _convert_config:

在YAML和JSON转换(Convert between YAML and JSON)
"""""""""""""""""""""""""""""""""""""""""""""""

.. code-block:: bash

    $ tmuxp convert <filename>

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

命令行
""""""

.. argparse::
    :module: tmuxp.cli
    :func: get_parser
    :prog: tmuxp

