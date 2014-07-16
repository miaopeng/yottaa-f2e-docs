JSHint Configration
======================

.. code-block:: json

  {

      // Allows globals: 'document', 'navigator' and 'FileReader'
      "browser": true,

      // Allows globals: 'escape' and 'unescape'
      "nonstandard": true,

      // Allows custom globals
      "globals": {
          "jQuery":  true,
          "$": true,
          "_": true
      },

      // Disallows globals: 'alert' and 'console'
      "devel":		false,

      // Disallows globals: 'debugger'
      "debug": 		false,

      // Disallows ES5 features. (ES5 is supported from IE9)
      "es3":			true,

      // Do not force to use strict mode
      "strict":		false,

      // Do not use ES6 syntax
      "esnext":		false,

      // Do not prohibits the use of == and != in favor of === and !==?
      "eqeqeq":		true,


      // Allows using '== null' comparisons
      "eqnull":		true,

      // Allows expressions like 'a && a()' or 'a ? a() : b()'
      "expr":			true,

      // Do not allow 'var a = function() { ... }();'
      // Recommendation: 'var a = (function() { ... })();' 
      "immed":		true,

      // Do not use arguments.caller and arguments.callee
      "noarg":		true,

      // Disallows undeclared variables
      "undef": true,

      // This option warns when you define and never use your variables
      "unused": true,

      // Allows code like 'if (a = 10) {}'
      "boss": true,

      // Allows eval
      "evil": true,

      "shadow": false,

      // Disallows using '__proto__' property
      "proto": false,

      "validthis": true,

      // Please add semicolons in the end of line
      "asi": false,

      "laxbreak": true,

      "laxcomma": true,

      // This option requires you to always put curly braces around blocks in 
      // loops and conditionals.?
      "curly": false,

      // Disallows to call constructor functions without assigning its result 
      // to any variable: 'new MyConstructor();'
      "nonew": true,

      // This option suppresses warnings about using [] notation when it can 
      // be expressed in dot notation: person['name'] vs. person.name.
      "sub": false,

      // Allows functions inside of loops
      "loopfunc": true,

      // Allows 'javascript:' URL
      "scripturl": true,

      // Allows correct multi-line strings, it still warns about multi-line
      // strings without escape characters or with anything in between the
      // escape character and a whitespace.
      "multistr": true
  }

