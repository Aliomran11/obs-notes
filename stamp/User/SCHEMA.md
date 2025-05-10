# User Schema

```javascript
{
  // Identification
  nameEn: String,      // English name (required)
  nameAr: String,      // Arabic name (required)
  email: String,       // Unique email (required)
  
  // Authentication
  password: String,    // Hashed password (required)
  plainPassword: String, // Unhashed password (transient)
  
  // Professional Details
  job_titleAr: String, // Arabic job title
  job_titleEn: String, // English job title
  
  // Location
  countryOfResidence: String,
  address: String,
  
  // Authorization
  role: String,        // enum: ['user','admin','superAdmin','editor']
  company_id: ObjectId // Reference to Company model
  
  // Automatic Timestamps
  createdAt: Date,
  updatedAt: Date
}