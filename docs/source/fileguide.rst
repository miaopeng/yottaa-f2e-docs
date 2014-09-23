File Organization Guideline
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
* Always try to reduce the js and css request count in every page. Each page
  should contains two js links and two css links - the core module and the
  current appliction module. The modules that did not need in render process
  should loaded with delay or loaded on-demand.
* If you need hack third-party files, you should avoid to change it directly. Try to 
  override or hack them in other file instead.

  If you are using gem for third-party assets, you should make a more meaningful
  named folder and reference the gem in the index file.
  
  e.g. ``require mods/suggestion`` is better than ``require atwho``, because
  maybe somebody don't know what is atwho.

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
  |   | -- dialog/
  |   |   | -- index.js             # Module entry file
  |   |   | -- dialog-1.0.1.js
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
  |-- vendor/                       # Third-Party (TODO)
  |
  |-- base.js                       # Primary base file for all page

Javascript requires 
-------------------

.. code-block:: javascript

  //= require v3/mods/pophelper
  //= require mods/dialog
  //= require ./viewer

Prohibit to require other application files

.. code-block:: javascript

  //= require apps/site/show   # This may cause problems!
  //= require ./viewer

Don't require module with specifc index file

.. code-block:: javascript

  //= require mods/dialog/index

Always use:

.. code-block:: javascript

  //= require mods/dialog

Always lists all your dependances, never use file globbings:

.. code-block:: javascript

  //= require_tree /common   # Hard to maintain while system grow up.
  //= require_tree .

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
  |   |    | -- index.css.scss
  |
  |-- mods/                         # Modules and partials
  |   | -- _variables.scss
  |   | -- _mixins.scss
  |   | -- _placeholders.scss
  |   | -- _typo.scss
  |   | -- _grid.scss
  |   | -- modals.css.scss
  |   | -- button.css.scss
  |
  |-- vendor/                         # Third-Party (TODO)
  |
  |-- base.css.scss                   # Primary base file for all page
  |-- _init.scss                      # include non-output modals (TODO)

Stylesheets imports
-------------------

.. code-block:: css

  @import 'v3/init';
  @import 'v3/mods/buttons';

The 'init.scss' contains none-output modals(variables, mixins, compass) and 
should be imported by all scss.(TODO)

Don't use Asset Pipeline require functions to import files. The 'requires'
way is slightly faster then import, but sometime may cause issues.

Always lists all your dependances, never use file globbings:

.. code-block:: css

    @import 'library/mixins/*'

Avoid using ``@import 'compass';`` directly.
Compiling ``@import 'compass'`` is very slow, we should specifc the package file:

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

* Rails 4.0 removed the assets group from Gemfile.
  Now assets are not precompiled on demand in production anymore

* Image assets in lib/ and vendor/ are no longer automatically precompiled

  http://blog.xdite.net/posts/2014/01/29/rails4-asset-mess
