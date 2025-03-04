# BB Point WebApp API Documentation

Welcome to the BB Point WebApp API documentation. This API allows users to interact with the BB Point ecosystem by sending and requesting payments, managing invoices, creating and claiming gifts, purchasing BB Points, and retrieving or updating user account settings.

## Available APIs

### 1. Payment APIs
- **Send Payment**: Allows users to send BB Points to another user.
- **Request Payment**: Users can request a payment from another user.
- **Request Status**: Check the status of a pending payment request.

### 2. Invoice APIs
- **Create Invoice**: Generate an invoice for a specified amount.
- **Invoice Status**: Retrieve the status of an existing invoice.

### 3. Gift APIs
- **Create Gift**: Create a gift for a specific user or multiple users
- **Claim Gift**: Allows a user to claim an available gift.

### 4. BB Point Purchase API
- **Get Buy Link**: Purchase BB Points through available payment methods.

### 5. User & Settings APIs
- **Get User Account**: Retrieve details of a user’s BB Point account.
- **Get Settings**: Fetch application or user-specific settings.
- **Update Settings**: Modify user preferences or application configurations.

## Getting Started
To start using the API, authenticate your requests using your API key. Each request should include the appropriate request body.

For detailed request and response formats, refer to the specific API sections.

**Authorization**: userId and pin, your pin works as your api key.
