### Why do we need to store it?
  - We store Aadhaar when the user shares it through an audio/text. We don't store the audio that is shared by the user. For the text part of, we store it until we give the final state of the user. If there is a failure, we remove it.
  - The need to store Aadhaar in plain text comes from
  - We used to store Aadhaar in the DB after the flow in order to save OTP verified state and for the same session user can get their status next time without entering the OTP again. We moved away from this flow and we invalidate the session as soon as the status response is delivered.
### Older Aadhaars?
  - Need to be removed from the Message Log
### Logging
  - We are not storing Aadhaar in logs right now


### Audit Requirements?

### Analytics Requirements?
