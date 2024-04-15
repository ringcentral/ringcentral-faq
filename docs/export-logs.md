# How do I export my call logs to another system?

**Question**

I have successfully retrieved both simple and detailed call log records from API calls. However, I am interested in obtaining every call log to store in our database. This would allow us to limit the amount of needed calls to the RingCentral API and the data would be much more accessible. To do that, I have a number of questions:

* Although the API returns data in a JSON format, does RingCentral provide any sort of data export in another format, like CSV?
* The `perPage` limit on the call log request has a maximum of 1000. Can this limit be increased?
* It is possible for us to write a script to call for these logs from the last several months and record the data from each call?
* When requesting call log data via the API I can only retrieve up to a certain date. Is there a date/data limit to the call log request?

**Answer**

Obviously, there are multiple questions here under the topic of exporting a company's call log. Let's take each in turn.

## Can I export call log data in CSV format?

Currently, the RingCentral API only allows for call log data to be accessed in a JSON format. The structure of a call log is variable enough that there is not a universal format we could define in a fixed format like CSV. Therefore, developers would need to convert JSON to CSV themselves if they require it in this format. 

## Can I increase the perPage limit when accessing call log data?

No. The perPage limit is fixed in order to protect against abuse. 

## Can I create a script to download data from several months ago?

RingCentral only stores call log data for a finite amount of time -- typically for 90 days, or less depending upon your subscription plan. So the API allows you to fetch data, but only as far back is we have data currently stored. 

## Is there a data or date limit to my call log requests?

See answer above. RingCentral only stores call log data for 90 days. 

## Additional resources

* [https://github.com/bdeanindy/ringcentral-call-log-download-demo](https://github.com/bdeanindy/ringcentral-call-log-download-demo)
