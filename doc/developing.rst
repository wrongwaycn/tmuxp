.. module:: tmuxp

.. _developing:

==================================
开发及测试(Developing and Testing)
==================================

.. todo::
    link to sliderepl or ipython notebook slides

测试用例位于 ``./tmuxp/testsuite`` 中，由
:py:mod:`unittest` 实现。

``./run_tests.py`` 使用 ``$ tmux -L test_case`` 在单独的一个 ``socket_name`` 上创建一个tmux服务(server)。

.. _install_dev_env:

从git获取最新代码并安装(Install the latest code from git)
---------------------------------------------------------

进行开发的第一步就是从git上获取最新代码:

.. code-block:: bash

    $ git clone git@github.com:tony/tmuxp.git
    $ cd tmuxp

接下来创建一个virtualenv环境，如果您尚不了解如何创建virtualenv环境，可以直接使用下面的命令:

.. code-block:: bash

    $ virtualenv .env

然后在当前终端(tty/terminal)下激活virtualenv环境:

.. code-block:: bash

    $ source .env/bin/activate

下面就可以安装tmuxp了:

.. code-block:: bash

    $ pip install -e .

使用pip包管理器可以在当前目录下安装python包， ``-e`` 表示 ``--editable``, 意味着你可以修改源代码，
而且修改结果会反映到已安装的包。

.. code-block:: bash

    $ tmuxp

测试运行器(Test Runner)
-----------------------

如上步骤所示，在完成python虚拟环境搭建后并进入该环境后，
当前 `PATH` 环境就会发生变化，以包含位一个位于 ``.env`` 目录下特定版本的自带类库的 ``python`` 。
然后就可以运行 ``tmuxp`` 命令。

接下来执行:

.. code-block:: bash

    $ ./run_tests.py

就会看到很多测试信息源源不断地滚屏显示。

如果您发现了问题或是想提交一个测试，你可以在 `在github上发起问题(issue on github)`_ 。

.. _test_specific_tests:

测试运行器的参数(Test runner options)
"""""""""""""""""""""""""""""""""""""

.. note::

    截止到v0.0.20, ``--tests`` 会默认使用 ``tmuxp.testsuite`` 。


    .. code-block:: bash

        $ ./run_tests.py --tests test_config.ImportExportTest

    等同于:

    .. code-block:: bash

        $ ./run_tests.py --tests tmuxp.testsuite.test_config.ImportExportTest


对特定的测试套件，测试案例，测试个体进行测试

.. code-block:: bash

    $ ./run_tests.py --help

上述操作将显示出您可选择的所有测试套件。比如 ``test_config`` :

使用 :py:class:`unittest.TestSuite` :

.. code-block:: bash

    $ ./run_tests.py test_config

使用 :py:class:`unittest.TestCase`:

.. code-block:: bash

    $ ./run_tests.py --tests test_config.ImportExportTest

单独测试:

.. code-block:: bash

    $ ./run_tests.py --tests test_config.ImportExportTest.test_export_json

多个测试之间可以用空格间隔开:

.. code-block:: bash

    $ ./run_tests.py --tests ImportExportTest.test_export_json \
        ImportExportTest.test_window

.. _test_builder_visually:

可视化的测试(Visual testing)
''''''''''''''''''''''''''''

您可以单独打开一个终端用来观察tmux测试套件如何创建会话(session)。

打开两个终端:

  - 终端 1: ``$ tmux -L test_case``
  - 终端 2: ``$ cd`` 进入tmuxp项目目录，并启用 ``virtualenv`` 进入虚拟环境
    (详见上文所述如何安装tmuxp开发版)，然后运行:

    .. code-block:: bash
    
        $ python ./run_tests.py --tests tests_workspacebuilder

终端1 会闪烁一下然后在您的肉眼查觉之前就已经完成了对会话(session)的创建。
tmuxp对普通用户隐藏了这部分信息。

记录和日志(Verbosity and logging)
'''''''''''''''''''''''''''''''''

``./run_tests.py`` supports two options, these are *optional* flags that
may be added to for :ref:`test_specific_tests` and
:ref:`test_builder_visually`.
``./run_tests.py`` 支持两个选项，可以添加到 :ref:`test_specific_tests` 和 :ref:`test_builder_visually` 。

1.  日志等级: ``-l`` 又可以表示为 ``--log-level``, 可以设为 ``debug``,
    ``info``, ``warn``, ``error``, ``fatal``. 默认为 ``INFO`` 。

    .. code-block:: bash

        $ ./run_tests.py --log-level debug

    简短形式:

    .. code-block:: bash

        $ ./run_tests.py -l debug

2.  单元测试记录:

    ``--verbosity`` 可以设置为 ``0``, ``1`` 和 ``2``.  默认为: ``2``.

    .. code-block:: bash

        $ ./run_tests.py --verbosity 0

保存文件时自动运行测试(Run tests on save)
-----------------------------------------

Tmux可以监控文件的改动，在保时时自动运行测试。

.. note::
    这个功能需要从pypi中安装 ``watching_testrunner`` 。

从 `pypi`_ 中安装 `watching_testrunner`_:

.. code-block:: bash

    $ pip install watching_testrunner

编辑任何一个 ``.py`` 文件都会引发所有测试:

.. code-block:: bash

    $ watching_testrunner --basepath ./ --pattern="*.py" python run_tests.py

如果只想引发 :ref:`test_builder_visually` :

.. code-block:: bash

    $ watching_testrunner --basepath ./ --pattern="*.py" python run_tests.py --visual

.. _watching_testrunner: https://pypi.python.org/pypi/watching_testrunner/1.0
.. _pypi: https://pypi.python.org/pypi

.. _tmuxp developer config:

tmuxp开发者配置(tmuxp developer config)
"""""""""""""""""""""""""""""""""""""""

.. image:: _static/tmuxp-dev-screenshot.png
    :scale: 100%
    :width: 60%
    :align: center

:ref:`install_dev_env` ，签出tmxp之后运行:

.. code-block:: bash

    $ tmuxp load .

上面的操作会在项目根目录下载入 ``.tmuxp.yaml`` 文件。

.. literalinclude:: ../.tmuxp.yaml
    :language: yaml

.. _travis:

Travis CI
"""""""""

Tmuxp使用 `travis-ci`_ 所提供的持续集成/自动化单元测试。

travis支持多种场景下的测试，当前tmuxp已通tmux1.8版本和python2.7下的测试。
`travis下tmuxp测试`_ 使用 `.travis.yml`_ 配置:

.. literalinclude:: ../.travis.yml
    :language: yaml

.. _travis-ci: http://www.travis-ci.org
.. _travis下tmuxp测试: http://www.travis-ci.org/tony/tmuxp
.. _.travis.yml: https://github.com/tony/tmuxp/blob/master/.travis.yml
.. _在github上发起问题(issue on github): https://github.com/tony/tmuxp/issues
