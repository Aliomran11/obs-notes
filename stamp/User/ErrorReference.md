## Status Codes

- 400: Validation errors
    
- 401: Unauthenticated
    
- 403: Forbidden
    
- 404: User not found
    
- 500: Server error
##  Error Reference
**Filename**: `ERRORS.md`  
**Location**: `/user/docs/`

```markdown
# Error Handling

## Common Errors
```json
{
  "code": "DUPLICATE_EMAIL",
  "message": "Email already registered",
  "field": "email"
}

{
  "code": "INVALID_ROLE",
  "message": "Role must be one of: user,admin,superAdmin,editor"
}

{
  "code": "AUTH_FAILED",
  "message": "Invalid email or password"
}