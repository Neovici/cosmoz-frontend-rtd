View overview
=============

Views are custom elements named after their URL, as described in
:ref:`url-view-structure`.

The views are dependant on several view-generic behaviors. Any
view-genericbehavior or function should be implemented in a common
Template/View behavior or maybe enriched (like some things are today) by the
:ref:`cosmoz-page-router`.

.. note ::

  Tip! The file locations presented in this reference are directly openable in
  :ref:`vscode` if you have opened the repository root folder in the editor,
  just run the path in the command palette (``Ctrl + Shift + P``).

.. _view-imports:

View imports
------------

All views should import the ``views/imports.html`` file which imports the most
common dependencies required for the views.

View behavior reference
-----------------------

Internal functions (those beginning with and underscore) are not listed here,
unless the behavior only has internal functions (which may indicate that the
functions are not correctly named in that behavior).

``Cosmoz.CommonBehaviors``
~~~~~~~~~~~~~~~~~~~~~~~~~~

This is a meta behavior that links to other behaviors:

* ``Cosmoz.DateHelperBehavior``
* ``Cosmoz.MoneyHelperBehavior``
* ``Cosmoz.TemplateHelperBehavior``

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

* ``confirmRequestCall(requestName, confirmationText)`` - Show a confirmation
  dialog before running a cz-apicall request

Located in::

  app/views/general/groups-users-helper-behavior.html

``cz.behaviors.AdministrationReasonCodesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for reason code administration views.

* ``openAddActionToReasonCodeDialog(saveSettings)`` - Render a dialog where the
  user can add actions to reason codes

Located in::

  app/views/administration/reasoncodes/helper-behavior.html

``cz.behaviors.AdministrationRolesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for role administration views.

* ``getAvailableFunctions(allFunctions)`` - Get functions available for adding
  to a role based on a list of all functions and omit those already in use
* ``isAbleToCreateOrUpdateRole(roleData)`` - Verify if role can be created or
  updated
* ``mangleFunctionsForOmnitable(functions)`` - Prepare function list for display
  in a cosmoz-omnitable
* ``openAddFunctionsDialog()`` - Render a dialog where user can add functions to
  a role
* ``removeFunctionsFromRoleButtonClick()`` - Render a dialog where user can
  remove functions from a role

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

* ``hasAction(item, actionId)`` - Find out if an item has one specific action
  based on id

Located in::

  app/views/purchase/suppliers/helper-behavior.html

``cz.behaviors.GeneralArticlesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for article views.

* ``createArticle()`` - Use properties in the view to do a request to create an
  article
* ``updateArticle(fields)`` - Update article properties in the view and do a
  request do update an article

Located in::

  app/views/general/articles-helper-behavior.html

``cz.behaviors.GeneralArticlesProductGroupsHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between article and product group views.

* ``mapProductGroupHierarchy(contents)`` - Iterate contents and remap data so
  the label and code are returned

Located in::

  app/views/general/articles-product-groups-helper-behavior.html

``cz.behaviors.GeneralInvoicesOrdersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between invoice and order views.

* ``getDiffRows(rows)`` - Get rows where match status is not fully matched
* ``getHistoryBadgeData(history)`` - Get the number of comments in history data
* ``getMatchInfo(document)`` - Get matching details by looking on both document
  header and rows
* ``getReasonsFromSelectedRowsActions(requestedAction, rowsNotify)`` - Get
  reason codes from actions on invoice/order rows
* ``hasRowAction(rowsNotify, actionId)`` - Check if rows has an action id
  present
* ``renderAbsMoney(amount)`` - Get the absolute value of an amount formatted as
  money with currency

Located in::

  app/views/general/invoices-orders-helper-behavior.html

``cz.behaviors.GeneralInvoicesOrdersMatchingHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between invoice and order matching views.

* ``batchResponsesChanged(newResponses)`` - Set matchSuggestions property to
  newResponses if it has a length
* ``computeBottomBarActive(numSelectedRows1, numSelectedRows2, selectedTab)`` -
  Get bottom bar state depending on selected rows amount and current tab
* ``computeCustomSuggestParams(fieldName, fieldValue, baseOtsQueryParams, run =
  true)`` - Calculate request parameters for custom suggestions
* ``computeLoadingMessage(rowQueueNotify)`` - Compose a loading message for
  match call
* ``getPotentialAmount(selectedRowSuggestionsNotify, matchSuggestionsNotify,
  unmatchedAmount, unformatted)`` - Get selected amount that is possible to
  match
* ``getPotentialQuantity(selectedRowSuggestionsNotify, unmatchedQuantity)`` -
  Get selected quantity that is possible to match
* ``getProgress(part, total)`` - Get percentage value for a progress bar
* ``getStartValue(part, total)`` - Get the start value for a progress bar
* ``showFilterBasedOnAvailableValues(rowNotify, rowValueProperty, suggestions,
  comparison)`` - Find out if a filter should be shown based on available rows
* ``showPackageUnitPriceFilter(selectedRowSuggestionsNotify,
  matchSuggestionsNotify, matchSuggestionsRowObjectProperty,
  matchSuggestionsSuggestionsProperty, rowProperty, rowSuggestionsProperty)`` -
  Find out if package unit price filter should be shown

Located in::

  app/views/general/invoices-orders-matching-helper-behavior.html

``cz.behaviors.GeneralRulesSuppliersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functions shared between rule and supplier views.

* ``isPathLocatorAncestor(pathLocatorAncestor, pathLocator)`` - Find out if one
  path locator is an ancestor of another path locator

Located in::

  app/views/general/rules-suppliers-helper-behavior.html

``cz.behaviors.GeneralRulesViewHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for rule views.

* ``_combineRuleAndType(rule, ruleInterface)`` - Combine rule and ruleInterface
  information
* ``_computeRulesParams(pathLocator)`` - Compute parameters for rule
* ``_getRule(rules, ruleInterface)`` - Get a rule
* ``_getRuleSettingParts(value, type)`` - Extract a datastructure from rule type
  description

Located in::

  app/views/general/rules/helper-behavior.html

``cz.behaviors.OmnitableSearchHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Omnitable search (OTS) shared functions.

* ``_capitalizeFirstLetter(string)`` - Capitalize the first letter of a string
* ``_computeBaseOtsQueryParams(pathLocator, myItemsOnly, baseSearchParams,
  filtersNotify)`` - Get parameters for the base request call
* ``_computeOtsExternalValues(local, baseOtsSearchParams)`` - Decide whether
  external values should be used or not
* ``_computeOtsOurReferenceSuggestParams(baseOtsQueryParams, query)`` - Get
  parameters for our reference suggestion call
* ``_computeOtsPathLocatorSuggestParams(baseOtsQueryParams)`` - Get parameters
  for path locator suggestion call
* ``_computeOtsSuggestParams(fieldName, baseOtsQueryParams, run = true)`` - Get
  parameters for a large amount of suggestion calls
* ``_computeOtsCategorySuggestParams(baseOtsQueryParams, categoryQuery)`` - Get
  parameters for category suggestion call
* ``_computeOtsSuppliersSuggestParams(baseOtsQueryParams, sellerPartyName,
  run)`` - Get parameters for supplier suggestion call
* ``_getISODateString(date)`` - Convert a date to an ISO date string
* ``_getLocalISODateString(date)`` - Convert a date to a local ISO date string
* ``_otsIsMoreRestrictive(origParams, newParams)`` - Decide whether omnitable
  search should be more restrictive or not
* ``_otsObserveSearchParams(viewParams, userParams, subPath)`` - Observer for
  user and view parameters that sets search parameters

Located in::

  app/views/general/omnitablesearch-helper-behavior.html

``cz.behaviors.OrderHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for order views.

* ``computeOrderLetter(amount)`` - Get letterball letter based on amount
* ``getOrderLetterColor(amount)`` - Get letterball color based on amount
* ``getReasonsFromActions(requestedAction, actionsBased)`` - Get reason codes
  from (invoice/order) actions

Located in::

  app/views/purchase/orders/helper-behavior.html

``cz.behaviors.PurchaseArticlesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for article views in purchase directory.

* ``getArticlesSearchParams(pathLocator)`` - Get request parameters for article
  search
* ``getSupplierListParams(pathLocator)`` - Get request parameter for supplier
  list

Located in::

  app/views/purchase/articles/helper-behavior.html

``cz.behaviors.PurchaseInvoicesHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for invoice views in purchase directory.

* ``computeInvoiceLetter(amount)`` - Get letterball letter based on amount
* ``getInvoiceLetterColor(amount)`` - Get letterball color based on amount
* ``getInvoiceStatus(header)``  - Get status style class from invoice header
* ``getInvoiceText(header)`` - Get status text from invoice header
* ``getReasonsFromActions(requestedAction, actionsBased)`` - Get reason codes
  from actions

Located in::

  app/views/purchase/invoices/helper-behavior.html

``cz.behaviors.PurchaseSuppliersHelperBehavior``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for supplier views in purchase directory. Provides only shared
arrays at the moment.

Located in::

  app/views/purchase/suppliers/helper-behavior.html

``cz.behaviors.SimpleActionPerformer``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Shared functions for simple actions.

* ``filterSimpleActions(action)`` - Get the simpleAction part of an action
* ``getSimpleRowActions(rows, numRows = 0)`` - Iterate invoice/order rows and
  get actions matching simple row action criterias

Located in::

  app/polymer/cz-actions/cz-simple-action-performer-behavior.html

``cz.behaviors.Template``
~~~~~~~~~~~~~~~~~~~~~~~~~

* ``created()``
* ``attached()``
* ``detached()``
* ``deepEquals(a, b)`` - Compare two arrays or objects deeply
* ``linkToCurrentPage(params, hashhash)`` - Construct a link to the current
  page
* ``findBranchById(branchId)`` - Recursively search cz.boot.organization for a
  branchId
* ``hasAnyRoleFunction(items)`` - Find out if any item has the required
  function for it
* ``hasRoleFunction(roleFunction, cz = this.cz)`` - Find out if user has a
  role function
* ``openDataDialog(event)`` - Generic helper to use 'data-dialog' attribute to
  find element ID of dialog to open
* ``validateForm(event, detail)`` - Validate data-dialog form

Located in::

  app/polymer/cz-behaviors/cz-behaviors.js