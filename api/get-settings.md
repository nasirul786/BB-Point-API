# Get Settings API

## Endpoint
**Method:** `GET` or `POST`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/settings`

## Query Parameters

| Parameter  | Type   | Required | Description |
|------------|--------|----------|-------------|
| `userId`   | String | Yes      | The user's Telegram ID. |
| `pin`      | String | Yes      | The PIN set by the user in the bot. |

### Example Request
```http
GET https://api.bots.business/v2/bots/1914078/web-app/settings?userId=7378059553&pin=pin786
```

---

## Success Response

```json
{
  "status": "success",
  "acceptRequest": true,
  "webhook": "Set now",
  "transactionAnnounce": true,
  "pin": "7866"
}
```

### Success Response Fields

| Field                | Type    | Description |
|----------------------|--------|-------------|
| `status`            | String | API response status (`success`). |
| `acceptRequest`     | Boolean | Whether the user accepts payment requests. |
| `webhook`          | String  | Webhook URL set by the user. |
| `transactionAnnounce` | Boolean | Whether transaction announcements are enabled. |
| `pin`              | String  | User's set PIN. |

---

## Error Response Example

```json
{
  "status": "error",
  "msg": "❌ Incorrect PIN. Use /myPin to retrieve it."
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
- If the **PIN** is incorrect, an error message will be returned.
