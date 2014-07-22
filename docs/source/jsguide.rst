Javascript Style Guideline
=================================

Linting
-------

Use JSHint to detect errors and potential problems.The options for JSHint are stored in a .jshintrc file;

Language Rules
--------------

Semicolons

  Always use semicolons.

Commas

  Do not do this:

  .. code-block:: javascript

    var arr = [1,2,3,];
 
Declarations

  Always use var for declarations. Avoid additional global variables.

  Multiple declarations in one var and go with line ending commas like below:

  .. code-block:: javascript

    var foo = '',
        bar = '',
        foobar;


 Declarations should always put top of content in function

 Good:

 .. code-block:: javascript

      var isvalid;
      if (n > 0) {
          isvalid = true;
      } 

 Bad:

 .. code-block:: javascript

      if (n > 0) {
          var isvalid = true;
      } 

* Do not use ``with`` ``void`` ``eval``
* Equality

  Strict equality checks (===) must be used in favor of abstract equality checks (==). 
  The only exception is when checking for ``undefined`` and ``null`` by way of ``null``

  .. code-block:: javascript

    undefOrNull == null


Style Rules
-----------

* Indentation

  4 spaces and no tabs.

* Quotes

  Prefer ``'`` over ``"``
