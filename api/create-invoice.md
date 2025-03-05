# Create Invoice API

## Endpoint
**Method:** `POST` or `GET`

**URL:** `https://api.bots.business/v2/bots/1914078/web-app/new-invoice`

## Request Body

| Parameter    | Type   | Required | Description |
|-------------|--------|----------|-------------|
| `amount`    | Number | Yes      | The amount to be charged. |
| `userId`    | Number | Yes      | The user's Telegram ID. |
| `pin`       | String | Yes      | The PIN set by the user in the bot. |
| `description` | String | Yes   | Description of the invoice (e.g., purpose of payment). |
| `title`     | String | Yes      | Title of the invoice. |
| `payload`   | String | Yes      | Custom payload for tracking the payment. |

### Example Request (JSON)
```json
{
  "amount": 150,
  "userId": 123456789,
  "pin": "123456",
  "description": "Payment for premium subscription",
  "title": "Premium Plan",
  "payload": "user123-payment"
}
```

---

## Success Response

```json
{
  "status": "success",
  "invoice": {
    "qrCode": "https://quickchart.io/qr?text=%7B%22invoiceId%22%3A%22invoice-JJD0EOPJ%22%2C%22title%22%3A%22Test%20Payment%22%2C%22amount%22%3A%2210%22%7D",
    "invoiceId": "invoice-JJD0EOPJ",
    "title": "Test Payment",
    "amount": "10",
    "userId": "7378059553",
    "payLink": "https://t.me/bbp_app_bot?start=invoice-JJD0EOPJ",
    "description": "Payment for test",
    "status": "unpaid",
    "paidBy": null
  }
}
```

### Success Response Fields

| Field       | Type    | Description |
|------------|--------|-------------|
| `status`   | String | API response status (`success`). |
| `invoice`  | Object | Contains invoice details. |
| `qrCode`   | String | QR code to pay the invoice. |
| `invoiceId` | String | Unique ID of the generated invoice. |
| `title`    | String | Invoice title. |
| `amount`   | String | Amount to be paid. |
| `userId`   | String | User ID of the invoice creator. |
| `payLink`  | String | Telegram link to pay the invoice. |
| `description` | String | Description of the invoice. |
| `status`   | String | Payment status (`unpaid` or `paid`). |
| `paidBy`   | String / `null` | User ID of the payer (if paid). |

---

## Error Response Example

```json
{
  "status": "error",
  "msg": "Missing parameters: amount, pin"
}
```

### Error Response Fields

| Field     | Type   | Description |
|-----------|--------|-------------|
| `status`  | String | API response status (`error`). |
| `msg`     | String | Error message explaining the issue. |

---

## Notes
- This API supports **POST** and **GET** both requests. POST is recomnded.
- All parameters are required.
- The generated `payLink` redirects the user to Telegram for payment.
- The `qrCode` can be used to easily scan and pay the invoice.
- The invoice `status` will remain `unpaid` until the payment is completed.
