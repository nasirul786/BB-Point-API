# Create Gift API

## Endpoint
**Method:** `POST` (Recommended) or `GET`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/create-gift`

## Request Parameters

| Parameter   | Type    | Required | Description |
|------------|---------|----------|-------------|
| `userId`   | String  | Yes      | The Telegram ID of the user creating the gift. |
| `pin`      | String  | Yes      | The user's PIN for authentication. |
| `amount`   | Number  | Yes      | The total amount to be distributed. |
| `note`     | String  | Yes      | A message attached to the gift. |
| `title`    | String  | Yes      | The title of the gift. |
| `totalUser` | Number | Yes      | The number of users who can claim the gift. |
| `password` | String  | No       | An optional password to restrict claims. |

### Example Request (JSON - for POST)
```json
{
  "userId": "12345678",
  "pin": "9876",
  "amount": 100,
  "note": "Happy Birthday! 🎉",
  "title": "Birthday Gift",
  "totalUser": 5,
  "password": "secure123"
}
```

### Example Request (GET)
```http
GET https://api.bots.business/v2/bots/1914078/web-app/create-gift?userId=12345678&pin=9876&amount=100&note=Happy%20Birthday!%20🎉&title=Birthday%20Gift&totalUser=5&password=secure123
```

---

## Success Response

```json
{
  "status": "success",
  "msg": "🎁 Gift successfully created!",
  "giftDetails": {
    "giftCode": "IPAOJLO9",
    "title": "Birthday Gift",
    "description": "Happy Birthday! 🎉",
    "totalUsers": 5,
    "prizePerUser": 1,
    "totalAmount": 5,
    "createdBy": "7378059553",
    "password": "No password set"
  }
}
```

### Success Response Fields

| Field         | Type    | Description |
|--------------|--------|-------------|
| `status`     | String | API response status (`success`). |
| `msg`        | String | Confirmation message for successful gift creation. |
| `giftDetails` | Object | Contains details of the created gift. |
| `giftCode`   | String | Unique code for the gift. |
| `title`      | String | Gift title. |
| `description` | String | Gift note/message. |
| `totalUsers` | Number | Total number of users who can claim the gift. |
| `prizePerUser` | Number | Amount each user will receive. |
| `totalAmount` | Number | Total distributed amount. |
| `createdBy`  | String | Telegram ID of the gift creator. |
| `password`   | String | Password for claiming the gift (if set). |

---

## Error Response Example

```json
{
  "status": "error",
  "msg": "❌ Missing required parameters: userId"
}
```

### Error Response Fields

| Field     | Type   | Description |
|-----------|--------|-------------|
| `status`  | String | API response status (`error`). |
| `msg`     | String | Error message explaining the issue. |

---

## Notes
- This API supports both **GET** and **POST** requests, but **POST is recommended** for better security.
- The **PIN** is required for authentication.
- The `password` parameter is optional but can restrict claims.
- If `totalUser` is greater than 1, the amount is split equally among claimants.
- If required parameters are missing, an error message is returned.
