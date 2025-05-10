# Error Handling

## Common Errors
```json
{
  "code": "DUPLICATE_FIELD",
  "message": "Phone number already exists",
  "field": "phoneNumber",
  "value": "+966501234567"
}

{
  "code": "FILE_UPLOAD_FAILED",
  "message": "Failed to upload contract file"
}

{
  "code": "INVALID_STATUS",
  "message": "Violation status must be one of: محلول,معلق,لم يحل"
}

## HTTP Status Codes
- 400: Validation errors
- 403: Authorization failure
- 404: Employee not found
- 500: Server/DB errors