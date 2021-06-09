# StackGo Philosophy


SaaS platforms are more ubiquitous than ever. They’re growing in popularity in an increasingly congested and finely stratified SaaS market. Product integrations into SaaS platforms can be a channel for growth, improving customer retention, creating seamless customer journeys and a hotbed for innovation on your core offering. We have written a lot about the importance of SaaS integrations on our blog, [feel free to check out this post](https://stackgo.io/software-marketplaces-for-growth/).

At StackGo we realise that devlopment time is a limiting factor in how many product integrations get built. Since each platform has its own data model, oAuth implementation and mode of operations. Therefore we are deeply commited to our vision of an ecosystem of developer tools that boost effiancy by a factor of 10 by reducing to allow for faster iterations and greater agilty. 

We have also written extensivley about how to find your ideal use-case for building product integrations for product and technology leaders. Please see [this blog for more details](https://stackgo.io/data-integration-and-saas-marketplaces/) 


### StackGo Suite

#### Managed Authentication 

All SaaS product integrations require authorization and authentication before any data can be transacted, this is where managed authentication comes in! 
StackGo offers its managed authentication to allow developers to get started quickly with oAuth based platforms with a standardised approache that is state of the art and secure implementation. Hence developers can focus on building features for customers rather than being bogged in the minutiae of authentication. It also reduces the cost of experimentation and starting integrations with new platforms.  

Interested in learning more? Please work through our tutorial for [a tutorial](linik)

#### Unified APIs

While helping customers with the their SaaS product integrations we worked with a large number of SaaS platforms that have similar offerings within a vertical. However due to differing views in API design and product terminology they refer to the same canonical elements of a domain with differing terminology and support different operations. 
Since StackGo is the nexus off all oAuth based connections as per the `Managed Authentication` offereing we added a layer of API translation that creates a notional standard for common resources within a vertical. For example, with CRMs, StackGo can define a standard for `Contact` and define CRUD operations and fields that can be applied to any CRM.

Want to see it in action? Here is an article that works its way through [an example](example)

#### FaaS - Function as a Service

APIs provided by SaaS platforms are the elemental operations for building workflows for SaaS product integrations. Often times a number of these operations need to be strung together to create a workflow that adds value to the end-users journey. With our `FaaS` offering we provide an easy to use interface to compose powerful workflows without having a large burden of changes on your existing code bases and having a very desireable de-coupliing of integration logic code from main applicaiton.

Ready to explore? Please get in [touch](link)

### Technical Architecture

Diagram




### Key Concepts



### Tutorial 
Follow along for a guided tour on how to use StackGo to make SaaS integrations easier. 


From a technical implementation point of view there are a few concepts to introduce to make the most of the StackGo platform.

For StackGo to provide with the best developer experiance our product suite starts off with a managed authentication process for building oAuth based app experiances. 

When you login to the StackGo platform you will see prompts asking you to select which platform would you like to create a connection. The first step for that would be 

User Foreign Identifer `userForeignIdentifer`

App Credentials Identifier `appSlug`



