# Webhook Notifications

## Overview
If a user has set a webhook URL in their settings, the bot will automatically send notifications for every transaction or event. The notifications will be sent as **POST** requests to the configured webhook URL.

## Event Format
Each event contains specific details about the transaction, including the `userId`, `amount`, `type`, `direction`, `date`, and other relevant fields.

---

## Webhook Event Types

### 1. Gift Created

```json
{
  "userId": "7378059553",
  "amount": 100,
  "type": "gift created",
  "direction": "debit",
  "date": "2025-03-05T12:34:56Z",
  "description": "Gift created successfully",
  "giftCode": "A1B2C3D4",
  "title": "Special Reward",
  "totalRecipients": 5,
  "prizePerUser": 20
}
```

| Field           | Type    | Description |
|----------------|--------|-------------|
| `userId`       | String | Telegram ID of the user who created the gift. |
| `amount`       | Number | Total amount allocated for the gift. |
| `type`         | String | Event type (`gift created`). |
| `direction`    | String | `debit` (amount deducted). |
| `date`         | String | Timestamp of the event (ISO format). |
| `description`  | String | Message about the gift creation. |
| `giftCode`     | String | Unique code for the created gift. |
| `title`        | String | Title of the gift. |
| `totalRecipients` | Number | Total users allowed to claim the gift. |
| `prizePerUser` | Number | Amount each recipient will receive. |

---

### 2. Claim Gift

```json
{
  "userId": 7378059553,
  "amount": 100,
  "type": "gift claim",
  "direction": "credit",
  "date": "2025-03-06T14:30:00.000Z",
  "description": "Gift claimed successfully",
  "giftCode": "ABC123"
}
```

| Field       | Type    | Description |
|------------|--------|-------------|
| `userId`   | String | Telegram ID of the user claiming the gift. |
| `amount`   | Number | Amount received from the gift. |
| `type`     | String | Event type (`gift claim`). |
| `direction` | String | `credit` (amount received). |
| `date`     | String | Timestamp of the event. |
| `description` | String | Message about the gift claim. |
| `giftCode` | String | Unique code of the claimed gift. |

---

### 3. Send Payment

```json
{
  "userId": 7378059553,
  "amount": 50,
  "type": "online pay",
  "direction": "debit",
  "date": "2025-03-06T14:30:00.000Z",
  "description": "Payment for services",
  "toUser": 519829299
}
```

| Field       | Type    | Description |
|------------|--------|-------------|
| `userId`   | String | Sender's Telegram ID. |
| `amount`   | Number | Amount sent. |
| `type`     | String | Event type (`online pay`). |
| `direction` | String | `debit` (amount deducted). |
| `date`     | String | Timestamp of the event. |
| `description` | String | Message about the payment. |
| `toUser`   | String | Receiver's Telegram ID. |

---

### 4. Receive Payment

```json
{
  "userId": 519829299,
  "amount": 50,
  "type": "online pay",
  "direction": "credit",
  "date": "2025-03-06T14:30:00.000Z",
  "description": "Payment received from user",
  "fromUser": 7378059553
}
```

| Field       | Type    | Description |
|------------|--------|-------------|
| `userId`   | String | Receiver's Telegram ID. |
| `amount`   | Number | Amount received. |
| `type`     | String | Event type (`online pay`). |
| `direction` | String | `credit` (amount added). |
| `date`     | String | Timestamp of the event. |
| `description` | String | Message about the received payment. |
| `fromUser` | String | Sender's Telegram ID. |

---

### 5. Accept Payment Request (Sender)

```json
{
  "amount": 50,
  "type": "request payment",
  "direction": "debit",
  "date": "2025-03-06T12:30:45Z",
  "description": "Payment for services",
  "fromUser": 7378059553,
  "toUser": 519829299
}
```

| Field       | Type    | Description |
|------------|--------|-------------|
| `amount`   | Number | Amount paid. |
| `type`     | String | Event type (`request payment`). |
| `direction` | String | `debit` (amount deducted). |
| `date`     | String | Timestamp of the event. |
| `description` | String | Message about the payment. |
| `fromUser` | String | Sender's Telegram ID. |
| `toUser`   | String | Receiver's Telegram ID. |

---

### 6. Accept Payment Request (Receiver)

```json
{
  "amount": 50,
  "type": "request payment",
  "direction": "credit",
  "date": "2025-03-06T12:30:45Z",
  "description": "Payment for services",
  "fromUser": 7378059553,
  "toUser": 519829299
}
```

| Field       | Type    | Description |
|------------|--------|-------------|
| `amount`   | Number | Amount received. |
| `type`     | String | Event type (`request payment`). |
| `direction` | String | `credit` (amount added). |
| `date`     | String | Timestamp of the event. |
| `description` | String | Message about the payment. |
| `fromUser` | String | Sender's Telegram ID. |
| `toUser`   | String | Receiver's Telegram ID. |

---

## Webhook Setup
- To receive webhook notifications, users must set a webhook URL using the **Update Settings API**.
- Can be setup from the officialWeb app too, on the setting section it is availavle.
- The bot will send a **POST** request to the provided URL each time an event occurs.
- Users should ensure their webhook URL is accessible and correctly handles incoming JSON data.

---

## Notes
- Webhook events are sent in **real-time** whenever a transaction occurs.
- Each event contains a **direction** field (`credit` or `debit`) to indicate money flow.
- Developers should verify the `type` field to correctly handle each event.
- It is **recommended** to log webhook data for debugging and tracking.
