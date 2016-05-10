# Voice - WebRTC FAQ

### Can I set Caller ID with WebRTC?

Yes. You can set Caller ID (CLID) using the [`ringcentral-web-phone` WebRTC SDK](https://github.com/ringcentral/ringcentral-web-phone). Just set the desired number as the `fromNumber` in the `webPhone.userAgent.invite()` method call.

### Can WebRTC support area code matching for Caller ID?

Yes. You will need to supply your own area-code matching algorithm, but as long as you have matching numbers for use in your account, you can set the CLID as you wish. One approach is to store your area-code CLID numbers as Auto-Receptionist Company Numbers.

### Are WebRTC call events captured via the event system?

Yes. Voice calls via WebRTC, RingOut and RingCentral endpoints are all captured via the event system. To check the presence status of an extension, you can call the extension presence API endpoint or subscribe to presence events via the subscription API or webhoks API.
