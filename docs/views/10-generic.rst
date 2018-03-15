View overview
=============

Views are custom elements named after their URL, as described in
:ref:`url-view-structure`.

The views are dependant on several view-generic behaviors. Any
view-genericbehavior or function should be implemented in a common
Template/View behavior or maybe enriched (like some things are today) by the
:ref:`cosmoz-page-router`.

.. _view-imports:

View imports
------------

All views should import the ``views/imports.html`` file which imports the most
common dependencies required for the views.

View Behaviors
--------------

``Cosmoz.CommonBehaviors``
~~~~~~~~~~~~~~~~~~~~~~~~~~

This is a meta behavior that links to other behaviors:
``Cosmoz.DateHelperBehavior``, ``Cosmoz.MoneyHelperBehavior`` and
``Cosmoz.TemplateHelperBehavior``.

Located in::

	app/bower_components/cosmoz-behaviors/cosmoz-behaviors.html

``Cosmoz.DateHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Provides date management functions.

* ``dayDiff(date1, date2)`` - Get difference in days between two date strings
* ``ensureDate(date)`` - Try to make sure a date (string or Date object) is a Date object
* ``isoDate(date)`` - Format a date string as an ISO-date, YYYY-MM-DD
* ``isoDT(date)`` - Format a date string as an ISO date and time, YYYY-MM-DD HH:mm:ss
* ``pastDate(date)`` - Check if a date string is in the past
* ``renderDate(date)`` - Alias for ``isoDate(date)``,
* ``renderDatetime(date)`` - Alias for ``isoDT(date)``
* ``timeago(date)`` - Get human readable string describing date's difference from now

Located in::

	app/bower_components/cosmoz-behaviors/cosmoz-datehelper-behavior.html

``Cosmoz.MoneyHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Currency handling functions.

* ``renderAmount(money)`` - Render an amount with decimal separator and currency symbol
* ``renderMoney(money)`` - Alias for ``renderAmount(money)``
* ``renderNumberAmount(money)`` - Render an amount with decimal separator but without currency symbol
* ``round(number, precision)`` - Round a number to a given precision
* ``unformatRenderedAmount(amount)`` - Remove currency formatting including decimal separator and currency symbol

Located in::

	app/bower_components/cosmoz-behaviors/cosmoz-moneyhelper-behavior.html

``Cosmoz.TabbedBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~

Cosmoz tabs functions.

* ``getIcon()`` - Returns the element's icon
* ``getIconStyle()`` - Returns the element's icon style

Located in::
	app/bower_components/cosmoz-tabs/cosmoz-tabbed-behavior.html

``Cosmoz.TemplateHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Various generic template handling functions.

* ``abs(number)`` - Alias for ``Math.abs(number)``, returns the absolute value of a number
* ``anyTrue(arg1, arg2...)`` - Check if any of the arguments are true
* ``concat(arg1, arg2...)`` - Concatenate all arguments to a string
* ``ifElse(iftrue, result, elseresult)`` - If iftrue is true, return result, otherwise return elseresult
* ``inArray(item, array)`` - Check if item exists in array
* ``isEmpty(obj)`` - Check if variable is undefined, null, empty Array list
* ``isEqual(arg1, arg2)`` - Check equality of the arguments
* ``toFixed(number, fixval)`` - Formats a number using fixed-point notation

Located in::

	app/bower_components/cosmoz-behaviors/cosmoz-templatehelper-behavior.html

``Cosmoz.TranslatableBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions related to translation.

* ``attached()``
* ``detached()``
* ``gettext(key)`` - Translate text
* ``ngettext(singular, plural)`` - Translate text in pluralis with interpolation
* ``pgettext(context, key)`` - Context translation with interpolation
* ``npgettext(context, singular, plural)`` - Plurals and context translation with interpolation

Located in::

	app/bower_components/cosmoz-i18next/cosmoz-i18next.js

``Cosmoz.ViewInfoBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~

* ``attached()``
* ``detached()``

Located in::

	app/bower_components/cosmoz-viewinfo/cosmoz-viewinfo.js

``cz.behaviors.AdministrationGroupsUsersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for user and group administration views.

* ``confirmRequestCall(requestName, confirmationText)`` - Show a confirmation dialog before running a cz-apicall request

Located in::

	app/views/general/groups-users-helper-behavior.html

``cz.behaviors.AdministrationReasonCodesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for reason code administration views.

* ``openAddActionToReasonCodeDialog(saveSettings)`` - Render a dialog where the user can add actions to reason codes

Located in::

	app/views/administration/reasoncodes/helper-behavior.html

``cz.behaviors.AdministrationRolesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for role administration views.

* ``getAvailableFunctions(allFunctions)`` - Get functions available for adding to a role based on a list of all functions and omit those already in use
* ``isAbleToCreateOrUpdateRole(roleData)`` - Verify if role can be created or updated
* ``mangleFunctionsForOmnitable(functions)`` - Prepare function list for display in a cosmoz-omnitable
* ``openAddFunctionsDialog()`` - Render a dialog where user can add functions to a role
* ``removeFunctionsFromRoleButtonClick()`` - Render a dialog where user can remove functions from a role

Located in::
	app/views/administration/roles/helper-behavior.html

``cz.behaviors.GeneralAgreementsArticlesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between agreement and article views.

* ``computeSuppliers(supplierListData)`` - Remap supplier data

Located in::

	app/views/general/agreements-articles-helper-behavior.html

``cz.behaviors.GeneralAgreementsPriceListsHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between agreement and price list views.

``cz.behaviors.GeneralArticlesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for article views.

* ``createArticle()`` - Use properties in the view to do a request to create an article
* ``updateArticle(fields)`` - Update article properties in the view and do a request do update an article

Located in::
	app/views/general/articles-helper-behavior.html

``cz.behaviors.GeneralArticlesProductGroupsHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between article and product group views.

``cz.behaviors.GeneralInvoicesOrdersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between invoice and order views.

``cz.behaviors.GeneralInvoicesOrdersMatchingHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between invoice and order matching views.

``cz.behaviors.GeneralRulesSuppliersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between rule and supplier views.

``cz.behaviors.GeneralRulesViewHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for rule views.

* ``_combineRuleAndType(rule, ruleInterface)`` - Combine rule and ruleInterface information
* ``_computeRulesParams(pathLocator)`` - Compute parameters for rule
* ``_getRule(rules, ruleInterface)`` - Get a rule
* ``_getRuleSettingParts(value, type)`` - Extract a datastructure from rule type description

Located in::

	app/views/general/rules/helper-behavior.html

``cz.behaviors.OmnitableSearchHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Omnitable search (OTS) Shared functions.

``cz.behaviors.OrderHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for order views.

* ``computeOrderLetter(amount)`` - Get letterball letter based on amount
* ``getOrderLetterColor(amount)`` - Get letterball color based on amount
* ``getReasonsFromActions(requestedAction, actionsBased)`` - Get reason codes from (invoice/order) actions

Located in::

	app/views/purchase/orders/helper-behavior.html

``cz.behaviors.PurchaseArticlesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for article views in purchase directory.

``cz.behaviors.PurchaseInvoicesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for invoice views in purchase directory.

``cz.behaviors.PurchaseSuppliersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for supplier views in purchase directory.

``cz.behaviors.SimpleActionPerformer``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for simple actions.

``cz.behaviors.Template``
~~~~~~~~~~~~~~~~~~~~~~~~~

.. todo:: Document view behaviors