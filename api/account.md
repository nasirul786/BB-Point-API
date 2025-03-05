# Get Account API

## Endpoint
**Method:** `GET` or `POST`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/account`

## Query Parameters

| Parameter   | Type   | Required | Description |
|------------|--------|----------|-------------|
| `user_id`  | String | Yes      | The unique ID of the user. |
| `user_name` | String | No       | The username of the account owner. |

### Example Request
```http
GET https://api.bots.business/v2/bots/1914078/web-app/account?user_id=7378059553&user_name=elon%02mask
```

---

## Response

```json
{
  "status": "success",
  "balance": 480,
  "qr_code": "https://quickchart.io/qr?text=%7B%22userId%22%3A%207378059553%2C%20%22title%22%3A%20%22elon%02mask%22%7D",
  "total": "47.00",
  "transactions": [
    {
      "amount": 10,
      "with": 7378059553,
      "note": "Payment for test",
      "date": "04/03/2025",
      "type": "invoice payment",
      "direction": "credit"
    },
    {
      "amount": 10,
      "with": "7378059553",
      "note": "Payment for test",
      "date": "04/03/2025",
      "type": "invoice payment",
      "direction": "debit"
    },
    {
      "amount": 3,
      "with": 7463617963,
      "note": "Pay pls",
      "date": "04/03/2025",
      "type": "request payment",
      "direction": "credit"
    },
    {
      "amount": 11,
      "with": "Gift Creation",
      "date": "04/03/2025",
      "type": "gift created",
      "direction": "debit"
    },
    {
      "amount": 13,
      "with": "Gift Claim",
      "date": "04/03/2025",
      "type": "gift claim",
      "direction": "credit"
    }
  ]
}
```

---

## Response Fields

### Main Fields

| Field       | Type    | Description |
|------------|--------|-------------|
| `status`   | String | API response status (`success` or `error`). if error, an `msg` field will be available with error description |
| `balance`  | Number | User's current balance. |
| `qr_code`  | String | QR code URL for receiving payment. |
| `total`    | String | Total transaction amount. |
| `transactions` | Array | List of the last 5 transactions. |

### Transactions Object

| Field       | Type    | Description |
|------------|--------|-------------|
| `amount`   | Number | Transaction amount. |
| `with`     | String/Number | User or entity involved in the transaction. |
| `note`     | String | Optional transaction note. |
| `date`     | String | Transaction date (DD/MM/YYYY). |
| `type`     | String | Transaction type (e.g., invoice payment, gift created). |
| `direction` | String | Indicates if it's a `credit` (incoming) or `debit` (outgoing). |

---

## Notes
- This API supports both **GET** and **POST** methods.
- The response contains **only the last 5 transactions**.
- The `qr_code` contains the account holder name and id, can be send payment by scanning from the App
