
Tips and Tricks
===============

jQuery
------

1. Don't use ``$.live`` and ``$.die``, use ``$.on`` instead.

2. Don't use ``$.browser`` to determine browser, try to use feature detection instead.

Passing data
------------

1. Don't use this pattern to pass data to javascript:

  .. code-block:: haml
    
    / Extra hidden html tags in haml.
    %input#profiles_list_url{:type => 'hidden', :value => ui_monitors_path}

  .. code-block:: javascript

    // js
    url = $('#profiles_list_url').val();

  Resolution 1: passing data to application global object with inline javascript:

  .. code-block:: haml

    / inline js in haml
    :javascript
      app.init({
        url: '#{@url}';
      });
  
  Resolution 2: use ``data`` attribute of related html elements and ``$.fn.data``

  .. code-block:: haml

    / haml
    #profile{data: { url: profile_path } }

  .. code-block:: javascript

    // js
    $('#profile').data();
