#  📖 StackGo-Tutorial

This is a guided tour of StackGo capabilities, we expect you to have read through the [StackGo Philosophy](Docs Home.md) before attempting this guided tour.

Open all links in a new tab so you can easily refer to the next steps. 

### Step 0: Sign up for StackGo
Follow along [here](SignUp-StackGo.md)

### Step 1: Generate some `SaaS platform` credentials

[Getting Started with Hubspot](https://docs.stackgo.io/docs/stackgo-docs/docs/GettingStarted-Hubspot.md#1-sign-up-for-a-developer-account---httpsdevelopershubspotcom) - Step 1

Add **only** `contacts` as a scope

### Step 2: Add credentials to StackGo to configure your connection
[Getting Started with Hubspot](https://docs.stackgo.io/docs/stackgo-docs/docs/GettingStarted-Hubspot.md#2-pass-credentials-to-stackgo) - Step 2

Ensure you select `contacts` scope in the StackGo configuration and leave the `redirect url` empty. 

Make a note of your `appSlug` for later steps.

### Step 3: Generate your StackGo access token
Visit the docs at [`Fetch StackGo Tokens`](https://docs.stackgo.io/docs/stackgo-docs/All-OpenApi3Json.json/paths/~1oauth~1token/post) and then add your add `client_id` and `client_secret` to the body in the `Try it now` panel and hit `Send`.

#### Sample Response:

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6ImhjNTN6T0ZoY2lXZXVTNHR5REF2dyJ9.eyJpc3MiOiJodHRwczovL3N0YWNrZ28uYXUuYXV0aDAuY29tLyIsInN1YiI6IkhBd0daVlF6cWhOQlY4bEt0RGNNcUV5dXdUd2ZWSjBFQGNsaWVudHMiLCJhdWQiOiJodHRwczovL3N0YWNrZ28ucHJvZC5hcGkiLCJpYXQiOjE2MjMyMjE0MDEsImV4cCI6MTYyMzMwNzgwMSwiYXpwIjoiSEF3R1pWUXpxaE5CVjhsS3REY01xRXl1d1R3ZlZKMEUiLCJndHkiOiJjbGllbnQtY3JlZGVudGlhbHMifQ.lovgvkRawqBofSd1lVvERti950dExdxFAlzA2rX7-mZi02fw6xaN5e6DA06la_NWxEGKy7PZ-9auz7GEehFNwjzw-TkLGLNCI6KfYarzeED4JeDGyM1HZ0UuL16Obf9ygGKnAtbLqFrhYOANm6iiK82i-cOMkA9tqIGpXLvvMjdNccnDGm522gd0YAY6-km33TKBO20Xr7RN_YQ9q5YE5QNcVTVtLxVsVI19Wvt2I0OI5rDNSTT-AYavqekqlgpVhSHsHA76r4Ch1mjs1lg8RtQXi3btG7oxq-rqhQLtk476SxXQSMVg0D2J_N7TbwGmGmEHkCnyjRh41xNAWMw5Xg",
  "expires_in": 86400,
  "token_type": "Bearer"
}
```

Store the value for the `access_token` perhaps in a text file or password manager. 

### Step 4: Create an 'Authorization Link` for your Hubspot

Visit the [Hubspot Generate Link](https://docs.stackgo.io/docs/stackgo-docs/All-OpenApi3Json.json/paths/~1hubspot~1auth~1%7BappSlug%7D/get) and in the rignt pane add any string as `userForeighIdentifer` and the `appSlug` from Step 2. Make a note of the `userForeighIdentifer` for the onward steps.

#### Sample Response

```json
{
  "url": "https://app.hubspot.com/oauth/authorize?client_id=6dc4b7ab-3ffd-4bcb-8046-7992dc102543&scope=contacts%20forms&redirect_uri=https%3A%2F%2Fapi-dot-stackgo-300922.ts.r.appspot.com%2Fhubspot%2Fhbdev-965a9683-a2bf-420b-9551-dcd3a62bb7b8%2Fcallback&state=test%40test.com",
  "userForeignIdentifier": "test@test.com",
  "UUID": "965a9683-a2bf-420b-9551-dcd3a62bb7b8"
}
```

### Step 5: Open the `URL` in a new tab, you will reach the consent screen to authorise and return to this screen.

```json
{
  "message": "User Registered",
  "userForeignIdentifier": "test@test.com"
}
```

### Step 6: Make proxy calls via StackGo to Hubspot
Visit the [Hubspot proxy calls] page(https://docs.stackgo.io/docs/stackgo-docs/All-OpenApi3Json.json/paths/~1raw~1%7BHubspotAppSlug%7D/post).

In the `Try-it-now hand side panel update the body to reflect your `appSlug` as the path parameter. In the body of the API call update `userForeignIdentifier`, the url `method` to `GET` and `url` to `https://api.hubapi.com/forms/v2/forms`  and hit `Send`

#### Sample Response 

```json
{
  "data": [
    {
      "portalId": 8511822,
      "guid": "f353e406-254c-4ae1-bca7-33968d1b4722",
      "name": "New registration form (January 28, 2021 11:05:02 AM) ",
      "action": "",
      "method": "POST",
      "cssClass": "hs-form stacked",
      "redirect": "",
      "submitText": "Submit",
      "followUpId": "",
      "notifyRecipients": "11766037",
      "leadNurturingCampaignId": "",
      "formFieldGroups": [
        {
          "fields": [
            {
              "name": "email",
              "label": "Email",
              "type": "string",
              "fieldType": "text",
              "description": "",
              "groupName": "contactinformation",
              "displayOrder": -1,
              "required": true,
              "selectedOptions": [],
              "options": [],
              "validation": {
                "name": "",
                "message": "",
                "data": "",
                "useDefaultBlockList": false,
                "blockedEmailAddresses": []
              },
              "enabled": true,
              "hidden": false,
              "defaultValue": "",
              "isSmartField": false,
              "unselectedLabel": "",
              "placeholder": "",
              "dependentFieldFilters": [],
              "labelHidden": false,
              "propertyObjectType": "CONTACT",
              "metaData": [],
              "objectTypeId": "0-1"
            }
          ],
          "default": true,
          "isSmartGroup": false,
          "richText": {
            "content": "",
            "type": "TEXT"
          },
          "isPageBreak": false
        },
        {
          "fields": [
            {
              "name": "firstname",
              "label": "First name",
              "type": "string",
              "fieldType": "text",
              "description": "",
              "groupName": "contactinformation",
              "displayOrder": -1,
              "required": false,
              "selectedOptions": [],
              "options": [],
              "validation": {
                "name": "",
                "message": "",
                "data": "",
                "useDefaultBlockList": false,
                "blockedEmailAddresses": []
              },
              "enabled": true,
              "hidden": false,
              "defaultValue": "",
              "isSmartField": false,
              "unselectedLabel": "",
              "placeholder": "",
              "dependentFieldFilters": [],
              "labelHidden": false,
              "propertyObjectType": "CONTACT",
              "metaData": [],
              "objectTypeId": "0-1"
            }
          ],
          "default": true,
          "isSmartGroup": false,
          "richText": {
            "content": "",
            "type": "TEXT"
          },
          "isPageBreak": false
        },
        {
          "fields": [
            {
              "name": "lastname",
              "label": "Last name",
              "type": "string",
              "fieldType": "text",
              "description": "",
              "groupName": "contactinformation",
              "displayOrder": -1,
              "required": false,
              "selectedOptions": [],
              "options": [],
              "validation": {
                "name": "",
                "message": "",
                "data": "",
                "useDefaultBlockList": false,
                "blockedEmailAddresses": []
              },
              "enabled": true,
              "hidden": false,
              "defaultValue": "",
              "isSmartField": false,
              "unselectedLabel": "",
              "placeholder": "",
              "dependentFieldFilters": [],
              "labelHidden": false,
              "propertyObjectType": "CONTACT",
              "metaData": [],
              "objectTypeId": "0-1"
            }
          ],
          "default": true,
          "isSmartGroup": false,
          "richText": {
            "content": "",
            "type": "TEXT"
          },
          "isPageBreak": false
        },
        {
          "fields": [
            {
              "name": "phone",
              "label": "Phone number",
              "type": "string",
              "fieldType": "text",
              "description": "",
              "groupName": "contactinformation",
              "displayOrder": -1,
              "required": false,
              "selectedOptions": [],
              "options": [],
              "validation": {
                "name": "",
                "message": "",
                "data": "7:20:true",
                "useDefaultBlockList": false,
                "blockedEmailAddresses": []
              },
              "enabled": true,
              "hidden": false,
              "defaultValue": "",
              "isSmartField": false,
              "unselectedLabel": "",
              "placeholder": "",
              "dependentFieldFilters": [],
              "labelHidden": false,
              "propertyObjectType": "CONTACT",
              "metaData": [],
              "objectTypeId": "0-1"
            }
          ],
          "default": true,
          "isSmartGroup": false,
          "richText": {
            "content": "",
            "type": "TEXT"
          },
          "isPageBreak": false
        }
      ],
      "createdAt": 1611792380136,
      "updatedAt": 1611792384849,
      "performableHtml": "",
      "migratedFrom": "",
      "ignoreCurrentValues": false,
      "metaData": [
        {
          "name": "lang",
          "value": "en"
        },
        {
          "name": "embedType",
          "value": "REGULAR"
        }
      ],
      "deletable": true,
      "inlineMessage": "Thanks for submitting the form.",
      "tmsId": "",
      "captchaEnabled": false,
      "campaignGuid": "",
      "cloneable": true,
      "editable": true,
      "formType": "HUBSPOT",
      "deletedAt": 0,
      "themeName": "canvas",
      "parentId": 0,
      "style": "{\"fontFamily\":\"arial, helvetica, sans-serif\",\"backgroundWidth\":\"100%\",\"labelTextColor\":\"#33475b\",\"labelTextSize\":\"13px\",\"helpTextColor\":\"#7C98B6\",\"helpTextSize\":\"11px\",\"legalConsentTextColor\":\"#33475b\",\"legalConsentTextSize\":\"14px\",\"submitColor\":\"#ff7a59\",\"submitAlignment\":\"left\",\"submitFontColor\":\"#ffffff\",\"submitSize\":\"12px\",\"paginationProgressColor\":\"#598aff\",\"paginationProgressTextColor\":\"#33475b\",\"paginationProgressShow\":true,\"paginationProgressTransition\":\"fade\",\"paginationProgressTheme\":\"default\",\"paginationContentUseScroll\":false,\"paginationContentScrollHeight\":\"100%\"}",
      "isPublished": true,
      "publishAt": 0,
      "unpublishAt": 0,
      "publishedAt": 0,
      "multivariateTest": {
        "variants": [],
        "startAtTimestamp": 0,
        "endAtTimestamp": 0,
        "winningVariantId": "",
        "finished": false,
        "controlId": ""
      },
      "kickbackEmailWorkflowId": 0,
      "kickbackEmailsJson": "",
      "customUid": "",
      "createMarketableContact": true,
      "editVersion": 0,
      "thankYouMessageJson": "",
      "themeColor": "",
      "alwaysCreateNewCompany": true,
      "internalUpdatedAt": 1611792384849,
      "businessUnitId": 0
    }
  ]
}
```
















