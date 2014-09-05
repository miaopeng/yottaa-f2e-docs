CSS Style Guideline
===================

Tools
-----

Precompiler:

  We use the css precompiler `SASS`_ and the ``SCSS`` syntax.

Linting:

  We use `scss-lint`_ for SASS coding style linting.

  The ``ui`` gem repository contains a configration file `.scss-lint.yml`_ for use with Yottaa projects.

  .. _.scss-lint.yml: https://github.com/Yottaa/ui/blob/develop/.scss-lint.yml

Mixins:

  We use `compass`_ for SASS mixins.

.. _SASS: http://sass-lang.com
.. _scss-lint: https://github.com/causes/scss-lint
.. _compass: http://compass-style.org

Selectors
---------

1. The most ideal way is only use the ``class`` selector.
   Beware of misusing the ``id`` selector and ``tag`` selector.

   The ``id`` selector is for unique views only.Elements that occur exactly once
   inside a page should use IDs, otherwise, use classes.

   * Good candidates for ids: header, footer, modal popups.
   * Bad candidates for ids: navs, listings, item views.
   
   Don't use comman ``tag`` selectors: ``div {}``, ``a {}``, ``span {}``

   Use ``tag`` selectors just for some fixed html structrues: ``.nav li {}``,
   ``.select option {}``

   A example of an over-qualified selector might be ``ul.nav li a {}``.
   We can instantly drop the ul and because we know ``.nav`` is a list, we 
   therefore know that any ``a`` must be in an ``li``, so we can get 
   ``ul.nav li a {}`` down to just ``.nav a {}``.

2. Avoding use ``tag``, ``[attr=value]`` and ``:hover`` as the last selector(key selector).

   Never use ``*`` selector.

   Avoding these slow efficiency selectors:
   
  .. code-block:: css

    body > * {...}
    ul > li > a {...}
    ul#top_blue_nav {...}
    #searbar span.submit a { ... }
    .target #target-node { ... }

3. Don't use to many level for selector. 1 ~ 3 levels is the best. In SCSS,
   only one nesting levels at most.


Naming
------

1. Using lowercase with hyphens for ids, classes, variable names and mixin names.

2. ID and class's name must clear and concisely. e.g. #users, .list

   The bad:

   .. code-block:: css

     #abc
     .red
     .corner_bl_4

   The good:

   .. code-block:: css

      #monitor-list
      .nav-item
      .infobox
      .pagehead


   The recommanded class names:

  .. list-table::

    * - Type
      - Example
    * - status
      - .on, .active, .disabled
    * - position
      - .main, .side, .first, .last
    * - structure
      - .mod, .hd, .bd, .ft
    * - common
      - .tb, .frm, .dlg, .nav, .list, .item, .info

3. JS hooks
   Use ``js-`` prefix classes for js hooks only. Don't define styles for ``js-``
   classes.

Style
-----

Multi line rules for scss files, single line for one rule or inline css.

  The good for multi lines of SASS:

  .. code-block:: css

    @import 'compass';

    //----------------------------------
    // Simple Card
    // 
    // @usage:
    //   <div class="simple-card">
    //     <div class="hd">Title</div>
    //     <div class="bd">Content</div>
    //   </div>
    //-----------------------------------


    // Placeholder %card

    %card {
      @include clearfix;
      @include border-radius(2px);
    }

    // simple-card

    .simple-card {
      @extend %card;
      border: 0;
      background-color: #ffe;

      > .bd { color: #444; }

      .nav-stack,
      .nav-list {
        padding: 0 5px 10px;
        @include opacity(.5);
      }
    }

  The good for single line of css:
  
  .. code-block:: css

    .monitor-list { display: block; padding: 0; margin: 0; }
    .monitor-list .hd { color: #333; }


Layout
------

1.Clear floats with ``overflow`` or ``after``, don't add extra tags in html.

  Preferred for the usual case:

  .. code-block:: css

    @include clearfix;

    // if the placeholder '%clearfix' exists
    @extend %clearfix;
   
  If you need to allowing positioned elements to hang outside the bounds of the container:

  .. code-block:: css

    @include pie-clearfix; // PIE = Position Is Everything

2. All components you build should be left totally free of widths; they should 
   always remain fluid and their widths should be governed by a parent/grid 
   system.
   
   Heights should never be be applied to elements. Heights should only be 
   applied to things which had dimensions before they entered the site 
   (i.e. images and sprites). Never ever set heights on ps, uls, divs, 
   anything. You can often achieve the desired effect with line-height 
   which is far more flexible.

3. ``Compass`` provides some good helpers to build layout structures:

   .. code-block:: css

     .ip-list {
       @include inline-block-list;
     }

Shorthand
---------

Shorthand CSS needs to be used with caution.

It might be tempting to use declarations like `background: red;` but in 
doing so what you are actually saying is ‘I want no image to scroll, 
aligned top-left, repeating X and Y, and a background colour of red’. 
Nine times out of ten this won’t cause any issues but that one time it does is 
annoying enough to warrant not using such shorthand. Instead use 
`background-color: red;`.

Deprecated
----------

Avoid 'style="..."' on html tags.

Avoid '<style>' tags in html body tag. style tag should go to html head.

Avoid 'filter' propery.

Avoid 'expression'.

Avoid @import in css.

Avoid '!important'.

