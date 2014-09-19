Files Organization Guideline
============================

Golden Rules
------------

1. Modular development.
2. Small Core.
3. Load modules on-demand.

Rules
-----

* The core module should contains must-have modules only, and keep it as small as possible.
* A module should be a standalone component, can be installed and removed
  easily. Mean that the module reference name should be simple, meaningful
  and easy to maintain.
* Modules and folders should been named by clearly meaning: 'lang', 'dialog', 'suggestion',
  instead of 'common', 'plugins' , 'frameworks'
* Always list all your dependances, never use file globbings.
* When you hack some lib, you should avoid to change it directly. Try to 
  override or hack them in other file instead.
* The third-party assets go to vendor folder.
* Always try to reduce the js and css request count in every page. Each page
  should contains two js links and two css links - the core module and the
  current appliction module. The modules that did not need in render process
  should loaded with delay or loaded on-demand.

Javascript file structure
-------------------------

.. code-block:: bash

  javascripts/
  |
  |-- admin/                        # Admin sub-project
  |   |-- apps/
  |   |-- mods/
  |
  |-- apps/                         # Applictions
  |   | -- site/
  |   |    | -- index.js
  |   |    | -- show.js
  |   |    | -- edit.js
  |   |
  |   | -- management/
  |
  |-- mods/                         # Modules
  |   | -- modals/
  |   |   | -- index.js             # Module entry file
  |   |   | -- modals-1.0.1.js
  |   |   | -- tests/
  |   |
  |   | -- graph/
  |   | -- lang/
  |
  |-- libs/                         # Libraries for wide use
  |   | -- jquery/
  |   | -- backbone/
  |
  |-- tpls/                         # Static templates (TODO)
  |
  |-- base.js                       # Primary base file for all page

Javascript requires 
-------------------

.. code-block:: javascript

  //= require v3/mods/pophelper
  //= require mods/modals
  //= require ./viewer

Prohibit to require other application files

.. code-block:: javascript

  //= require apps/site/show   # This may cause problems!
  //= require ./viewer

Don't require module with specifc index file

.. code-block:: javascript

  //= require mods/modals/index

Always use:

.. code-block:: javascript

  //= require mods/modals

Always lists all your dependances, never use file globbings:

.. code-block:: javascript

  //= require_tree /common   # When system grow up, these files will become
  //= require_tree .         # hard to maintain.

Stylesheets file structure
--------------------------

.. code-block:: bash

  stylesheets/
  |
  |-- admin/                        # Admin sub-project
  |   |-- apps/
  |   |-- mods/
  |
  |-- apps/                         # Applictions
  |   | -- site/
  |   |    | -- index.scss
  |
  |-- mods/                         # Modules and partials
  |   | -- _typo.scss
  |   | -- _grid.scss
  |   | -- modals.scss
  |   | -- button.scss
  |
  |-- base.scss                       # Primary base file for all page
  |-- init.scss                       # include non-output modals (TODO)
  |-- variables.scss
  |-- mixins.scss
  |-- placeholders.scss

Stylesheets imports
-------------------

.. code-block:: css

  @import 'v3/init';
  @import 'v3/mods/buttons';

The 'init.scss' contains none-output modals(variables, mixins, compass) and 
should be imported by all SCSS files.(TODO)

Don't use Asset Pipeline require functions to import files. The 'requires'
way is slightly faster then import, but sometime may cause issues.

Always lists all your dependances, never use file globbings:

.. code-block:: css

    @import 'library/mixins/*'

``@import 'compass'`` is very slow, we should use specifc package file:

foo.scss:

.. code-block:: css

  @import 'compass';
  .x { .y { @include link-colors(#00c, #0cc, #c0c, #ccc, #cc0)}} 

bar.scss:

.. code-block:: css

  @import 'compass/typography/links/link-colors';
  .x { .y { @include link-colors(#00c, #0cc, #c0c, #ccc, #cc0)}} 

Compare the compile speed:

.. code-block:: bash

  $ time sass --compass app/assets/stylesheets/foo.scss
  $ sass --compass app/assets/stylesheets/foo.scss  1.75s user 0.15s system 99% cpu 1.905 total

  $ time sass --compass app/assets/stylesheets/bar.scss
  $ sass --compass app/assets/stylesheets/bar.scss  1.41s user 0.13s system 99% cpu 1.543 total

Changes in Rails 4
------------------

Image assets in lib/ and vendor/ are no longer automatically precompiled
