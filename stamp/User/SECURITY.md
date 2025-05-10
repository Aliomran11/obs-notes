# Authentication & Authorization

## Password Handling
- Uses bcryptjs with 10-round salt
- Plaintext password stored transiently during save
- Never returned in API responses

## Roles
1. **user**: Basic access
2. **editor**: Content management
3. **admin**: Company administration
4. **superAdmin**: Full system access

## Company Association
- Users can be linked to companies
- Company admins have scope-limited privileges
# Password Handling System

## Encryption Flow
1. User submits plaintext password
2. Mongoose pre-save hook triggers
3. Plaintext stored in `plainPassword` (transient)
4. bcrypt hashes password (10 rounds)
5. Hashed version stored in `password` field

## Security Notes
- Plaintext never persisted to database
- Hashing occurs before document save
- Comparison uses bcrypt.compare()
- Password strength should be validated pre-hash

## Reset Process
1. Generate temporary token
2. Store hashed token in DB
3. Email reset link with token
4. Verify token on reset endpoint
5. Apply standard hashing to new password