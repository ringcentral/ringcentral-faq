# How can I archive my company's call logs?

**Question**

I am new to coding and need help in archiving call logs. Please guide me with c# code to automatically archive call logs older than 3 days.

**Answer**

Our Developer Guide provies a [useful code sample](https://developers.ringcentral.com/guide/voice/call-log/reading-call-log#C#) in a number of different programming languages to cover the call log archival use case.

To define the period of time you want to read the call log, specify the `dateFrom` and `dateTo` as an example below:

```
parameters.dateFrom = "2019-08-05T00:00:00.000Z" 
parameters.dateTo = "2019-08-08T23:59:59.999Z" 
```

If you don't specify the `dateTo` parameter, it will take the current date and time.

Extra credit: Implement the [call log synchronization API](https://developers.ringcentral.com/api-reference/Call-Log/syncUserCallLog) to archive call log data periodically.

## Additional resources

* [Use Message Sync API to archive your SMS, Fax and Voicemail Messages](https://medium.com/ringcentral-developers/use-message-sync-api-to-archive-your-sms-fax-and-voicemail-messages-cd23748e188f)
