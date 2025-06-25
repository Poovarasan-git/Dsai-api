# 🛒 Create Shop Question API 
## 🔍 Validation Rules
| Field         | Rule                                              |
|---------------|---------------------------------------------------|
| questionText  | Must be a non-empty string & only allow text with ? (max: 250)              |
| screenNumber  | Should be numeric or convertible to number. (max : 5)      |
| fieldType     | Must be one of `"SL"`, `"TX"`, etc.               |
| minLength     | Integer > 0  ====> (1 to 5)                                  |
| maxLength     | Integer > minLength ====> (2 to 250)                            |
| isRequired    | Must be `"1"` or `"0"`                            |
| options       | Required only for `"SL"` fieldType                |
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
### OLD Method
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
# 🛒 LIST Shop Question API 
#### ✅ Endpoint
```http
Method: GET  http://localhost:8000/api/v1/shop-question/list
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
### OLD Method
## ❌ Common Mistakes

| Input Format                        | ❌ Problem                              | ✅ Fix                             |
|-------------------------------------|-----------------------------------------|-------------------------------------|
| `"options": "[{}, {}]"`             | Options are empty objects               | Use real values or remove them      |
| `"options": "[{"key":"rented"}]"`   | Invalid JSON string in string format    | Use array, not stringified JSON     |
| `"options": []`,                    | Empty options                           | Filter out blank                    |

#### 📥 Request Body ❌ Not Required
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
- screenNumber — Consider unifying types
- "screenNumber": "1" ← ❌ string
```json
{
    "success": true,
    "message": "Questions list fetched",
    "data": [
        {
            "id": 6,
            "❌screenNumber": "1",
            "questionText": "check",
            "fieldType": "SL",
            "options": [
                {
                    "key": "rented",
                    "value": "Rented"
                },
                {
                    "key": "owned",
                    "value": "Owned"
                },
                {
                    "key": "parental",
                    "value": "Parental"
                },
                {
                    "key": "other",
                    "value": "Other"
                }
            ],
            "minLength": 1,
            "maxLength": 4735,
            "isRequired": true,
            "isActive": "1",
            "createdAt": "2025-06-25T10:53:31.000Z",
            "updatedAt": "2025-06-25T10:53:31.000Z"
        },
        {
            "id": 4,
            "❌screenNumber": "1",
            "questionText": "What is your test",
            "fieldType": "SL",
            "❌options": [
                {},
                {}
            ],
            "minLength": 1,
            "maxLength": 4735,
            "isRequired": true,
            "isActive": "1",
            "createdAt": "2025-06-25T10:13:34.000Z",
            "updatedAt": "2025-06-25T10:13:34.000Z"
        },
        {
            "id": 2,
            "❌screenNumber": "1",
            "questionText": "What is your product",
            "fieldType": "TX",
            "❌options": [],
            "minLength": 1,
            "maxLength": 4735,
            "isRequired": true,
            "isActive": "1",
            "createdAt": "2025-06-25T09:31:09.000Z",
            "updatedAt": "2025-06-25T09:31:09.000Z"
        },
     
    ]
}
```

# 🛒 Update Shop Question API 
#### ✅ Endpoint
```http
Method: POST  http://localhost:8000/api/v1/shop-question/update
```
#### 📥 Request Body
```json
{
  "id":1,
  "questionText": "check update",
  "screenNumber": "1",
  "fieldType": "SL",
  "minLength": 1,
  "maxLength": 47,
  "isRequired": "1",
  "✅options": ["other", "owned"]
}
```
#### 📤 Response (Success)
```json
{
  "success": true,
  "message": "Question create",
  "data": {
    "id": 1,
    "questionText": "check update",
    "screenNumber": "1",
    "fieldType": "SL",
    "minLength": 1,
    "maxLength": 47,
    "isRequired": "1",
    "✅options": [
      { "key": "other", "value": "Other" },
      { "key": "owned", "value": "Owned" }
    ],
    "isActive": "1",
    "createdAt": "2025-06-25T10:40:00.000Z",
    "updatedAt": "2025-06-25T10:40:00.000Z"
  }
}
```
### OLD Method
#### 📥 Request Body
```json
{
  "id":1,
  "questionText": "check update",
  "screenNumber": "1",
  "fieldType": "SL",
  "minLength": 1,
  "maxLength": 47,
  "isRequired": "1",
  "❌options": [{"key": "rented", "value": "Rented"},{"key": "owned", "value": "Owned"},{"key": "parental", "value": "Parental"},{"key": "other", "value": "Other"}]
}
```
#### 📤 Response (Success)
```json
{
    "success": true,
    "message": "Question Updated",
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
# 🛒 DELETE Shop Question API 
#### ✅ Endpoint
```http
Method: DELETE  http://localhost:8000/api/v1/shop-question/delete
```
#### 📥 Request Body
```json
{
  "✅id": 1
}
```
#### 📤 Response (Success)
```json
{
    "success": true,
    "message": "Question deleted",
    "data": {
        "id": 1,
        "questionText": "check Delete",
        "isActive": "0",
        "updatedAt": "2025-06-25T12:34:08.203Z"
    }
}
```
### OLD Method
#### 📥 Request Body 
```json
{
  "✅id": 1,
  "❌questionText": "check Delete",
  "❌screenNumber": "1",
  "❌fieldType": "SL",
  "❌minLength": 1,
  "❌maxLength": 4735,
  "❌isRequired": "1",
 "❌options": [{"key": "rented", "value": "Rented"},{"key": "owned", "value": "Owned"},{"key": "parental", "value": "Parental"},{"key": "other", "value": "Other"}]
}
```
#### 📤 Response (Success)
```json
{
    "success": true,
    "message": "Question deleted",
    "data": {
        "id": 1,
        "questionText": "check Delete",
        "isActive": "0",
        "updatedAt": "2025-06-25T12:34:08.203Z"
    }
}
```







