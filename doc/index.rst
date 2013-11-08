tmuxp
=====

.. image:: _static/tmuxp-dev-screenshot.png
    :scale: 35%
    :width: 100%
    :align: right


tmuxp是一个全新的tmux协助工具，它使用 `python对象`_ 来管理 `tmux(1)`_ (>= 1.8) 的工作区，极大改善了tmux的使用体验。

- 实现了对 `冻结活动会话`_ 的基本支持。
- 可以 `导入`_  `teamocil`_ 和 `tmuxinator`_ 。
- 使用JSON或YAML进行 `简单`_ 或 `更灵活复杂`_ 的配置。
- 支持 `bash, zsh 以及 tcsh`_ 。
- 已在tmux(1.8版及git下的最新版)下通过单元测试。详见 `travis.yml`_
  ， `Travis CI下自动测试tmuxp`_ 和 `测试`_ 。
- `文档`_, `示例`_, `内部构造`_ 。
- `了解更多`_ 。


如果您有兴趣，不妨先试看看 `快速入门`_ 。

.. _Travis CI下自动测试tmuxp: http://travis-ci.org/tony/tmuxp
.. _文档: http://tmuxp_cn.rtfd.org/
.. _tmux(1): http://tmux.sourceforge.net/
.. _tmuxinator: https://github.com/aziz/tmuxinator
.. _teamocil: https://github.com/remiprev/teamocil
.. _示例: examples.html
.. _冻结活动会话: cli.html#freeze-sessions
.. _导入: cli.html#import
.. _travis.yml: developing.html#travis-ci
.. _测试: developing.html#test-runner
.. _python对象: api.html#api
.. _简单: examples.html#short-hand-inline
.. _更灵活复杂: examples.html#super-advanced-dev-environment
.. _bash, zsh 以及 tcsh: cli.html#bash-completion
.. _了解更多: about.html#minor-tweaks
.. _快速入门: quickstart.html
.. _内部构造: internals.html


Explore:

.. toctree::
    :maxdepth: 2

    about
    cli
    quickstart
    examples
    internals
    developing
    api
    changes
    roadmap
    about_tmux
    glossary

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
