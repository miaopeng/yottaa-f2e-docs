JSHint Configration
===================

The ``ui`` gem repository contains a standard `.jshintrc`_ for use with Yottaa projects.

.. _.jshintrc: https://github.com/Yottaa/ui/blob/develop/.jshintrc

See:

* `Install JSHint`_
* `JSHint options`_

.. _Install JSHint: http://www.jshint.com/install/ 
.. _JSHint options: http://www.jshint.com/docs/options/

Intergration With VIM
---------------------

Manually run JSHint with a hotkey

.. code-block:: vim

  " vimrc
  noremap <F2> <ESC>:JSHint<CR>

Auto run JSHint with ``Syntastic`` plugin when saving file 

.. code-block:: vim

  " vimrc
  Plugin 'Syntastic'
  let g:syntastic_javascript_checkers = ['jshint']
