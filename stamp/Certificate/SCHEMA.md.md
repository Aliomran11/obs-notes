# Certificate Schema

```javascript
{
  // Organization Information
  orgNameEn: String,    // English organization name
  orgNameAr: String,    // Arabic organization name
  orgAddressEn: String, // English address
  orgAddressAr: String, // Arabic address
  
  // Certificate Details
  certNameEn: String,   // English certificate name
  certNameAr: String,   // Arabic certificate name
  certNumber: String,   // Unique certificate number
  expiryDate: String,   // ISO date string or 'لا يوجد'
  
  // Relationships
  company: ObjectId,    // Reference to Company model
  userId: ObjectId,     // Reference to uploading User
  
  // File Storage
  certificateFile: String, // GCS public URL
  
  // Automatic Fields
  createdAt: Date,
  updatedAt: Date
}