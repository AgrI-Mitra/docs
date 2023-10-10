### Why log?
1. Audit
2. Debugging

### What do we log?
1. User Input.
2. Session id (When new session is started).
3. PM kisan Encrypted request data while sending OTP.
4. Bhasini API logs
  a. API end point when triggered
  b. Responded status (if its responded or not)
  c. Message to indicate retry
5. Final response.
6. Final translated response.

### Log Format
<Timestamp> <SessionID> <ActionName> <ActionData>

### Complete List of Logs
1. Error:
- BhashiniTranslate
- BhashiniASR
- BhashiniT2S
- PMKisanSendOTP
- PMKisanVerifyOTP
- PMKisanUserDetails
- PMKisanBeneficiaryStatus
- DatabaseService
- Classifier
- Miscellaneous
2. Info:
- BhashiniRetry
- BhashiniResponseStatus
- PMKisanResponseStatus
