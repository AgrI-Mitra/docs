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

### Immediate Clearing on Session Completion
<img width="479" alt="Screenshot 2024-07-02 at 10 22 04 AM" src="https://github.com/AgrI-Mitra/docs/assets/130033232/cc3ced68-66fb-4037-9e11-d572d74b8a38">

### Incomplete/Inactive sessions
<img width="395" alt="Screenshot 2024-07-02 at 9 52 14 AM" src="https://github.com/AgrI-Mitra/docs/assets/130033232/3b95c085-4e12-4d9c-a73f-2d1c4c63ebb0">