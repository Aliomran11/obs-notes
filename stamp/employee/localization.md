# Multi-language Support

## Implementation
- Language detected from `accept-language` header
- Messages fetched using `getMessages(lang)`
- Dynamic field selection (nameEn/nameAr)

## Supported Fields
- Names (first/last)
- Job titles
- Nationality
- Violation descriptions
- System messages

## Response Formatting
- Dates formatted as YYYY-MM-DD
- Field names standardized (no language suffixes)
- Violation statuses localized