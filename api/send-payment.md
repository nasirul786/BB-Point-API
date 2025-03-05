# Send Payment API

## Endpoint
**Method:** `GET` or `POST`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/send`

## Request Parameters

| Parameter   | Type    | Required | Description |
|------------|---------|----------|-------------|
| `fromUser` | String  | Yes      | The Telegram ID of the sender. |
| `pin`      | String  | Yes      | The sender's authentication PIN. |
| `toUser`   | String  | Yes (Only if `invoiceId` is not provided) | The Telegram ID of the recipient. |
| `amount`   | Number  | Yes (Only if `invoiceId` is not provided) | The amount to be sent. |
| `note`     | String  | No       | Optional message with the payment. |
| `invoiceId` | String | Yes (If paying an invoice) | The ID of the invoice being paid. |

### Example Requests

#### **1. Sending Payment Without Invoice**
```http
GET https://api.bots.business/v2/bots/1914078/web-app/send?fromUser=7378059553&pin=pin786&toUser=7463617963&amount=5&note=test
```

#### **2. Paying an Invoice**
```http
GET https://api.bots.business/v2/bots/1914078/web-app/send?fromUser=7378059553&pin=pin786&invoiceId=INVOICE_ID
```

---

## Success Response

```json
{
  "status": "success",
  "msg": "✅ Transaction completed successfully! Sent 5 BBP to user ID: 7463617963."
}
```

### Success Response Fields

| Field     | Type    | Description |
|-----------|--------|-------------|
| `status`  | String | API response status (`success`). |
| `msg`     | String | Confirmation message for successful transaction. |

---

## Error Response Example

```json
{
  "status": "error",
  "msg": "Invalid invoiceId."
}
```

### Error Response Fields

| Field     | Type   | Description |
|-----------|--------|-------------|
| `status`  | String | API response status (`error`). |
| `msg`     | String | Error message explaining the issue. |

---

## Notes
- **GET and POST** methods are supported.
- If an `invoiceId` is provided, only `fromUser`, `pin`, and `invoiceId` are required.  
- When paying an invoice, `toUser` and `amount` should **not** be included.
- The optional `note` field can be added when sending a direct payment.
- If any required fields are missing, an error message will be returned.
