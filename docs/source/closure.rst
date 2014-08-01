Google Closure Linter
=====================

Use ``gjslint`` check javascript files for style issues.
Use ``fixjsstyle`` fix many of the issues automatically.

See: `Google Closure Linter`_

.. _Google Closure Linter: https://developers.google.com/closure/utilities/

Install
-------

.. code-block:: bash

  sudo easy_install http://closure-linter.googlecode.com/files/closure_linter-latest.tar.gz

Intergration With VIM
---------------------

.. code-block:: vim

  " function for run fixjsstyle on current file
  function! ModifyByFixJsStyle()
    " save positions
    let pos = s:SavePositions()

    let tempfile = tempname() . '.js'
    silent call writefile(getbufline(bufname('%'), 1, '$'), tempfile)
    try
        " use fixjsstyle as filter
        silent! execute '!fixjsstyle --nojsdoc' tempfile

        1,$delete "_
        execute 'read' tempfile
        1delete "_

        " restore positions
        call s:RestorePositions(pos)
    catch
        echoerr v:exception
    finally
        call delete(tempfile)
    endtry
  endfunction

Intergration With Atom
----------------------

Install the Atom package `Closure Linter`_, and reopen the Atom editor with:

.. code-block:: bash
  
  atom .

Then you can run `fixjsstyle` on current file with `⌃⌘j` (ctrl-cmd-j) or select 
'Closure Linter: Fixjsstyle' command on the command menu.

.. _Closure Linter: https://atom.io/packages/closure-linter
