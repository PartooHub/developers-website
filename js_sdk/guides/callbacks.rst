.. _callbacks:

Capturing Partoo App events with callbacks
========================================================

When integrating Partoo App view, you might want to get notified when some Partoo App event occurs.
To achieve that, it is possible to define callbacks that will be triggered on specific Partoo app event.

Depending on the event, the callback can be **blocking**, meaning the default action in Partoo app will not be triggered, or **non-blocking**, meaning the callback will be called but the default action will occure.


Configuring a callback
--------------------------------------------------------

To configure a callback, you need to use the ``on``, see :ref:`references_page_on`, function of the ``page`` instance generated with ``Partoo.init``, see :ref:`references_partoo_init`.

This function expects 2 parameters:
    - the **eventId**: the event for which we want to define a callback
    - the **callback**: a JS function that will be triggered when the event occurs. This function should expect an argument ``data``. The content and type of ``data`` change depending on the event.

For instance, the following code will log the ``data`` of the ``subscribe`` event.

.. code-block:: javascript

    const subscribeCallback = (data) => console.log(data);

    partooPage.on(
        'subscribe',  // the subcribe event id
        subscribeCallback,  // the callback to be called on subscribe event
    )


.. _callbacks_available_events:

Available callback events
--------------------------------------------------------

.. _callbacks_subscribe_business_callback:

Subscribe business
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when a user clicks on subscribe.

**Event id:** ``subscribe``.

**Event data:** a JS object with the following stucture

.. code-block:: javascript

    {
        "productName": "presence_management",  // or "review_management"
        "businesses": [
            {
                "id": "5a2ab4edb12ff67cba1b7e1b",
                "org_id": 709,
                "name": "SCEP du Caire",
            }
        ]
    }

.. _callbacks_open_business_callback:


Open business
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when a user click a link to open a business page.

**Event id:** ``open_business``.

**Event data:** the business id (a string). For instance: ``5a2ab4edb12ff67cba1b7e1b``


.. _callbacks_business_created_callback:

Business created
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when the user has created a business, has clicked on save and the business has been saved in the Partoo DB.

.. warning::
	This callback does not prevent redirection to the business edit page

**Event id:** ``business_created``.

**Event data:** the business id (a string). For instance: ``5a2ab4edb12ff67cba1b7e1b``

.. _callbacks_business_additional_info_updated_callback:

Business additional info updated
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when then user has successfully updated the additionnal info of his/her business (in the *additionnal info tab*, he/she clicked on save).

.. warning::
	This is a none blocking callback

**Event id:** ``business_additional_info_updated``.

**Event data:** a JS object

.. _callbacks_business_address_updated_callback:

Business address updated
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when then user has successfully updated the address of his/her business (in the *address tab*, he/she clicked on save).

.. warning::
	This is a none blocking callback

**Event id:** ``business_address_updated``.

**Event data:** a JS object

.. _callbacks_business_contact_updated_callback:

Business contact updated
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when then user has successfully updated contact of his/her business (in the *contact tab*, he/she clicked on save).

.. warning::
	This is a none blocking callback

**Event id:** ``business_contact_updated``.

**Event data:** a JS object

.. _callbacks_business_description_updated_callback:

Business description updated
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when then user has successfully updated the description of his/her business (in the *description tab*, he/she clicked on save).

.. warning::
	This is a none blocking callback

**Event id:** ``business_description_updated``.

**Event data:** a JS object

.. _callbacks_business_open_hours_updated_callback:

Business open hours updated
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when then user has successfully updated the open hours of his/her business (in the *open hours tab*, he/she clicked on save).

.. warning::
	This is a none blocking callback

**Event id:** ``business_open_hours_updated``.

**Event data:** a JS object

.. _callbacks_lab_create_callback:

Lab create
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when the user click on create business in the lab view.

**Event id:** ``lab_create``.

**Event data:** a JS object with the following stucture

.. code-block:: javascript

	{
		"civlity": "Mr",
		"email": "deLaBatte@gmail.com",
		"first_name": "Hubert",
		"last_name": "de la Batte",
		"password": "zzzzzzzz",
		"phone": "0102030405"
	}

.. _callbacks_lab_results_received_callback:

Lab results received
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This events happens when the lab has returned results.

**Event id:** ``lab_results_received``.

**Event data:** a JS object with the following stucture

.. code-block:: javascript

	{
		"annuaire": {
			"stats": {
				"detailed": {},
				"summary": {
					"accurate": 0,
					"not_found": 1,
					"error": 0
				}
			},
			"business": {}
		},
		"le118000": {
			"stats": {
				"detailed": {},
				"summary": {
					"accurate": 0,
					"not_found": 1,
					"error": 0
				}
			},
			"business": {}
		},
	}

With a key per integration displayed in the view (``google_my_business``, ``annuaire``, ``le118000``)

.. _callbacks_lab_sign_up_callback:

Lab sign up button
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when a user click on the sign up button in the Lab View.

**Event id:** ``lab_sign_up_button``.

**Event data:** null

.. _callbacks_lab_login_callback:

Lab login button
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when a user click on the login button in the Lab View.

**Event id:** ``lab_login_button``.

**Event data:** null

.. _callbacks_error_callback:

Error
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when an error 400, 403, 404, 500 happens during page rendering.

**Event id:** ``error``.

**Event data:** the HTTP response code:
  - ``400``, client error
  - ``403``, not authorized
  - ``404``, not found
  - ``500``, server error


.. _callbacks_no_business_callback:

No business button click
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when a use click on a `No Business` button.

.. code-block:: javascript

	partooPage.on('no_business_click', function() { /* the code you want to be executed on click */});

.. _callbacks_no_eligible_callback:

No business eligible button click
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when a use click on a `No Business` button.

.. code-block:: javascript

	partooPage.on('no_eligible_business_click', function() { /* the code you want to be executed on click */});

.. _callbacks_go_to_edit_callback:

Presence Management go to edit click
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when a use click on a `Edit` link in the presence management view that should redirect him to business edit view.

.. code-block:: javascript

	partooPage.on('pm_view_go_to_edit_click', function() { /* the code you want to be executed on click */});


.. _callbacks_go_to_partner_connection_callback:

Presence Management go to partner connection click
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This event happens when a use click on a `Edit` link in the presence management view that should redirect him to connection view.

.. code-block:: javascript

	partooPage.on('pm_view_go_to_partner_connection_click', function() { /* the code you want to be executed on click */});


.. include:: ../utils/intercom.rst
