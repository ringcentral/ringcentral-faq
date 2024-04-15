Call Log API not matching Performance Report
Times do not match between the Call Log APIs for Call Sessions and the information displayed in the Analytics Performance Report. Details are attached.

Discrepancy in Duration of Total Call Time, IVR, Talk Time. Also, Queue time and Hold Time is not available through Call Log API. No Tie to Transferred Call.

Where is the data stored that is being used to populate the Performance Report. Are there API calls to retrieve this? Do not want to implement subscriptions/notifications.

**Answer**

The Analytics Performance Report application does not use much of platform APIs to catch and calculate those data. Currently, there is no API to access processed (nor raw) data from the performance report. You can send your feature requests to the product support so they may assist you better.

You are right about the call log data, it contains only basic call data which may not be enough for call analytics. Since you are not interested at implementing subscription/notification, I cannot help you much with any solution.