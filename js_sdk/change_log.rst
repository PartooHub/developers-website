Change Log
=================================

You can find below the changes made on the JS API order by descending date.

2021-04-30: Major change
---------------------------------
  - because of third party cookies policy, the Partoo JS SDK is now using JWT token to keep the user logged instead of session cookie.

2019-03-20: Minor changes
---------------------------------

Added 4 callbacks:
  - business_additional_info_updated :ref:`callbacks_business_additional_info_updated_callback`
	- business_address_updated :ref:`callbacks_business_address_updated_callback`
	- business_contact_updated :ref:`callbacks_business_contact_updated_callback`
	- business_description_updated :ref:`callbacks_business_description_updated_callback`
	- business_open_hours_updated :ref:`callbacks_business_open_hours_updated_callback`

2018-08-23: Minor changes
---------------------------------

Added 2 callbacks:
  - pm_view_go_to_edit_click
  - pm_view_go_to_partner_connection_click


2018-08-10: Minor changes
---------------------------------

Fixed bug that was preventing `startPage` param to work when set to `business`.

Added `startPageAnchorParam` to add an anchor param in the login URL.
