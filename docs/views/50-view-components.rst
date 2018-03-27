View components
===============

Components used in Cosmoz views.

.. _cz-apicall:

cz-apicall
----------

A component to make asynchronous requests. It is a wrapper for ``iron-ajax``
with some differences:

-  Centrally configurable defaults, such as

   -  Content-type

   -  Client timeout

   -  Response default (json)

   -  auto (request)

-  URL basepath set to ``cz.options.backendBaseUri``
-  Automatic loading message handling

   -  With moduleInfo

Data mangling with cz-apicall
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Normally, the API should be designed so that we can bind the data
property of the ``cz-apicall`` instance as input for another component, like
:ref:`cosmoz-omnitable`.

Even though it should be avoided, we might sometimes want to handle/mangle the data received
before forwarding to another component, and the best way to describe
this is to call the computing method at the input for the other
component, example:

.. code-block:: html

    <cz-apicall data="{{ supplierListData }}"></cz-apicall>
    <cosmoz-omnitable data="[[ _getSuppliers(supplierListData) ]]"></cosmoz-omnitable>

This will reduce the need of a computed property which would mean “one
more logic step to follow” and also highlight that the data property for
:ref:`cosmoz-omnitable` is one way since any updates from :ref:`cosmoz-omnitable` will
be lost.

API call parameters
~~~~~~~~~~~~~~~~~~~

``myItemsOnly`` (bool)
^^^^^^^^^^^^^^^^^^^^^^

``myItemsOnly`` is a generic parameter that should be sent whenever the
:term:`Swagger` API documentation mentions MyItemsOnly in Implementation Notes.

The value to send is the value of ``cz.state.myItemsOnly``, controlled by
the toggle in the right menu.

This should be present as an argument to the computing function of the
API call parameters.

``pathLocator`` (string)
^^^^^^^^^^^^^^^^^^^^^^^^

``pathLocator`` should be sent for any API call requesting it.

The value to send is the value of ``cz.state.currentLocationPath``,
controlled by the treenode navigator in the right menu.

This should be present as an argument to the computing function of the
API call parameters.

Example
~~~~~~~

.. code-block:: html

    <template>
        <cz-apicall
            api="api/supplier-invoices/for-approval"
            needs-params
            params="[[ _computeSupplierInvoiceParams(cz.state.currentLocationPath, cz.state.myItemsOnly) ]]"
            loading-message="[[ _('Fetching invoices list', t) ]]"
            data="{{ supplierInvoices }}">
        </cz-apicall>
    </template>

.. code-block:: js

    _computeSupplierInvoiceParams: function (pathLocator, myItemsOnly) {
        return {
            approvableByMe: true,
            myItemsOnly: myItemsOnly,
            pathLocator: pathLocator,
            recursive: true
        };
    },

Explanation

-  ``needs-params`` makes sure that the call will not be executed before
   ``params`` is something else than ``undefined``

   -  ``_computeSupplierInvoiceParams()`` must run

-  The compute method ``_computeSupplierInvoiceParams()`` will not be run
   until all parameters are something else than undefined

   -  The ``cz.state`` properties must be defined

-  When ``params`` changes, the api-call will be executed again, refreshing
   the data, and re-rendering any part of the view that uses it
-  ``params`` will change when the user selects another branch in the right
   menu, or toggles the prioritization of own items

Controlling call submission triggers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

By default, ``cz-apicall`` will send the call as soon as it is ready - and 
this does not include that parameters are ready - which likely is not the
intent.

To make it wait for parameters, set the ``needs-params`` property. It will then
wait for data on the ``params`` property. This is the recommended approach for
``GET`` calls and some ``POST`` calls.

For ``POST`` calls that might require user input and should be triggered on a
specific event, use ``no-auto`` property and manually call ``generateRequest()``
on the element when it should be fired, much like ``iron-ajax``.

.. seealso::
    `Localhost Polymer documentation <http://localhost:3000/polymer/cz-apicall/index.html#cz-apicall>`_

.. _cz-apicall-batch:

cz-apicall-batch
----------------

This is a wrapper of ``cz-apicall`` that can batch requests. It puts all the
calls in one request and sends it in for processing to backend which runs them
one by one and then returns a summary of all requests in one single response.

Attributes
~~~~~~~~~~

``calls`` (array)
^^^^^^^^^^^^^^^^^

A list of calls to be done. Each call in the array consists of an object with
the format of:

.. code-block:: js

    {
        api: 'path/to/call/' + czcore.param({
            parameter1: "value 1",
            ...
        }),
        contentType: 'application/json',
        method: '<GET/POST/DELETE...>'
    }

``responses`` (array)
^^^^^^^^^^^^^^^^^^^^^

The returned result from the series of calls.

Example
~~~~~~~

.. code-block:: html

    <template>
        <cz-apicall-batch
            calls="[[ requestParams.batch ]]"
            id="batchCall"
            responses="{{ batchResponses }}">
        </cz-apicall-batch>
    </template>

.. code-block:: js

    this.set('requestParams.batch', this.selectedMatchesRows.map(item => ({
        api: 'view-api/v2/supplier-invoices/matches/{id}?' + czcore.param({
            comment: this.formProperties.supplierInvoiceRowUnmatchComment,
            id: item.id,
            invoiceRowId: item.rowId,
            reasonCodeId: this.formProperties.supplierInvoiceRowUnmatchReasonId
        }),
        contentType: 'application/json',
        method: 'DELETE'
    })));
    this.$.batchCall.generateRequest();

.. seealso::
    `cz-apicall-batch on localhost <http://localhost:3000/polymer/cz-apicall/index.html#cz-apicall-batch>`_

.. _cosmoz-bottom-bar:

cosmoz-bottom-bar
-----------------

A responsive bottom-bar that dynamically displays action buttons and menu.

.. seealso::

    `cosmoz-bottom-bar at webcomponents.org <https://www.webcomponents.org/element/neovici/cosmoz-bottom-bar/elements/cosmoz-bottom-bar>`_

.. _cosmoz-bottom-bar-view:

cosmoz-bottom-bar-view
----------------------

A responsive bottom-bar that dynamically displays action buttons and menu.
``cosmoz-bottom-bar-view`` contains a content section and a bottom bar with
actions.

Example
~~~~~~~

.. code-block:: html

        <div class="vertical layout fit">
            <cosmoz-bottom-bar-view active="[[ bottomBarActive ]]">
                <div slot="scroller-content">
                </div>
            </cosmoz-bottom-bar-view>
        </div>

.. seealso::

    `cosmoz-bottom-bar-view at webcomponents.org <https://www.webcomponents.org/element/neovici/cosmoz-bottom-bar/elements/cosmoz-bottom-bar-view>`_

.. _cosmoz-data-nav:

cosmoz-data-nav
---------------

A navigator that can be used to display items from a list one at time.

Example
~~~~~~~

.. seealso::
    * :ref:`view_type_list_queue`
    * `cosmoz-data-nav on GitHib <https://github.com/Neovici/cosmoz-data-nav>`_

.. _cosmoz-tabs:

cosmoz-tabs
-----------

Main component, meant as a placeholder for the different tabs used to provide information in different sections, for desktop
views in tabs and for mobile views as cards.

Example
~~~~~~~

.. code-block:: html

    <div slot="scroller-content">
        <cosmoz-tabs id="tabs" accordion="[[ viewInfo.mobile ]]" class="flex" hash-param="invoices-view-core-tab" selected="{{ selectedInvoiceTab }}">
            <cosmoz-tab heading="[[ _('Overview', t) ]]" name="overview">
            </cosmoz-tab>
        </cosmoz-tabs>
    </div>

.. seealso::
    `cosmoz-tabs on GitHub <https://github.com/Neovici/cosmoz-tabs/blob/master/README.md>`_

.. todo:: Document cosmoz-tabs

.. _cosmoz-tab:

cosmoz-tab
----------

Will in desktop mode represent a tab, and in mobile mode represent a
card, unless it contains a cosmoz-tab-cards element.

Example
~~~~~~~

.. code-block:: html

    <cosmoz-tabs id="tabs" accordion="[[ viewInfo.mobile ]]" class="flex" hash-param="invoices-view-core-tab" selected="{{ selectedInvoiceTab }}">
        <cosmoz-tab heading="[[ _('Overview', t) ]]" name="overview">
            <cosmoz-tab-card heading="[[ _('Invoice requirements', t) ]]">
            </cosmoz-tab-card>
        </cosmoz-tab>
    </cosmoz-tabs>

.. _cosmoz-tab-card:

cosmoz-tab-card
~~~~~~~~~~~~~~~

A fixed-width card on desktop to enable multiple cards
horizontally. Displayed as a card on mobile.

Example
~~~~~~~

.. code-block:: html

    <cosmoz-tab heading="[[ _('Overview', t) ]]" name="overview">
        <cosmoz-tab-card heading="[[ _('Invoice data', t) ]]" icon="warning" icon-color="#15b0d3">
            <div class="row">
            </div>
        </cosmoz-tab-card>
    </cosmoz-tab>

``row`` class
~~~~~~~~~~~~~

The shared CSS class ``row`` should be used for divs in :ref:`cosmoz-tab-card`
components to provide key/value rows.

.. _cosmoz-omnitable:

cosmoz-omnitable
----------------

Responsive, flexible data grid / table solution for listing/sorting/filtering/grouping data.

    .. seealso::
        `cosmoz-omnitable on GitHub <https://github.com/Neovici/cosmoz-omnitable>`_

.. todo:: Document cosmoz-omnitable

cz-history
----------

History listing component, to show invoice and order history and similar data.

Attributes
~~~~~~~~~~

``collapsed`` (bool)
^^^^^^^^^^^^^^^^^^^^^^^

Set layout mode to collapsed or not, used by ``viewInfo.mobile``.

``events`` (array)
^^^^^^^^^^^^^^^^^^

List of events to display in this format:

.. code-block:: js

    {
        "cosmozItemId": "<cosmoz-item-id>",
        "user": {
            "id": "<id>",
            "fullName": "<Name>"
        },
        "comment": "<comment>",
        "createDate": "YYYY-MM-DDTHH:MM:SS.MSZ",
        "eventType": <number>,
        "eventCode": <number>,
        "eventDescription": {
            "text": "<Text>",
            "arguments": []
        }
    },

Example
~~~~~~~

.. code-block:: html

    <cosmoz-tab heading="[[ _('History', t) ]]" name="history" badge="{{ getHistoryBadgeData(order.history) }}">
        <cz-history collapsed="[[ viewInfo.mobile ]]" events="[[ order.history ]]">
        </cz-history>
    </cosmoz-tab>

.. todo:: Document cz-history