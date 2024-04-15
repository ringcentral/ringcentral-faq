# Looking up your account and extesion ID

**Question**

Often an API endoint calls for an account ID and/or an extension ID. Where do I find these values so that I can insert them into my URL?

**Answer**

The RingCentral service allows its customers to create and register an account that is usually associated with the customer's company. After registering the account with the company main number the user can create extensions of different types and functionality. The extensions can further be assigned with the phone numbers and phone devices.

The first thing you need to know is that it is rarely necessary to know your account ID. When formulating the URI for an API endpoint that requires you to input an account ID, you can use a tilda (`~`) as a shorthand for "the current account of the currently authenticated user."

Extension IDs can be found using the [List Extensions](https://developers.ringcentral.com/api-reference/Extensions/listExtensions). When specifying an extension ID, developers should be aware of the following:

1. Like when referencing an account ID, the tilda (`~`) can be used as a shorthand to refer to the "extension of the currently authenticated user."

2. The extension number, what one dials to reach a person on the phone, is NOT the same thing as an extension ID, which is a globally unique identifier across all of RingCentral.
