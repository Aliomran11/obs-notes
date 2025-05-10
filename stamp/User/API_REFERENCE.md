# User API Endpoints

## Base URL
`http://[host]:[port]/user`

## Authentication
JWT Bearer token required for all endpoints except registration/login

### 1. User Registration
`POST /register`
- **Fields**: All required schema fields
- **Response**: User object (without password)

### 2. User Login
`POST /login`
- **Fields**: email, password
- **Response**: JWT token

### 3. Get User Profile
`GET /profile`
- **Permissions**: Authenticated users
- **Response**: Localized user data

### 4. Update User
`PUT /:id`
- **Permissions**: Self or admin
- **Fields**: Any updatable fields

### 5. Delete User
`DELETE /:id`
- **Permissions**: Self or admin