Getting started
=============================================

In order to embed Partoo inside your own webpage, you can use our JS SDK.
The JS SDK will insert an Iframe in your webpage an provide you with an helper to handle this iFrame.

Notes on environments
------------------------------------------------------

Partoo provides its clients and partners with 2 environments:

- **Sandbox environment** maint for developers teams to safely tests Partoo integrations during development. The JS SDK for this environment can be found here: https://sandbox.static.partoo.co/javascript/build/partoo.js
- **Production environment** delivering the actual application. The JS SDK for this environment can be found here: https://static.partoo.co/javascript/build/partoo.js

Step 1 - Import JS SDK in your HTML page
---------------------------------------------------------------

You can import our JS SDK by adding this script tag in your ``<head>`` section :

.. code-block:: html

    <script src="https://static.partoo.co/javascript/build/partoo.js" type="text/javascript"></script>

It adds ``Partoo`` var that can be used by your own script.

Step 2 - Generate a connection token to authenticate your user
------------------------------------------------------------------

To display a Partoo app view, you need to authenticate your user by generating a connection token.
The API endpoint documentation can be found `here <https://developers.partoo.co/rest_api/v2/#operation/generateConnectionToken>`_.

Step 3 - Display your first page
-------------------------------------------------------------------

You first need to add a ``div`` in your HTML where the Partoo App Iframe is going to be inserted. For instance:

.. code-block:: html

    <div id="your-specific-id"></div>

Then to display you first Partoo App view inside your HTML page:

.. code-block:: javascript

    const connectionToken = 'connectionTokenGeneratedInPreviousStep'; // Connection Token you generated previously

    const options = { // this is a list of options you can configure to adapt page display/behaviour
        'startPage': 'presenceManagement', // here the user will be redirected to the presenceManagement view after logging
        'displayIntercom': false, // true by default
        'displayUserParams': false, // true by default
        'displayAddButton': false, // true by detault
    };

    const partooPage = Partoo.init(
        'your-specific-id', // id of the div where you want the Iframe to be inserted
        options
    ); // instantiates the Partoo page (A loader appears)

    partooPage.login(connectionToken) // logs the user and redirects him to the `startPage`


Step 4 - Navigate through pages
----------------------------------------------------------------

Once you logged your user and land on the start page, you can navigate through pages using the generated `partooPage`.
For instance:

.. code-block:: js

    partooPage.navigate('businesses'); // go to businesses list view

    partooPage.back();  // return to previous page

    partooPage.forward();  // opposite of back

    partooPage.destroy();  // destory Iframe


Next Steps
------------------------------------------------------

Thanks to this quick tutorial, you learned how to display your first Partoo app view thanks to the JS SDK.
To build a production ready integration, you might want to check the :ref:`guides`.

.. include:: utils/intercom.rst
