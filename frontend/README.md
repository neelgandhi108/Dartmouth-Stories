# Frontend Application Hosting
The frontend application, constructed with NextJS, resides in App Runner. The App Runner container is granted permissions to interact with the DynamoDB table to access stories. Stories are automatically purged from the table after 2 days due to TTL settings.
