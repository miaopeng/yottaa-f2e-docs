Javascript Style Guideline
=================================

Linting
-------

Use ``JSHint`` to detect errors and potential problems.

More information can be found in the :doc:`jshint` page.

Use ``Google Closure Linter`` to detect and fix coding style erros.

More information can be found in the :doc:`closure` page.

Language Rules
--------------

1. Semicolons

  Always use semicolons.

  *validator: JSHint*

2. Commas

  Do not do this:

  .. code-block:: javascript

    var arr = [1,2,3,];

  *validator: JSHint(es3: true)*
 
3. Declarations

  Avoid undeclared variables. 

  *validator: JSHint(undef: true)*

  Avoid additional global variables.

4. Equality

  Strict equality checks (===) must be used in favor of abstract equality checks (==). 
  The only exception is when checking for ``undefined`` and ``null`` by way of ``null``

  .. code-block:: javascript

    undefOrNull == null

  *validator: JSHint(eqeqeq: true, eqnull: true)*

5. Eval

   Avoid to use ``eval``. 
   Using ``JSON.parse()`` or ``$.parseJSON()`` instead of ``eval()`` to parse JSON result.

   *validator: JSHint*
 
6. Deprecated

   Don't use ``with``, ``__proto__``, ``arguments.caller`` and ``arguments.callee``

   *validator: JSHint(noarg: true, proto: false)*


Style Rules
-----------

1. Naming

  In general, use ClassNamesLikeThis, functionNamesLikeThis, 
  variableNamesLikeThis, CONSTANT_VALUES_LIKE_THIS and file_names_like_this.js.

  We do not force use prefix on variable names and method names. 
  But if you do, then meaning you follow some rules below: 

  .. list-table::

    * - Prefix
      - Type
      - Example
    * - $
      - jQuery Object
      - $body
    * - _
      - Private Method
      - _init
    * - s
      - String
      - sName
    * - o
      - Object
      - oResult
    * - is, can, has
      - Boolean
      - isRoot

   

2. Indentation

  4 spaces and no tabs.

3. Quotes

  Prefer ``'`` over ``"``

4. Declarations

  Multiple declarations in one ``var`` and go with line ending commas like below:

  .. code-block:: javascript

    var foo = '',
        bar = '',
        foobar;


  Declarations should always put top of content in function.

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

