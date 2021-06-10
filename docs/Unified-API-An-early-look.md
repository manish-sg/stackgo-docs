# Unified API - An early look

Due to the ubiquity of SaaS each vertical and business function has a large number of competing players largely focussed around the same business outcomes. Here are some examples:

Customer Realationship Management (CRM): Salesforce, Hubspot, Pipedrive, SugarCRM etc.
Accounting: Xero, MYOB, QuickBooks, Netsuite etc.
E-Commerce: Shopify, WooCommerce, BigCommerce, Magento etc.

Largely, they are composed of the same or similiar resouces however developers seeking to integrate with multiple players in a single vertical are frustrated since each SaaS platform will have differing API designs and differing naming convetions. 

With this proof of concep of StackGo's unification api service we will show how such integration problems can be circumvented. 

Proof of concept in CRM space with a StackGo defined `generic resource` called `Contact` for Hubspot and Pipedrive. Regardless of the underlying API structure and the naming convention we can defined methods for `list`, `create`, `read`, `update` and `delete` that return normalised and uniform repsonses regardless of the underlying implmentations.

See below for an example of a `get contact` API call made to pipdedrive and hubspot and how the only differece between the request's is the `appSlug` with `hbdev` being a Hubspot account and `pd` being a pipedrive instance. This powerful layer of abstraction can protect from versionaing changes and allow developers to add lots of a functionality in a small amount of time.

If you would like to have a deeper look at this preview, please email us team@stackgo.io

## Hubsport 


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