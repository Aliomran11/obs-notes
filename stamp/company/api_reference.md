# API Reference

## Base URL
`http://[host]:[port]/company`

## Authentication
Required for all endpoints via JWT in Authorization header

## Endpoints

### 1. Create Company
`POST /create-company`
- **Permissions**: Super Admin
- **Request Format**: multipart/form-data
- **Request Fields**:
  - nameEn (string): English company name
  - nameAr (string): Arabic company name
  - adminEmail (string): Admin user's email
  - commercialRegister (string)
  - startDate (date)
  - endDate (date)
  - cityEn (string)
  - cityAr (string)
  - typeEn (string)
  - typeAr (string)
  - employment_quota (number)
  - logo (file): Company logo image

### 2. Update Company
`PUT /update-company/:companyId`
- **Permissions**: Company Admin
- **Request Body**: JSON with fields to update

### 3. Get Company
`GET /get-company/:companyId`
- **Permissions**: Company Admin
- **Response**: Localized company data

### 4. Delete Company
`DELETE /delete-company/:companyId`
- **Permissions**: Super Admin

### 5. List Companies
`GET /get-company`
- **Permissions**: Super Admin
- **Response**: Array of localized company data