# Creating resources 

In this chapter, you will learn how to create an organization, a business and a user linked to it using Partoo API.

**📕Note:** All the examples below are using sandbox environment. In production, you will to change the url to use production one. 

## STEP 1 - Create an organisation

**⚠️ Warning:** This step is only necessary if you are a `PROVIDER` user.
If you are an `ORG_ADMIN`you cannot create an organization, the users and businesses your are will automatically be linked to your organisation so go the next step.

Python
---------------------------------------------------------------
```python
# std
import os
from pprint import pprint
# 3p
import requests

# API variables
API_KEY = os.getenv('PARTOO_API_KEY')  # it is a good practice to store secret in ENV variable
# in production you need to change below URL for 'https://api.partoo.co/v2'  
API_BASE_URL = 'https://sandbox.api.partoo.co/v2'    

# Make request to Partoo REST API to create the organization
# for endpoint documentation see https://developers.partoo.co/rest_api/v2/#tag/Organisations/paths/~1org/post
response = requests.post('%s/org' % API_BASE_URL, 
            data={'name': 'The Milk Company'},
            headers={'x-APIKey': API_KEY},
)
organisation = response.json()
pprint(organisation, indent=2)
"""
Should return:
{
    "org_id": 42,
    "name": "The Milk Company",
    "alias": "the_milk_company",
}
"""
```

## STEP 2 - Create a business


### If you are a PROVIDER user

We assume the step before was completed successfully.
Now that we created a organisation, we can create a business that will be belong to it.

Python
-----------------
```python
# std
import os
from pprint import pprint
# 3p
import requests

# API variables
API_KEY = os.getenv('PARTOO_API_KEY')  # it is a good practice to store secret in ENV variable
# in production you need to change below URL for 'https://api.partoo.co/v2'  
API_BASE_URL = 'https://sandbox.api.partoo.co/v2'    

# We assume the previous call to create an organisation was successful

# Make request to Partoo REST API to create the business
# for endpoint documentation see https://developers.partoo.co/rest_api/v2/#operation/createBusiness
response = requests.post(
            '%s/business' % API_BASE_URL,  # resource endpoint
            data={
                    'name': 'Corner shop',
                    'org_id': organization['org_id'],  # the organization we created in the previous state
                    'country': 'FR',
                    'city': 'Paris',
                    'zipcode': 75019,
                    'categories': [],  # Partoo categories ids, see https://developers.partoo.co/rest_api/v2/#operation/searchCategories
                  },
            headers={'x-APIKey': API_KEY},   # for authentication
)
response_body = response.json()
pprint(response_body, indent=2)
"""
Should return:
{
   "status": "success",
   "id": "5409c35a97bbc544d8e26737"  # id of the business you just created
}
"""
```

### If you are an ORG_ADMIN user

Python
-----------------
```python
# std
import os
from pprint import pprint
# 3p
import requests

# API variables
API_KEY = os.getenv('PARTOO_API_KEY')  # it is a good practice to store secret in ENV variable
# in production you need to change below URL for 'https://api.partoo.co/v2'  
API_BASE_URL = 'https://sandbox.api.partoo.co/v2'    

# Make request to Partoo REST API to create the business
# for endpoint documentation see https://developers.partoo.co/rest_api/v2/#operation/createBusiness
response = requests.post(
            '%s/business' % API_BASE_URL,  # resource endpoint
            data={
                    'name': 'Corner shop',
                    'country': 'FR',
                    'city': 'Paris',
                    'zipcode': 75019,
                    'categories': [],  # Partoo categories ids, see https://developers.partoo.co/rest_api/v2/#operation/searchCategories
                  },
            headers={'x-APIKey': API_KEY},   # for authentication
)
response_body = response.json()
pprint(response_body, indent=2)
"""
Should return:
{
   "status": "success",
   "id": "5409c35a97bbc544d8e26737"  # id of the business you just created
}
"""
```
