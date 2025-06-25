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







# 🐞 API Consistency & Data Format Bug Report

This document outlines current known inconsistencies and data format issues across CRUD operations in the Shop Question API.

---
## 🚧 1. CREATE Endpoint Bugs
### 1. `screenNumber` Type Inconsistency
- `"screenNumber": "1"` is passed as a string.
- ✅ **Fix:** Unify to number type (`screenNumber: 1`) for consistency.

### 2. `options` Stored as JSON String Instead of Array
```json
❌ "options": "[{\"key\":\"rented\",\"value\":\"Rented\"}]"
```
- Stored as a **stringified JSON** instead of a real JSON array.
- ✅ **Fix:** Store `options` as native JSON array using `Sequelize.JSON` or equivalent type.

---

## 📖 2. READ/List Endpoint Bugs

### 1. `isRequired` Type Inconsistency
| Action    | Value Returned |
|-----------|----------------|
| Create/Update | `"1"` or `"0"` *(string)* |
| Read/List     | `true` / `false` *(boolean)* ❌

- ✅ **Fix:** Return `isRequired` as consistent boolean or string in all endpoints.

### 2. Invalid `options` Format Cases
| Input Format                            | ❌ Problem                        | ✅ Fix                                 |
|-----------------------------------------|----------------------------------|----------------------------------------|
| `"options": "[{}, {}]"`                 | Options are empty objects        | Use real values or remove              |
| `"options": "[{\"key\":\"rented\"}]"` | Invalid stringified JSON format | Use actual array, not a JSON string    |
| `"options": []`                         | Empty options                    | Filter out blank entries on save/read  |

## 🛠 3. UPDATE Endpoint Bugs

### 1. `options` Field Format Bug
- Same issue as **CREATE**: stored as stringified JSON instead of array.
- ✅ **Fix:** Normalize and validate `options` as an array before saving.

## ❌ 4. DELETE Endpoint Bugs

### 1. Unvalidated Extra Fields Accepted
```json
// Accepted (but should be rejected)
{
  "id": 1,
  "questionText": "Test",
  "fieldType": "SL",
  "options": [ ... ]
}
```
- ❌ DELETE accepts full question object but only needs `id`.
- ✅ **Fix:** Validate request to allow only `id`, and reject extra fields.

## ✅ Recommendations Summary
- 🔁 Normalize `isRequired` as boolean in **all** endpoints.
- 🧹 Store `options` as proper JSON array (not string).
- 🧪 Add request validation to **CREATE**, **UPDATE**, and **DELETE** endpoints.
- 📦 Clean up unused or invalid `options` entries.
---







