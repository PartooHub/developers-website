# Partoo Environments

Partoo has 2 environments:

- Production
- Sandbox: environment meant for client/partner technical teams that want to test our API/App or that need a development environment to integrate our API/App

The 2 environments are running the same code however there are 2 important differences:

- Sandbox servers are smaller compared to production ones so performances in sandbox environment are not as great in production environment
- Notification/fetch/push functionalities have been deactivated on Sandbox to prevent spam and malicious use. Sandbox environment is "isolated from the word". Reviews and analytics data on it are fake data to mock production.

## Sandbox

Sandbox base urls are:

- for the API: [https://sandbox.api.partoo.co/v2](https://sandbox.api.partoo.co/v2)
- for the application: [https://sandbox.partoo.co/app/](https://sandbox.partoo.co/app/)

## Production

> **⚠️ Warning:** It was previously possible to access the api using https://www.partoo.co/api/v2. This base url
> is DEPRECATED and is going to be sun set on July 1st 2020

Production base urls are:

- for the API: [https://api.partoo.co/v2](https://api.partoo.co/v2)
- for the application:
    - [https://www.partoo.co/app/](https://www.partoo.co/app/)
    - [https://www.localoo.es/app/](https://www.localoo.es/app/)
