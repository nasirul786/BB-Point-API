# Claim Gift API

## Endpoint
**Method:** `POST` (Recommended) or `GET`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/claim-gift`

## Request Parameters

| Parameter   | Type    | Required | Description |
|------------|---------|----------|-------------|
| `giftCode` | String  | Yes      | The unique code of the gift being claimed. |
| `userId`   | String  | Yes      | The Telegram ID of the user claiming the gift. |
| `password` | String  | No (Required only for protected gifts) | The password set by the creator for restricted gifts. |

### Example Request (JSON - for POST)
```json
{
  "giftCode": "A1B2C3D4",
  "userId": "987654321",
  "password": "secure123"
}
```

### Example Request (GET)
```http
GET https://api.bots.business/v2/bots/1914078/web-app/claim-gift?giftCode=A1B2C3D4&userId=987654321&password=secure123
```

---

## Success Response

```json
{
    "status": "success",
    "msg": "🎉 Gift successfully claimed!",
    "claimDetails": {
        "giftCode": "IPAOJLO9",
        "title": "Birthday Gift",
        "description": "Happy Birthday! 🎉",
        "amountReceived": 1,
        "totalUsers": 5,
        "remainingClaims": 4
    }
}
```

### Success Response Fields

| Field            | Type    | Description |
|-----------------|--------|-------------|
| `status`        | String | API response status (`success`). |
| `msg`           | String | Confirmation message for successful claim. |
| `claimDetails`  | Object | Contains details of the claimed gift. |
| `giftCode`      | String | Unique code of the gift. |
| `title`         | String | Title of the gift. |
| `description`   | String | Message attached to the gift. |
| `amountReceived` | Number | Amount received by the user. |
| `totalUsers`    | Number | Total number of users allowed to claim the gift. |
| `remainingClaims` | Number | Number of claims left for the gift. |

---

## Error Response Example

```json
{
    "status": "error",
    "msg": "❌ You have already claimed this gift."
}
```

### Error Response Fields

| Field     | Type   | Description |
|-----------|--------|-------------|
| `status`  | String | API response status (`error`). |
| `msg`     | String | Error message explaining the issue. |

---

## Notes
- This API supports both **GET** and **POST** methods, but **POST is recommended** for security.
- If the gift is password-protected, the `password` field must be provided.
- A user can only claim a gift once.
- If the gift has already been fully claimed, the request will fail.
- If required parameters are missing, an error message will be returned.
