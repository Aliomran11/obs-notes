# Database Schema

## Collections

### 1. Company
```javascript
{
  _id: ObjectId,
  nameEn: String,
  nameAr: String,
  adminEmail: ObjectId, // Reference to User
  commercialRegister: String,
  startDate: Date,
  endDate: Date,
  cityEn: String,
  cityAr: String,
  typeEn: String,
  typeAr: String,
  employment_quota: Number,
  logo: String, // File path
  createdAt: Date,
  updatedAt: Date
}


{
  _id: ObjectId,
  email: String,
  password: String,
  role: String, // 'admin' or 'superadmin'
  company_id: ObjectId, // Reference to Company
  // ... other user fields
}
	```
```


