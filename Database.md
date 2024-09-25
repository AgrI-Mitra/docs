# Database Documentation
## Models
### conversation
- This model stores data related to conversations, including metadata such as context and state. Each conversation can have associated feedback.

  - id: A unique identifier for each conversation, stored as a UUID.
  - createdAt: Timestamp for when the conversation was created, defaults to the current time.
  - updatedAt: Timestamp for the most recent update, automatically set on update.
  - userId: A UUID representing the user who initiated the conversation.
  - context: JSON object storing any contextual information related to the conversation.
  - state: A string representing the current state of the conversation.
  - flowId: A string representing the flow identifier for the conversation.
  - feedback: An optional relation to the feedback model, indicating feedback associated with this conversation.
  - @@unique([id]): Ensures that the id field is unique for each record.
-----------
### User
- This model stores information about users who interact with the system.

  - id: A unique identifier for each user, stored as a UUID.
  - createdAt: Timestamp for when the user was created, defaults to the current time.
  - identifier: Optional string representing an identifier for the user (e.g., username or email).
  - isVerified: A boolean indicating whether the user is verified or not, defaults to false.
  - messages: A one-to-many relationship to the Message model, representing all messages sent by this user.
-----------
### Message
- This model stores individual messages exchanged between users and the system.

  - id: A unique identifier for each message, stored as a UUID.
  - createdAt: Timestamp for when the message was created, defaults to the current time.
  - text: Optional string storing the message text.
  - audio: Optional string storing an audio message.
  - type: A string indicating the type of message (e.g., text, audio).
  - userId: A UUID linking the message to a specific user.
  - user: A relation to the User model.
  - flowId: A string representing the flow identifier for the message.
  - reaction: An integer field representing the user’s reaction to the message, with a default value of 0.
  - messageType: Optional string field for classifying the type of message.
----------
### Metrics
- This model stores key performance metrics related to the system's operations.

  - id: An auto-incremented integer serving as the primary key.
  - createdAt: Timestamp for when the metric was recorded, defaults to the current time.
  - name: A unique string identifier for the metric.
  - value: A string representing the value of the metric.
----------
### feedback
- This model stores feedback information from users about the system, particularly regarding chatbot functionality, translation accuracy, and information provided.

  - id: An auto-incremented integer serving as the primary key.
  - conversation: An optional relation to the conversation model, representing feedback associated with a particular conversation.
  - conversationId: Optional UUID linking the feedback to a specific conversation.
  - translation: An integer rating (default 0) indicating the quality of translations.
  - information: An integer rating (default 0) representing the accuracy of the information provided.
  - chatbotFunctionality: An integer rating (default 0) representing the chatbot’s functionality.
  - feedback: Optional string field for additional feedback provided by the user.
