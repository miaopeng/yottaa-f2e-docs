CSS Style Guideline
===================

Precompiler
-----------

  We use the css precompiler `SASS` and the `SCSS` syntax.

Linting
-------

  We use `scss-lint` for SCSS coding style linting.

Selectors
---------

1. The most ideal way is only use the `class` selector.
   Beware of misusing the `id` selector and `tag` selector.

   The `id` selector is for unique views only.Elements that occur exactly once
   inside a page should use IDs, otherwise, use classes.

   * Good candidates for ids: header, footer, modal popups.
   * Bad candidates for ids: navs, listings, item views.
   
   Don't use comman `tag` selectors: `div {}`, `a {}`, `span {}`

   Use `tag` selectors just for some fixed html structrues: `.nav li {}`,
   `.select option {}`

   A example of an over-qualified selector might be `ul.nav li a {}`.
   We can instantly drop the ul and because we know `.nav` is a list, we 
   therefore know that any `a` must be in an `li`, so we can get 
   `ul.nav li a {}` down to just `.nav a {}`.

2. Don't use to many level for selector. 1 ~ 3 levels is the best. In SCSS,
   only one nesting levels at most.

3. Don't use element inline styles(`style="..."`). You can only use inline css
   blocks in the html head element.

Naming
------

#. Use hyphen for ids, classes, variable names and mixin names.

#. ID and class's name must clear and concisely. e.g. #users, .list

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

    * - Name
      - Example
    * - status
      - .on, .active, .disabled
    * - position
      - .main, .side, .first, .last
    * - structure
      - .mod, .hd, .bd, .ft
    * - common
      - .tb, .frm, .nav, .list, .item, .info

#. JS hooks
   Use `js-` prefix classes for js hooks only. Don't define styles for `js-`
   classes.

Style
-----

1. Multi line rules for scss files, single line for one rule or inline css.

Layout
------

1. Clear floats with `after` or `overflow`, don't add extra tags in html.
2. All components you build should be left totally free of widths; they should 
   always remain fluid and their widths should be governed by a parent/grid 
   system.
   
   Heights should never be be applied to elements. Heights should only be 
   applied to things which had dimensions before they entered the site 
   (i.e. images and sprites). Never ever set heights on ps, uls, divs, 
   anything. You can often achieve the desired effect with line-height 
   which is far more flexible.

Shorthand
---------

Shorthand CSS needs to be used with caution.

It might be tempting to use declarations like background: red; but in 
doing so what you are actually saying is ‘I want no image to scroll, 
aligned top-left, repeating X and Y, and a background colour of red’. 
Nine times out of ten this won’t cause any issues but that one time it does is 
annoying enough to warrant not using such shorthand. Instead use 
background-color: red;.
