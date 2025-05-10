# Multi-language Support

## Localized Fields
- nameEn/nameAr
- job_titleEn/job_titleAr

## Response Strategy
- Detect language from `accept-language` header
- Return appropriate field version
- Fallback to English if unspecified

## Example Response
```json
{
  "name": "Ahmed",       // Localized based on request
  "job_title": "Manager" // Localized based on request
}