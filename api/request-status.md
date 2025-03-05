# Request Status API

## Endpoint
**Method:** `GET` or `POST`  
**URL:** `https://api.bots.business/v2/bots/1914078/web-app/request-status`

## Query Parameters

| Parameter   | Type   | Required | Description |
|------------|--------|----------|-------------|
| `requestId` | String | Yes      | The unique ID of the payment request. |

### Example Request
```http
GET https://api.bots.business/v2/bots/1914078/web-app/request-status?requestId=bjR2tUmB
```

---

## Success Response

```json
{
  "status": "pending",
  "requestId": "bjR2tUmB",
  "requesterId": 7378059553,
  "amount": "57",
  "note": "pay pls"
}
```

### Success Response Fields

| Field         | Type    | Description |
|--------------|--------|-------------|
| `status`     | String | Current status of the request (`pending`, `paid`, `cancelled`, or `error` for api error). |
| `requestId`  | String | Unique ID of the payment request. |
| `requesterId` | Number | Telegram ID of the user who made the request. |
| `amount`     | String | Requested payment amount. |
| `note`       | String | Message attached to the payment request. |

---

## Error Response Example

```json
{
  "status": "error",
  "msg": "Invalid request ID."
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
- Only `requestId` is required since no financial risk is involved.
- The `status` field will indicate whether the request is **pending**, **paid**, or **cancelled**.
- If the `requestId` is invalid, an error message is returned.
