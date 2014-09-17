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
* When you hack some lib, you should avoid to change it directly. Try to 
  override or hack them in other file instead.
* folders should named by clearly meaning instead of 'common', 'plugins'
  , 'frameworks'
* Always lists all your dependances, never use file globbings  
* The third-party assets go to vendor folders.

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
  |-- mods/                         # Modules (or partials)
  |   | -- modals.scss
  |   | -- button.scss
  |   | -- alerts.scss
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
should be imported by all SCSS files exclude partials.(TODO)

Don't use Asset Pipeline require functions to impport files.

Always lists all your dependances, never use file globbings:

.. code-block:: css

    @import 'library/mixins/*'

Gems
-----
compass-load-once

sprockets_better_errors
