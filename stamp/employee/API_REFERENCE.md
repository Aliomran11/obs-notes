# Employee API Reference

## Base URL
`http://[host]:[port]/employee`

## Authentication
Required for all endpoints via JWT in Authorization header

## Endpoints

### 1. Add/Update Employee
`POST /add-employee`
- **Permissions**: Admin/Super Admin
- **Request Format**: multipart/form-data
- **Fields**:
  - employeeId (string, optional): For updates
  - All employee fields (see schema)
  - contractFile (file): PDF contract

### 2. Update Employee
`PUT /update-employee/:id`
- **Permissions**: Admin/Super Admin
- **Request Format**: multipart/form-data
- **Fields**: All updatable employee fields

### 3. Add Violation
`PUT /add-violation/:id`
- **Permissions**: Admin/Super Admin
- **Body**:
  ```json
  {
    "descriptionEn": "string",
    "descriptionAr": "string",
    "status": "enum['محلول','معلق','لم يحل']"
	  }
	  
	  ```
```



_-__
### 4. List Employees

`GET /employees/:companyId`

- **Permissions**: Admin/Super Admin
    
- **Query Params**:
    
    - search: General search term
        
    - status: Filter by status
        
    - visaStatus: Filter by visa status
        
    - etc. (all employee fields filterable)
        

### 5. Get Employee

`GET /employee/:id`

- **Permissions**: Admin/Super Admin
    

### 6. Delete Employee

`DELETE /delete-employee/:id`

- **Permissions**: Admin/Super Admin
    

### 7. Update Violations

`PUT /update-violations/:id`

- **Permissions**: Admin/Super Admin
    
- **Body**: Complete violations array
    

Copy

Download