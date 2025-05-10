
## 3. Database Schema
**Filename**: `SCHEMA.md`  
**Location**: `/employee/docs/`

```markdown
# Employee Schema

```javascript
{
  // Identification
  nameEn: String,
  nameAr: String,
  firstNameEn: String,
  firstNameAr: String,
  lastNameEn: String,
  lastNameAr: String,
  
  // Employment Details
  jobTitleEn: String,
  jobTitleAr: String,
  employmentType: String, // enum: ['دوام كامل', 'دوام جزئي']
  experienceYears: Number,
  company: ObjectId, // Ref to Company
  
  // Contact Information
  phoneNumber: String, // unique
  email: String,
  address: String,
  
  // Documents
  passportNumber: String,
  idNumber: String, // unique
  contractFile: String, // GCS URL
  
  // Status
  status: String, // enum: ['نشط', 'منتهي']
  constractStatus: String,
  visaStatus: String,
  stayStatus: String,
  
  // Dates
  startDate: String,
  endDate: String,
  contractTime: String,
  
  // Violations
  violations: [{
    descriptionEn: String,
    descriptionAr: String,
    status: String, // enum: ['محلول','معلق','لم يحل']
    date: Date
  }],
  
  // Additional Info
  nationalityEN: String, // enum from nationalitiesEn
  nationalityAr: String, // enum from nationalities
  gendar: String, // enum: ['ذكر','أنثى']
  maritalStatus: String, // enum: ['أعزب','متزوج','مطلق','أرمل']
  religion: String, // enum: ['مسلم','مسيحي','يهودي']
  countryOfResidence: String,
  countryOfBirth: String,
  
  // Timestamps
  createdAt: Date,
  updatedAt: Date
}