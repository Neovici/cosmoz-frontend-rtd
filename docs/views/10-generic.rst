View overview
=============

Views are custom elements named after their URL, as described in
:ref:`url-view-structure`.

.. _view-imports:

View imports
------------

All views should import the ``views/imports.html`` file which imports the most
common dependencies required for the views.

View behavior reference
-----------------------

The views are dependant on several view-generic behaviors. Any
generic view behavior or function should be implemented in a common
Template/View behavior or maybe enriched (like some things are today) by the
:ref:`cosmoz-page-router`.

Internal functions (those beginning with and underscore) are not listed here,
unless the behavior only has internal functions (which may indicate that the
functions are not correctly named in the behavior).

.. note ::

  Tip! The file locations presented in this reference are directly openable in
  :ref:`vscode` if you have opened the repository root folder in the editor,
  just run the path in the command palette (``Ctrl + Shift + P``).

``Cosmoz.CommonBehaviors``
~~~~~~~~~~~~~~~~~~~~~~~~~~

This is a meta behavior that links to other behaviors:

* ``Cosmoz.DateHelperBehavior``
* ``Cosmoz.MoneyHelperBehavior``
* ``Cosmoz.TemplateHelperBehavior``

.. todo::

  TODO - Webcomponents.org documentation?

Located in::

  app/bower_components/cosmoz-behaviors/cosmoz-behaviors.html

``Cosmoz.DateHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Provides date management functions.

* ``dayDiff(date1, date2)`` - Get difference in days between two date strings
* ``ensureDate(date)`` - Try to make sure a date (string or Date object) is a
  Date object
* ``isoDate(date)`` - Format a date string as an ISO-date, YYYY-MM-DD
* ``isoDT(date)`` - Format a date string as an ISO date and time, YYYY-MM-DD
  HH:mm:ss
* ``pastDate(date)`` - Check if a date string is in the past
* ``renderDate(date)`` - Alias for ``isoDate(date)``,
* ``renderDatetime(date)`` - Alias for ``isoDT(date)``
* ``timeago(date)`` - Get human readable string describing date's difference
  from now

.. todo::

  TODO - Webcomponents.org documentation?

Located in::

  app/bower_components/cosmoz-behaviors/cosmoz-datehelper-behavior.html

``Cosmoz.MoneyHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Currency handling functions.

* ``renderAmount(money)`` - Render an amount with decimal separator and currency
  symbol
* ``renderMoney(money)`` - Alias for ``renderAmount(money)``
* ``renderNumberAmount(money)`` - Render an amount with decimal separator but
  without currency symbol
* ``round(number, precision)`` - Round a number to a given precision
* ``unformatRenderedAmount(amount)`` - Remove currency formatting including
  decimal separator and currency symbol

.. todo::

  TODO - Webcomponents.org documentation?

Located in::

  app/bower_components/cosmoz-behaviors/cosmoz-moneyhelper-behavior.html

``Cosmoz.TabbedBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~

Cosmoz tabs functions.

* ``getIcon()`` - Returns the element's icon
* ``getIconStyle()`` - Returns the element's icon style

.. todo::

  TODO - Webcomponents.org documentation?

Located in::

  app/bower_components/cosmoz-tabs/cosmoz-tabbed-behavior.html

``Cosmoz.TemplateHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Various generic template handling functions.

* ``abs(number)`` - Alias for ``Math.abs(number)``, returns the absolute value
  of a number
* ``anyTrue(arg1, arg2...)`` - Check if any of the arguments are true
* ``concat(arg1, arg2...)`` - Concatenate all arguments to a string
* ``ifElse(iftrue, result, elseresult)`` - If iftrue is true, return result,
  otherwise return elseresult
* ``inArray(item, array)`` - Check if item exists in array
* ``isEmpty(obj)`` - Check if variable is undefined, null or empty Array list
* ``isEqual(arg1, arg2)`` - Check equality of the arguments
* ``toFixed(number, fixval)`` - Formats a number using fixed-point notation

.. todo::

  TODO - Webcomponents.org documentation?

Located in::

  app/bower_components/cosmoz-behaviors/cosmoz-templatehelper-behavior.html

``Cosmoz.TranslatableBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions related to translation.

* ``attached()``
* ``detached()``
* ``gettext(key)`` - Translate text
* ``ngettext(singular, plural)`` - Translate text in pluralis with interpolation
* ``npgettext(context, singular, plural)`` - Plurals and context translation
  with interpolation
* ``pgettext(context, key)`` - Context translation with interpolation

.. todo::

  TODO - Webcomponents.org documentation?

Located in::

  app/bower_components/cosmoz-i18next/cosmoz-i18next.js

``Cosmoz.ViewInfoBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~

* ``attached()``
* ``detached()``

.. todo::

  TODO - Webcomponents.org documentation?

Located in::

  app/bower_components/cosmoz-viewinfo/cosmoz-viewinfo.js

``cz.behaviors.AdministrationGroupsUsersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for user and group administration views.

.. seealso::

  `cz.behaviors.AdministrationGroupsUsersHelperBehavior on localhost <http://localhost:3000/views/general/groups-users-helper-behavior-docs.html>`_

Located in::

  app/views/general/groups-users-helper-behavior.html

``cz.behaviors.AdministrationReasonCodesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for reason code administration views.

.. seealso::

  `cz.behaviors.AdministrationReasonCodesHelperBehavior on localhost <http://localhost:3000/views/administration/reasoncodes/helper-behavior-docs.html>`_

Located in::

  app/views/administration/reasoncodes/helper-behavior.html

``cz.behaviors.AdministrationRolesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for role administration views.

.. seealso::

  `cz.behaviors.AdministrationRolesHelperBehavior on localhost <http://localhost:3000/views/administration/roles/helper-behavior-docs.html>`_

Located in::

  app/views/administration/roles/helper-behavior.html

``cz.behaviors.GeneralAgreementsArticlesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between agreement and article views.

.. seealso::

  `cz.behaviors.GeneralAgreementsArticlesHelperBehavior on localhost <http://localhost:3000/views/general/agreements-articles-helper-behavior-docs.html>`_

Located in::

  app/views/general/agreements-articles-helper-behavior.html

``cz.behaviors.GeneralAgreementsPriceListsHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between agreement and price list views.

.. seealso::

  `cz.behaviors.GeneralAgreementsPriceListsHelperBehavior on localhost <http://localhost:3000/views/general/agreements-price-lists-helper-behavior-docs.html>`_

Located in::

  app/views/general/agreements-price-lists-helper-behavior.html

``cz.behaviors.GeneralArticlesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for article views.

.. seealso::

  `cz.behaviors.GeneralArticlesHelperBehavior on localhost <http://localhost:3000/views/general/articles-helper-behavior-docs.html>`_

Located in::

  app/views/general/articles-helper-behavior.html

``cz.behaviors.GeneralArticlesProductGroupsHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between article and product group views.

.. seealso::

  `cz.behaviors.GeneralArticlesProductGroupsHelperBehavior on localhost <http://localhost:3000/views/general/articles-product-groups-helper-behavior-docs.html>`_

Located in::

  app/views/general/articles-product-groups-helper-behavior.html

``cz.behaviors.GeneralInvoicesOrdersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between invoice and order views.

.. seealso::

  `cz.behaviors.GeneralInvoicesOrdersHelperBehavior on localhost <http://localhost:3000/views/general/invoices-orders-helper-behavior-docs.html>`_

Located in::

  app/views/general/invoices-orders-helper-behavior.html

``cz.behaviors.GeneralInvoicesOrdersMatchingHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between invoice and order matching views.

.. seealso::

  `cz.behaviors.GeneralInvoicesOrdersMatchingHelperBehavior on localhost <http://localhost:3000/views/general/invoices-orders-matching-helper-behavior-docs.html>`_

Located in::

  app/views/general/invoices-orders-matching-helper-behavior.html

``cz.behaviors.GeneralRulesSuppliersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between rule and supplier views.

.. seealso::

  `cz.behaviors.GeneralRulesSuppliersHelperBehavior on localhost <http://localhost:3000/views/general/rules-suppliers-helper-behavior-docs.html>`_

Located in::

  app/views/general/rules-suppliers-helper-behavior.html

``cz.behaviors.GeneralRulesViewHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for rule views.

.. seealso::

  `cz.behaviors.GeneralRulesViewHelperBehavior on localhost <http://localhost:3000/views/general/rules/helper-behavior-docs.html>`_

Located in::

  app/views/general/rules/helper-behavior.html

``cz.behaviors.OmnitableSearchHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Omnitable search (OTS) shared functions.

.. seealso::

  `cz.behaviors.OmnitableSearchHelperBehavior on localhost <http://localhost:3000/views/general/omnitablesearch-helper-behavior-docs.html>`_

Located in::

  app/views/general/omnitablesearch-helper-behavior.html

``cz.behaviors.OrderHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for order views.

.. seealso::

  `cz.behaviors.OrderHelperBehavior on localhost <http://localhost:3000/views/purchase/orders/helper-behavior-docs.html>`_

Located in::

  app/views/purchase/orders/helper-behavior.html

``cz.behaviors.PurchaseArticlesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for article views in purchase directory.

.. seealso::

  `cz.behaviors.PurchaseArticlesHelperBehavior on localhost <http://localhost:3000/views/purchase/articles/helper-behavior-docs.html>`_

Located in::

  app/views/purchase/articles/helper-behavior.html

``cz.behaviors.PurchaseInvoicesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for invoice views in purchase directory.

.. seealso::

  `cz.behaviors.PurchaseInvoicesHelperBehavior on localhost <http://localhost:3000/views/purchase/invoices/helper-behavior-docs.html>`_

Located in::

  app/views/purchase/invoices/helper-behavior.html

``cz.behaviors.PurchaseSuppliersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for supplier views in purchase directory. Provides only shared
arrays at the moment.

.. seealso::

  `cz.behaviors.PurchaseSuppliersHelperBehavior on localhost <http://localhost:3000/views/purchase/suppliers/helper-behavior-docs.html#cz.behaviors.PurchaseSuppliersHelperBehavior>`_

Located in::

  app/views/purchase/suppliers/helper-behavior.html

``cz.behaviors.SimpleActionPerformer``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for simple actions.

.. seealso::

  `cz.behaviors.SimpleActionPerformer on localhost <http://localhost:3000/polymer/cz-actions/index.html>`_

Located in::

  app/polymer/cz-actions/cz-simple-action-performer-behavior.html

``cz.behaviors.Template``
~~~~~~~~~~~~~~~~~~~~~~~~~

.. seealso::

  `cz.behaviors.Template on localhost <http://localhost:3000/polymer/cz-behaviors/index.html#cz.behaviors.TemplateViewCommonBehavior>`_

Located in::

  app/polymer/cz-behaviors/cz-behaviors.js