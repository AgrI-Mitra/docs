# Clearing Personal Information from Inactive or Completed Sessions

## Overview

This repository contains code to automatically remove personal information, specifically Aadhaar numbers, from user sessions. The process clears data immediately upon session completion and also runs every 30 minutes to clear data from inactive or incomplete sessions.

## How It Works

### Immediate Clearing on Session Completion

When a session is marked as complete, the system immediately clears the following personal information from the session context:
- `userAadhaarNumber`
- `lastAadhaarDigits`
- `userIdentifier`
- Various state indicators (`type`, `query`, `state`, `currentState`, `response`).

### Scheduled Task for Inactive/Incomplete Sessions

The process is scheduled to run every 30 minutes using a cron job. During each execution, it performs the following steps:

1. **Find Inactive/Incomplete Sessions**:
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

## Flow chart representation of the process:
<img width="479" alt="Screenshot 2024-07-02 at 10 26 31 AM" src="https://github.com/AgrI-Mitra/docs/assets/130033232/5a74f996-44ca-4c07-9d3d-ccb6acdbf780">

