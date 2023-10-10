# Backend application

Upon story creation, EventBridge emits events to multiple consumers (audio processing, image creation, and SNS), potentially resulting in race conditions. There may be instances where audio or images are not yet available when the user accesses the story. The application checks for the presence of audio and images, reverting to rendering only the story if this data is not yet accessible (owing to asynchronous processing). While this approach suffices for simple use cases, waiting for completion may necessitate exploration of patterns such as aggregators or step function workflows to manage state.

## Three DynamoDB Tables vs. One

The application, being relatively straightforward, utilizes three tables. The characters and scenes table experiences infrequent updates, while the stories table stores the generated stories. Scaling for numerous users demands thoughtful consideration of access patterns and table design.
