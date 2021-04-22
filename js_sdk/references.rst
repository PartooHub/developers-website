References
======================================================

Partoo
------------------------------------------------------

**Partoo** is a JS object that it is made available globally when you add this script your page header.

.. code-block:: html

    <script src="https://static.partoo.co/javascript/build/partoo.js" type="text/javascript"></script>

Methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _references_partoo_init:

**init** (divId: `string`, options: `Option Object`)
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Insert the iFrame in the div whose id equal ``divId`` and returns a `Page`_ .

**Parameters:**

- divId (**mandatory**): id of the div where the iFrame should be inserted
- options (optional): option JS object to override some behaviour on Partoo App. See `Options object`_

Page
------------------------------------------------------

**Page** is the JS object is returned by ``Partoo.init`` method.
It provides a set of methods to manipulate the iFrame.

.. code-block:: javascript

    // Instantiating the page object that will handle the manipulation
    // of the iFrame in the div whose id is 'divId'
    const page = Partoo.init('divId');

Methods
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**setOptions** (options: `Option Object`)
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Set options to override some behaviour on Partoo App.

**Parameters:**

- options (**mandatory**): option JS object. See `Options object`_.

**login** (connectionToken: `string`)
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Log user on Partoo App using the ``connectionToken`` and redirects to the ``startPage`` defined in `Options object`_.

**Parameters:**

- connectionToken (**mandatory**): connection token generated with `generate connection token endpoint <https://developers.partoo.co/rest_api/v2/#operation/generateConnectionToken>`_.

**navigate** (route: `string`, seedData: `Object`, additionalParams: `Object`)
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Go to specific page.

**Parameters:**

- route (**mandatory**): name of the page that we want to reach. See :ref:`pages_integration_available_pages`
- seedData (optional): to seed to data in lab form
- additionalParams (optional): to send params on the page

**back** ()
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Go back to previous page.

**forward** ()
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
Go forward to next page. Opposite of back.

.. _references_page_on:

**on** (eventId: `string`, callback: `Function`)
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Define a callback on a specific Partoo app event.

**Parameters:**

- eventId (**mandatory**): Id of the event for which we want to define a callback. See :ref:`callbacks_available_events`
- callback (**mandatory**): Function that will be triggered on event. This function should expect one argument.

Miscellaneous
------------------------------------------------------

Options object
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The options can be provided to both the ``Partoo`` global object (being default options) or to a page instance, result of ``Partoo.init()`` using the following syntax

.. code-block:: javascript

    var partooPage = Partoo.init(elemId, userToken, options);
    partooPage.setOptions(options);

``options`` is an object with the following keys.

===================================== ============= ========================= ========================================================================
Parameter                             Type          Default                   Description
===================================== ============= ========================= ========================================================================
**startPage**                         string        ``businesses``            The navigation start page when doing ``login()``
**startPageAnchorParam**              string        ``null``                  Add an anchor param in the login url
**displayIntercom**                   boolean       ``true``                  Display the intercom help button in the lower right corner
**displayUserParams**                 boolean       ``true``                  Display the user's parameter dialog
**displayAddButton**                  boolean       ``true``                  Display the add business button on the top banner
**displayPartnerConnexionBanner**     boolean       ``true``                  Display the partner connexion (Google My Business) banner on edit
**displayBusinessListSearch**         boolean       ``true``                  Display the search dialog on the business list
**displayMultibusinessSelection**     boolean       ``true``                  Allow selection of multiple business on the business list
**displayPresenceManagementDownload** boolean       ``true``                  Display the download data button on the presence management view
**displayLabButtons**                 boolean       ``true``                  Display the Create Account button and Connection button in lab view
**displayBusinessAdmin**              boolean       ``true``                  Display the menu item to close a business in edit view
**displayLabConnectionForm**          boolean       ``true``                  Display the connection form when the business is found after lab search
**displayEditBusinessSelector**       boolean       ``true``                  Display the business selector on the business edit view
**displayLabFoundView**               boolean       ``true``                  Display the result of the lab when the business is already in db
**businessFoundBannerText**           string        ``''``                    Change the text of the lab business found banner
===================================== ============= ========================= ========================================================================


.. include:: utils/intercom.rst