# BB Point Purchase Link API

## Endpoint
**Method:** `GET` or `POST`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/buyLink`

## Request Parameters

| Parameter  | Type   | Required | Description |
|-----------|--------|----------|-------------|
| `userId`  | String | Yes      | The Telegram ID of the user purchasing BB Points. |
| `amount`  | Number | Yes      | The number of **stars** to be purchased (1 star = 2 BB Points). Must be a whole number. |

### Example Request
```http
GET https://api.bots.business/v2/bots/1914078/web-app/buyLink?userId=7378059553&amount=2
```

---

## Success Response

```json
{
  "status": "success",
  "msg": "✅ Invoice link generated successfully.",
  "link": "https://t.me/$O61XedY6QFa0AQAAebbvLmDMmKc"
}
```

### Success Response Fields

| Field     | Type    | Description |
|-----------|--------|-------------|
| `status`  | String | API response status (`success`). |
| `msg`     | String | Confirmation message for successful invoice generation. |
| `link`    | String | Telegram link where the user can pay star to purchase BB Points. |

---

## Error Response Example

```json
{
  "status": "error",
  "msg": "❌ Both userId and amount must be numeric, and amount must be a whole number."
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
- The **amount must be a whole number** (e.g., `2`, `5`, `10`) and **cannot have decimal points** (e.g., `2.5` is invalid).
- 1 **Star** = **2 BB Points**.
- Users can click the generated `link` to complete the purchase on Telegram.
- If the `userId` is invalid or the `amount` contains decimals, an error is returned.
