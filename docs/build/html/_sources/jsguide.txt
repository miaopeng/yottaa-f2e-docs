Yottaa Javascript Style Guideline
=================================

Linting
-------

Use JSHint to detect errors and potential problems.The options for JSHint are stored in a .jshintrc file;

Language Rules
--------------

* Semicolons

  Always use semicolons.

* Commas

  Do not do this:

  .. code-block:: bash

    var arr = [1,2,3,];
 
* Declarations

  Always use var for declarations. Avoid additional global variables.

  Multiple declarations in one var and go with line ending commas like below:

  .. code-block:: bash

    var foo = '',
        bar = '',
        foobar;

Style Rules
-----------

* Indentation

  For spaces and no tabs.

* Quotes

  Prefer ' over "
