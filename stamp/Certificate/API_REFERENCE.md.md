# Certificate API Reference

## Base URL
`http://[host]:[port]/certificate`

## Authentication
Required for all endpoints via JWT in Authorization header

## Endpoints

### 1. Upload Certificate
`POST /upload`
- **Permissions**: Authenticated users
- **Request Format**: multipart/form-data
- **Fields**:
  - orgNameEn (required): Organization name (English)
  - orgNameAr (required): Organization name (Arabic)
  - orgAddressEn (required): Organization address (English)
  - orgAddressAr (required): Organization address (Arabic)
  - certNameEn (required): Certificate name (English)
  - certNameAr (required): Certificate name (Arabic)
  - certNumber (required): Certificate number
  - expiryDate: Expiration date (YYYY-MM-DD)
  - company (required): Associated company ID
  - certificate (required): PDF file

### 2. Get Company Certificates
`GET /certificates/:id`
- **Permissions**: Authenticated users
- **Response**: Sorted by expiry date with localized fields

### 3. Get All Certificates (Admin)
`GET /admin/certificates`
- **Permissions**: Super Admin only
- **Response**: All certificates with localized fields

### 4. Delete Certificate
`DELETE /certificates/:id`
- **Permissions**: Certificate owner or admin