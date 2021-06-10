# Unified API - An early look

Due to the ubiquity of SaaS, each vertical and business function has a large number of competing players largely focussed around the same business outcomes. Here are some examples:

Customer Relationship Management (CRM): Salesforce, Hubspot, Pipedrive, SugarCRM etc.
Accounting: Xero, MYOB, QuickBooks, Netsuite etc.
E-Commerce: Shopify, WooCommerce, BigCommerce, Magento etc.

Largely, they are composed of the same or similar resources however developers seeking to integrate with multiple players in a single vertical are frustrated since each SaaS platform will have differing API designs and different naming conventions. 

With this proof of concept of StackGo's unification API service, we will show how such integration problems can be circumvented. 

Proof of concept in CRM space with a StackGo defined `generic resource` called `Contact` for Hubspot and Pipedrive. Regardless of the underlying API structure and the naming convention we can define methods for `list`, `create`, `read`, `update` and `delete` that return normalised and uniform reponses regardless of the underlying implementation.

See below for an example of a `get contact` API call made to Pipedrive and Hubspot and how the only difference between the requests is the `appSlug` with `hbdev` being a Hubspot account and `pd` being a Pipedrive instance. This powerful layer of abstraction can protect from versioning changes and allow developers to add lots of functionality in a small amount of time.

If you would like to have a deeper look at this preview, please email at team@stackgo.io

## Hubspot 


### Request

```bash
curl 'api/graphql?userForeignIdentifier=m@m.com&appSlug=hbdev'  \n
-H 'Content-Type: application/json' \n
-H 'Accept: application/json'  \n
--data-binary '{"query":"query genericContactsHs {\n  getGenericContact(id: 1) {\n    name\n    id\n    email\n  }\n}"}'
```

### Response 

```json
{
  "data": {
    "getGenericContact": {
      "name": "MariaJohnson (Sample Contact)",
      "id": 1,
      "email": "emailmaria@hubspot.com"
    }
  }
}
```


## Pipedrive

### Request 
```bash
curl 'api/graphql?userForeignIdentifier=manish@pipe.com&appSlug=pd' \n
 -H 'Content-Type: application/json' \n
-H 'Accept: application/json' \n
--data-binary '{"query":"query genericContactsPd {\n  getGenericContact(id: 2) {\n    name\n    id\n    email\n  }\n}"}'
```

### Response

```json
{
  "data": {
    "getGenericContact": {
      "name": "testinf per",
      "id": 2,
      "email": "testing@per.com
    }
  }
}
```