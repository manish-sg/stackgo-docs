# StackGo Philosophy 🧠


SaaS platforms are more ubiquitous than ever. They’re growing in popularity in an increasingly congested and finely stratified SaaS market. Product integrations into SaaS platforms can be a channel for growth, a driver for improving customer retention and a hotbed for innovation on your core offering. We have written a lot about the importance of SaaS integrations on our blog, [check out this post](https://stackgo.io/software-marketplaces-for-growth/).

At StackGo we realise that development resources are a limiting factor in how many product integrations get shipped. Each platform has its data model, OAuth implementation and mode of operation adding to the complexity of SaaS integrations even before the use-cases and workflow are being worked out. Therefore, we have committed to our vision of an ecosystem of developer tools that boost developer efficacy and efficiency by reducing time to go live. 

We have also written extensively about how to find your ideal use case for building product integrations for product and technology leaders. Please see [this blog for more details](https://stackgo.io/data-integration-and-saas-marketplaces/) 


### StackGo Suite 📚

#### Managed Authentication 

<!-- theme: success -->
> StackGo's core value proposition is to enable SaaS providers to allow their users to connect to the SaaS platforms they already use and create a seamless user experience.

All SaaS product integrations require authorization and authentication before they can transact any data. This is where managed authentication comes in. 
StackGo offers its managed authentication capability to allow developers to get started quickly with oAuth based platforms. Using StackGo developers can leverage a standardised approach that is both state-of-the-art and secure. Hence developers can focus on building features for the end customers rather than being bogged in the minutiae of enabling these connections. It also reduces the cost of experimentation and barrier to starting integrations with new platforms.  

> Interested in learning more? Please work through our tutorial for [a walkthrough of our offereing](StackGo-Tutorial.md)

#### Unified APIs

While helping customers with their SaaS product integrations, we integrated with numerous SaaS platforms that have similar offerings within a vertical. However, because of to differing views in API design and product terminology, they refer to the same canonical elements with differing terminology and support different operations. 
Since StackGo is the nexus of all OAuth based connections, we added a layer of API translation that creates a standard for common resources within SaaS platforms of a vertical. For example, with CRMs, StackGo can define a standard for `Contacts` and define CRUD operations that can apply to any CRM.

> Want to see it in action? Here is an article that works its way through [an example](Unified-API-An-early-look.md)

#### FaaS - Function as a Service

APIs provided by SaaS platforms are the elemental operations for building workflows for SaaS product integrations. Often  several of these operations need to be strung together to create a workflow that adds value to the end-users journey. With our `FaaS` offering, we provide an easy-to-use interface to compose powerful workflows without having a enormous burden of changes on your existing codebases and having a very desirable de-coupling of integration logic code from the main application.

> Ready to explore? Please get in [touch](mailto:team@stackgo.io)

### Technical Architecture (High Level)

![../assets/sg_philosophy/StackGoasaService.jpg](../assets/sg_philosophy/StackGoasaService.jpg)

StackGo at its core is an API middleware solution and it shields your application and developers from the complexity of the API standards and authentication systems. In doing so, StackGo offers an alternative approach to managing authentication with third party systems by creating a secure standardised approach. By offloading aspects of token management and the power-up from the unified APIs and faas StackGo's offerings will boost your team's productivity without sacrificing the quality.

<!-- theme: warning -->
> ### Key Concepts
>From a technical implementation point of view there are a few concepts to introduce to make the most of the StackGo platform.

Note: Here we use the generic term `SaaS Platform` to represent any modern API enabled multi-tenanted SaaS offering such as Shopify, Salesforce, Xero and others.

The basic steps to get started are:

- Register a developer account on the SaaS platform

- Generate OAuth credentials (`client id`, `client secret,` `permissions`)

- Sign up for StackGo and configure the connector for your SaaS platform with credentials from the previous step

- StackGo will generate a custom `redirect URL`, register this URL with the SaaS platform

- Follow the `Generate Authorization Link` API to generate an installation link. You might have to get access to a trial or developer version of the SaaS platform to use the link.

- Complete the app installation via StackGo via the consent screen and then you can you the `proxy calls` API to start transacting data as per the API documentation

Example of a Google consent screen:

![../assets/sg_philosophy/GoogleOAuthConsent.png](../assets/sg_philosophy/GoogleOAuthConsent.png)


#### App Credentials Identifier `appSlug`
Each set of credentials  (`client id`, `client secret,` `permissions`) generated from the SaaS platform are referenced with an identifier in StackGo called the `appSlug`. This is important since it allows developers to maintain several integrations for each SaaS platform which is important to allow for different credentials for each environment (dev/test/prod) or custom integrations for different clients. 


#### User Foreign Identifier `userForeignIdentifer`
StackGo allows developers to register multiple users from their application to connect with their instance of the SaaS platform. E.g. Offering the user the ability to connect to their Shopify accounts and sync orders. To enable this, StackGo API consumers need to assign a user identifier for each API call they make. This usually takes the form of an identifier that is already in the system that denotes a unique tenant such as an `email`, `user id`, `organization id`, `uuid` and so on. 


### Tutorial 
Can't wait to get started? 
[Follow along for a guided tour on how to use StackGo to make SaaS integrations easier](StackGo-Tutorial.md). 






