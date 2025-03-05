# Invoice Status API

## Endpoint
**Method:** `GET` or `POST`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/invoice-status`

## Query Parameters

| Parameter   | Type   | Required | Description |
|------------|--------|----------|-------------|
| `invoiceId` | String | Yes      | The unique ID of the invoice. |
| `pin`       | String | Yes      | The PIN of the invoice creator. |

### Example Request
```http
GET https://api.bots.business/v2/bots/1914078/web-app/invoice-status?invoiceId=invoice-JJD0EOPJ&pin=123456
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
| `qrCode`   | String | QR code for the invoice. |
| `invoiceId` | String | Unique ID of the invoice. |
| `title`    | String | Invoice title. |
| `amount`   | String | Invoice amount. |
| `userId`   | String | User ID of the invoice creator. |
| `payLink`  | String | Telegram link to pay the invoice. |
| `description` | String | Invoice description. |
| `status`   | String | Payment status (`unpaid` or `paid`). |
| `paidBy`   | String / `null` | User ID of the payer (if paid). |

---

## Error Response Example

```json
{
  "status": "error",
  "msg": "Invoice has been paid already."
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
- The **PIN** is required to check the invoice status.
- If the **invoiceId** is invalid or the **PIN** is incorrect, an error is returned.
- The response contains the **current status** of the invoice (`unpaid` or `paid`).
- The `qrCode` and `payLink` can be used to facilitate payments.
