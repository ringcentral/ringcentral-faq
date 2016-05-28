#Usage Plan FAQ

### What is usage plan?
The Usage Plan is a scheme specifying limits of using the API resources. Applying usage plans enables consistent load allocation through correct interaction with RingCentral Connect Platform.

### How many requests of each API group the usage plan support?

Each usage plan features rates specifying how many requests to each API group are allowed. Currently four API groups are distinguished: Light,Medium, Heavy, Auth . Each request in API Reference is marked as heavy, medium, light or auth under the header Usage Plan Group. Each one inform you how many requests of each API group the usage plan supports and what is the time frame in seconds for every request.

### Does the  Rate Limit (Requests per Min - RPM) apply for API Group or for an API End Point?

 Rate Limits is per API Group. Explaination is as below:

 The /call-log api and  /active-calls api belongs to Heavy API group. For Basic Usage Plan we allow only 10 RPM for Heavy API group.

 If your application is using both /call-log and /active-calls APIs , you can only make 10 RPM of these APIs collectively and should not be considered as 10 API calls or /call-log and 10 API calls for /active-calls (not per API endpoint).

  If you exceed these limitations the server returns the 429 Too Many Requests HTTP error code. It means that the client is throttled by the server due to high request rate. Specific retry period in seconds, after which the requests can be sent, is specified in Retry-After response header.
