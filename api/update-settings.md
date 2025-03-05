# Update Settings API

## Endpoint
**Method:** `GET` or `POST`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/update-settings`

## Query Parameters

| Parameter             | Type    | Required | Description |
|-----------------------|--------|----------|-------------|
| `userId`             | String | Yes      | The user's Telegram ID. |
| `pin`               | String | Yes      | The PIN set by the user in the bot. |
| `newWebhook`         | String | No       | New URL for the webhook. |
| `acceptRequest`      | Boolean | No       | Whether the user accepts payment requests. |
| `transactionAnnounce` | Boolean | No       | Whether transaction announcements are enabled. |

### Example Request
```http
GET https://api.bots.business/v2/bots/1914078/web-app/update-settings?userId=7378059553&pin=pin786&newWebhook=https://mywebhook.com&acceptRequest=true&transactionAnnounce=false
```

---

## Success Response

```json
{
  "status": "success",
  "msg": "✅ Settings updated successfully."
}
```

### Success Response Fields

| Field     | Type   | Description |
|-----------|--------|-------------|
| `status`  | String | API response status (`success`). |
| `msg`     | String | Confirmation message for successful update. |

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
- At least one setting must be provided for an update.
- The **PIN** is required for authentication.
- If the **PIN** is incorrect, an error message will be returned.
- Multiple settings can be updated at once.
