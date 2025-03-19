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

## POST /users/login

### Description
This endpoint logs in an existing user. It validates the provided credentials and returns a token along with user information if authenticated.

### Request Body
- `email`: (string, required) Must be a valid email.
- `password`: (string, required) Must be at least 6 characters.

**Example:**
```json
{
  "email": "john.doe@example.com",
  "password": "secret123"
}
```

### Responses

- **200 OK**
  - Successfully logged in.
  - Response includes a token and user details.
  
- **400 Bad Request**
  - Data validation errors; response includes details about the issues.
  
- **401 Unauthorized**
  - Incorrect email or password; response contains an error message.

## POST /captains/register

### Description
This endpoint registers a new captain. It validates the incoming data and creates a new captain record if validations pass.

### Request Body
- `fullname`: An object containing:
  - `firstname`: (string, required) Must be at least 3 characters.
  - `lastname`: (string, optional)
- `email`: (string, required) Must be a valid email.
- `password`: (string, required) Must be at least 6 characters.
- `vehicle`: An object containing:
  - `color`: (string, required) Must be at least 3 characters.
  - `plate`: (string, required) Must be at least 3 characters.
  - `capacity`: (number, required) Must be at least 1.
  - `vehicleType`: (string, required) Must be one of `car`, `motorcycle`, or `auto`.

**Example:**
```json
{
  "fullname": {
    "firstname": "Alice",
    "lastname": "Smith"
  },
  "email": "alice.smith@example.com",
  "password": "securePass123",
  "vehicle": {
    "color": "Red",
    "plate": "XYZ123",
    "capacity": 4,
    "vehicleType": "car"
  }
}
```

### Responses

- **201 Created**
  - Captain successfully registered.
  - Response includes a token and captain information.

- **400 Bad Request**
  - Validation errors or if the captain already exists.
  - Response includes error details.
