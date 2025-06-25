# 🛒 Create Shop Question API 
#### ✅ Endpoint
```http
Method: POST  http://localhost:8000/api/v1/shop-question/create
```
#### 📥 Request Body
```json
{
  "questionText": "What is your housing status?",
  "screenNumber": "1",
  "fieldType": "SL",
  "minLength": 1,
  "maxLength": 200,
  "isRequired": "1",
  "options": ["other", "owned"]
}
```
#### 📤 Response (Success)
```json
{
  "success": true,
  "message": "Question created",
  "data": {
    "id": 7,
    "questionText": "What is your housing status?",
    "screenNumber": "1",
    "fieldType": "SL",
    "minLength": 1,
    "maxLength": 200,
    "isRequired": "1",
    "options": [
      { "key": "other", "value": "Other" },
      { "key": "owned", "value": "Owned" }
    ],
    "isActive": "1",
    "createdAt": "2025-06-25T10:40:00.000Z",
    "updatedAt": "2025-06-25T10:40:00.000Z"
  }
}
```
---


# OLD
#### 📥 Request Body
```json
{
  "questionText": "check",
  "screenNumber": "1",
  "fieldType": "SL",
  "minLength": 1,
  "maxLength": 4735,
  "isRequired": "1",
"options": [{"key": "rented", "value": "Rented"},{"key": "owned", "value": "Owned"},{"key": "parental", "value": "Parental"},{"key": "other", "value": "Other"}]
}
```
#### 📤 Response (Success)
```json
{
    "success": true,
    "message": "Question created",
    "data": {
        "id": 6,
        "questionText": "check",
      "❌options": "[{\"key\":\"rented\",\"value\":\"Rented\"},{\"key\":\"owned\",\"value\":\"Owned\"},{\"key\":\"parental\",\"value\":\"Parental\"},{\"key\":\"other\",\"value\":\"Other\"}]", 
        "isRequired": "1",
        "screenNumber": "1",
        "fieldType": "SL",
        "minLength": 1,
        "maxLength": 4735,
        "isActive": "1",
        "updatedAt": "2025-06-25T10:53:31.729Z",
        "createdAt": "2025-06-25T10:53:31.729Z"
    }
}
```







