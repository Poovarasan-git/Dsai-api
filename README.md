# 🛒 Create Shop Question API
Creates a new question for dynamic shop form input.
---

## ✅ Endpoint

```http
POST /shop-question/create
Content-Type: application/json
```

---

## 📥 Request Body

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


---

## 🔁 Backend Processing

## 📤 Response (Success)

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

## 🔍 Validation Rules

| Field         | Rule                                              |
|---------------|---------------------------------------------------|
| questionText  | Must be a non-empty string                        |
| screenNumber  | Should be numeric or convertible to number        |
| fieldType     | Must be one of `"SL"`, `"TX"`, etc.               |
| minLength     | Integer ≥ 0                                       |
| maxLength     | Integer ≥ minLength                               |
| isRequired    | Must be `"1"` or `"0"`                            |
| options       | Required only for `"SL"` fieldType                |

---

## ❌ Common Mistakes

| Input Format                        | ❌ Problem                              | ✅ Fix                              |
|-------------------------------------|-----------------------------------------|-------------------------------------|
| `"options": "[{}, {}]"`             | Options are empty objects               | Use real values or remove them      |
| `"options": "[{"key":"x"}]"`    | Invalid JSON string in string format    | Use array, not stringified JSON     |
| `"options": [""]`                   | Empty options                           | Filter out blank entries            |

---


