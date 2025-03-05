# Request Payment API

## Endpoint
**Method:** `GET` or `POST`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/request`

## Request Parameters

| Parameter     | Type   | Required | Description |
|--------------|--------|----------|-------------|
| `userId`     | String | Yes      | The Telegram ID of the user receiving the request. |
| `requesterId` | String | Yes      | The Telegram ID of the user making the request. |
| `pin`        | String | Yes      | The PIN of the requester for authentication. |
| `amount`     | Number | Yes      | The amount being requested. |
| `note`       | String | No       | A message or reason for the payment request. |

### Example Request
```http
GET https://api.bots.business/v2/bots/1914078/web-app/request?userId=123456789&requesterId=987654321&pin=123456&amount=150&note=Pay%20this%20amount
```

#### Example Request (JSON - for POST)
```json
{
  "userId": "123456789",
  "requesterId": "987654321",
  "pin": "123456",
  "amount": 150,
  "note": "Pay this amount."
}
```

---

## Success Response

```json
{
  "status": "success",
  "msg": "Your payment request has been sent successfully!",
  "requestId": "gPFZZmnv",
  "amount": "150",
  "userId": "7378059553",
  "note": "Pay this amount."
}
```

### Success Response Fields

| Field      | Type    | Description |
|------------|--------|-------------|
| `status`   | String | API response status (`success`). |
| `msg`      | String | Confirmation message for successful request. |
| `requestId` | String | Unique ID for tracking the payment request. |
| `amount`   | String | Requested payment amount. |
| `userId`   | String | Telegram ID of the requester. |
| `note`     | String | Message attached to the payment request. |

---

## Error Response Example

```json
{
  "status": "error",
  "msg": "Incorrect PIN.\n\nPlease enter the correct PIN. You can retrieve your PIN by sending:\n`/myPin`"
}
```

### Error Response Fields

| Field     | Type   | Description |
|-----------|--------|-------------|
| `status`  | String | API response status (`error`). |
| `msg`     | String | Error message explaining the issue. |

---

## Notes
- This API supports both **GET** and **POST** methods.
- The **PIN** is required for authentication.
- If the **PIN** is incorrect, an error message is returned.
- The `requestId` can be used to track the payment request.
- The optional `note` parameter allows users to include a message with their request.
