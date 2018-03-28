# SDKs & Programming

## SDKs

### Where can I find the list of RingCentral SDKs?

https://developer.ringcentral.com/library/sdks.html

Or you can check RingCentral's GitHub page: https://github.com/ringcentral

### Which official C# SDK should be used?

https://github.com/ringcentral/ringcentral-csharp-client is the correct one

https://github.com/ringcentral/ringcentral-csharp has been deprecated.

### The C# SDK provides async style APIs, what are the proper ways to invoke them?

There are two ways to invoke C# async methods: `await f()` or `f().Result`. The former is async while the latter is sync.

### How to catch and print exceptions with RingCentral C# SDK?

Please read the sample code here: https://github.com/ringcentral/ringcentral-csharp-client#exception-handling

## Programming

### How to use RingCentral together with React?

React is a generic solution for frontend development. If you want a sample application for RingCentral with React, here it is: https://github.com/ringcentral/ringcentral-js-widgets

### How to programmatically dial a number?

You can either invoke the ringOut api or use the RingCentral webphone SDK. Please read this ticket: https://devcommunity.ringcentral.com/ringcentraldev/topics/programmatically-dial-a-number

### How can I set the presence of the current logged in user via API?

You can set the presence of the current logged in user by updating extension presence: https://developer.ringcentral.com/api-docs/latest/index.html#!#RefUpdateExtensionPresence

### How can I start RingCentral app to dial a number via command line?

On macOS, you can execute the following command in terminal: `open "rcmobile://call?number=1234567890"`
