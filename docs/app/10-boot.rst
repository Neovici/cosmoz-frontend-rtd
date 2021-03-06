Bootup and application start
============================

Core loading phase
------------------

The core loading phase exists to load as quickly as possible and display
loading progress for the main application, to avoid a blank page.

Files included in core:

-  ``index.html``
-  ``scripts/core/cz.core.js``
-  ``css/core/core.css``

The core setup has an async import for ``start.html`` which, once loaded, enters next phase.

boot / start / :ref:`cz-start`
------------------------------

The next phase of the startup is to load the core dependencies of the
application, needed regardless of state, these include:

-  ``start.html``

   -  ``css/app/style.css``

   -  ``bower_components`` libraries (not components)

   -  ``scripts/app/cz.*``

   -  ``polymer/cz-login-components``

      -  ``polymer/cz-start``
      -  ``polymer/cz-modal-info``

-  ``polymer/cz-start``

   -  ``polymer/cz-login-screen``

   -  Injects async html import of ``polymer/cz-app-components`` when ready

      -  Possibly a vulcanized version

The idea is that cz-start can decide depending on login state whether we
need to load the whole application or just the cz-login-screen for
starters. (And also if the user is already logged in, we shouldn’t need
the login screen but we import it anyway right now.)

.. todo:: This should be replaced with ``polymer build`` which does this more intelligently with bundles and fragments through a dependency graph.

.. _cz-start:

cz-start
--------

cz-start has a few important tasks when it comes to state tracking and global options:

-  Localization

      - Fetching translations for :ref:`cosmoz-i18next`
      - Setting locale for :ref:`cosmoz-moment`

-  Discovering the correct backend instance, see :ref:`backend-config`
-  Session

      -  Checking login status - ``api/Auth/CheckStatus``
      -  Managing logouts
      -  Managing ``cz-session-manager``

-  Fetching application boot - ``cz.boot`` / ``api/Boot/InitClient``
-  Displaying offline status

.. _backend-config:

Backend config
--------------

``app/cz.config.js``
~~~~~~~~~~~~~~~~~~~~

This file sets what backend service - production, demo, alpha, beta and so on -
to use with the frontend. It can be created if needed.

Example (fill in <text> with appropriate details):

.. code-block:: js

      /*global cz*/
      cz.config = {
            backendBaseUri: '<backend-api-url>',
            googleClientId: '<google-client-id>',
      };

Required properties:

* backendBaseUri, required, the backend base URL
* googleClientId, required, Google client ID to use

``app/cz.version.js``
~~~~~~~~~~~~~~~~~~~~~

This file contains informative read-only properties generated when the frontend
is built on Travis-CI:

* debug, true when building staging, false otherwise
* version, dev when building staging, latest tag otherwise
* commit, the commit that triggered the build
* buildNumber, Travis-CI build number

Backend override
----------------

It's possible to override the backend base URL set in ``cz.config.js`` by using
the backenBaseUri query parameter, which will stick to the address the whole
session.

Example, using a localhost frontend (replace backend-api url-with the real URL):

``http://localhost:3000/?backendBaseUri=https://<backend-api-url>/&cpl=1##start-tab=personal``

.. _cz-login-screen:

cz-login-screen
---------------

The (full screen) component used to handle login if the user is not logged in.
Toggled by :ref:`cz-start`.

.. _cz-application:

cz-application
--------------

The application wrapper component run if user is logged in.

Manages

-  :ref:`cosmoz-theme-switcher`
-  General application design (drawers/panels)
-  :ref:`cosmoz-viewinfo`
-  :ref:`cosmoz-page-router`
-  moduleInfo

   -  Used by views to present loading/status information replacing the
          view, to avoid templates without information and users
          clicking around while a request is in-flight

-  “OmniSearch” and search results
-  Notifications
-  dataEntry

   -  Generic way to request information from a user through a dialog