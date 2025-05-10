
## 5. Error Reference
**Filename**: `ERROR_REFERENCE.md`  
**Location**: `/docs/`

```markdown
# Error Reference

## HTTP Status Codes
- 400: Bad Request (validation errors)
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 500: Internal Server Error

## Common Errors
```json
{
  "code": "DUPLICATE_FIELD",
  "message": "Company name already exists",
  "field": "nameEn",
  "value": "Test Company"
}

{
  "code": "FILE_UPLOAD_ERROR",
  "message": "Failed to process uploaded file"
}

{
  "code": "LANGUAGE_NOT_SUPPORTED",
  "message": "Requested language not available"
}