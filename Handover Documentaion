## PM KISAN Handover session 1
---
### 1. Architecture.
[[<img width="664" alt="Screenshot 2024-11-29 at 9 32 40 AM" src="https://gist.github.com/user-attachments/assets/fece6924-fe63-46a2-85d5-14d739b002db">](https://drive.google.com/file/d/15ERCcbI5Ugm264h6fTpgZklRPOgVGSxN/view)](https://drive.google.com/file/d/15ERCcbI5Ugm264h6fTpgZklRPOgVGSxN/view?usp=sharing
)

Xstate Diagram

```mermaid
stateDiagram-v2
    [*] --> checkStateAndJump
    checkStateAndJump --> getUserQuestion: currentState = "getUserQuestion"
    checkStateAndJump --> checkType1: currentState = "checkType1"
    checkStateAndJump --> confirmInput1: currentState = "confirmInput1"
    checkStateAndJump --> questionClassifier: currentState = "questionClassifier"
    checkStateAndJump --> askingAadhaarNumber: currentState = "askingAadhaarNumber"
    checkStateAndJump --> checkType2: currentState = "checkType2"
    checkStateAndJump --> confirmInput2: currentState = "confirmInput2"
    checkStateAndJump --> validatingAadhaarNumber: currentState = "validatingAadhaarNumber"
    checkStateAndJump --> askLastAaadhaarDigits: currentState = "askLastAaadhaarDigits"
    checkStateAndJump --> checkType4: currentState = "checkType4"
    checkStateAndJump --> confirmInput4: currentState = "confirmInput4"
    checkStateAndJump --> askingOTP: currentState = "askingOTP"
    checkStateAndJump --> checkType3: currentState = "checkType3"
    checkStateAndJump --> confirmInput3: currentState = "confirmInput3"
    checkStateAndJump --> validatingOTP: currentState = "validatingOTP"
    checkStateAndJump --> fetchingUserData: currentState = "fetchingUserData"
    checkStateAndJump --> error: currentState = "error"
    checkStateAndJump --> endFlow: currentState = "endFlow"

    getUserQuestion --> checkType1: USER_INPUT
    checkType1 --> confirmInput1: ifAudio
    checkType1 --> questionClassifier: else
    checkType1 --> error: onError
    confirmInput1 --> checkType1: USER_INPUT

    questionClassifier --> endFlow: ifConvoStarterOrEnder
    questionClassifier --> endFlow: ifInvalidClassifier
    questionClassifier --> checkIfOTPHasBeenVerified: else
    questionClassifier --> error: onError

    checkIfOTPHasBeenVerified --> fetchingUserData: ifOTPHasBeenVerified
    checkIfOTPHasBeenVerified --> askingAadhaarNumber: else

    askingAadhaarNumber --> checkType2: USER_INPUT
    checkType2 --> confirmInput2: ifAudio
    checkType2 --> validatingAadhaarNumber: else
    checkType2 --> error: onError
    confirmInput2 --> checkType2: USER_INPUT

    validatingAadhaarNumber --> askingAadhaarNumber: ifNotValidAadhaar
    validatingAadhaarNumber --> askLastAaadhaarDigits: ifMultipleAadhaar
    validatingAadhaarNumber --> askingAadhaarNumber: ifNoRecordsFound
    validatingAadhaarNumber --> askingAadhaarNumber: ifTryAgain
    validatingAadhaarNumber --> askingOTP: ifOTPSend
    validatingAadhaarNumber --> error: else

    askLastAaadhaarDigits --> checkType4: USER_INPUT
    checkType4 --> confirmInput4: ifAudio
    checkType4 --> validatingAadhaarNumber: else
    checkType4 --> error: onError
    confirmInput4 --> checkType4: USER_INPUT

    askingOTP --> checkType3: USER_INPUT
    checkType3 --> confirmInput3: ifAudio
    checkType3 --> validatingAadhaarNumber: resendOTP
    checkType3 --> validatingOTP: else
    checkType3 --> error: onError
    confirmInput3 --> checkType3: USER_INPUT

    validatingOTP --> askingOTP: ifInvalidOTP
    validatingOTP --> askingOTP: ifTryAgain
    validatingOTP --> fetchingUserData: else
    validatingOTP --> error: onError

    fetchingUserData --> endFlow: onDone
    fetchingUserData --> error: onError

    error --> endFlow: onDone
    endFlow --> [*]
```

### 2. Tech stack used.

- NodeJS (NestJS)
- Prisma
- Redis

### 3. Project setup.

To integrate BFF into your project, follow these steps:

1. Clone the repository.
```sh
git clone https://github.com/AgrI-Mitra/bff.git
```

2. Setting up the server

```sh
# Setup DB and Hasura
# For Local:
docker-compose -f ./docker-compose.local.yaml up -d --build
# For Server:
ocker-compose up -d

# Migrate Database
npx prisma migrate dev
# Due to a certain glitch in the matrix, doing it twice works for dev setup.

# Start dev server
yarn start:dev
```
[Deployment steps](https://github.com/AgrI-Mitra/docs/blob/main/deployment.md)

4. Deploy and run BFF to start orchestrating API calls and managing the conversation flow.
### 3. Code structure.
```
project-root/
│
├── src/
│   ├── common/
│   ├── global-services/
│   ├── modules/
│   ├── xstate/
|   ├── app.controller.ts
|   ├── app.module.ts
|   └── app.service.ts
|
└── prisma/
    ├── migrations/
    └── schema.prisma/
```
### 5. Overview of DB schema.
![prisma-erd (1)](https://gist.github.com/user-attachments/assets/144a0696-103c-48e5-87f1-68f4deada6ca)

Schema details: https://github.com/AgrI-Mitra/docs/blob/main/Database.md
### 6. Overview of APIs.

Backend APIs:
https://api.postman.com/collections/12306310-8d8d72c8-456d-4233-85c2-6d61d22f2164?access_key=PMAT-01JC2KXC1H3E85THTTS8CVB04G

External APIs:
1. Bhashini:
   https://api.postman.com/collections/12306310-1b450077-8f4e-447c-b7a7-7221263798ad?access_key=PMAT-01JC2N1WJSG6JTW91HK794E452
2. PM KISAN and Wadhwani:
   https://api.postman.com/collections/12306310-99206e81-40ae-41bc-af77-b0935067b5c8?access_key=PMAT-01JDV151RFKF5QQR3DGEEWM020

### 7. Methods to debug issues.

- Debugging via logs.
- Debugging through Xstate.
