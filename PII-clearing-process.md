# Clear Personal Information from Sessions

## Overview

This repository contains code to automatically remove personal information, specifically Aadhaar numbers, from inactive user sessions. The process runs every 30 minutes, ensuring that sensitive data is cleared from completed or inactive sessions to maintain data privacy.

## How It Works

### Scheduled Task

The process is scheduled to run every 30 minutes using a cron job. During each execution, it performs the following steps:

1. **Find Inactive Sessions**:
   - Identify conversations last updated more than 30 minutes ago.
   - Check if the `userAadhaarNumber` field in the conversation context is not empty.

2. **Update Conversations**:
   - For each identified conversation, clear sensitive information.
   - Update the context by removing Aadhaar numbers and resetting related fields:
     - `userAadhaarNumber`
     - `lastAadhaarDigits`
     - `userIdentifier`
     - Various state indicators (`type`, `query`, `state`, `currentState`, `response`).

3. **Logging**:
   - Log the success of the operation.
   - In case of an error, log the error for debugging purposes.


<img width="395" alt="Screenshot 2024-07-02 at 9 52 14 AM" src="https://github.com/AgrI-Mitra/docs/assets/130033232/3b95c085-4e12-4d9c-a73f-2d1c4c63ebb0">
