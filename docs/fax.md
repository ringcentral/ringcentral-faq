# Fax FAQ

RingCentral Fax allows you to send and receive faxes using our API as well as our endpoint apps including RC mobile apps and Online Account Portal.

## General

### What are the general questions about fax?

General information about the RingCentral fax service can be found on the End-User Fax Service FAQ [here](http://success.ringcentral.com/articles/en_US/RC_Knowledge_Article/7027).

### How do I know if a fax transmission through the API succeeded?

When you are sending a fax message through the FaxOut API, you can check the status of this transmission. Outgoing faxes pass through several workflow phases, so when you have just sent an API request `messageStatus` property `Queued` (this status is returned in the FaxOut API response). After some time (usually within couple of minutes) the status of the fax message will be changed to either `Sent` (which means that message was sent successfully) or to `Sending Failed`. You can call the Get Message or the Get Message List API to check the status of a particular message. The Get Message end point is provided in the `uri` property of the Send Fax response.

### Can I set the cover page "To" value?

Yes. The To attribute on the cover page is set two ways. If the `to.name` property is set in the request body, that value will be used on the cover page. If it is not set, the system will create a name by concatenating the `firstName` and `lastName` attributes of the address book contact with a matching `businessFax` number attribute.

### Can I send multiple files as one fax?

Yes. Just add each file as a MIME part. You can mix and match different MIME types. The Ruby fax helper has an `.add_file()` method that can be used in succession to add multiple files.

### What file types are supported for faxes?

RingCentral supports 29 file types including PDF, TIFF, DOCX, DOC, XLSX, XLS, RTF, HTML, XML and many more. These are listed in the [API Developer Guide](https://developers.ringcentral.com/api-docs/) along with the accepted MIME types.

### Is there a limit on fax file size?

Fax files are limited to 20 MB or 200 pages.

### How can I view sent faxes in the Service Web Portal?

Yes, faxes sent via the API can be viewed in the Service Web Portal (https://service.ringcentral.com) in both `Messages > Sent Items` and in the `Call Log`. The rendered fax documents can be downloaded from `Messages > Sent Items`.

### How can I retrieve a sent fax via API?

When sending a fax via the API, the fax message `messageId` and rendered fax `attachmentId` can be used in the message store end points to retrieve the message information or attachment. Authorized apps can retrieve faxes for the user that authorized the app. Admin user authorized apps can retrieve faxes for the account.

### What formats can faxes be stored and retrieved in?

RingCentral supports storing faxes as PDF and TIFF files. The configuration preference is available per extension. Upon retrieval, the `Content-Type` HTTP response header will be set to `application/pdf` or `image/tiff`.

### Is it possible to find out why a fax failed?

If a fax transmission fails, the reason is reported in the Call Log Record's `result` property. It is also presented in the Service Web Portal.

### Is it possible to send a fax without the fax header line?

Not at this time. In the US, it is unlawful to send a fax with out the header line consisting of the following "the date and time it is sent and an identification of the business, other entity, or individual sending the message and the telephone number of the sending machine or of such business, other entity, or individual." This applies to all faxes based on content and delivery method (e-fax or traditional fax machines). This is specified in [US 47 CFR &#167; 68.318(d)](https://www.law.cornell.edu/cfr/text/47/68.318). For advertising specifically, this is also covered under the Telephone Consumer Protection Act of 1991 (TCPA), [47 USC &#167; 227(d)(1)(B)](https://www.law.cornell.edu/uscode/text/47/227).

## Technical Questions

### Is providing a filename in the Content-Disposition header necessary?

A filename isn't necessary but if you provide one, it will be displayed in the [RingCentral Online Account Portal](https://service.ringcentral.com).

### Why can the faxPageCount change?

When a fax request is first submitted the `faxPageCount` is set to 0 when when `messageStatus` is set to `Queued` because the fax hasn't been rendered yet so the number of pages haven't been counted. When the fax is successfully rendered and sent with `messageStatus` set to `Sent` the `faxPageCount` will be properly populated. In the event that the message is not successfully sent and the `messageStatus` is set to `SendingFailed`, the `faxPageCount` property may or may not be sent depending on the type of failure.

### Will retrieving a rendered fax attachment change the read status?

Retrieving a fax attachment file via the API will not change the read status to `Read` from `Unread`. This is desirable as retrieving the fax document may be for archival and other purposes that should not indicate the fax was read. To change the status use the Update Message API call.

### Why does my PDF fax have rendering issues.

Some faxes may use unsupported features and require flattening before sending them to the RingCentral API. Some PDF flattening tools include [GraphicsMagick](http://www.graphicsmagick.org/) / [ImageMagick](http://www.imagemagick.org/) and [Ghostscript](http://www.ghostscript.com/).

### What is causing the delay in delivery of my faxes?

Usually, sending faxes with the RingCentral API takes our services less than 2 minutes to send fax from the moment when the request has been successfully processed from your request(s).

However the delay between moment when a fax is created in the RingCentral database (for logging and processing) and when it was sent can depend on many parameters (number of recipients, complexity and size of attached files, etc).

### When sending a fax, what does the API error "No call time. You did not have enough available Calling Credits to send this fax" mean?

Sandbox accounts have a limited number of fax minutes per month. This API error means the account has run out of minutes for the current month. By default, sandbox accounts come with 1000 minutes per month. You can view your monthly minute usage and rollover date in the sandbox Online Account Portal. Login to the sandbox Online Account Portal at [https://service.devtest.ringcentral.com](https://service.devtest.ringcentral.com) with an administrator account and then go to `Billing` > `Service Plan`. Your usage for the current month is available under `Usage Info` and your rollover date is listed as `Next Billing Date`.

## Application Configuration

### Do I need multple sandbox accounts to support multiple fax numbers?

This depends on how you intend your application to work with the multiple fax numbers.

If you intend the multiple fax numbers to be owned by a single production RingCentral customer, then you only need a single Sandbox Account to represent the single Production Account. Within a single Sandbox (or Production) Account, you can create multiple Direct Numbers for fax that can be either Company Numbers (no extension) or a Direct Extension Number (associated with an extension).

If you intend the multiple fax numbers to be owned by and associated with multiple production RingCentral Customers, then you can create multiple Sandbox Accounts to represent the multiple Production Accounts.

### How many faxes can I send per minute or per hour via the API?

The throttling rates per API are determined by your [RingCentral API Usage Plan](https://developer.ringcentral.com/api-docs/latest/index.html#!#UsagePlan.html) and the API group for the API in question. The fax API is classified as a *Heavy* API which is set to 10 requests / minute by default so the fax rate is 10 per minute or 600 per hour. Higher rate usage plans may be avaiable to you depending on your use case. Create a support case if you wish to request an increase your sending rate.
