# apiauth

---

# 📚 API Endpoint Documentation

---

## 🔐 User Signup

**URL:** `/api/signup/`  
**Method:** `POST`  
**Description:** Registers a new user using `username`, `email`, and `password`.

### ✅ Request Body:

```json
{
  "username": "john",
  "email": "john@example.com",
  "password": "test1234"
}
```

### 🟢 Success Response:

**Status:** `201 Created`

```json
{
  "id": 1,
  "username": "john",
  "email": "john@example.com"
}
```

---

## 🔑 User Login (JWT Token)

**URL:** `/api/login/`  
**Method:** `POST`  
**Description:** Authenticates a user and returns access + refresh JWT tokens.

### ✅ Request Body:

```json
{
  "username": "john",
  "password": "test1234"
}
```

### 🟢 Success Response:

**Status:** `200 OK`

```json
{
  "refresh": "eyJ0eXAiOiJKV1QiLCJh...",
  "access": "eyJ0eXAiOiJKV1QiLCJh..."
}
```

### 🔴 Error Response:

**Status:** `401 Unauthorized`

```json
{
  "detail": "No active account found with the given credentials"
}
```

---

## ♻️ Refresh Token

**URL:** `/api/token/refresh/`  
**Method:** `POST`  
**Description:** Takes in a valid refresh token and returns a new access token.

### ✅ Request Body:

```json
{
  "refresh": "<your_refresh_token>"
}
```

### 🟢 Success Response:

**Status:** `200 OK`

```json
{
  "access": "new_access_token_here"
}
```

---

## 👤 Get User Profile

**URL:** `/api/profile/`  
**Method:** `GET`  
**Description:** Returns the currently logged-in user's profile info.  
**Authentication:** Requires JWT access token.

### ✅ Headers:

```
Authorization: Bearer <access_token>
```

### 🟢 Success Response:

**Status:** `200 OK`

```json
{
  "id": 1,
  "username": "john",
  "email": "john@example.com",
  "date_joined": "2025-04-17T10:34:56.123Z"
}
```

### 🔴 Error Response:

**Status:** `401 Unauthorized`

```json
{
  "detail": "Authentication credentials were not provided."
}
```

---
