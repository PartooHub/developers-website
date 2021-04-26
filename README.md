# Partoo developers website

This repo contains the developer documentation provided to our clients when they want to integrate Partoo.

## Good habits

To limit the confusions and demands from clients, the documentation needs to respect the following:
- be as clear as possible: if you come back in a year, will you find answers to all your questions?
- each API should have a context: people won’t read your API documentation in order, and you can’t predict which 
part they will land on. 
- each parameter and all of their possible values, including their types, formatting, rules, and whether or 
not they are required.


## Partoo documentations

There are two different approaches to integrate our solution:
- JS SDK (documentation built using [Sphinx](https://pypi.org/project/Flask-Sphinx-Themes/)): Partoo app integrated as 
 White Label. The SDK will generate an Iframe.
- APIs (documentation built using [ReDoc](https://github.com/Redocly/redoc)): Usually used to automatically send new POIs 
(businesses) or to do statistics. 


## Deployment

Any modification on the documentation needs to be double checked on preprod before deployed in prod.
Therefore, you can use the following two branches:
- `master` branch will deploy in [preprod](https://preprod.developers.partoo.co/rest_api/v2/)
- `prod` branch will deploy in [production](https://developers.partoo.co/rest_api/v2/)
The deployment is done using [ansible](https://github.com/PartooHub/partoo/tree/master/devops/ansible).

## Running project locally

### JS SDK - documentation
Setup the evnironement
```shell script
virtualenv -p python3 venv  # install the venv if you don't have it
source venv/bin/activate
pip install -r requirements.txt
```

Run the project
```shell script
source venv/bin/activate  # if it's not activated already
make html  
```
The open in the browser the generated files from ~/developers/_build/html/js_sdk/index.html 

### REST API - documentation
Using yarn:
```shell script
yarn
yarn watch  # will start a server on port http://127.0.0.1:8081
```

Using npm:
```shell script
npm install
npm run watch  # will start a server on port http://127.0.0.1:8081
```
