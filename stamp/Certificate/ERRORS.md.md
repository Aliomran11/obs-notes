# Error Handling Reference
## HTTP Status Codes

- 400: Invalid request (missing fields)
    
- 401: Unauthenticated
    
- 403: Forbidden (admin-only endpoints)
    
- 404: Certificate not found
    
- 500: Server/DB errors
## Common Errors
```json
{
  "code": "MISSING_FILE",
  "message": "Certificate file is required"
}

{
  "code": "STORAGE_ERROR",
  "message": "Failed to upload certificate file"
}

{
  "code": "INVALID_COMPANY",
  "message": "Specified company does not exist"
}