# API Documentation

## POST /users/register

### Description
This endpoint registers a new user. It validates the incoming data and creates a new user record if validations pass.

### Request Body
- `fullname`: An object containing:
  - `firstname`: (string, required) Must be at least 3 characters.
  - `lastname`: (string, optional) Minimum 3 characters if provided.
- `email`: (string, required) Must be a valid email.
- `password`: (string, required) Must be at least 6 characters.

**Example:**
```json
{
  "fullname": {
    "firstname": "John",
    "lastname": "Doe"
  },
  "email": "john.doe@example.com",
  "password": "secret123"
}
```

### Responses

- **201 Created**
  - User successfully registered.
  - Response includes a token and user information.
  
- **400 Bad Request**
  - Data validation errors or if the user already exists.
  - Response includes errors or a message detailing the issue.

### Example Response
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "_id": "60d0fe4f5311236168a109ca",
    "fullname": {
      "firstname": "Rajat",
      "lastname": "Kuamr"
    },
    "email": "rajat@email.com"
  }
}
```
