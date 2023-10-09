### Why Store audio?
1. Debugging
2. Audit

### Various Origins for audio (TABLE)
   | Part of the flow | User/Machine generated | Frequency in a flow | Cached or not | Should we store? | Storage time | Cost of storing |
   | -----------------| ---------------------- | ------------------- | ------------- | ---------------- | ------------ | --------------- |
   | 1. User opens the bot. | Machine | 1 | No | No | - | - |
   | 2. User asks bot a question via audio | User | 1 | No | Yes | 30days | - |
   | 3. Bot response to above question (invalid question, asking otp, conversation starter default response) | Machine | based on user question | Yes | Yes (debug) | 30days | - |
   | 4. User speaks Aadhaar number | User | 1 | No | Yes (audit) | 30days | - |
   | 5. Bot responds via asking OTP | Machine | 1 | Yes | No | - | - |
   | 6. User speaks OTP | User | depends on user to enter correct OTP | No | Yes (audit) | 30days | - |
   | 7. Bot responds with user status | machine | 1 | Yes | Yes (audit) | 30days | - |

### Number of Sessions in a Day

### Calculation on Storage Requirements
