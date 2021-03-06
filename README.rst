==============================================
 Jedi.el - a Python auto-completion for Emacs
==============================================

Jedi.el is a Python auto-completion package for Emacs.

Links:

* `Documentation (at GitHub Pages) <http://tkf.github.com/emacs-jedi/>`_
* `Repository (at GitHub) <https://github.com/tkf/emacs-jedi>`_
* `Issue tracker (at GitHub) <https://github.com/tkf/emacs-jedi/issues>`_


Requirements
============

Jedi.el uses jedi_ library to compute completion and EPC_ (an RPC
stack for Emacs Lisp) and its `Python binding`_ to commentate with
Python process.  It also uses excellent Emacs auto-complete_ module to
start completion automatically.  As Jedi.el always calls Python
function asynchronously (thanks to EPC_), it will not block your Emacs
while your are editing.

.. _jedi: https://github.com/davidhalter/jedi
.. _EPC: https://github.com/kiwanami/emacs-epc
.. _Python binding: python-epc_
.. _python-epc: https://github.com/tkf/python-epc
.. _auto-complete: https://github.com/auto-complete/auto-complete


Install
=======

el-get
------

The easiest way to install Jedi.el is to use el-get_:
just do ``M-x el-get-install jedi``.
You need to have `virtualenv` to automatically install Python module
dependencies.  If your el-get does not have the recipes for Jedi.el
yet, get them from `this pull request`_.

.. _el-get: https://github.com/dimitri/el-get
.. _this pull request: https://github.com/dimitri/el-get/pull/927

Manual install
--------------

1. Install EPC_ and auto-complete_.
2. Install Jedi.el.  Download this repository and add it to
   `load-path`.
3. Install Jedi_ and python-epc_ by ``make requirements`` or ``pip
   install jedi epc`` if you want to determine where to install them.
4. Add ``(require 'jedi)`` in your Emacs configuration.


Setup
=====

All you need to do is to call `jedi:setup` in python buffer.
To do that, add the following in your Emacs configuration::

   (add-hook 'python-mode-hook 'jedi:setup)

If auto-completion is all you need, use `jedi:ac-setup` instead::

   (add-hook 'python-mode-hook 'jedi:ac-setup)

If you want to manually invoke completion, use something like this::

   (define-key python-mode-map (kbd "<C-tab>") 'jedi:complete)
