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
| Timestamp | SessionID | Log Type | ActionName | ActionData |
| --------- | --------- | -------- | ---------- | ---------- |
* Action Data may vary for each action (It will be an JSON).

### Complete List of Logs Actions:
| Action | Log Type | Log Data | 
| ------ | -------- | -------- |
| SessionState | INFO | State at which current session in |
| BhashiniTranslate | INFO | Retry indicator |
| BhashiniTranslate | INFO | Success indicator |
| BhashiniTranslate | ERROR | Any error received |
| BhashiniASR | INFO | Retry indicator |
| BhashiniASR | INFO | Success indicator |
| BhashiniASR | ERROR | Any error received |
| BhashiniT2S | INFO | Retry indicator |
| BhashiniT2S | INFO | Success indicator |
| BhashiniT2S | ERROR | Any error received |
| PMKisanSendOTP | INFO | Success indicator |
| PMKisanSendOTP | ERROR | Any error received |
| PMKisanVerifyOTP | INFO | Success indicator |
| PMKisanVerifyOTP | ERROR | Any error received |
| PMKisanUserDetails | INFO | Success indicator |
| PMKisanUserDetails | ERROR | Any error received |
| PMKisanBeneficiaryStatus | INFO | Success indicator |
| PMKisanBeneficiaryStatus | ERROR | Any error received |
| DatabaseService | ERROR | Invalid operations/missing data |
| Classifier | ERROR | Any error received |
| Miscellaneous | ERROR | Unexpected/Unidentified errors |
